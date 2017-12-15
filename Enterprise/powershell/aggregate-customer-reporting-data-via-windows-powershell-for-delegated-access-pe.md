---
title: "委任アクセス許可 (DAP) パートナー用 Windows PowerShell 経由で顧客レポート データを集約する"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: "概要:Office 365 の Windows PowerShell を使用すると、顧客のすべてのテナンシーでレポートを取得し、1 つの場所にデータを集約できます。"
ms.openlocfilehash: 89651971424d1b9a494335572d2654d8402ec146
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a>委任アクセス許可 (DAP) パートナー用 Windows PowerShell 経由で顧客レポート データを集約する

 **の概要:**顧客 tenancies のすべてのレポートを取得し、1 つの場所にデータを集計するには、Office 365 用の Windows PowerShell を使用します。
  
既定では、Office 365 の Windows PowerShell には、複数の顧客テナンシーからデータをレポートする組み込みの集約がありません。ただし、この Office 365 の Windows PowerShell のサンプル スクリプトを使用すると、顧客のすべてのテナンシーを反復処理して、顧客ごとに 1 つのレポートを取得してから、1 つの場所にレポートのデータを集約することができます。結果として、顧客のテナントすべてを 1 つにしたレポートが得られます。 
  
委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。それらの企業は、顧客に提供するサービスに Office 365 サブスクリプションをバンドルします。 Office 365 サブスクリプションを販売する際に、顧客テナンシー に対する「代理で管理」(AOBO) 権限が自動的に付与されるため、顧客テナンシーを管理し、顧客テナンシーに関するレポートを作成できます。
## <a name="before-you-begin"></a>開始する前に

このスクリプトを使用するには、次の変数を実際の特定の値に置き換えます。
  
- **$UserName** - パートナー管理者のユーザー名。これらの資格情報は、すべての顧客テナンシーの接続に使用されます。
    
- **$OutputFile** - レポートのデータの集約先のコンマ区切り値 (CSV) ファイル。
    
- **$ErrorFile** - エラー用のテキスト形式のログ ファイル。
    
- **$ScriptBlock** - このサンプル スクリプトでは、手始めとして、 **Get-MailboxActivityReport** およびパラメーター (開始日と終了日など) を使用します。 他のレポートを実行する場合は、目的のレポート名および **Get-MailboxActivityReport** の必要なパラメーターを置き換えます。
    
- 「[委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)」に記載する手順を使用して、Exchange Online に対するリモートの Windows PowerShell セッションを開きます。
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a>Windows PowerShell を使用して、顧客のテナント レポートを 1 か所に集約します。

1. このスクリプトをコピーして、メモ帳に貼り付けます。
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\\ReportOutput.csv"

$ErrorFile = ".\\Errors.txt"

# This is the report to run and all the necessary parameters.

$ScriptBlock = {Get-MailboxActivityReport -ReportType Daily -StartDate 03/18/2015 -EndDate 03/18/2015}

$LinesToSkip = 0

# This is the prompt for the password of the partner admin user name.

$Cred = get-credential -Credential $UserName

# Establish a Windows PowerShell session with Office 365.

Connect-MsolService -Credential $Cred

# Get all the contracts for the signed-in partner.  
# Contracts define the AOBO/DAP relationship between the partner and the customers.

$Contracts = Get-MsolPartnerContract -All

Write-Host "Found $($Contracts.Count) customers for this Partner."

# For each of the contracts (customers), run the specified report and output the information.

foreach ($c in $contracts) { 

    # Get the initial domain for the customer.

    $InitialDomain = Get-MsolDomain -TenantId $c.TenantId | Where {$_.IsInitial -eq $true}

    # Construct the URL with the DelegatedOrg parameter.
    
    $DelegatedOrgURL = "https://ps.outlook.com/powershell-liveid?DelegatedOrg=" + $InitialDomain.Name
        
    Write-Host "Running report for $($InitialDomain.Name)"

    # Invoke-Command establishes a Windows PowerShell session based on the URL,
    # runs the command, and closes the Windows PowerShell session.
    
    $ReportInfo = Invoke-Command -ConnectionUri $DelegatedOrgURL -Credential $Cred -Authentication Basic -ConfigurationName Microsoft.Exchange -AllowRedirection -ScriptBlock $ScriptBlock -HideComputerName

    # If Invoke-Command returned information (that is, it's not NULL), format and output the information.
    
    If ($ReportInfo) {

        Write-Host "Writing report information for $($InitialDomain.Name) to $OutputFile"  -foregroundcolor green

        # Convert the report data to CSV format.
        # For the first time, don't skip any lines, so include the header.
        # For all other times, skip the first line (so don't rewrite the header).
        
        $OutputInfo = $ReportInfo |  ConvertTo-CSV -NoTypeInformation | Select -Skip $LinesToSkip

        Out-File $OutputFile -InputObject $OutputInfo -Append

        $LinesToSkip = 1

    } else {

        # If Invoke-Command didn't return and report data, log an error.
        
        Write-Host "No report information for $($InitialDomain.Name)." -foregroundcolor yellow
           
        Out-File $ErrorFile  -InputObject @("No report information for $($InitialDomain.Name).") -Append
    }

}

  ```

2. スクリプトを、GetMailboxActivityReport.ps1 という名前で、見つけやすい場所に保存します。この例では、ファイルは C:\\O365 Scripts に保存されます。 
    
3. 次の構文に従って、スクリプトをリモートの Windows PowerShell で実行します。
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

このサンプル スクリプトでは、集約されたレポートを ReportOutput.csv ファイルに配置します。
  
## <a name="see-also"></a>See also

#### 

[パートナーのヘルプ](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[Office 365 レポート Web サービス](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Exchange Online のレポート作成のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=526430)

