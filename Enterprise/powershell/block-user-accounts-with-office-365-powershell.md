---
title: Office 365 PowerShell でユーザー アカウントをブロックする
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
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Office 365 PowerShell を使用して Office 365 アカウントへのアクセスをブロックおよびブロック解除する方法について説明します。
ms.openlocfilehash: a2edecf7bc47d39aa9aeb965c7b2834e37820a36
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069213"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="9dda6-103">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="9dda6-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="9dda6-104">**概要:** Office 365 PowerShell を使用して Office 365 アカウントへのアクセスをブロックおよびブロック解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="9dda6-105">Office 365 アカウントへのアクセスをブロックすると、ユーザーがアカウントを使用して Office 365 組織のサービスとデータにサインインしてアクセスするのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="9dda6-105">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="9dda6-106">Office 365 PowerShell を使用して、個別および複数のユーザーアカウントへのアクセスをブロックすることができます。</span><span class="sxs-lookup"><span data-stu-id="9dda6-106">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="9dda6-107">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="9dda6-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="9dda6-108">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="9dda6-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="9dda6-109">個別のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="9dda6-109">Block access to individual user accounts</span></span>

<span data-ttu-id="9dda6-110">個々のユーザーアカウントをブロックするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="9dda6-111">AzureAD コマンドレットの-ObjectID パラメーターは、アカウントのサインイン名 (ユーザープリンシパル名とも呼ばれる)、またはアカウントのオブジェクト ID のいずれかを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="9dda6-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="9dda6-112">この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="9dda6-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="9dda6-113">このユーザー アカウントのブロックを解除するには、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="9dda6-114">ユーザーの表示名に基づいてユーザーアカウント UPN を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="9dda6-115">この例では、Caleb/Ls という名前のユーザーのユーザーアカウント UPN を表示します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="9dda6-116">ユーザーの表示名に基づいてアカウントをブロックするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="9dda6-117">次のコマンドを使用して、ユーザーアカウントのブロックされた状態をいつでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="9dda6-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="9dda6-118">複数のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="9dda6-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="9dda6-119">複数のユーザーアカウントへのアクセスをブロックするには、次のように各行に1つのアカウントサインイン名を含むテキストファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="9dda6-120">次のコマンドでは、サンプルテキストファイルは C:\My Documents\accounts.txt です。</span><span class="sxs-lookup"><span data-stu-id="9dda6-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="9dda6-121">これをテキストファイルのパスとファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9dda6-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="9dda6-122">テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="9dda6-123">テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="9dda6-124">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="9dda6-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="9dda6-125">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="9dda6-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="9dda6-126">個別のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="9dda6-126">Block access to individual user accounts</span></span>

<span data-ttu-id="9dda6-127">個々のユーザー アカウントへのアクセスをブロックするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="9dda6-128">この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="9dda6-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="9dda6-129">ユーザー アカウントのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="9dda6-130">次のコマンドを使用して、ユーザーアカウントのブロックされた状態をいつでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="9dda6-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="9dda6-131">複数のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="9dda6-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="9dda6-132">最初に、次のような各行に1つのアカウントを含むテキストファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="9dda6-133">次のコマンドでは、サンプルテキストファイルは C:\My Documents\accounts.txt です。</span><span class="sxs-lookup"><span data-stu-id="9dda6-133">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="9dda6-134">これをテキストファイルのパスとファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9dda6-134">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="9dda6-135">テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="9dda6-136">テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="9dda6-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="9dda6-137">See also</span></span>

[<span data-ttu-id="9dda6-138">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="9dda6-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="9dda6-139">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="9dda6-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9dda6-140">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="9dda6-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
