---
title: Office 365 PowerShell を使用してユーザーアカウントを削除する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Office 365 PowerShell を使用して Office 365 ユーザーアカウントを削除する方法について説明します。
ms.openlocfilehash: dd7e5052f8933955267302a5d03870017702a7fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069043"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="4c3f1-103">Office 365 PowerShell を使用してユーザーアカウントを削除する</span><span class="sxs-lookup"><span data-stu-id="4c3f1-103">Delete user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="4c3f1-104">**概要:** Office 365 PowerShell を使用して Office 365 ユーザーアカウントを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-104">**Summary:**  Learn how to use Office 365 PowerShell to delete Office 365 user accounts.</span></span>
  
<span data-ttu-id="4c3f1-105">Office 365 PowerShell を使用して、ユーザーアカウントを削除できます。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-105">You can use Office 365 PowerShell to delete a user account.</span></span>

   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="4c3f1-106">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="4c3f1-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="4c3f1-107">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="4c3f1-108">接続したら、以下の構文を使用してユーザー アカウントを個別に削除します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-108">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="4c3f1-109">この例では、ユーザー アカウント fabricec@litwareinc.com を削除します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-109">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="4c3f1-110">**AzureAD**コマンドレットの **-ObjectID**パラメーターは、アカウントのサインイン名 (ユーザープリンシパル名とも呼ばれる)、またはアカウントのオブジェクト ID のいずれかを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-110">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="4c3f1-111">ユーザーの名前に基づいてアカウント名を表示するには、以下のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-111">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="4c3f1-112">この例では、Caleb Sills という名前のユーザーのアカウント名を表示します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-112">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="4c3f1-113">ユーザーの表示名に基づいてアカウントを削除するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-113">To remove an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="4c3f1-114">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="4c3f1-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="4c3f1-115">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用してユーザーアカウントを削除しても、そのアカウントは完全に削除されません。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-115">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted.</span></span> <span data-ttu-id="4c3f1-116">削除されたユーザー アカウントは 30 日以内であれば復元できます。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-116">You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="4c3f1-117">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="4c3f1-118">ユーザー アカウントを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-118">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="4c3f1-119">この例では、ユーザー アカウント BelindaN@litwareinc.com を削除します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-119">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="4c3f1-120">削除されたユーザー アカウントを 30 日間の猶予期間内に復元するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-120">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="4c3f1-121">この例では、削除されたユーザー アカウント BelindaN@litwareinc.com を復元します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-121">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="4c3f1-122">**メモ:**</span><span class="sxs-lookup"><span data-stu-id="4c3f1-122">**Notes:**</span></span>
  
- <span data-ttu-id="4c3f1-123">復元できる削除されたユーザーの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-123">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="4c3f1-124">ユーザーアカウントの元のユーザープリンシパル名が別のアカウントで使用されている場合、ユーザーアカウントを復元するときに別のユーザープリンシパル名を指定するには、 _UserPrincipalName_の代わりに_newuserprincipalname_パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-124">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="4c3f1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c3f1-125">See also</span></span>

[<span data-ttu-id="4c3f1-126">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="4c3f1-126">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="4c3f1-127">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="4c3f1-127">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4c3f1-128">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="4c3f1-128">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

