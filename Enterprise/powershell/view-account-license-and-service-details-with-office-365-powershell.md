---
title: Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Office 365 の PowerShell を使用してユーザーに割り当てられている Office 365 のサービスを確認する方法について説明します。
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213954"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="f2133-103">Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="f2133-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="f2133-104">**の概要:** Office 365 の PowerShell を使用してユーザーに割り当てられている Office 365 のサービスを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2133-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="f2133-p101">、Office 365 では、計画のライセンスからライセンス (も呼び出された Sku または Office 365 プラン) ユーザーにそれらの計画に定義されている Office 365 サービスへのアクセスを提供します。ただし、[ユーザーはそれらに現在割り当てられているライセンスで使用可能なすべてのサービスへのアクセスをいない可能性があります。ユーザー アカウントのサービスの状態を表示するのには、Office 365 の PowerShell を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2133-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="f2133-108">始める前に</span><span class="sxs-lookup"><span data-stu-id="f2133-108">Before you begin</span></span>

- <span data-ttu-id="f2133-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2133-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="f2133-111">コマンドを使用して、`Get-MsolAccountSku`と`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`、次の情報を検索します。</span><span class="sxs-lookup"><span data-stu-id="f2133-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="f2133-112">組織で使用可能なライセンス プラン。</span><span class="sxs-lookup"><span data-stu-id="f2133-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="f2133-113">各ライセンス プランで使用可能なサービス、およびサービスがリストされる順序 (インデックス番号)。</span><span class="sxs-lookup"><span data-stu-id="f2133-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="f2133-114">計画、ライセンス、およびサービスのライセンスの詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2133-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="f2133-115">コマンドを使用して`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`(インデックス番号) を一覧には、ユーザー、および順に割り当てられているライセンスが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="f2133-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="f2133-116">_All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="f2133-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="f2133-117">ユーザー アカウントのサービスを表示するには</span><span class="sxs-lookup"><span data-stu-id="f2133-117">To view services for a user account</span></span>

<span data-ttu-id="f2133-118">ユーザーへのアクセス権を持っているすべての Office 365 サービスを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f2133-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="f2133-p103">この例では、BelindaN@litwareinc.com のユーザーのアクセスを持っているサービスを使用します。自分のアカウントに割り当てられているすべてのライセンスに関連付けられているサービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2133-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="f2133-121">次の例では、ユーザー BelindaN@litwareinc.com が、アカウントに割り当てられている最初のライセンス (インデックス番号 0) からアクセスできるサービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2133-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="f2133-122">*複数のライセンス*が割り当てられているユーザーのためのすべてのサービスを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f2133-122">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a><span data-ttu-id="f2133-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2133-123">See also</span></span>

<span data-ttu-id="f2133-124">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f2133-124">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="f2133-125">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="f2133-125">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f2133-126">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="f2133-126">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f2133-127">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="f2133-127">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f2133-128">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="f2133-128">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f2133-129">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="f2133-129">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="f2133-130">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f2133-130">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="f2133-131">Convertto-html コマンドレット</span><span class="sxs-lookup"><span data-stu-id="f2133-131">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="f2133-132">Format-List</span><span class="sxs-lookup"><span data-stu-id="f2133-132">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="f2133-133">Get-msoluser</span><span class="sxs-lookup"><span data-stu-id="f2133-133">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="f2133-134">Select-Object</span><span class="sxs-lookup"><span data-stu-id="f2133-134">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="f2133-135">Where-Object</span><span class="sxs-lookup"><span data-stu-id="f2133-135">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="f2133-136">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="f2133-136">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]