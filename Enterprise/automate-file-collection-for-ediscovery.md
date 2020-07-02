---
title: 電子情報開示用にファイル収集を自動化する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 概要:電子情報開示用にユーザーのコンピューターのファイル収集を自動化する方法について説明します。
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997978"
---
# <a name="automate-file-collection-for-ediscovery"></a>電子情報開示用にファイル収集を自動化する

All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel. 
  
eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.
  
Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.
  
## <a name="what-this-solution-does"></a>このソリューションで行うこと

This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery. 
  
> [!IMPORTANT]
> This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file. 
  
次の図は、ソリューションのすべての手順と要素を順を追って説明しています。
  
![自動ファイル コレクション ソリューションの概要](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|****凡例****||
|:-----|:-----|
|![マゼンタの吹き出し 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|グループ ポリシー オブジェクト (GPO) を作成し、コレクションのログオン スクリプトと関連付ける。  <br/> |
|![マゼンタの吹き出し 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)|   GPO セキュリティ フィルターを構成して、管理者グループにのみ GPO を適用する <br/> |
|![マゼンタの吹き出し 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|保管担当者がログオンし、GPO が実行され、コレクションのログオン スクリプトが呼び出される。  <br/> |
|![マゼンタの吹き出し 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|コレクションのログオン スクリプトは、保管担当者のコンピューターにローカルにアタッチされたドライブのすべてのインベントリを作成し、目的のファイルを検索し、その場所を記録します。  <br/> |
|![マゼンタの吹き出し 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|コレクションのログオン スクリプトは、ステージング サーバー上の非表示のファイル共有に、インベントリが作成されたファイルをコピーします。  <br/> |
|![マゼンタの吹き出し 6](media/99589726-0c7e-406b-a276-44301a135768.png)| (オプション A) PST インポート スクリプトを手動で実行して、収集した PST ファイルを Exchange Server 2013 にインポートします。 <br/> |
|![マゼンタの吹き出し 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(オプション B)Microsoft 365 インポートツールとプロセスを使用して、収集した PST ファイルを Exchange Online にインポートします。  <br/> |
|![マゼンタの吹き出し 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|MoveToColdStorageSystem Center Orchestrator 2012 R2 Runbook での長期保存用に、収集したファイルをすべて Azure ファイル共有に移動します。 <br/> |
|![マゼンタの吹き出し 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|SharePoint 2013 によりコールド ストレージ ファイル共有にファイルのインデックスを作成します。  <br/> |
|![マゼンタの吹き出し 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|コールド ストレージとオンプレミスの Exchange Server 2013 のコンテンツで eDiscovery を実行します。  <br/> |
|![マゼンタの吹き出し 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|Microsoft 365 のコンテンツに対して電子情報開示を実行します。  <br/> |
   
## <a name="prerequisites"></a>前提条件

The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.
  
### <a name="base-configuration"></a>基本構成

|**要素**|**リンク**|
|:-----|:-----|
|Active Directory ドメイン サービス (AD DS) ドメイン  <br/> ||
|オンプレミス ネットワークからのインターネット接続  <br/> ||
|SharePoint 2013 と System Center Orchestrator 2012 R2 をサポートする SQL Server 2012  <br/> |[System Center 2012 - Orchestrator の展開](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| eDiscovery 用のオンプレミスまたは Azure ベースの SharePoint 2013 (オプション A で必要) <br/> ||
|ステージング用のオンプレミス ファイル共有サーバー  <br/> ||
|オプション A の PST をインポートするためのオンプレミス Exchange Server 2013  <br/> |CU5 (15.913.22) は、「[CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)」で入手できます。  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[System Center 2012 - Orchestrator の展開](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Microsoft 365 E3 with Exchange Online および SharePoint Online (オプション B に必要)  <br/> |Microsoft 365 E3 サブスクリプションにサインアップするには、「 [microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab)」を参照してください。  <br/> |
|仮想マシンでの Azure サブスクリプション  <br/> |Azure にサインアップするには、「[Microsoft Azure をサブスクライブする](https://go.microsoft.com/fwlink/p/?LinkId=512010)」をご覧ください。 <br/> |
|オンプレミス ネットワークと Azure サブスクリプションの間の VPN 接続  <br/> |Azure サブスクリプションとオンプレミス ネットワークの間に VPN トンネルをセット アップするには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](https://go.microsoft.com/fwlink/p/?LinkId=613507)」をご覧ください。  <br/> |
|SharePoint 2013SharePoint と Exchange Server 2013、および必要に応じて Lync Server 2013 の間で検索するように eDiscovery を構成  <br/> |この方法で eDiscovery を構成するには、「[電子情報開示を構成する (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=613508)」および「[テスト ラボ ガイド: Exchange、Lync、SharePoint、Windows のファイル共有テスト ラボの電子情報開示を構成する](https://go.microsoft.com/fwlink/p/?LinkId=393130)」をご覧ください。  <br/> |
|Microsoft 365 の電子情報開示 (SharePoint Online および Exchange Online)  <br/> |Microsoft 365 で電子情報開示を構成するには、「 [SharePoint Online で電子情報開示センターをセットアップ](https://go.microsoft.com/fwlink/p/?LinkId=613628)する」を参照してください。  <br/> |
   
## <a name="configure-the-environment"></a>環境を構成する

基本構成の準備が整ったので、 ソリューション自体の構成に進むことができます。 
  
### <a name="staging-file-share"></a>ステージング ファイル共有

1. オンプレミス ドメインで、Custodians という名前のグローバル セキュリティ グループを作成します。
    
2. Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.
    
3. 次の共有アクセス許可を設定します。
    
  - 保管担当者:変更、読み取り
    
  - 管理者 :フル コントロール
    
  - Exchange Trusted Subsystem:変更、読み取り
    
4. Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:
    
  - **種類:拒否**
    
  - **適用対象:このフォルダー、サブフォルダー、およびファイル**
    
5. **[高度なアクセス許可]** をクリックし、以下を選びます。
    
  - **属性の読み取り**
    
  - **拡張属性の読み取り**
    
  - **アクセス許可の読み取り**
    
6. 以下を実行して、Cases$ ファイル共有にテスト アクセスします。
    
1. 保管担当者グループにユーザーを追加します。
    
2. Cases$ フォルダーにファイルを配置します。
    
3. As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.
    
4. Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.
    
5. Try to open the file you previously placed in the share. This should fail.
    
### <a name="logon-script"></a>ログオン スクリプト

1. この Windows PowerShell スクリプトをコピーして、メモ帳に貼り付けます。
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. 上記のスクリプトを、CollectionScript.ps1 として、C:\\AFCScripts などの見つけやすい場所に保存します。
    
3. Use the Go To feature in Notepad. Make the following changes, as needed:
    
|**行番号**|**変更するために必要な事柄**|**必須かどうか**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. <br/> |オプション  <br/> |
|76 と 77  <br/> |Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. <br/> |オプション  <br/> |
|80  <br/> |**$CaseRootLocation** 変数は、ステージング サーバー コレクション ファイル共有に設定する必要があります。例: **\\\\Staging\\Cases$** <br/> |必須  <br/> |
   
4. ドメイン コントローラーの Netlogon ファイル共有に CollectionScript.ps1 ファイルを配置します。 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>ログオン スクリプトと保管担当者グループの GPO を構成します。

1. トピック「[グループ ポリシーで起動、シャットダウン、ログオン、ログオフ スクリプトを使用する](https://go.microsoft.com/fwlink/p/?LinkId=614844)」の「ユーザー ログオン スクリプトを割り当てる方法」セクションに従って、保管担当者グループに対してログオン スクリプトを構成します。
    
2. **セキュリティ フィルター** から認証ユーザーを削除し、保管担当者グループを追加します。
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>PST インポートのオプション A (Exchange Server 2013 用のスクリプト)

1.  次の Windows PowerShell スクリプトをコピーして、メモ帳に貼り付けます。
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.
    
3. メモ帳の移動機能を使用して、必要に応じて次の変更を行います。
    
|**行番号**|**変更するために必要な事柄**|**必須かどうか**|
|:-----|:-----|:-----|
|12   <br/> |**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. <br/> |省略可能  <br/> |
|17   <br/> |**$ConnectionUri** は独自のサーバーに設定する必要があります。 <br/> > [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.          |必須  <br/> |
   
4. Exchange Trusted Subsystem アカウントに、\\\\Staging\\Cases$ 共有に対する読み取り、書き込み、実行のアクセス許可があることを確認します。
    
5. PST インポート スクリプトには、次の 2 つの入力パラメーターが必要です。
    
  - **$SourcePath** たとえば \\\\Staging\\Cases$ などの、インポートする PST ファイルの場所
    
  - **$MailboxAlias** インポートされたメール アイテムを受信するターゲット メールボックスのエイリアス
    
6. たとえば、すべての PST ファイルをパス \\Staging\Cases$ からエイリアス eDiscoveryMailbox を持つメールボックスにインポートする場合は、次のようなスクリプトを実行します `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`。
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST インポートのオプション B (Exchange Online の場合)

-  Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>コールド ストレージ

1. Azure Virtual Machine にファイル共有を作成します。ここに収集したすべてのファイルを配置します。例: \\\\AZFile1\\ContentColdStorage
    
2. Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).
    
3. PST ファイルを \\\\AZFile1\\ContentColdStorage からインポートすることを見込んでいる場合は、Exchange Trusted Subsystem に対して共有への読み取り、書き込み、実行のアクセス許可を付与します。
    
### <a name="orchestrator"></a>Orchestrator

1. Microsoft ダウンロード センターから、[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) をダウンロードします。
    
2. Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.
    
3. **[ファイルの場所]** ボックスで、インポートする Runbook のパスとファイル名を入力するか、省略記号 ( **...**) をクリックしてインポートするファイルを参照します。 
    
4. Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.
    
5. [ **完了**] をクリックします。
    
6. **MoveFilesToColdStorage** Runbook を次のように編集します。
    
1. **Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.
    
2. **[フォルダーの削除]** アクティビティ - **[パス]** をコレクション ファイル共有 (例: \\\\Staging\\cases$\\*) に設定し、 **[すべてのファイルとサブフォルダーを削除する]** を選びます。 
    
7. 「[Runbook の展開](https://go.microsoft.com/fwlink/p/?LinkId=615120)」にある手順を使用して、 **MoveToColdStorage** Runbook を展開します。
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>コールド ストレージ用 SharePoint オンプレミス検索

1. Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>ソリューションの使用

There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:
  
1. 保管担当者グループのユーザー メンバーシップを管理する。
    
2. Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them
    
3. PST のインポート プロセスを管理する。
    
4. コレクション ファイルをコールド ストレージに移動する。
    
他のすべての手順は、このソリューションに固有のものではありません。 SharePoint 2013、Microsoft 365、および Azure で実行する標準的な管理タスクです。 このソリューションでは、次のような会社のニーズに基づいて、解決する必要があるガイダンスが提供されていません。
  
1. eDiscovery のケースを追跡し、どの保管担当者がどのケースに関連付けられているかを追跡する。
    
2. どのファイル コレクションのセットがどの eDiscovery のケースに関連付けられているかを追跡する。
    
3. インポートのタイミングを調整し、コールド ストレージのステップに移動する。
    
4. Azure で使用するファイル領域を管理する。
    
5. PST のインポート先メールボックスを管理する。
    
6. すべてのオンプレミス データのバックアップおよび復元。
    
### <a name="custodian-management"></a>保管担当者管理

- To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>収集ファイルの監視とログ ファイルの確認

1. Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .
    
2. When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:
    
  - One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.
    
    > [!NOTE]
    > The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer. 
  
  - One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>PST インポートのオプション A (Exchange Server 2013 の場合)

1. Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.
    
3. Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. エラーの出力を確認します。
    
5. Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST インポートのオプション B (Exchange Online の場合)

- 収集した PST ファイルを Exchange Online に配置するには、「Microsoft 365 へのファイルのインポートに[ネットワークアップロード](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files)を使用する」の手順を実行します。
    
### <a name="move-to-cold-storage"></a>コールド ストレージに移動

1. [Runbook の実行](https://go.microsoft.com/fwlink/p/?LinkId=615123)に関する手順を使用して、 **Movetocoldstorage** runbook を実行します。
    
2. Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.
    
### <a name="ediscovery"></a>電子情報開示

1. Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. PST ファイルのインポートにオプション A を使用した場合は、SharePoint 2013 に eDiscovery ケースを作成します。オプション B を使用した場合は、SharePoint Online に eDiscovery ケースを作成します。
    

