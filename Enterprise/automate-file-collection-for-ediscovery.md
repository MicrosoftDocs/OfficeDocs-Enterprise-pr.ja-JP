---
title: 電子情報開示用にファイル収集を自動化する
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 概要:電子情報開示用にユーザーのコンピューターのファイル収集を自動化する方法について説明します。
ms.openlocfilehash: bfbe3b9218ed81727f2cc6ad9fabcb02e76d486b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490837"
---
# <a name="automate-file-collection-for-ediscovery"></a>電子情報開示用にファイル収集を自動化する

 **概要:** 電子情報開示用にユーザーのコンピューターのファイル収集を自動化する方法について説明します。
  
すべての企業は、訴訟やその他の法的措置の可能性に直面しています。法務部門はリスクの軽減に努める一方で、訴訟はビジネス ライフの 1 つの現実です。企業は、必要とする法的措置に直面すると、法的証拠開示のプロセスを通じて、裁判所および相手方の弁護士にすべての関連資料を提供します。 
  
電子情報開示は、電子的な形式の関連資料を企業がインベントリ作成、検索、識別、保持、フィルター処理、使用可能化するプロセスです。 SharePoint 2013、Exchange Server 2013、Lync Server 2013、SharePoint Online、Exchange Online は、大量の文書コンテンツを保持できます。 これらの製品のバージョンによっては、eDiscovery とインプレース保持がサポートされています (Lync は Exchange Server 経由)。これにより、法務チームは、訴訟に最も関係のある内容のインデックスの作成、特定、保持、フィルター処理を行いやすくなります。
  
多くのドキュメントは一元的に 1 つの場所にまとめられておらず、ユーザー (保管担当者) のローカル コンピューターに保存されています。このため、SharePoint 2013 は基本的に検索ができなくなり、検索ができないと eDiscovery に含めることができません。このソリューションでは、ログオン スクリプト、Exchange Server の System Center Orchestrator 2012 R2 および Windows PowerShell を使用して、ユーザーのコンピューターから資料の特定と収集を自動で行う方法を示します。
  
## <a name="what-this-solution-does"></a>このソリューションで行うこと

このソリューションでは、グローバル セキュリティ グループ、グループ ポリシー、Windows PowerShell スクリプトを使用して、ユーザーのローカル コンピューターから非表示のファイル共有に対してコンテンツと Outlook の個人用ストア (PST) ファイルの特定、インベントリ作成、収集を行います。PST ファイルは、ここから Exchange Server 2013 または Exchange Online のいずれかにインポートできます。すべてのファイルは、長期保存および SharePoint 2013 によるインデックス作成用に、System Center Orchestrator 2012 R2 Runbook を使用して Microsoft Azure の別のファイル共有に移動されます。次に、通常 eDiscovery を行うのと同じように、オンプレミスの SharePoint 2013 展開や SharePoint Online で eDiscovery センターを使用します。 
  
> [!IMPORTANT]
> このソリューションでは、robocopy を使用して、保管担当者のコンピューターから一元管理されたファイル共有にファイルをコピーします。robocopy では開いているまたはロックされているファイルはコピーされないため、PST ファイルを含め、保管担当者が開いているファイルは収集されません。そのようなものは手動で収集する必要があります。このソリューションでは、コピーできないファイルと各ファイルへの完全パスを明示的に識別する一覧が作成されます。 
  
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
|![マゼンタの吹き出し 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(オプション B) Office 365 インポート ツールとプロセスを使用して、収集した PST ファイルを Exchange Online にインポートします。  <br/> |
|![マゼンタの吹き出し 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|MoveToColdStorageSystem Center Orchestrator 2012 R2 Runbook での長期保存用に、収集したファイルをすべて Azure ファイル共有に移動します。 <br/> |
|![マゼンタの吹き出し 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|SharePoint 2013 によりコールド ストレージ ファイル共有にファイルのインデックスを作成します。  <br/> |
|![マゼンタの吹き出し 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|コールド ストレージとオンプレミスの Exchange Server 2013 のコンテンツで eDiscovery を実行します。  <br/> |
|![マゼンタの吹き出し 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|Office 365 のコンテンツで eDiscovery を実行します。  <br/> |
   
## <a name="prerequisites"></a>前提条件

このソリューションの構成には、多くの 要素が 必要になります。eDiscovery を検討している場合、それらの要素の多くは既に配置され、構成されている可能性があります。ないかもしれない要素や、特定の構成を必要とする要素については、基本構成の構築に必要なリンクが用意されます。ソリューション自体を構成する前に、基本構成を整えておく必要があります。
  
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
|Exchange Online と SharePoint Online による Office 365 (E3 プラン) (オプション B で必要)  <br/> |Office 365 E3 サブスクリプションにサインアップするには、「[Office 365 E3 サブスクリプション](https://go.microsoft.com/fwlink/p/?LinkId=613504)」をご覧ください。  <br/> |
|仮想マシンでの Azure サブスクリプション  <br/> |Azure にサインアップするには、「[Microsoft Azure をサブスクライブする](https://go.microsoft.com/fwlink/p/?LinkId=512010)」をご覧ください。 <br/> |
|オンプレミス ネットワークと Azure サブスクリプションの間の VPN 接続  <br/> |Azure サブスクリプションとオンプレミス ネットワークの間に VPN トンネルをセット アップするには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](https://go.microsoft.com/fwlink/p/?LinkId=613507)」をご覧ください。  <br/> |
|SharePoint 2013SharePoint と Exchange Server 2013、および必要に応じて Lync Server 2013 の間で検索するように eDiscovery を構成  <br/> |この方法で eDiscovery を構成するには、「[電子情報開示を構成する (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=613508)」および「[テスト ラボ ガイド: Exchange、Lync、SharePoint、Windows のファイル共有テスト ラボの電子情報開示を構成する](https://go.microsoft.com/fwlink/p/?LinkId=393130)」をご覧ください。  <br/> |
|SharePoint Online と Exchange Online 用の Office 365 の eDiscovery  <br/> |Office 365 の eDiscovery を構成するには、「[SharePoint Online で電子情報開示センターをセットアップする](https://go.microsoft.com/fwlink/p/?LinkId=613628)」をご覧ください。  <br/> |
   
## <a name="configure-the-environment"></a>環境を構成する

基本構成の準備が整ったので、 ソリューション自体の構成に進むことができます。 
  
### <a name="staging-file-share"></a>ステージング ファイル共有

1. オンプレミス ドメインで、Custodians という名前のグローバル セキュリティ グループを作成します。
    
2. 保管担当者のコンピューターから収集されるファイルのために非表示のファイル共有を作成します。これはオンプレミス サーバー上に作成する必要があります。たとえば、Staging というサーバーに、Cases$ というファイル共有を作成します。非表示の共有にするには、 **$** が必要です。
    
3. 次の共有アクセス許可を設定します。
    
  - 保管担当者:変更、読み取り
    
  - 管理者 :フル コントロール
    
  - Exchange Trusted Subsystem:変更、読み取り
    
4. **[セキュリティ]** タブを開き、[保管担当者] グループを追加して、 **[詳細設定]** をクリックします。[保管担当者] グループに対して、次のアクセス許可を設定します。
    
  - **種類:拒否**
    
  - **適用対象:このフォルダー、サブフォルダー、およびファイル**
    
5. **[高度なアクセス許可]** をクリックし、以下を選びます。
    
  - **属性の読み取り**
    
  - **拡張属性の読み取り**
    
  - **アクセス許可の読み取り**
    
6. 以下を実行して、Cases$ ファイル共有にテスト アクセスします。
    
1. 保管担当者グループにユーザーを追加します。
    
2. Cases$ フォルダーにファイルを配置します。
    
3. ユーザーとして、ステージング サーバーを参照します。たとえば、\\\\Staging 共有を参照して、使用可能な共有を表示します。 **Cases$** 共有は一覧表示されないはずです。
    
4. Cases$ 共有への完全パスを手動で Explorer に入力します。これにより、Cases$ 共有が開きます。
    
5. 以前共有に配置したファイルを開いてみます。これは失敗するはずです。
    
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
    
3. メモ帳の移動機能を使用して、必要に応じて次の変更を行います。
    
|**行番号**|**変更するために必要な事柄**|**必須かどうか**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes** 変数。スクリプトがインベントリ作成と配列変数への収集を行うファイルの種類の拡張子がすべて含まれます。<br/> |省略可能  <br/> |
|76 と 77  <br/> |**$CaseNo** 変数を構築する方法をニーズに合わせて変更します。スクリプトは、現在の日時をキャプチャし、ユーザー名をそれに追加します。<br/> |省略可能  <br/> |
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
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
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

2. スクリプトを、PSTImportScript.ps1 という名前を付けて見つけやすい場所に保存します。例として、使いやすくするため、ステージング サーバーに \\\\Staging\\AFCScripts というフォルダーを作成して、そこに保存します。
    
3. メモ帳の移動機能を使用して、必要に応じて次の変更を行います。
    
|**行番号**|**変更するために必要な事柄**|**必須かどうか**|
|:-----|:-----|:-----|
|12  <br/> |**$FolderIdentifier** は、PST がインポートされるメールボックス フォルダーにタグを付けます。必要な場合は変更します。<br/> |省略可能  <br/> |
|17   <br/> |**$ConnectionUri** は独自のサーバーに設定する必要があります。 <br/> > [!IMPORTANT]> **$ConnectionUri** が https:// の場所ではなく http:// の場所を指し示していることをご確認ください。https:// では機能しません。          |必須  <br/> |
   
4. Exchange Trusted Subsystem アカウントに、\\\\Staging\\Cases$ 共有に対する読み取り、書き込み、実行のアクセス許可があることを確認します。
    
5. PST インポート スクリプトには、次の 2 つの入力パラメーターが必要です。
    
  - **$SourcePath** たとえば \\\\Staging\\Cases$ などの、インポートする PST ファイルの場所
    
  - **$MailboxAlias** インポートされたメール アイテムを受信するターゲット メールボックスのエイリアス
    
6. たとえば、すべての PST ファイルをパス \\Staging\Cases$ からエイリアス eDiscoveryMailbox を持つメールボックスにインポートする場合は、次のようなスクリプトを実行します `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`。
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST インポートのオプション B (Exchange Online の場合)

-  インポートした PST ファイルを配置するメールボックス構造を作成します。Exchange Online にユーザーのメールボックスを作成する方法の詳細については、「[Exchange Online でユーザー メールボックスを作成する](https://go.microsoft.com/fwlink/p/?LinkId=615118)」をご覧ください。
    
### <a name="cold-storage"></a>コールド ストレージ

1. Azure Virtual Machine にファイル共有を作成します。ここに収集したすべてのファイルを配置します。例: \\\\AZFile1\\ContentColdStorage
    
2. 既定のコンテンツ アクセス アカウントに対して、少なくとも共有およびすべてのサブフォルダーとファイルへの読み取りのアクセス許可を付与します。SharePoint 2013 検索の構成の詳細については、「[SharePoint Server 2013 で Search Service アプリケーションを作成および構成する](https://go.microsoft.com/fwlink/p/?LinkId=614940)」をご覧ください。
    
3. PST ファイルを \\\\AZFile1\\ContentColdStorage からインポートすることを見込んでいる場合は、Exchange Trusted Subsystem に対して共有への読み取り、書き込み、実行のアクセス許可を付与します。
    
### <a name="orchestrator"></a>Orchestrator

1. Microsoft ダウンロード センターから、[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) をダウンロードします。
    
2. **Runbook Designer** を開き、 **[接続]** ウィンドウで、Runbook のインポート先のフォルダーをクリックします。 **[アクション]** メニューをクリックしてから、 **[インポート]** をクリックします。 **[インポート]** ダイアログ ボックスが表示されます。
    
3. **[ファイルの場所]** ボックスで、インポートする Runbook のパスとファイル名を入力するか、省略記号 ( **...**) をクリックしてインポートするファイルを参照します。 
    
4. **[Runbook のインポート]** と **[Orchestrator で暗号化されたデータのインポート]** を選びます。 **[カウンター]**、 **[スケジュール]**、 **[変数]**、 **[コンピューター グループ]**、 **[グローバル構成のインポート]**、 **[既存のグローバル設定の上書き]** をクリアします。
    
5. [ **完了**] をクリックします。
    
6. **MoveFilesToColdStorage** Runbook を次のように編集します。
    
1. **[ファイルの移動]** アクティビティ - **[ソース ファイル]** のパスを、コレクション ファイル共有 (例: \\\\Staging\\cases$) に設定します。 **[移動先フォルダー]** を、Azure のコールド ストレージ ファイル共有 (例: \\\\AZFile1\\ContentColdStorage) に設定します。 **[一意の名前でファイルを作成する]** を選びます。
    
2. **[フォルダーの削除]** アクティビティ - **[パス]** をコレクション ファイル共有 (例: \\\\Staging\\cases$\\*) に設定し、 **[すべてのファイルとサブフォルダーを削除する]** を選びます。 
    
7. 「[Runbook の展開](https://go.microsoft.com/fwlink/p/?LinkId=615120)」にある手順を使用して、 **MoveToColdStorage** Runbook を展開します。
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>コールド ストレージ用 SharePoint オンプレミス検索

1. Azure のコールド ストレージ共有の SharePoint 2013 ファームに新しいコンテンツ ソースを作成します (例: \\\\AZFile1\\ContentColdStorage)。コンテンツ ソースの管理の詳細については、「[SharePoint Server 2013 でコンテンツ ソースを追加、編集、または削除する](https://go.microsoft.com/fwlink/p/?LinkId=615004)」をご覧ください。
    
2. フル クロールを開始します。詳細については、「[SharePoint Server 2013 でクロールを開始、一時停止、再開、または停止する](https://go.microsoft.com/fwlink/p/?LinkId=615005)」をご覧ください。
    
## <a name="using-the-solution"></a>ソリューションの使用

Exchange Server 2013 と Exchange Online の両方に PST ファイルをインポートしないことを前提として、このソリューションの使用には主に 5 つのステップがあります。このセクションでは、このすべてのステップの手順について記載します。ソリューションでの主な操作は次のとおりです。
  
1. 保管担当者グループのユーザー メンバーシップを管理する。
    
2. エラー
    
3. PST のインポート プロセスを管理する。
    
4. コレクション ファイルをコールド ストレージに移動する。
    
その他すべてのステップはこのソリューション固有ではありません。SharePoint 2013、および Office 365 と Azure で実行する標準の管理タスクです。このソリューションでは、企業のニーズに基づいて作業する必要があるガイダンスを提供しない項目があります。それらは次のとおりです。
  
1. eDiscovery のケースを追跡し、どの保管担当者がどのケースに関連付けられているかを追跡する。
    
2. どのファイル コレクションのセットがどの eDiscovery のケースに関連付けられているかを追跡する。
    
3. インポートのタイミングを調整し、コールド ストレージのステップに移動する。
    
4. Azure で使用するファイル領域を管理する。
    
5. PST のインポート先メールボックスを管理する。
    
6. すべてのオンプレミス データのバックアップおよび復元。
    
### <a name="custodian-management"></a>保管担当者管理

- 個々のユーザーに対して自動ファイル収集プロセスを開始するには、このユーザーを Custodian グループに追加します。 次回ユーザーがログオンすると、グループ ポリシーを介して Custodian グループに割り当てられているログオン スクリプトが実行されます。 
    
### <a name="monitor-collected-files-and-review-log-files"></a>収集ファイルの監視とログ ファイルの確認

1. ユーザーのコレクション フォルダーのコレクション ファイル共有 (例: \\\\Staging\\cases$\\*) を監視します。フォルダーの名前は  *yyyyMMddHHmm_UserName*  のような形式になります。
    
2. 収集が完了したら、コレクション フォルダーを開き、_Log フォルダーを参照します。_Log フォルダーに以下が表示されます。
    
  - ユーザーのコンピューターのローカル ドライブごとに 1 つの XML ファイル (例: **A.xml** 、 **C.xml** )。これらのファイルに含まれるインベントリ ドライブは、robocopy の操作にちなんだ名前が付けられ、その操作に使用されます。
    
    > [!NOTE]
    > コレクション スクリプトは、スクリプト自体で定義したファイルの種類のインベントリ ファイルだけにエントリを作成します。ユーザーのコンピューター上のすべてのファイルにインベントリのエントリが作成されるわけではありません。 
  
  - コレクションごとに FileCopyErrors.log という名前の 1 つのログ ファイルが実行されます。このファイルには、robocopy がファイル コレクション共有にコピーできなかったファイルの一覧が含まれています (例: \\\\Staging\\cases$\\*)。これを確認し、これらの不足しているファイルに対して実行するアクションを決定する必要があります。通常、ファイルが必要な場合は手動で収集するか、ファイルは不要であるためコレクションから省略してもよいと決定することができます。
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>PST インポートのオプション A (Exchange Server 2013 の場合)

1. コレクション ファイル共有をホストするサーバーにログオンしてから (例: **ステージング** )、Windows PowerShell を開きます。Windows PowerShell の開始の詳細については、「[Windows サーバー上で Windows PowerShell を開始する](https://go.microsoft.com/fwlink/p/?LinkId=615115)」をご覧ください。
    
2. 実行ポリシーを無制限に設定します。Windows PowerShell に  `Set-ExecutionPolicy Unrestricted -Scope Process` と入力し、Enter キーを押します。
    
3. PSTImportScript.ps1 ファイルを実行し、 **$SourcePath** パラメーターと **$MailboxAlias** パラメーターを指定します。Windows PowerShell スクリプトの実行の詳細については、「[スクリプトの実行](https://go.microsoft.com/fwlink/p/?LinkID=615117)」をご覧ください。
    
4. エラーの出力を確認します。
    
5. 同じメールボックスに同じ名前の PST ファイルをインポートしようとする前に、メールボックスのインポート要求を削除する必要があります。これを行うには、次のコマンドを実行します。 `Get-MailboxImportRequest | Remove-MailboxImportRequest`個々の要求をキューから削除するようにメッセージが表示されます。必要に応じて対処します。
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST インポートのオプション B (Exchange Online の場合)

- 収集した PST ファイルを Exchange Online に配置するには、「[Office 365 インポート サービス](https://go.microsoft.com/fwlink/p/?LinkId=614938)」の「ネットワーク アップロードによりファイルを Office 365 にインポートする」セクションにある手順に従います。
    
### <a name="move-to-cold-storage"></a>コールド ストレージに移動

1. 「[Runbook の実行](https://go.microsoft.com/fwlink/p/?LinkId=615123)」にある手順を使用して、 **MoveToColdStorage** Runbook を実行します。
    
2. 長期保存用の Azure ファイル共有 (例: \\\\AZFile1\\ContentColdStorage) とオンプレミス コレクション ファイル共有 (例: \\\\Staging\\cases$) を監視します。ファイルとフォルダーがコールド ストレージのファイル共有に表示され、コレクション ファイル共有からは非表示になります。
    
### <a name="ediscovery"></a>電子情報開示

1. コールド ストレージ ファイル共有のフル クロールをスケジュールとして実行できるようにするか、クロールを開始できるようにします。フル クロールまたは増分クロールの開始の詳細については、「[SharePoint Server 2013 でクロールを開始、一時停止、再開、または停止する](https://go.microsoft.com/fwlink/p/?LinkId=615005)」をご覧ください。
    
2. PST ファイルのインポートにオプション A を使用した場合は、SharePoint 2013 に eDiscovery ケースを作成します。オプション B を使用した場合は、SharePoint Online に eDiscovery ケースを作成します。
    

