---
title: Office 365 PowerShell を使用してユーザー アカウントを作成する
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Office 365 PowerShell を使用して Office 365 でユーザー アカウントを作成する方法について学習します。
ms.openlocfilehash: 902f44dd4fc42d8f29ce92748cbbf1ce03c6615b
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730312"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="69431-103">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="69431-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="69431-104">**概要:** Office 365 PowerShell を使用して Office 365 でユーザー アカウントを作成する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="69431-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="69431-p101">Office 365 PowerShell を使用すると、特に複数のユーザー アカウントを効率的に作成できます。Office 365 PowerShell でユーザー アカウントを作成する場合、特定のプロパティは常に必須です。他のプロパティはアカウントを作成する際に必須ではありませんが、別の面で重要となります。次の表で、これらのプロパティを説明します。</span><span class="sxs-lookup"><span data-stu-id="69431-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
|<span data-ttu-id="69431-109">**プロパティ名**</span><span class="sxs-lookup"><span data-stu-id="69431-109">**Property name**</span></span>|<span data-ttu-id="69431-110">**必須**</span><span class="sxs-lookup"><span data-stu-id="69431-110">**Required?**</span></span>|<span data-ttu-id="69431-111">**説明**</span><span class="sxs-lookup"><span data-stu-id="69431-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="69431-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="69431-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="69431-113">はい</span><span class="sxs-lookup"><span data-stu-id="69431-113">Yes</span></span>  <br/> |<span data-ttu-id="69431-p102">これは、Office 365 サービスで使用される表示名です。たとえば、Caleb Sills。</span><span class="sxs-lookup"><span data-stu-id="69431-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="69431-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="69431-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="69431-117">はい</span><span class="sxs-lookup"><span data-stu-id="69431-117">Yes</span></span>  <br/> |<span data-ttu-id="69431-p103">これは、Office 365 サービスにサインインするために使用されるアカウント名です。たとえば、CalebS@contoso.onmicrosoft.com。</span><span class="sxs-lookup"><span data-stu-id="69431-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="69431-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="69431-120">**FirstName**</span></span> <br/> |<span data-ttu-id="69431-121">いいえ</span><span class="sxs-lookup"><span data-stu-id="69431-121">No</span></span>  <br/> ||
|<span data-ttu-id="69431-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="69431-122">**LastName**</span></span> <br/> |<span data-ttu-id="69431-123">いいえ</span><span class="sxs-lookup"><span data-stu-id="69431-123">No</span></span>  <br/> ||
|<span data-ttu-id="69431-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="69431-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="69431-125">いいえ</span><span class="sxs-lookup"><span data-stu-id="69431-125">No</span></span>  <br/> |<span data-ttu-id="69431-p104">これはライセンシング プラン (ライセンス プラン、Office 365 プラン、SKU とも呼ばれる) で、ここから使用可能なライセンスがユーザー アカウントに割り当てられます。ライセンスによって、アカウントに利用できる Office 365 サービスが定義されます。アカウントを作成するときにユーザーにライセンスを割り当てる必要はありませんが、アカウントは Office 365 サービスにアクセスするためのライセンスを必要とします。ユーザー アカウントにライセンスを割り当てる期間は作成後 30 日です。</span><span class="sxs-lookup"><span data-stu-id="69431-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="69431-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="69431-130">**Password**</span></span> <br/> |<span data-ttu-id="69431-131">いいえ</span><span class="sxs-lookup"><span data-stu-id="69431-131">No</span></span>  <br/> | <span data-ttu-id="69431-p105">パスワードを指定しない場合、ランダムなパスワードがユーザー アカウントに割り当てられ、パスワードはコマンドの結果に表示されます。パスワードを指定する場合、小文字、大文字、数字、記号のうちの 3 つの種類の文字を使った 8 から 16 文字の ASCII テキスト文字にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="69431-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="69431-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="69431-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="69431-135">いいえ</span><span class="sxs-lookup"><span data-stu-id="69431-135">No</span></span>  <br/> |<span data-ttu-id="69431-p106">これは、有効な ISO 3166-1 alpha-2 の国別コードです。たとえば、米国は US、フランスは FR です。いくつかの Office 365 サービスは特定の国では使用できないため、この値を提供することは重要です。アカウントにこの値を設定しない限り、ユーザー アカウントにライセンスを割り当てることはできません。詳細については、「[ライセンスによる使用制限について](https://go.microsoft.com/fwlink/p/?LinkId=691730)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69431-p106">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="69431-140">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="69431-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="69431-141">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="69431-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="69431-142">接続したら、以下の構文を使用して個別のアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="69431-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="69431-143">この例では、米国の Caleb Sills というユーザーのアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="69431-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="69431-144">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="69431-144">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

<span data-ttu-id="69431-145">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="69431-145">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="69431-146">個別のユーザー アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="69431-146">Create an individual user account</span></span>

<span data-ttu-id="69431-147">個別のアカウントを作成するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="69431-147">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

<span data-ttu-id="69431-148">使用可能なライセンスのプラン名を一覧表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="69431-148">To list the available licensing plan names, use this command:</span></span>

````
Get-MsolAccountSku
````

<span data-ttu-id="69431-149">この例では、米国の Caleb Sills という名前のユーザーにアカウントを作成し、 `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="69431-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="69431-150">複数のユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="69431-150">Create the user accounts.</span></span>

1. <span data-ttu-id="69431-p107">必要なユーザー アカウント情報を含むコンマ区切り (CSV) ファイルを作成します。例:</span><span class="sxs-lookup"><span data-stu-id="69431-p107">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="69431-153">CSV ファイルの最初の行の列名と順序は任意ですが、ファイルの残りの部分のデータが列名の順序と一致するかどうかを確認し、Office 365 PowerShell コマンドのパラメーター値に列名を使用します。</span><span class="sxs-lookup"><span data-stu-id="69431-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="69431-154">次の構文を使用してください。</span><span class="sxs-lookup"><span data-stu-id="69431-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="69431-155">この例は、C:\My Documents\NewAccounts.csv という名前のファイルからユーザー アカウントを作成し、C:\My Documents\NewAccountResults.csv という名前のファイルに結果を記録します。</span><span class="sxs-lookup"><span data-stu-id="69431-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="69431-p108">出力ファイルで結果を確認します。パスワードを指定しなかったため、Office 365 により生成されたランダムなパスワードが出力ファイルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="69431-p108">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="69431-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="69431-158">See also</span></span>

[<span data-ttu-id="69431-159">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="69431-159">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="69431-160">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="69431-160">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="69431-161">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="69431-161">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
