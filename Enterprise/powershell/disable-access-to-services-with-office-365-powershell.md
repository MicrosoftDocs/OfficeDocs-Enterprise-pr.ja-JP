---
title: "Office 365 PowerShell を使ったサービスへのアクセスを無効にする"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Office 365 の PowerShell を使用して追加または、組織内のユーザーの Office 365 サービスへのアクセスを削除する方法について説明します。"
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="0f4c8-103">Office 365 PowerShell を使ったサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="0f4c8-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="0f4c8-104">**の概要:**Office 365 の PowerShell を使用して追加または、組織内のユーザーの Office 365 サービスへのアクセスを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-104">**Summary:** Explains how to use Office 365 PowerShell to add or remove access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="0f4c8-p101">Office 365 アカウントは、ライセンス計画からライセンスが割り当てられているが、ときに Office 365 のサービスが割り当てられているユーザー ライセンスからです。ただし、ユーザーがアクセスできる Office 365 サービスを制御できます。などの場合でも、ライセンスは、SharePoint Online へのアクセスを許可へのアクセス権を無効にすることができます。実際には、任意の数のためのサービスへのアクセスを無効にするのには、Office 365 の PowerShell を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>
- <span data-ttu-id="0f4c8-109">個々のアカウント。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-109">An individual account.</span></span>
    
- <span data-ttu-id="0f4c8-110">アカウントのグループ。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-110">A group of accounts.</span></span>
    
- <span data-ttu-id="0f4c8-111">組織内のすべてのアカウント。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-111">All accounts in your organization.</span></span>
    
 <span data-ttu-id="0f4c8-112">**内容:**[短いバージョン (手順説明なし)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[長いバージョン (詳細な説明と指示)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[参照してください。](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span><span class="sxs-lookup"><span data-stu-id="0f4c8-112">**Contents:**[The short version (instructions without explanations)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[The long version (instructions with detailed explanations)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[See also](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="0f4c8-113">開始する前に</span><span class="sxs-lookup"><span data-stu-id="0f4c8-113">Before you begin</span></span>
<span data-ttu-id="0f4c8-114"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="0f4c8-114"></span></span>

- <span data-ttu-id="0f4c8-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="0f4c8-p103">**Get MsolAccountSku**コマンドレットを使用するには使用可能なライセンスの計画、およびそれらのプランで利用可能な Office 365 サービスを表示します。詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="0f4c8-119">参照してくださいするのには、前に、このトピックで説明する手順の実行結果の後は、 [Office 365 の PowerShell でアカウントのライセンスおよびサービスの詳細を表示](view-account-license-and-service-details-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-119">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="0f4c8-p104">このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。具体的に言うと、このスクリプトにより、Office 365 組織のサービス (Sway を含む) を表示し、無効化できます。詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="0f4c8-123">_All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-123">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="0f4c8-124">簡略版 (説明なしの手順)</span><span class="sxs-lookup"><span data-stu-id="0f4c8-124">The short version (instructions without explanations)</span></span>
<span data-ttu-id="0f4c8-125"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="0f4c8-125"></span></span>

<span data-ttu-id="0f4c8-p105">このセクションでは、余分な説明を省いて簡潔に手順を示します。ご質問がある場合、または詳細情報が必要な場合には、このトピックの残りの部分をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p105">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="0f4c8-128">1 つのライセンスについてのユーザーの Office 365 サービスを無効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-128">To disable Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="0f4c8-129">ライセンスについての次の構文を使用して、不要なサービスを識別します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-129">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="0f4c8-130">次の使用例という名前のライセンス プランで、Office オンライン サービスと SharePoint のオンライン サービスを無効にする**LicenseOptions**オブジェクトを作成する`litwareinc:ENTERPRISEPACK`(Office 365 エンタープライズ E3)。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-130">This example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="0f4c8-131">1 つまたは複数のユーザーには、手順 1 から**LicenseOptions**オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-131">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="0f4c8-132">サービスが無効になっている新しいアカウントを作成するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-132">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="0f4c8-133">この例では、Allie Bellew の新しいアカウントを作成して、手順 1 で説明されているライセンスの割り当てとサービスの無効化を行います。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-133">This example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="0f4c8-134">Office 365 の PowerShell でのユーザー アカウントの作成の詳細については、 [Office 365 の PowerShell でのユーザー アカウントの作成](create-user-accounts-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-134">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="0f4c8-135">ライセンスを付与された既存のユーザー用のサービスを無効にするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-135">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="0f4c8-136">この例では、ユーザー BelindaN@litwareinc.com に対してサービスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-136">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="0f4c8-137">すべての既存のライセンスを受けたユーザーの手順 1 で説明されているサービスを無効にするには、 **Get MsolAccountSku**コマンドレット ( **litwareinc:ENTERPRISEPACK** ) などの表示から、Office 365 のプランの名前を指定し、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-137">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - <span data-ttu-id="0f4c8-138">既存のユーザーのグループに対してサービスを無効にするには、次のいずれかの方法を使用して、ユーザーを特定します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-138">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="0f4c8-139">**既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-139">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="0f4c8-140">この例では、米国内の販売部門のユーザーに対してサービスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-140">This example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="0f4c8-141">**特定のアカウントの一覧を使用する** これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-141">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="0f4c8-142">次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-142">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    <span data-ttu-id="0f4c8-143">この例で、テキスト ファイルは、c:\\マイ ドキュメント\\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-143">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="0f4c8-144">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-144">Run the following command:</span></span>
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="0f4c8-145">ライセンスが必要にそれらを割り当てるときにユーザーの Office 365 サービスを無効にするには、[ユーザー ライセンスを割り当てる際にサービスへのアクセスを無効にする](disable-access-to-services-while-assigning-user-licenses.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-145">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
<span data-ttu-id="0f4c8-146">使用可能なライセンスのすべての計画では、ユーザーの Office 365 サービスを無効にする、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-146">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="0f4c8-147">このスクリプトをコピーして、メモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-147">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="0f4c8-148">環境に合わせて次の値をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-148">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="0f4c8-149">_<UndesirableService>_この例では、Office オンラインおよび SharePoint Online を使用します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-149">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="0f4c8-150">_<Account>_この例では、belindan@litwareinc.com を使用します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-150">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="0f4c8-151">カスタマイズされたスクリプトは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-151">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="0f4c8-p106">としてスクリプトを保存する`RemoveO365Services.ps1`を簡単に検索することができる場所にします。この例でファイルを保存しましたが「 `C:\\O365 Scripts`」です。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p106">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in " `C:\\O365 Scripts`".</span></span>
    
4. <span data-ttu-id="0f4c8-154">Office 365 の PowerShell のスクリプトを実行するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-154">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="0f4c8-155">これらの手順のいずれかの効果を逆にする (つまり、無効になっているサービスを再度有効にする) プロシージャを実行できません、ですが、値を使用して、 `$null` _DisabledPlans_パラメーターの。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-155">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value  `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="0f4c8-156">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0f4c8-156">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="0f4c8-157">詳細版 (詳細な説明付きの手順)</span><span class="sxs-lookup"><span data-stu-id="0f4c8-157">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="0f4c8-158"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="0f4c8-158"></span></span>

<span data-ttu-id="0f4c8-p107">既定では、Office 365 の PowerShell を使用してライセンスを発行するときにすべてのサービスを有効にします。良いことは多くの場合: を割り当てることができます迅速かつ簡単にライセンス ユーザーに方法に沿って、各サービスを有効にするかを指定せずに、ことを意味します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p107">By default, all services are enabled when you issue a license by using Office 365 PowerShell. And often that's a good thing: that means that you can quickly and easily assign licenses to users without having to specify that each and every service be enabled along the way.</span></span>
  
<span data-ttu-id="0f4c8-p108">ただし、されても、ユーザーの利用可能なサービスを制限する場合は trueなどの一部のユーザーが Office Professional Plus、ビジネス オンライン、および Exchange Online では、Skype へのアクセス権を持つかもしれませんが、同じユーザーが SharePoint Online または Office Online へのアクセスを持つべきではありません。その方法でアカウントを制限することができますか。結局のところ、以下の操作を実行できます。このしくみについて説明するために、みましょう次の 2 つの方法この問題に対処するため。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p108">Having said that, however, it's also true that you might want to restrict the services available some of your users; for example, maybe some users should have access to Office Professional Plus, Skype for Business Online, and Exchange Online, but those same users shouldn't have access to SharePoint Online or to Office Online. Can you restrict accounts in that fashion? As it turns out, you can. To help explain how this works, let's take a two-step approach to tackling this problem:</span></span>
  
1. <span data-ttu-id="0f4c8-165">自動的にすべてのサービスを有効にする Office 365 のライセンスをユーザーに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-165">Assign the user an Office 365 license that automatically enables all the services.</span></span>
    
2. <span data-ttu-id="0f4c8-166">1 組のユーザーの指定されたサービスを無効にする Office 365 の PowerShell コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-166">Run a pair of Office 365 PowerShell commands that disable specified services for that user.</span></span>
    
<span data-ttu-id="0f4c8-p109">既にきました手順 1: ユーザー (Belinda ようにしてください。) が彼女をすべての Office 365 サービスへのアクセスを提供する Office 365 のライセンスを持ちます。彼女 SharePoint Online へのアクセス権がないように、Belinda のアカウントを変更する、( `SHAREPOINTENTERPRISE`) または Office Online に ( `SHAREPOINTWAC`)。ですが、方法は、利用すべきですか。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p109">We've already taken care of step 1: our user (Belinda Newman) has an Office 365 license that provides her with access to all the Office 365 services. However, we want to modify Belinda's account so that she doesn't have access to SharePoint Online ( `SHAREPOINTENTERPRISE`) or to Office Online ( `SHAREPOINTWAC`). But how are we supposed to do that?</span></span>
  
<span data-ttu-id="0f4c8-p110">ここではどのようにします。まず始めに、無効にするサービスを含む**LicenseOption**オブジェクトを作成する**新規 MsolLicenseOptions**コマンドレットを使用するつもりです。Belinda の場合は、無効にする`SHAREPOINTENTERPRISE`と`SHAREPOINTWAC`ので、このコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p110">Here's how. To begin with, we're going to use the **New-MsolLicenseOptions** cmdlet to create a **LicenseOption** object that contains the services that we want disabled. In Belinda's case, we want to disable `SHAREPOINTENTERPRISE` and `SHAREPOINTWAC`, so we use this command:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="0f4c8-p111">しくみを参照してください。ライセンス計画を指定する ( `litwareinc:ENTERPRISEPACK`) の各サービスを無効にすると、コンマを使用してこれらのサービスを分離することを指定するとします。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p111">See how that works? You specify the licensing plan ( `litwareinc:ENTERPRISEPACK`) and then indicate each of the services that you want disabled, separating those services by using commas.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0f4c8-p112">新しい**LicenseOption**オブジェクトを変数に格納することを確認します。使用して上記の例では、 `$x`、有効な Windows PowerShell の変数名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p112">Make sure you store your new **LicenseOption** object in a variable. In the preceding example, we used `$x`, although you can use any valid Windows PowerShell variable name.</span></span> 
  
<span data-ttu-id="0f4c8-177">この時点で 2 つのサービスへの Belinda のアクセスを無効にするのに次のコマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-177">At this point we can use the following command to disable Belinda's access to the two services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="0f4c8-p113">特別なここでは、いずれか:**セット MsolUserLicense**コマンドレットを呼び出すし、 _LicenseOptions_パラメーターと変数が含まれますが私たちだけ ( `$x`) を無効にする計画が含まれています。何が表示されるようになりましたかどうかは時間をかけて Belinda のライセンス情報をコマンドを実行して、:`(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`でしょうか。ここに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p113">Nothing too fancy here, either: we just call the **Set-MsolUserLicense** cmdlet and include the _LicenseOptions_ parameter, along with the variable ( `$x`) containing the plans we want to disable. And what do we see now if we take a peek at Belinda's license information by running the command:  `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? We see this:</span></span>
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

<span data-ttu-id="0f4c8-p114">なかなか良いと思いませんか。もちろんにすれば同じことを複数のユーザーに必要な場合です。たとえば、これらのコマンドは、すべてのライセンスを受けたユーザーの同じ 2 つのサービスを無効にします。**Get MsolAccountSku**コマンドレット ( **litwareinc:ENTERPRISEPACK** ) などの表示から、Office 365 のプランの名前を指定し、それらを実行します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p114">Pretty cool, huh? And, of course, we could do this same thing to multiple users if we wanted to. For example, these commands disable the same two services for all our licensed users. Specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run them.</span></span>
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

<span data-ttu-id="0f4c8-p115">Belinda がまだ有効な Office 365 ライセンスのことに留意してください。あっただけですので、彼女は、以下のサービスへのアクセス。2 つのサービスを無効にし、前に Belinda がニュースフィード、OneDrive、および SharePoint へのアクセス オンライン サイト。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p115">Keep in mind that Belinda still has a valid Office 365 license; it's just that now she has access to fewer services. Before we disabled the two services, Belinda had access to newsfeeds, OneDrive, and SharePoint Online sites:</span></span>
  
![SharePoint アクセス権を持つユーザー。](images/o365_powershell_with_sharepoint.png)
  
<span data-ttu-id="0f4c8-188">今、彼女はこれらのオプションを利用できません。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-188">Now those options are no longer available to her:</span></span>
  
![SharePoint アクセス権を持たないユーザー。](images/o365_powershell_without_sharepoint.png)
  
<span data-ttu-id="0f4c8-190">これで望みどおりになりました。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-190">Which is exactly what we hoped would happen.</span></span>
  
<span data-ttu-id="0f4c8-p116">場合変更後に、: これらのサービスを再度有効にすることは可能でしょうか。当然です。ユーザーのすべてのサービスを再度有効にするには、次の**LicenseOption**オブジェクトを作成するのにこのコマンドを使用しました。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p116">And what if we change our mind later on: is it possible to re-enable these services? You bet it is. To re-enable all the services for a user, just use this command to create the following **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="0f4c8-p117">そのコマンドは何をしますか。先頭に、Windows PowerShell の定数を`$null`"nothing"の意味(または、「null 値」を意味に少しそれ以上の技術的な言語で)ご存知、サービスを無効にすることを示すためにある**新規 MsolLicenseOptions**コマンドレットを使用する場合。この例では、たくはありませんを無効にするサービスのいずれかです。_DisabledPlans_パラメーターの値は指定してコマンドを次のようなコマンドを使用するいると判断して潜在顧客を可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p117">What does that command do? To begin with, the Windows PowerShell constant  `$null` means "nothing." (Or, in slightly-more technical language, it means a "null value.") As you recall, when we use the **New-MsolLicenseOptions** cmdlet we have to indicate the services that we want disabled. In this case, we don't want any of the services to be disabled. That might lead you to believe that we could use a command like the following, a command where we don't specify a value for the _DisabledPlans_ parameter:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

<span data-ttu-id="0f4c8-p118">ただし、次のように使うことはできません。代わりに、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p118">However, that won't work. Instead, it generates an error message:</span></span>
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
<span data-ttu-id="0f4c8-201">幸いなことに、パラメーター値を設定`$null`が機能します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-201">Fortunately for us, setting the parameter value to  `$null` does work:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="0f4c8-202">つまり、**セット MsolUserLicense**コマンドレットを実行するとということですね**セット MsolUserLicense**されないようにするため Belinda がすべて無効になっているサービス。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-202">This simply means that, when we run the **Set-MsolUserLicense** cmdlet, we're telling **Set-MsolUserLicense** that we don't want Belinda to have any disabled services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="0f4c8-203">また、論理的には、無効になるサービスがないということは、すべてのサービスが有効になるということを意味します。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-203">And, logically enough, if none of the services are disabled that must mean that all of the services are enabled.</span></span>
  
<span data-ttu-id="0f4c8-p119">このスクリプトの動作方法を理解したら、みましょうを表示するライセンスを発行し、指定されたサービスと同じコマンドを使用してすべてを無効にする方法です。サウンドの非常に印象的ですが、正直に言うと、本当に何もすること: するだけで_AddLicenses_と_LicenseOptions_のパラメーターの両方を同じコマンドに含めます。つまり、最初にオブジェクトを作成する、 **LicenseOption** 。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p119">Now that you understand how this all works, let's show you how you can issue a license and disable specified services, and all with the same command. That sounds pretty impressive, but, to be honest, there's really nothing to it: you just include both the  _AddLicenses_ and the _LicenseOptions_ parameters in the same command. In other words, you first create your **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="0f4c8-207">前述のように、使用する_AddLicenses_および_LicenseOptions_パラメーターの両方のようにします。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-207">And then, as noted previously, you use both the  _AddLicenses_ and the _LicenseOptions_ parameters in your command:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

<span data-ttu-id="0f4c8-208">コマンドが発行していること Belinda ようにしてください。 新しいライセンスがライセンスを Skype でのオンライン ビジネス ( `SHAREPOINTWAC`) とは、SharePoint Online ( `SHAREPOINTENTERPRISE`) どちらも使用できません。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-208">That command will issue Belinda Newman a new license, but a license in which Skype for Business Online ( `SHAREPOINTWAC`) and SharePoint Online ( `SHAREPOINTENTERPRISE`) are both disabled.</span></span>
  
[<span data-ttu-id="0f4c8-209">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0f4c8-209">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a><span data-ttu-id="0f4c8-210">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="0f4c8-210">New to Office 365?</span></span>
<span data-ttu-id="0f4c8-211"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="0f4c8-211"></span></span>

||
|:-----|
|<span data-ttu-id="0f4c8-p120">![LinkedIn Learning の小さいアイコン](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 を初めて使用する場合は、**         LinkedIn Learning が提供する **Office 365 admins and IT pros** のための無料のビデオ コースをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-p120">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="0f4c8-214">See also</span><span class="sxs-lookup"><span data-stu-id="0f4c8-214">See also</span></span>
<span data-ttu-id="0f4c8-215"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="0f4c8-215"></span></span>

<span data-ttu-id="0f4c8-216">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-216">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="0f4c8-217">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="0f4c8-217">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0f4c8-218">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="0f4c8-218">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0f4c8-219">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="0f4c8-219">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0f4c8-220">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="0f4c8-220">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0f4c8-221">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="0f4c8-221">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="0f4c8-222">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0f4c8-222">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="0f4c8-223">Get-Content</span><span class="sxs-lookup"><span data-stu-id="0f4c8-223">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="0f4c8-224">Get MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="0f4c8-224">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="0f4c8-225">新しい-MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="0f4c8-225">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="0f4c8-226">Get MsolUser</span><span class="sxs-lookup"><span data-stu-id="0f4c8-226">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="0f4c8-227">新しい-MsolUser</span><span class="sxs-lookup"><span data-stu-id="0f4c8-227">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="0f4c8-228">セット MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="0f4c8-228">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="0f4c8-229">ForEach オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0f4c8-229">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="0f4c8-230">Where-Object</span><span class="sxs-lookup"><span data-stu-id="0f4c8-230">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[<span data-ttu-id="0f4c8-231">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0f4c8-231">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  

