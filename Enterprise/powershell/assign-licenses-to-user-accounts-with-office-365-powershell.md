---
title: Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123294"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8ded2-103">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="8ded2-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8ded2-104">**概要:** Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8ded2-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="8ded2-p101">ユーザーは自分のアカウントにライセンスが供与されるまで Office 365 サービスを一切使用できないため、Office 365 のユーザー アカウントへのライセンス供与は重要です。Office 365 PowerShell を使用することにより、効率的にライセンスをライセンスのないアカウント、特に複数のアカウントに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="8ded2-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="8ded2-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="8ded2-107">Before you begin</span></span>
<span data-ttu-id="8ded2-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="8ded2-108"><a name="RTT"> </a></span></span>

- <span data-ttu-id="8ded2-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ded2-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="8ded2-p103">**Get-MsolAccountSku** コマンドレットを使用して、利用可能なライセンス プランと組織で利用可能なライセンスのプランごとの数を表示します。各プランで利用可能なライセンスの数は、**ActiveUnits** - **WarningUnits** - **ConsumedUnits** です。ライセンス プラン、ライセンス、サービスの詳細については、「[Office 365 PowerShell でライセンスとサービスを確認する](view-licenses-and-services-with-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ded2-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="8ded2-114">組織内のライセンスのないアカウントを検索するには、コマンド  `Get-MsolUser -All -UnlicensedUsersOnly` を実行します。</span><span class="sxs-lookup"><span data-stu-id="8ded2-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="8ded2-p104">ライセンスは、**UsageLocation** プロパティが有効な ISO 3166-1 alpha-2 の国別コードに設定されているユーザー アカウントにのみ割り当てることができます。たとえば、米国は US、フランスは FR です。一部の Office 365 サービスは特定の国では使用できません。詳細については、「[ライセンスによる使用制限について](https://go.microsoft.com/fwlink/p/?LinkId=691730)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ded2-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="8ded2-p105">**UsageLocation** 値のないアカウントを検索するには、コマンド `Get-MsolUser -All | where {$_.UsageLocation -eq $null}` を実行します。アカウントに **UsageLocation** 値を設定するには、構文 `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>` を使用します。例: `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。</span><span class="sxs-lookup"><span data-stu-id="8ded2-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="8ded2-122">`-All` パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="8ded2-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>

## <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="8ded2-123">ユーザー アカウントにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="8ded2-123">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="8ded2-124">ユーザーにライセンスを割り当てるには、Office 365 PowerShell で次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="8ded2-124">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="8ded2-125">この例では、ライセンスを `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスのないユーザー `belindan@litwareinc.com` に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8ded2-125">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="8ded2-126">ライセンスのない多数のユーザーにライセンスを割り当てるには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="8ded2-126">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="8ded2-127">**メモ**</span><span class="sxs-lookup"><span data-stu-id="8ded2-127">**Notes**</span></span>
  
- <span data-ttu-id="8ded2-128">複数のライセンスを同じライセンス プランのユーザーに割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="8ded2-128">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="8ded2-129">十分な数の利用可能なライセンスをお持ちでない場合は、使用可能なライセンスがなくなるまで、ライセンスは **Get-MsolUser** コマンドレットによって返される順序でユーザーに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8ded2-129">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="8ded2-130">この例では、ライセンスを `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスのないユーザーすべてに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8ded2-130">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="8ded2-131">この例では、これらの同じライセンスを米国内にある営業部のライセンスのないユーザーに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8ded2-131">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="8ded2-132">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="8ded2-132">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="8ded2-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ded2-133">See also</span></span>
<span data-ttu-id="8ded2-134"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="8ded2-134"></span></span>

<span data-ttu-id="8ded2-135">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8ded2-135">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="8ded2-136">ユーザー アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="8ded2-136">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8ded2-137">削除し、ユーザー アカウントを復元します。</span><span class="sxs-lookup"><span data-stu-id="8ded2-137">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8ded2-138">ブロックのユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="8ded2-138">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8ded2-139">ユーザー アカウントからライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="8ded2-139">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="8ded2-140">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8ded2-140">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="8ded2-141">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="8ded2-141">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="8ded2-142">Get-msoluser</span><span class="sxs-lookup"><span data-stu-id="8ded2-142">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="8ded2-143">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="8ded2-143">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="8ded2-144">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="8ded2-144">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="8ded2-145">Select-Object</span><span class="sxs-lookup"><span data-stu-id="8ded2-145">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="8ded2-146">Where-Object</span><span class="sxs-lookup"><span data-stu-id="8ded2-146">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

