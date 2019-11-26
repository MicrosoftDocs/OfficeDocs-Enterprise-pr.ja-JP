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
ms.openlocfilehash: e62c06981a861580804dde852ad3da7bd729fdbe
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257648"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d38f9-103">Office 365 PowerShell を使用してユーザーアカウントを削除する</span><span class="sxs-lookup"><span data-stu-id="d38f9-103">Delete user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d38f9-104">Office 365 PowerShell を使用して、ユーザーアカウントを削除できます。</span><span class="sxs-lookup"><span data-stu-id="d38f9-104">You can use Office 365 PowerShell to delete a user account.</span></span>
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d38f9-105">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="d38f9-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d38f9-106">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="d38f9-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="d38f9-107">接続したら、以下の構文を使用してユーザー アカウントを個別に削除します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-107">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

>[!Note]
><span data-ttu-id="d38f9-108">PowerShell Core では、Microsoft Azure Active Directory モジュール for Windows PowerShell モジュールと、名前に**Msol**を指定したコマンドレットはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d38f9-108">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d38f9-109">これらのコマンドレットを引き続き使用するには、これらのコマンドレットを Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d38f9-109">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="d38f9-110">この例では、ユーザー アカウント fabricec@litwareinc.com を削除します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-110">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="d38f9-111">**AzureAD**コマンドレットの **-ObjectID**パラメーターは、アカウントのサインイン名 (ユーザープリンシパル名とも呼ばれる)、またはアカウントのオブジェクト ID のいずれかを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="d38f9-111">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="d38f9-112">ユーザーの名前に基づいてアカウント名を表示するには、以下のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-112">To display the account name based on the user's name, use the following commands:</span></span>
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d38f9-113">この例では、Caleb Sills という名前のユーザーのアカウント名を表示します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-113">This example displays the account name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d38f9-114">ユーザーの表示名に基づいてアカウントを削除するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-114">To remove an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d38f9-115">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="d38f9-115">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d38f9-116">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用してユーザーアカウントを削除しても、そのアカウントは完全に削除されません。</span><span class="sxs-lookup"><span data-stu-id="d38f9-116">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted.</span></span> <span data-ttu-id="d38f9-117">削除されたユーザー アカウントは 30 日以内であれば復元できます。</span><span class="sxs-lookup"><span data-stu-id="d38f9-117">You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="d38f9-118">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="d38f9-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="d38f9-119">ユーザー アカウントを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-119">To delete a user account, use the following syntax:</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="d38f9-120">この例では、ユーザー アカウント BelindaN@litwareinc.com を削除します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-120">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="d38f9-121">削除されたユーザー アカウントを 30 日間の猶予期間内に復元するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-121">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="d38f9-122">この例では、削除されたユーザー アカウント BelindaN@litwareinc.com を復元します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-122">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="d38f9-123">**メモ:**</span><span class="sxs-lookup"><span data-stu-id="d38f9-123">**Notes:**</span></span>
  
- <span data-ttu-id="d38f9-124">復元できる削除されたユーザーの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-124">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="d38f9-125">ユーザーアカウントの元のユーザープリンシパル名が別のアカウントで使用されている場合、ユーザーアカウントを復元するときに別のユーザープリンシパル名を指定するには、 _UserPrincipalName_の代わりに_newuserprincipalname_パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-125">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="d38f9-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="d38f9-126">See also</span></span>

[<span data-ttu-id="d38f9-127">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="d38f9-127">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d38f9-128">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="d38f9-128">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d38f9-129">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="d38f9-129">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

