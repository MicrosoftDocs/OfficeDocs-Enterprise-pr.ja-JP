---
title: PowerShell を使用して Microsoft 365 ユーザーアカウントを作成する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: この記事では、PowerShell を使用してユーザーアカウントまたは Microsoft 365 の複数のユーザーアカウントを作成する方法について説明します。
ms.openlocfilehash: 2f4d7b42e68e3bd426ea73c8568e0c603af06dcb
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605993"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="bcec5-103">PowerShell を使用して Microsoft 365 ユーザーアカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="bcec5-103">Create Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="bcec5-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="bcec5-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="bcec5-105">Microsoft 365 の PowerShell を使用すると、ユーザーアカウント、特に複数のユーザーアカウントを効率的に作成できます。</span><span class="sxs-lookup"><span data-stu-id="bcec5-105">You can use PowerShell for Microsoft 365 to efficiently create user accounts, especially multiple user accounts.</span></span> <span data-ttu-id="bcec5-106">PowerShell でユーザーアカウントを作成する場合、特定のアカウントのプロパティが常に必要です。</span><span class="sxs-lookup"><span data-stu-id="bcec5-106">When you create user accounts in PowerShell, certain account properties are always required.</span></span> <span data-ttu-id="bcec5-107">他のプロパティはアカウントを作成する際に必須ではありませんが、別の面で重要となります。</span><span class="sxs-lookup"><span data-stu-id="bcec5-107">Other properties aren't required to create the account, but are otherwise important.</span></span> <span data-ttu-id="bcec5-108">次の表では、これらのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bcec5-108">These properties are described in the following table:</span></span>
  
|<span data-ttu-id="bcec5-109">**プロパティ名**</span><span class="sxs-lookup"><span data-stu-id="bcec5-109">**Property name**</span></span>|<span data-ttu-id="bcec5-110">**必須**</span><span class="sxs-lookup"><span data-stu-id="bcec5-110">**Required?**</span></span>|<span data-ttu-id="bcec5-111">**説明**</span><span class="sxs-lookup"><span data-stu-id="bcec5-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bcec5-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="bcec5-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="bcec5-113">はい</span><span class="sxs-lookup"><span data-stu-id="bcec5-113">Yes</span></span>  <br/> |<span data-ttu-id="bcec5-114">これは、Microsoft 365 サービスで使用される表示名です。</span><span class="sxs-lookup"><span data-stu-id="bcec5-114">This is the display name that's used in Microsoft 365 services.</span></span> <span data-ttu-id="bcec5-115">たとえば、Caleb Sills。</span><span class="sxs-lookup"><span data-stu-id="bcec5-115">For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="bcec5-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="bcec5-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="bcec5-117">はい</span><span class="sxs-lookup"><span data-stu-id="bcec5-117">Yes</span></span>  <br/> |<span data-ttu-id="bcec5-118">これは、Microsoft 365 サービスへのサインインに使用されるアカウント名です。</span><span class="sxs-lookup"><span data-stu-id="bcec5-118">This is the account name that's used to sign in to Microsoft 365 services.</span></span> <span data-ttu-id="bcec5-119">たとえば、CalebS@contoso.onmicrosoft.com。</span><span class="sxs-lookup"><span data-stu-id="bcec5-119">For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="bcec5-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="bcec5-120">**FirstName**</span></span> <br/> |<span data-ttu-id="bcec5-121">いいえ</span><span class="sxs-lookup"><span data-stu-id="bcec5-121">No</span></span>  <br/> ||
|<span data-ttu-id="bcec5-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="bcec5-122">**LastName**</span></span> <br/> |<span data-ttu-id="bcec5-123">いいえ</span><span class="sxs-lookup"><span data-stu-id="bcec5-123">No</span></span>  <br/> ||
|<span data-ttu-id="bcec5-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="bcec5-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="bcec5-125">いいえ</span><span class="sxs-lookup"><span data-stu-id="bcec5-125">No</span></span>  <br/> |<span data-ttu-id="bcec5-126">これは、使用可能なライセンスがユーザーアカウントに割り当てられているライセンスプラン (ライセンスプランまたは SKU とも呼ばれます) です。</span><span class="sxs-lookup"><span data-stu-id="bcec5-126">This is the licensing plan (also known as the license plan or SKU) from which an available license is assigned to the user account.</span></span> <span data-ttu-id="bcec5-127">ライセンスでは、アカウントで利用可能な Microsoft 365 サービスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="bcec5-127">The license defines the Microsoft 365 services that are available to account.</span></span> <span data-ttu-id="bcec5-128">アカウントの作成時にライセンスをユーザーに割り当てる必要はありませんが、そのアカウントには Microsoft 365 サービスにアクセスするためのライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="bcec5-128">You don't have to assign a license to a user when you create the account, but the account requires a license to access Microsoft 365 services.</span></span> <span data-ttu-id="bcec5-129">ユーザー アカウントにライセンスを割り当てる期間は作成後 30 日です。</span><span class="sxs-lookup"><span data-stu-id="bcec5-129">You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="bcec5-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="bcec5-130">**Password**</span></span> <br/> |<span data-ttu-id="bcec5-131">いいえ</span><span class="sxs-lookup"><span data-stu-id="bcec5-131">No</span></span>  <br/> | <span data-ttu-id="bcec5-p105">パスワードを指定しない場合、ランダムなパスワードがユーザー アカウントに割り当てられ、パスワードはコマンドの結果に表示されます。パスワードを指定する場合、小文字、大文字、数字、記号のうちの 3 つの種類の文字を使った 8 から 16 文字の ASCII テキスト文字にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcec5-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="bcec5-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="bcec5-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="bcec5-135">いいえ</span><span class="sxs-lookup"><span data-stu-id="bcec5-135">No</span></span>  <br/> |<span data-ttu-id="bcec5-136">これは有効な ISO 3166-1 alpha 国コードです。</span><span class="sxs-lookup"><span data-stu-id="bcec5-136">This is a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="bcec5-137">たとえば、米国は US、フランスは FR です。</span><span class="sxs-lookup"><span data-stu-id="bcec5-137">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="bcec5-138">一部の Microsoft 365 サービスは特定の国では利用できないため、この値を指定することは重要です。そのため、アカウントにこの値が設定されていない限り、ユーザーアカウントにライセンスを割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="bcec5-138">It's important to provide this value, because some Microsoft 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured.</span></span> <span data-ttu-id="bcec5-139">詳細については、「[ライセンス制限につい](https://go.microsoft.com/fwlink/p/?LinkId=691730)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcec5-139">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>  <br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="bcec5-140">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="bcec5-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="bcec5-141">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="bcec5-141">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="bcec5-142">接続したら、以下の構文を使用して個別のアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="bcec5-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="bcec5-143">この例では、米国の Caleb Sills というユーザーのアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="bcec5-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="bcec5-144">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="bcec5-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="bcec5-145">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="bcec5-145">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="bcec5-146">個別のユーザー アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="bcec5-146">Create an individual user account</span></span>

<span data-ttu-id="bcec5-147">個別のアカウントを作成するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="bcec5-147">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
><span data-ttu-id="bcec5-148">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="bcec5-148">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="bcec5-149">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcec5-149">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="bcec5-150">使用可能なライセンスのプラン名を一覧表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bcec5-150">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="bcec5-151">この例では、米国の Caleb Sills という名前のユーザーにアカウントを作成し、 `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="bcec5-151">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="bcec5-152">複数のユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="bcec5-152">Create multiple user accounts</span></span>

1. <span data-ttu-id="bcec5-p108">必要なユーザー アカウント情報を含むコンマ区切り (CSV) ファイルを作成します。例:</span><span class="sxs-lookup"><span data-stu-id="bcec5-p108">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="bcec5-155">CSV ファイルの最初の行の列名とその順序は任意ですが、ファイルの残りの部分のデータが列名の順序と一致していることを確認し、Microsoft 365 コマンドの PowerShell のパラメーター値として列名を使用します。</span><span class="sxs-lookup"><span data-stu-id="bcec5-155">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the PowerShell for Microsoft 365 command.</span></span>
    
2. <span data-ttu-id="bcec5-156">次の構文を使用してください。</span><span class="sxs-lookup"><span data-stu-id="bcec5-156">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="bcec5-157">この例は、C:\My Documents\NewAccounts.csv という名前のファイルからユーザー アカウントを作成し、C:\My Documents\NewAccountResults.csv という名前のファイルに結果を記録します。</span><span class="sxs-lookup"><span data-stu-id="bcec5-157">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="bcec5-158">出力ファイルで結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="bcec5-158">Review the output file to see the results.</span></span> <span data-ttu-id="bcec5-159">パスワードを指定していないため、Microsoft 365 によって生成されたランダムなパスワードが出力ファイルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bcec5-159">We didn't specify passwords, so the random passwords that Microsoft 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="bcec5-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcec5-160">See also</span></span>

[<span data-ttu-id="bcec5-161">Microsoft 365 ユーザー アカウント、ライセンス、PowerShell を使用したグループを管理する</span><span class="sxs-lookup"><span data-stu-id="bcec5-161">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="bcec5-162">PowerShell で Microsoft 365を管理する</span><span class="sxs-lookup"><span data-stu-id="bcec5-162">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="bcec5-163">Microsoft 365 用 PowerShell の使用を開始する</span><span class="sxs-lookup"><span data-stu-id="bcec5-163">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
