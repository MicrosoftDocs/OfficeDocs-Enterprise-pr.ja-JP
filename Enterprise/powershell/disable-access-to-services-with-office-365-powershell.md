---
title: Office 365 PowerShell を使ったサービスへのアクセスを無効にする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/08/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Office 365 の PowerShell を使用して、組織内のユーザーの Office 365 サービスへのアクセスを無効にする方法について説明します。
ms.openlocfilehash: 44b0ed84bb8fd098412c69258834194b2b1eeb2f
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "22196824"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="93768-103">Office 365 PowerShell を使ったサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="93768-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="93768-104">**の概要:** Office 365 の PowerShell を使用して、組織内のユーザーの Office 365 サービスへのアクセスを無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="93768-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="93768-p101">Office 365 アカウントは、ライセンス計画からライセンスが割り当てられているが、ときに Office 365 のサービスが割り当てられているユーザー ライセンスからです。ただし、ユーザーがアクセスできる Office 365 サービスを制御できます。などの場合でも、ライセンスは、SharePoint Online へのアクセスを許可へのアクセス権を無効にすることができます。実際には、任意の数のためのサービスへのアクセスを無効にするのには、Office 365 の PowerShell を使用できます。</span><span class="sxs-lookup"><span data-stu-id="93768-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>

- <span data-ttu-id="93768-109">個々のアカウント。</span><span class="sxs-lookup"><span data-stu-id="93768-109">An individual account.</span></span>
    
- <span data-ttu-id="93768-110">アカウントのグループ。</span><span class="sxs-lookup"><span data-stu-id="93768-110">A group of accounts.</span></span>
    
- <span data-ttu-id="93768-111">組織内のすべてのアカウント。</span><span class="sxs-lookup"><span data-stu-id="93768-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="93768-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="93768-112">Before you begin</span></span>
<span data-ttu-id="93768-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="93768-113"></span></span>

- <span data-ttu-id="93768-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93768-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93768-p103">**Get MsolAccountSku**コマンドレットを使用するには使用可能なライセンスの計画、およびそれらのプランで利用可能な Office 365 サービスを表示します。詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93768-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93768-118">参照してくださいするのには、前に、このトピックで説明する手順の実行結果の後は、 [Office 365 の PowerShell でアカウントのライセンスおよびサービスの詳細を表示](view-account-license-and-service-details-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93768-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93768-p104">このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。具体的に言うと、このスクリプトにより、Office 365 組織のサービス (Sway を含む) を表示し、無効化できます。詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="93768-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93768-122">**Get MsolUser**コマンドレットを使用するには、_すべて_のパラメーターを使用せず、最初の 500 のユーザー アカウントのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="93768-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a><span data-ttu-id="93768-123">1 つのライセンスについての特定のユーザーに対して特定の Office 365 サービス</span><span class="sxs-lookup"><span data-stu-id="93768-123">Specific Office 365 services for specific users for a single licensing plan</span></span>
  
<span data-ttu-id="93768-124">1 つのライセンスについてのユーザーの Office 365 サービスの特定のセットを無効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="93768-124">To disable a specific set of Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="93768-125">ライセンスについての次の構文を使用して、不要なサービスを識別します。</span><span class="sxs-lookup"><span data-stu-id="93768-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="93768-126">ライセンス プランという名前で、Office オンライン サービスと SharePoint のオンライン サービスを無効にする**LicenseOptions**オブジェクトを作成する例を次`litwareinc:ENTERPRISEPACK`(Office 365 エンタープライズ E3)。</span><span class="sxs-lookup"><span data-stu-id="93768-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="93768-127">手順 1 の **LicenseOptions** オブジェクトを、1 人以上のユーザーに使用します。</span><span class="sxs-lookup"><span data-stu-id="93768-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="93768-128">サービスが無効になっている新しいアカウントを作成するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="93768-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="93768-129">Allie Bellew、ライセンスが割り当てられ、手順 1 で説明されているサービスを無効にするため、新しいアカウントを作成する例を次にします。</span><span class="sxs-lookup"><span data-stu-id="93768-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="93768-130">Office 365 の PowerShell でのユーザー アカウントの作成の詳細については、 [Office 365 の PowerShell でのユーザー アカウントの作成](create-user-accounts-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93768-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="93768-131">ライセンスを付与された既存のユーザー用のサービスを無効にするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="93768-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="93768-132">この例では、ユーザー BelindaN@litwareinc.com に対してサービスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="93768-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="93768-133">すべての既存のライセンスを受けたユーザーの手順 1 で説明されているサービスを無効にするには、 **Get MsolAccountSku**コマンドレット ( **litwareinc:ENTERPRISEPACK**) などの表示から、Office 365 のプランの名前を指定し、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="93768-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="93768-134">既存のユーザーのグループに対してサービスを無効にするには、次のいずれかの方法を使用して、ユーザーを特定します。</span><span class="sxs-lookup"><span data-stu-id="93768-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="93768-135">**既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="93768-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="93768-136">次の使用例は、米国内の販売部門のユーザー用のサービスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="93768-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="93768-137">**特定のアカウントの一覧を使用する** これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="93768-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="93768-138">次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="93768-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="93768-139">この例で、テキスト ファイルは、c:\\マイ ドキュメント\\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="93768-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="93768-140">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="93768-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="93768-141">ライセンスが必要にそれらを割り当てるときにユーザーの Office 365 サービスを無効にするには、[ユーザー ライセンスを割り当てる際にサービスへのアクセスを無効にする](disable-access-to-services-while-assigning-user-licenses.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93768-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a><span data-ttu-id="93768-142">ライセンス プランのすべてのユーザーに対して特定の Office 365 サービス</span><span class="sxs-lookup"><span data-stu-id="93768-142">Specific Office 365 services for users from all licensing plans</span></span>
  
<span data-ttu-id="93768-143">使用可能なライセンスのすべての計画では、ユーザーの Office 365 サービスを無効にする、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="93768-143">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="93768-144">このスクリプトをコピーして、メモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="93768-144">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="93768-145">環境に合わせて次の値をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="93768-145">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="93768-146">_<UndesirableService>_ この例では、Office オンラインおよび SharePoint Online を使用します。</span><span class="sxs-lookup"><span data-stu-id="93768-146">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="93768-147">_<Account>_ この例では、belindan@litwareinc.com を使用します。</span><span class="sxs-lookup"><span data-stu-id="93768-147">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="93768-148">カスタマイズされたスクリプトは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="93768-148">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="93768-p105">としてスクリプトを保存する`RemoveO365Services.ps1`を簡単に検索することができる場所にします。この例でファイルを保存しましたが`C:\\O365 Scripts`。</span><span class="sxs-lookup"><span data-stu-id="93768-p105">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in `C:\\O365 Scripts`.</span></span>
    
4. <span data-ttu-id="93768-151">Office 365 の PowerShell のスクリプトを実行するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="93768-151">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="93768-152">これらの手順のいずれかの効果を逆にする (つまり、無効になっているサービスを再度有効にする) プロシージャを実行できません、ですが、値を使用して、 `$null` _DisabledPlans_パラメーターの。</span><span class="sxs-lookup"><span data-stu-id="93768-152">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="93768-153">先頭へ戻る</span><span class="sxs-lookup"><span data-stu-id="93768-153">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)



## <a name="new-to-office-365"></a><span data-ttu-id="93768-154">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="93768-154">New to Office 365?</span></span>
<span data-ttu-id="93768-155"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="93768-155"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="93768-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="93768-156">See also</span></span>
<span data-ttu-id="93768-157"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="93768-157"></span></span>

<span data-ttu-id="93768-158">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="93768-158">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="93768-159">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="93768-159">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93768-160">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="93768-160">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93768-161">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="93768-161">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93768-162">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="93768-162">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93768-163">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="93768-163">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="93768-164">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="93768-164">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="93768-165">Get-Content</span><span class="sxs-lookup"><span data-stu-id="93768-165">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="93768-166">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="93768-166">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="93768-167">新しい-MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="93768-167">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="93768-168">Get-msoluser</span><span class="sxs-lookup"><span data-stu-id="93768-168">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="93768-169">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="93768-169">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="93768-170">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="93768-170">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="93768-171">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="93768-171">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="93768-172">Where-Object</span><span class="sxs-lookup"><span data-stu-id="93768-172">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

