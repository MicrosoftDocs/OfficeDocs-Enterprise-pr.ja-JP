---
title: "Office 365 PowerShell を使用してユーザー アカウントを作成する"
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
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: "Office 365 PowerShell を使用して Office 365 でユーザー アカウントを作成する方法について学習します。"
ms.openlocfilehash: 9f6eb4cafa82ae511e806b7e32f2ed98a065d52e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="7fb66-103">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="7fb66-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="7fb66-104">**の概要:**Office 365 の PowerShell を使用して Office 365 のユーザー アカウントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7fb66-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="7fb66-p101">Office 365 PowerShell を使用すると、特に複数のユーザー アカウントを効率的に作成できます。Office 365 PowerShell でユーザー アカウントを作成する場合、特定のプロパティは常に必須です。他のプロパティはアカウントを作成する際に必須ではありませんが、別の面で重要となります。次の表で、これらのプロパティを説明します。</span><span class="sxs-lookup"><span data-stu-id="7fb66-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
****

|<span data-ttu-id="7fb66-109">**プロパティ名**</span><span class="sxs-lookup"><span data-stu-id="7fb66-109">**Property name**</span></span>|<span data-ttu-id="7fb66-110">**必須かどうか**</span><span class="sxs-lookup"><span data-stu-id="7fb66-110">**Required?**</span></span>|<span data-ttu-id="7fb66-111">**説明**</span><span class="sxs-lookup"><span data-stu-id="7fb66-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="7fb66-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="7fb66-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="7fb66-113">はい</span><span class="sxs-lookup"><span data-stu-id="7fb66-113">Yes</span></span>  <br/> |<span data-ttu-id="7fb66-p102">これは、Office 365 サービスで使用される表示名です。たとえば、Caleb Sills。</span><span class="sxs-lookup"><span data-stu-id="7fb66-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="7fb66-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="7fb66-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="7fb66-117">はい</span><span class="sxs-lookup"><span data-stu-id="7fb66-117">Yes</span></span>  <br/> |<span data-ttu-id="7fb66-p103">これは、Office 365 サービスにサインインするために使用されるアカウント名です。たとえば、CalebS@contoso.onmicrosoft.com。</span><span class="sxs-lookup"><span data-stu-id="7fb66-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="7fb66-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="7fb66-120">**FirstName**</span></span> <br/> |<span data-ttu-id="7fb66-121">いいえ</span><span class="sxs-lookup"><span data-stu-id="7fb66-121">No</span></span>  <br/> ||
|<span data-ttu-id="7fb66-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="7fb66-122">**LastName**</span></span> <br/> |<span data-ttu-id="7fb66-123">いいえ</span><span class="sxs-lookup"><span data-stu-id="7fb66-123">No</span></span>  <br/> ||
|<span data-ttu-id="7fb66-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="7fb66-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="7fb66-125">いいえ</span><span class="sxs-lookup"><span data-stu-id="7fb66-125">No</span></span>  <br/> |<span data-ttu-id="7fb66-p104">これはライセンシング プラン (ライセンス プラン、Office 365 プラン、SKU とも呼ばれる) で、ここから使用可能なライセンスがユーザー アカウントに割り当てられます。ライセンスによって、アカウントに利用できる Office 365 サービスが定義されます。アカウントを作成するときにユーザーにライセンスを割り当てる必要はありませんが、アカウントは Office 365 サービスにアクセスするためのライセンスを必要とします。ユーザー アカウントにライセンスを割り当てる期間は作成後 30 日です。</span><span class="sxs-lookup"><span data-stu-id="7fb66-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.  </span></span><br/> <span data-ttu-id="7fb66-p105">組織で利用可能なライセンスとライセンスの計画 ( **AccountSkuId** ) を表示するのには、 **Get MsolAccountSku**コマンドレットを使用します。詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fb66-p105">Use the **Get-MsolAccountSku** cmdlet to view the licensing plans ( **AccountSkuId** ) and available licenses in your organization. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  </span></span><br/> |
|<span data-ttu-id="7fb66-132">**Password**</span><span class="sxs-lookup"><span data-stu-id="7fb66-132">**Password**</span></span> <br/> |<span data-ttu-id="7fb66-133">いいえ</span><span class="sxs-lookup"><span data-stu-id="7fb66-133">No</span></span>  <br/> | <span data-ttu-id="7fb66-p106">パスワードを指定しない場合、ランダムなパスワードがユーザー アカウントに割り当てられ、パスワードはコマンドの結果に表示されます。パスワードを指定する場合、次の複雑さの条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fb66-p106">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to meet the following complexity requirements:</span></span> <br/>  <span data-ttu-id="7fb66-136">8 から 16 文字の ASCII テキスト文字。</span><span class="sxs-lookup"><span data-stu-id="7fb66-136">8 to 16 ASCII text characters.</span></span> <br/>  <span data-ttu-id="7fb66-137">次のうちの 3 つの種類の文字: 小文字、大文字、数字、記号。</span><span class="sxs-lookup"><span data-stu-id="7fb66-137">Characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="7fb66-138">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="7fb66-138">**UsageLocation**</span></span> <br/> |<span data-ttu-id="7fb66-139">いいえ</span><span class="sxs-lookup"><span data-stu-id="7fb66-139">No</span></span>  <br/> |<span data-ttu-id="7fb66-p107">これは、有効な ISO 3166-1 alpha-2 の国別コードです。たとえば、米国は US、フランスは FR です。いくつかの Office 365 サービスは特定の国では使用できないため、この値を提供することが重要です。アカウントにこの値を設定しない限り、ユーザー アカウントにライセンスを割り当てることはできません。詳細については、「[ライセンスによる使用制限について](https://go.microsoft.com/fwlink/p/?LinkId=691730)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fb66-p107">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   
## <a name="before-you-begin"></a><span data-ttu-id="7fb66-144">開始する前に</span><span class="sxs-lookup"><span data-stu-id="7fb66-144">Before you begin</span></span>

<span data-ttu-id="7fb66-p108">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fb66-p108">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a><span data-ttu-id="7fb66-147">Office 365 PowerShell を使用して個別のユーザー アカウントを作成します</span><span class="sxs-lookup"><span data-stu-id="7fb66-147">Use Office 365 PowerShell to create individual user accounts</span></span>

<span data-ttu-id="7fb66-148">個別のアカウントを作成するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="7fb66-148">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

<span data-ttu-id="7fb66-149">この例では、米国の Caleb Sills という名前のユーザーにアカウントを作成し、 `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7fb66-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a><span data-ttu-id="7fb66-150">Office 365 PowerShell を使用して複数のユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="7fb66-150">Use Office 365 PowerShell to create multiple user accounts</span></span>

1. <span data-ttu-id="7fb66-p109">必要なユーザー アカウント情報を含むコンマ区切り (CSV) ファイルを作成します。例:</span><span class="sxs-lookup"><span data-stu-id="7fb66-p109">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="7fb66-153">列名と CSV ファイルの最初の行の順序は任意ですが、ファイルの残りの部分のデータには、列名の順序が一致するかどうかを確認、パラメーターの値の列名を使用して、Office 365 の PowerShell コマンドで</span><span class="sxs-lookup"><span data-stu-id="7fb66-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="7fb66-154">次の構文を使用してください。</span><span class="sxs-lookup"><span data-stu-id="7fb66-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="7fb66-155">この例は、C:\My Documents\NewAccounts.csv という名前のファイルからユーザー アカウントを作成し、C:\My Documents\NewAccountResults.csv という名前のファイルに結果を記録します。</span><span class="sxs-lookup"><span data-stu-id="7fb66-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="7fb66-p110">出力ファイルで結果を確認します。パスワードを指定しなかったため、生成されたランダムなパスワードが出力ファイルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fb66-p110">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a><span data-ttu-id="7fb66-158">個別のユーザー アカウントを作成するには Azure Active Directory V2 PowerShell モジュールを使用します</span><span class="sxs-lookup"><span data-stu-id="7fb66-158">Use the Azure Active Directory V2 PowerShell module to create individual user accounts</span></span>

<span data-ttu-id="7fb66-p111">Azure Active Directory V2 PowerShell モジュールから**新しい AzureADUser**コマンドレットを使用するには、まずお客様のサブスクリプションに接続する必要があります。この手順では、 [Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fb66-p111">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="7fb66-161">接続したら、以下の構文を使用して個別のアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7fb66-161">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="7fb66-162">この例では、米国の Caleb Sills というユーザーのアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7fb66-162">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a><span data-ttu-id="7fb66-163">See also</span><span class="sxs-lookup"><span data-stu-id="7fb66-163">See also</span></span>

<span data-ttu-id="7fb66-164">Office 365 の PowerShell でユーザーを管理する方法は次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fb66-164">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="7fb66-165">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="7fb66-165">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="7fb66-166">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="7fb66-166">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="7fb66-167">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="7fb66-167">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="7fb66-168">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="7fb66-168">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="7fb66-169">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7fb66-169">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="7fb66-170">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="7fb66-170">Export-Csv</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [<span data-ttu-id="7fb66-171">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="7fb66-171">Import-Csv</span></span>](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)
    
- [<span data-ttu-id="7fb66-172">新しい-MsolUser</span><span class="sxs-lookup"><span data-stu-id="7fb66-172">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="7fb66-173">ForEach オブジェクト</span><span class="sxs-lookup"><span data-stu-id="7fb66-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="7fb66-174">新しい-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="7fb66-174">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

