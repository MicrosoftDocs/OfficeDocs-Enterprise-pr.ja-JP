---
title: Office 365 PowerShell でユーザー アカウントをブロックする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
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
ms.openlocfilehash: 748d24f95f9dca651158dae2fe15e9c655eb021e
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915412"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="2d53f-103">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="2d53f-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="2d53f-104">**の概要:** Office 365 の PowerShell を使用してブロックし、Office 365 アカウントへのアクセスをブロック解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="2d53f-p101">Office 365 アカウントへのアクセスをブロックできなくなりますアカウントを使用してサインインして、サービスと Office 365 の組織内のデータにアクセスします。アカウントへのアクセスを禁止すると、サインインを試みると、ユーザーは次のエラー メッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2d53f-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. When you block access to the account, the user receives the following error message when they attempt to sign in:</span></span>
  
![ブロックされた Office 365 アカウント。](media/o365-powershell-account-blocked.png)
  
<span data-ttu-id="2d53f-108">Office 365 の PowerShell を使用するには個別にアクセスし、複数のユーザー アカウントをブロックします。</span><span class="sxs-lookup"><span data-stu-id="2d53f-108">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="2d53f-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="2d53f-109">Before you begin</span></span>

- <span data-ttu-id="2d53f-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d53f-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="2d53f-112">ユーザー アカウントをブロックするとは限りすべてのユーザーのデバイスとクライアントを有効にするために 24 時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2d53f-112">When you block a user account, it might take as long as 24 hours to take effect on all the user's devices and clients.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="2d53f-113">Office 365 PowerShell を使用して、個々のユーザー アカウントへのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="2d53f-113">Use Office 365 PowerShell to block access to individual user accounts</span></span>

<span data-ttu-id="2d53f-114">個々のユーザー アカウントへのアクセスをブロックするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-114">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

<span data-ttu-id="2d53f-115">この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="2d53f-115">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="2d53f-116">ユーザー アカウントのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-116">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

<span data-ttu-id="2d53f-117">いつでも、次のコマンドでユーザー アカウントのブロック状態をチェックできます。</span><span class="sxs-lookup"><span data-stu-id="2d53f-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a><span data-ttu-id="2d53f-118">Office 365 の PowerShell を使用して複数のユーザー アカウントへのアクセスをブロックするには</span><span class="sxs-lookup"><span data-stu-id="2d53f-118">Use Office 365 PowerShell to block access to multiple user accounts</span></span>

<span data-ttu-id="2d53f-119">最初に、次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-119">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="2d53f-p103">次のコマンドでは、テキスト ファイルの例とは、C:\My Documents\Accounts.txt です。これをテキスト ファイルのパスとファイル名で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2d53f-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="2d53f-122">テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="2d53f-123">テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a><span data-ttu-id="2d53f-124">Azure Active Directory V2 PowerShell モジュールを使用して、ユーザー アカウントへのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="2d53f-124">Use the Azure Active Directory V2 PowerShell module to block access to user accounts</span></span>

<span data-ttu-id="2d53f-p104">Azure Active Directory V2 PowerShell モジュールから **New-AzureADUser** コマンドレットを使用するには、まず自分のサブスクリプションに接続する必要があります。手順については、「[Azure Active Directory V2 PowerShell モジュールを使用した接続](https://go.microsoft.com/fwlink/?linkid=842218)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d53f-p104">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="2d53f-127">接続したら、以下の構文を使用して、個別のユーザー アカウントをブロックします。</span><span class="sxs-lookup"><span data-stu-id="2d53f-127">After you have connected, use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="2d53f-128">Set-AzureAD コマンドレットの -ObjectID パラメーターは、アカウント名 (ユーザー プリンシパル名とも呼ばれる) か、アカウントのオブジェクト ID のいずれかを受け付けます。</span><span class="sxs-lookup"><span data-stu-id="2d53f-128">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="2d53f-129">この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="2d53f-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="2d53f-130">このユーザー アカウントのブロックを解除するには、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-130">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="2d53f-131">UPN は、ユーザーの表示名に基づくユーザー アカウントを表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-131">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="2d53f-132">この例では、氏の窓台をという名前のユーザーのユーザー アカウント UPN を使用します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-132">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="2d53f-133">ユーザーの名前に基づいてアカウントをブロックするには、以下のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-133">To block an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="2d53f-134">いつでも、次のコマンドでユーザー アカウントのブロック状態をチェックできます。</span><span class="sxs-lookup"><span data-stu-id="2d53f-134">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

<span data-ttu-id="2d53f-135">複数のユーザー アカウントへのアクセスをブロックするには、次のように各行に 1 つのアカウント名を含むテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-135">To block access to multiple user accounts, create a text file that contains one account name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="2d53f-p105">次のコマンドでは、テキスト ファイルの例とは、C:\My Documents\Accounts.txt です。これをテキスト ファイルのパスとファイル名で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2d53f-p105">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="2d53f-138">テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-138">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="2d53f-139">テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2d53f-139">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="see-also"></a><span data-ttu-id="2d53f-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d53f-140">See also</span></span>

<span data-ttu-id="2d53f-141">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2d53f-141">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="2d53f-142">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="2d53f-142">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="2d53f-143">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="2d53f-143">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="2d53f-144">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="2d53f-144">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="2d53f-145">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="2d53f-145">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="2d53f-146">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2d53f-146">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="2d53f-147">Get-Content</span><span class="sxs-lookup"><span data-stu-id="2d53f-147">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [<span data-ttu-id="2d53f-148">セット MsolUser</span><span class="sxs-lookup"><span data-stu-id="2d53f-148">Set-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [<span data-ttu-id="2d53f-149">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="2d53f-149">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

