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
ms.openlocfilehash: 09cfdaf1485837713d03949cca456b9d07b66b00
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257668"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="9efca-103">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="9efca-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="9efca-104">**概要:** Office 365 PowerShell を使用して Office 365 アカウントへのアクセスをブロックおよびブロック解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9efca-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="9efca-105">Office 365 アカウントへのアクセスをブロックすると、ユーザーがアカウントを使用して Office 365 組織のサービスとデータにサインインしてアクセスするのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="9efca-105">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="9efca-106">Office 365 PowerShell を使用して、個別および複数のユーザーアカウントへのアクセスをブロックすることができます。</span><span class="sxs-lookup"><span data-stu-id="9efca-106">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="9efca-107">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="9efca-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="9efca-108">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="9efca-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="9efca-109">個別のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="9efca-109">Block access to individual user accounts</span></span>

<span data-ttu-id="9efca-110">個々のユーザーアカウントをブロックするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="9efca-110">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="9efca-111">AzureAD コマンドレットの-ObjectID パラメーターは、アカウントのサインイン名 (ユーザープリンシパル名とも呼ばれる)、またはアカウントのオブジェクト ID のいずれかを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="9efca-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="9efca-112">この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="9efca-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="9efca-113">このユーザー アカウントのブロックを解除するには、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9efca-113">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="9efca-114">ユーザーの表示名に基づいてユーザーアカウント UPN を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9efca-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="9efca-115">この例では、Caleb/Ls という名前のユーザーのユーザーアカウント UPN を表示します。</span><span class="sxs-lookup"><span data-stu-id="9efca-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="9efca-116">ユーザーの表示名に基づいてアカウントをブロックするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9efca-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="9efca-117">次のコマンドを使用して、ユーザーアカウントのブロックされた状態をいつでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="9efca-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="9efca-118">複数のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="9efca-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="9efca-119">複数のユーザーアカウントへのアクセスをブロックするには、次のように各行に1つのアカウントサインイン名を含むテキストファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9efca-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="9efca-120">次のコマンドでは、サンプルテキストファイルは C:\My Documents\accounts.txt です。</span><span class="sxs-lookup"><span data-stu-id="9efca-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="9efca-121">これをテキストファイルのパスとファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9efca-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="9efca-122">テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9efca-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="9efca-123">テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9efca-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="9efca-124">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="9efca-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="9efca-125">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="9efca-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="9efca-126">個別のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="9efca-126">Block access to individual user accounts</span></span>

<span data-ttu-id="9efca-127">個々のユーザー アカウントへのアクセスをブロックするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="9efca-127">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="9efca-128">PowerShell Core では、Microsoft Azure Active Directory モジュール for Windows PowerShell モジュールと、名前に**Msol**を指定したコマンドレットはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9efca-128">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="9efca-129">これらのコマンドレットを引き続き使用するには、これらのコマンドレットを Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9efca-129">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="9efca-130">この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="9efca-130">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="9efca-131">ユーザー アカウントのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9efca-131">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="9efca-132">次のコマンドを使用して、ユーザーアカウントのブロックされた状態をいつでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="9efca-132">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="9efca-133">複数のユーザーアカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="9efca-133">Block access to multiple user accounts</span></span>

<span data-ttu-id="9efca-134">最初に、次のような各行に1つのアカウントを含むテキストファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9efca-134">First, create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="9efca-135">次のコマンドでは、サンプルテキストファイルは C:\My Documents\accounts.txt です。</span><span class="sxs-lookup"><span data-stu-id="9efca-135">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="9efca-136">これをテキストファイルのパスとファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9efca-136">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="9efca-137">テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9efca-137">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="9efca-138">テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9efca-138">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="9efca-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="9efca-139">See also</span></span>

[<span data-ttu-id="9efca-140">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="9efca-140">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="9efca-141">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="9efca-141">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9efca-142">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="9efca-142">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
