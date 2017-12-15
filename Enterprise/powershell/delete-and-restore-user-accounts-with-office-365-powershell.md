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
- DecEntMigration
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Office 365 の PowerShell を使用して削除し、Office 365 ユーザー アカウントを復元する方法について説明します。"
ms.openlocfilehash: 8404395ea9594cea1a2e772cecbeb011756b7754
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a><span data-ttu-id="f9d80-103">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="f9d80-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="f9d80-104">**の概要:** Office 365 の PowerShell を使用して削除し、Office 365 ユーザー アカウントを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-104">**Summary:**  Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts.</span></span>
  
<span data-ttu-id="f9d80-p101">Office 365 PowerShell を使用してユーザー アカウントを削除する場合、アカウントは完全には削除されません。削除されたユーザー アカウントは 30 日以内であれば復元できます。</span><span class="sxs-lookup"><span data-stu-id="f9d80-p101">When you use Office 365 PowerShell to delete a user account, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="f9d80-107">開始する前に</span><span class="sxs-lookup"><span data-stu-id="f9d80-107">Before you begin</span></span>

- <span data-ttu-id="f9d80-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9d80-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="f9d80-110">使用せず、 **Get MsolUser**コマンドレットを使用するかどうかは、_のすべて_パラメーターでは、最初の 500 個のアカウントのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="f9d80-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="f9d80-111">Office 365 PowerShell を使用して、個々のユーザー アカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="f9d80-111">Use Office 365 PowerShell to block access to individual user accounts</span></span>
<span data-ttu-id="f9d80-112"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="f9d80-112"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="f9d80-113">ユーザー アカウントを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-113">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="f9d80-114">この例では、ユーザー アカウント BelindaN@litwareinc.com を削除します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-114">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="f9d80-115">削除されたユーザー アカウントを 30 日間の猶予期間内に復元するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-115">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="f9d80-116">この例では、削除されたユーザー アカウント BelindaN@litwareinc.com を復元します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-116">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="f9d80-117">**メモ:**</span><span class="sxs-lookup"><span data-stu-id="f9d80-117">**Notes:**</span></span>
  
- <span data-ttu-id="f9d80-118">復元できる削除されたユーザーの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-118">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="f9d80-119">ユーザー アカウントの元のユーザー プリンシパル名を別のアカウントで使用している場合は、ユーザー アカウントを復元する際に、 _UserPrincipalName_ の代わりに _NewUserPrincipalName_ パラメーターを使用して別のユーザー プリンシパル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-119">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a><span data-ttu-id="f9d80-120">Azure Active Directory V2 PowerShell モジュールを使用したユーザー アカウントの削除</span><span class="sxs-lookup"><span data-stu-id="f9d80-120">Use the Azure Active Directory V2 PowerShell module to remove a user account</span></span>
<span data-ttu-id="f9d80-121"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="f9d80-121"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="f9d80-p103">Azure Active Directory V2 PowerShell モジュールから**削除 AzureADUser**コマンドレットを使用するには、まずお客様のサブスクリプションに接続する必要があります。この手順では、 [Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9d80-p103">To use the **Remove-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="f9d80-124">接続したら、以下の構文を使用してユーザー アカウントを個別に削除します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-124">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <Account>
```

<span data-ttu-id="f9d80-125">この例では、ユーザー アカウント fabricec@litwareinc.com を削除します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-125">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="f9d80-126">**Remove-AzureAD** コマンドレットの **-ObjectID** パラメーターは、別名ユーザー プリンシパル名であるアカウント名か、アカウントのオブジェクト ID のいずれかを受け付けます。</span><span class="sxs-lookup"><span data-stu-id="f9d80-126">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="f9d80-127">ユーザーの名前に基づいてアカウント名を表示するには、以下のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-127">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="f9d80-128">この例では、Caleb Sills という名前のユーザーのアカウント名を表示します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-128">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="f9d80-129">ユーザーの名前に基づいてアカウントを削除するには、以下のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9d80-129">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a><span data-ttu-id="f9d80-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9d80-130">See also</span></span>
<span data-ttu-id="f9d80-131"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="f9d80-131"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="f9d80-132">Office 365 の PowerShell でユーザーを管理する方法は次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9d80-132">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="f9d80-133">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="f9d80-133">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f9d80-134">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="f9d80-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f9d80-135">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="f9d80-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f9d80-136">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="f9d80-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="f9d80-137">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f9d80-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="f9d80-138">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="f9d80-138">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="f9d80-139">Remove-MsolUser</span><span class="sxs-lookup"><span data-stu-id="f9d80-139">Remove-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [<span data-ttu-id="f9d80-140">Restore-MsolUser</span><span class="sxs-lookup"><span data-stu-id="f9d80-140">Restore-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [<span data-ttu-id="f9d80-141">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="f9d80-141">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

