---
title: Office 365 PowerShell でユーザー アカウントをブロックする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Office 365 の PowerShell を使用してブロックし、Office 365 アカウントへのアクセスをブロック解除する方法について説明します。
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546478"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="f119c-103">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="f119c-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="f119c-104">**の概要:** Office 365 の PowerShell を使用してブロックし、Office 365 アカウントへのアクセスをブロック解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f119c-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="f119c-p101">Office 365 アカウントへのアクセスをブロックできなくなりますアカウントを使用してサインインして、サービスと Office 365 の組織内のデータにアクセスします。Office 365 の PowerShell を使用するには個別にアクセスし、複数のユーザー アカウントをブロックします。</span><span class="sxs-lookup"><span data-stu-id="f119c-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f119c-107">Azure Active Directory の PowerShell を使用して、グラフのモジュールの</span><span class="sxs-lookup"><span data-stu-id="f119c-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="f119c-108">最初は[、Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="f119c-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="f119c-109">個々 のユーザー アカウントへのアクセスをブロック</span><span class="sxs-lookup"><span data-stu-id="f119c-109">Block access to individual user accounts</span></span>

<span data-ttu-id="f119c-110">個々 のユーザー アカウントをブロックするのにには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f119c-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="f119c-111">セット AzureAD コマンドレットでのオブジェクト Id パラメーターは、どちらかのアカウントでサインイン名、ユーザー プリンシパル名、またはアカウントのオブジェクト ID とも呼ばれますを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="f119c-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="f119c-112">この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="f119c-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="f119c-113">このユーザー アカウントのブロックを解除するには、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f119c-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="f119c-114">UPN は、ユーザーの表示名に基づくユーザー アカウントを表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f119c-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="f119c-115">この例では、氏の窓台をという名前のユーザーのユーザー アカウント UPN を使用します。</span><span class="sxs-lookup"><span data-stu-id="f119c-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="f119c-116">ユーザーの表示名を基に、アカウントをブロックするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f119c-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="f119c-117">いつでも、次のコマンドでユーザー アカウントのブロック状態をチェックできます。</span><span class="sxs-lookup"><span data-stu-id="f119c-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="f119c-118">複数のユーザー アカウントへのアクセスをブロック</span><span class="sxs-lookup"><span data-stu-id="f119c-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="f119c-119">複数のユーザー アカウントへのアクセスをブロックするには、1 アカウントでサインイン名次のように各行に含まれているテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f119c-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="f119c-p102">次のコマンドでは、テキスト ファイルの例とは、C:\My Documents\Accounts.txt です。これをテキスト ファイルのパスとファイル名で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f119c-p102">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="f119c-122">テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f119c-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="f119c-123">テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f119c-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f119c-124">モジュールを使用して、Microsoft Azure Active Directory Windows PowerShell の</span><span class="sxs-lookup"><span data-stu-id="f119c-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f119c-125">最初は[、Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="f119c-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="f119c-126">個々 のユーザー アカウントへのアクセスをブロック</span><span class="sxs-lookup"><span data-stu-id="f119c-126">Block access to individual user accounts</span></span>

<span data-ttu-id="f119c-127">個々のユーザー アカウントへのアクセスをブロックするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f119c-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="f119c-128">この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="f119c-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="f119c-129">ユーザー アカウントのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f119c-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="f119c-130">いつでも、次のコマンドでユーザー アカウントのブロック状態をチェックできます。</span><span class="sxs-lookup"><span data-stu-id="f119c-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="f119c-131">複数のユーザー アカウントへのアクセスをブロック</span><span class="sxs-lookup"><span data-stu-id="f119c-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="f119c-132">最初に、次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f119c-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="f119c-p103">次のコマンドでは、テキスト ファイルの例とは、C:\My Documents\Accounts.txt です。これをテキスト ファイルのパスとファイル名で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f119c-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="f119c-135">テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f119c-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="f119c-136">テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f119c-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="f119c-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="f119c-137">See also</span></span>

[<span data-ttu-id="f119c-138">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="f119c-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f119c-139">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="f119c-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f119c-140">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="f119c-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
