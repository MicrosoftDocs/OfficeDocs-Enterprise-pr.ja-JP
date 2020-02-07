---
title: Office 365 PowerShell でユーザー アカウントをブロックする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Office 365 PowerShell を使用して Office 365 アカウントへのアクセスをブロックおよびブロック解除する方法について説明します。
ms.openlocfilehash: 18c7cea2df2514d7402dfcfd894acc03ed69b1c9
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841694"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="fcf85-103">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="fcf85-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="fcf85-104">Office 365 アカウントへのアクセスをブロックすると、ユーザーがアカウントを使用して Office 365 組織のサービスとデータにサインインしてアクセスするのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="fcf85-104">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="fcf85-105">Office 365 PowerShell を使用して、個別および複数のユーザーアカウントへのアクセスをブロックすることができます。</span><span class="sxs-lookup"><span data-stu-id="fcf85-105">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="fcf85-106">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="fcf85-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="fcf85-107">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="fcf85-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="fcf85-108">個別のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="fcf85-108">Block access to individual user accounts</span></span>

<span data-ttu-id="fcf85-109">個々のユーザーアカウントをブロックするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-109">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="fcf85-110">AzureAD コマンドレットの-ObjectID パラメーターは、アカウントのサインイン名 (ユーザープリンシパル名とも呼ばれる)、またはアカウントのオブジェクト ID のいずれかを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="fcf85-110">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="fcf85-111">この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="fcf85-111">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="fcf85-112">このユーザー アカウントのブロックを解除するには、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-112">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="fcf85-113">ユーザーの表示名に基づいてユーザーアカウント UPN を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-113">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="fcf85-114">この例では、Caleb/Ls という名前のユーザーのユーザーアカウント UPN を表示します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-114">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="fcf85-115">ユーザーの表示名に基づいてアカウントをブロックするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-115">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="fcf85-116">次のコマンドを使用して、ユーザーアカウントのブロックされた状態をいつでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="fcf85-116">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="fcf85-117">複数のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="fcf85-117">Block access to multiple user accounts</span></span>

<span data-ttu-id="fcf85-118">複数のユーザーアカウントへのアクセスをブロックするには、次のように各行に1つのアカウントサインイン名を含むテキストファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-118">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="fcf85-119">次のコマンドでは、サンプルテキストファイルは C:\My Documents\accounts.txt です。</span><span class="sxs-lookup"><span data-stu-id="fcf85-119">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="fcf85-120">これをテキストファイルのパスとファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="fcf85-120">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="fcf85-121">テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-121">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="fcf85-122">テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-122">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="fcf85-123">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="fcf85-123">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="fcf85-124">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="fcf85-124">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="fcf85-125">個別のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="fcf85-125">Block access to individual user accounts</span></span>

<span data-ttu-id="fcf85-126">個々のユーザー アカウントへのアクセスをブロックするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-126">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="fcf85-127">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="fcf85-127">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="fcf85-128">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcf85-128">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="fcf85-129">この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="fcf85-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="fcf85-130">ユーザー アカウントのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-130">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="fcf85-131">次のコマンドを使用して、ユーザーアカウントのブロックされた状態をいつでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="fcf85-131">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="fcf85-132">複数のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="fcf85-132">Block access to multiple user accounts</span></span>

<span data-ttu-id="fcf85-133">最初に、次のような各行に1つのアカウントを含むテキストファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-133">First, create a text file that contains one account on each line like this:</span></span>
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

<span data-ttu-id="fcf85-134">次のコマンドでは、サンプルテキストファイルは C:\My Documents\accounts.txt です。</span><span class="sxs-lookup"><span data-stu-id="fcf85-134">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="fcf85-135">これをテキストファイルのパスとファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="fcf85-135">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="fcf85-136">テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-136">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="fcf85-137">テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fcf85-137">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="fcf85-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcf85-138">See also</span></span>

[<span data-ttu-id="fcf85-139">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="fcf85-139">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="fcf85-140">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="fcf85-140">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fcf85-141">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="fcf85-141">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
