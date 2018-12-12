---
title: 委任アクセス許可 (DAP) パートナー用 Windows PowerShell 経由で顧客レポート データを集約する
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: 概要:Office 365 の Windows PowerShell を使用すると、顧客のすべてのテナンシーでレポートを取得し、1 つの場所にデータを集約できます。
ms.openlocfilehash: eba2c3be848b878670321485718317b5552b2db3
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
ms.locfileid: "18812108"
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="dd6ba-103">委任アクセス許可 (DAP) パートナー用 Windows PowerShell 経由で顧客レポート データを集約する</span><span class="sxs-lookup"><span data-stu-id="dd6ba-103">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="dd6ba-104">**概要:** Office 365 の Windows PowerShell を使用すると、顧客のすべてのテナンシーでレポートを取得し、1 つの場所にデータを集約できます。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-104">**Summary:** Use Windows PowerShell for Office 365 to retrieve reports on all customer tenancies and aggregate the data into a single location.</span></span>
  
<span data-ttu-id="dd6ba-p101">既定では、Office 365 の Windows PowerShell には、複数の顧客テナンシーからデータをレポートする組み込みの集約がありません。ただし、この Office 365 の Windows PowerShell のサンプル スクリプトを使用すると、顧客のすべてのテナンシーを反復処理して、顧客ごとに 1 つのレポートを取得してから、1 つの場所にレポートのデータを集約することができます。結果として、顧客のテナントすべてを 1 つにしたレポートが得られます。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-p101">By default, Windows PowerShell for Office 365 does not have a built-in aggregation of reporting data from multiple customer tenancies. However, you can use this sample Windows PowerShell for Office 365 script to iterate through all your customer tenancies to retrieve a single report for each of your customers and then aggregate the reporting data into a single location. The result is that you'll have a single report for all your customer tenants.</span></span> 
  
<span data-ttu-id="dd6ba-p102">委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。それらの企業は、顧客に提供するサービスに Office 365 サブスクリプションをバンドルします。 Office 365 サブスクリプションを販売する際に、顧客テナンシー に対する「代理で管理」(AOBO) 権限が自動的に付与されるため、顧客テナンシーを管理し、顧客テナンシーに関するレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="dd6ba-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="dd6ba-112">Before you begin</span></span>

<span data-ttu-id="dd6ba-113">このスクリプトを使用するには、次の変数を実際の特定の値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-113">To use this script, substitute your particular values in for these variables:</span></span>
  
- <span data-ttu-id="dd6ba-p103">**$UserName** - パートナー管理者のユーザー名。これらの資格情報は、すべての顧客テナンシーの接続に使用されます。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-p103">**$UserName** - This is your partner administrator user name. These credentials will be used to connect to all your customer tenancies.</span></span>
    
- <span data-ttu-id="dd6ba-116">**$OutputFile** - レポートのデータの集約先のコンマ区切り値 (CSV) ファイル。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-116">**$OutputFile** - This is the comma-separated value file that reporting data will be aggregated to.</span></span>
    
- <span data-ttu-id="dd6ba-117">**$ErrorFile** - エラー用のテキスト形式のログ ファイル。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-117">**$ErrorFile** - This is the text log file for errors.</span></span>
    
- <span data-ttu-id="dd6ba-p104">**$ScriptBlock** - このサンプル スクリプトでは、手始めとして、 **Get-MailboxActivityReport** およびパラメーター (開始日と終了日など) を使用します。 他のレポートを実行する場合は、目的のレポート名および **Get-MailboxActivityReport** の必要なパラメーターを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-p104">**$ScriptBlock** - This sample script uses **Get-MailboxActivityReport** and parameters (such as start and end dates) so you have a way to get started. If you want other reports, substitute the report name that you want and necessary parameters for **Get-MailboxActivityReport**.</span></span>
    
- <span data-ttu-id="dd6ba-120">「[委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)」に記載する手順を使用して、Exchange Online に対するリモートの Windows PowerShell セッションを開きます。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-120">Open a remote Windows PowerShell session to Exchange Online by using the steps in [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a><span data-ttu-id="dd6ba-121">Windows PowerShell を使用して、顧客のテナント レポートを 1 か所に集約します。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-121">Use Windows PowerShell to aggregate customer tenant reports to a single location</span></span>

1. <span data-ttu-id="dd6ba-122">このスクリプトをコピーして、メモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-122">Copy and paste this script into Notepad.</span></span>
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\ReportOutput.csv"

$ErrorFile = ".\Errors.txt"

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

2. <span data-ttu-id="dd6ba-p105">スクリプトを、GetMailboxActivityReport.ps1 という名前で、見つけやすい場所に保存します。この例では、ファイルは C:\\O365 Scripts に保存されます。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-p105">Save the script as GetMailboxActivityReport.ps1 in a location that's easy for you to find. For the example, the file is saved in C:\\O365 Scripts.</span></span> 
    
3. <span data-ttu-id="dd6ba-125">次の構文に従って、スクリプトをリモートの Windows PowerShell で実行します。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-125">Run the script in remote Windows PowerShell by following this syntax.</span></span>
    
  ```
  &amp; "C:\O365 Scripts\GetMailboxActivityReport.ps1"
  ```

<span data-ttu-id="dd6ba-126">このサンプル スクリプトでは、集約されたレポートを ReportOutput.csv ファイルに配置します。</span><span class="sxs-lookup"><span data-stu-id="dd6ba-126">This sample script places the aggregated report in the ReportOutput.csv file.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dd6ba-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd6ba-127">See also</span></span>

#### 

[<span data-ttu-id="dd6ba-128">パートナーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="dd6ba-128">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[<span data-ttu-id="dd6ba-129">Office 365 レポート Web サービス</span><span class="sxs-lookup"><span data-stu-id="dd6ba-129">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="dd6ba-130">Exchange Online のレポート作成のコマンドレット</span><span class="sxs-lookup"><span data-stu-id="dd6ba-130">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)

