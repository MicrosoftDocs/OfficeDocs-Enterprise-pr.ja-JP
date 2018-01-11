---
title: "Office 365 PowerShell を使用したユーザー アカウントの削除と復元"
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Office 365 PowerShell を使用した Office 365 ユーザー アカウントの削除と復元の方法について説明します。"
ms.openlocfilehash: fc72d51532780d2ddaaff20ecc6aebab06a001f4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a><span data-ttu-id="40971-103">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="40971-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="40971-104">**概要:** Office 365 PowerShell を使用した Office 365 ユーザー アカウントの削除と復元の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40971-104">**Summary:**  Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts.</span></span>
  
<span data-ttu-id="40971-p101">Office 365 PowerShell を使用してユーザー アカウントを削除する場合、アカウントは完全には削除されません。削除されたユーザー アカウントは 30 日以内であれば復元できます。</span><span class="sxs-lookup"><span data-stu-id="40971-p101">When you use Office 365 PowerShell to delete a user account, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="40971-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="40971-107">Before you begin</span></span>

- <span data-ttu-id="40971-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40971-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="40971-110">_-All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="40971-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="40971-111">Office 365 PowerShell を使用して、個々のユーザー アカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="40971-111">Use Office 365 PowerShell to block access to individual user accounts</span></span>
<span data-ttu-id="40971-112"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="40971-112"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="40971-113">ユーザー アカウントを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="40971-113">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="40971-114">この例では、ユーザー アカウント BelindaN@litwareinc.com を削除します。</span><span class="sxs-lookup"><span data-stu-id="40971-114">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="40971-115">削除されたユーザー アカウントを 30 日間の猶予期間内に復元するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="40971-115">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="40971-116">この例では、削除されたユーザー アカウント BelindaN@litwareinc.com を復元します。</span><span class="sxs-lookup"><span data-stu-id="40971-116">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="40971-117">**メモ:**</span><span class="sxs-lookup"><span data-stu-id="40971-117">**Notes:**</span></span>
  
- <span data-ttu-id="40971-118">復元できる削除されたユーザーの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="40971-118">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="40971-119">ユーザー アカウントの元のユーザー プリンシパル名を別のアカウントで使用している場合は、ユーザー アカウントを復元する際に、 _UserPrincipalName_ の代わりに _NewUserPrincipalName_ パラメーターを使用して別のユーザー プリンシパル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="40971-119">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a><span data-ttu-id="40971-120">Azure Active Directory V2 PowerShell モジュールを使用したユーザー アカウントの削除</span><span class="sxs-lookup"><span data-stu-id="40971-120">Use the Azure Active Directory V2 PowerShell module to remove a user account</span></span>
<span data-ttu-id="40971-121"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="40971-121"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="40971-p103">Azure Active Directory V2 PowerShell モジュールから **Remove-AzureADUser** コマンドレットを使用するには、まず自分のサブスクリプションに接続してください。手順については、「[Azure Active Directory V2 PowerShell モジュールを使用した接続](https://go.microsoft.com/fwlink/?linkid=842218)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40971-p103">To use the **Remove-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="40971-124">接続したら、以下の構文を使用してユーザー アカウントを個別に削除します。</span><span class="sxs-lookup"><span data-stu-id="40971-124">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <Account>
```

<span data-ttu-id="40971-125">この例では、ユーザー アカウント fabricec@litwareinc.com を削除します。</span><span class="sxs-lookup"><span data-stu-id="40971-125">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="40971-126">**Remove-AzureAD** コマンドレットの **-ObjectID** パラメーターは、別名ユーザー プリンシパル名であるアカウント名か、アカウントのオブジェクト ID のいずれかを受け付けます。</span><span class="sxs-lookup"><span data-stu-id="40971-126">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="40971-127">ユーザーの名前に基づいてアカウント名を表示するには、以下のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="40971-127">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="40971-128">この例では、Caleb Sills という名前のユーザーのアカウント名を表示します。</span><span class="sxs-lookup"><span data-stu-id="40971-128">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="40971-129">ユーザーの名前に基づいてアカウントを削除するには、以下のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="40971-129">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a><span data-ttu-id="40971-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="40971-130">See also</span></span>
<span data-ttu-id="40971-131"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="40971-131"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="40971-132">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="40971-132">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="40971-133">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="40971-133">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="40971-134">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="40971-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="40971-135">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="40971-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="40971-136">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="40971-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="40971-137">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="40971-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="40971-138">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="40971-138">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="40971-139">Remove-MsolUser</span><span class="sxs-lookup"><span data-stu-id="40971-139">Remove-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [<span data-ttu-id="40971-140">Restore-MsolUser</span><span class="sxs-lookup"><span data-stu-id="40971-140">Restore-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [<span data-ttu-id="40971-141">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="40971-141">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

