---
title: "Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する"
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
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Office 365 PowerShell を使用して、ユーザーに割り当てられている Office 365 ライセンスを削除する方法について説明します。"
ms.openlocfilehash: 21aed391cf0395bf51a7e99cf9f8f0e34bfd9d10
ms.sourcegitcommit: f10e47df0dca4a241659f33061db5217ebc3401e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="6a258-103">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="6a258-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="6a258-104">**概要:** Office 365 PowerShell を使用して、ユーザーに割り当てられている Office 365 ライセンスを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6a258-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="6a258-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="6a258-105">Before you begin</span></span>

- <span data-ttu-id="6a258-p101">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a258-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6a258-108">組織のライセンス プラン ( **AccountSkuID** ) 情報を表示する方法については、以下のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6a258-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="6a258-109">Office 365 PowerShell でライセンスとサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="6a258-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="6a258-110">Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="6a258-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="6a258-111">_-All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="6a258-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="6a258-112">簡略版 (説明なしの手順)</span><span class="sxs-lookup"><span data-stu-id="6a258-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="6a258-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="6a258-113"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="6a258-p102">このセクションでは、余分な説明を省いて簡潔に手順を示します。ご質問がある場合、または詳細情報が必要な場合には、このトピックの残りの部分をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6a258-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="6a258-116">既存のユーザー アカウントからライセンスを削除するには、次の構文を使用します:</span><span class="sxs-lookup"><span data-stu-id="6a258-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="6a258-117">次の例では、ユーザー アカウント BelindaN@litwareinc.com から  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="6a258-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="6a258-118">ライセンス付与済みの既存のユーザーのグループからライセンスを削除するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a258-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="6a258-119">**既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a258-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="6a258-120">この例では、米国内の販売部門のユーザーのすべてのアカウントから  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="6a258-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="6a258-121">**特定のアカウントの一覧を使用する** これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6a258-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="6a258-122">次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成し、保存します。</span><span class="sxs-lookup"><span data-stu-id="6a258-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="6a258-123">次の構文を使用してください。</span><span class="sxs-lookup"><span data-stu-id="6a258-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="6a258-124">この例では、テキスト ファイル C:\My Documents\Accounts.txt で定義されているユーザー アカウントから `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="6a258-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="6a258-125">既存のすべてのユーザー アカウントからライセンスを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a258-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="6a258-126">次の例では、ライセンスを付与された既存の全ユーザー アカウントから  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="6a258-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="6a258-127">詳細版 (詳細な説明付きの手順)</span><span class="sxs-lookup"><span data-stu-id="6a258-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="6a258-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="6a258-128"><a name="LongVersion"> </a></span></span>

<span data-ttu-id="6a258-p103">永遠に続くものなどありません。これは Office 365 のライセンスにも該当します。遅かれ早かれユーザー アカウントからライセンスを削除しなければならないときがきます。休暇をとる、ライセンスが必要でなくなるなど、ユーザー ライセンスを削除する理由は無数にあります。</span><span class="sxs-lookup"><span data-stu-id="6a258-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="6a258-p104">詳しい説明に入る前に、気を付けなければならない重要なポイントは、ライセンスを削除するには、やはりライセンスを削除しなければならないという点です。つまり、ライセンスのすべてのサービスを無効にしても、それはライセンスの削除とはなりません。たとえば、Office 365 のライセンスをすべて使用してしまい、利用できるライセンスが 1 つもないとします。「[Office 365 PowerShell を使ったサービスへのアクセスを無効にする](disable-access-to-services-with-office-365-powershell.md)」の手順に従って、たとえば Belinda Newman のアカウントのすべてのサービスを無効にすることにします。このコマンドを実行した後、利用できるライセンスの数はいくつになりますか?そうです。ゼロです。このトピックの手順では、Belinda のライセンスのすべてのサービスを *無効*  にしますが、ライセンス自体を無効にする (つまり、削除する) わけではありません。ライセンスは有効のままで、Belinda Newman に割り当てられたままです。Belinda は、このライセンスを使用して Office 365 のサービスにアクセスできなくなるにすぎません。</span><span class="sxs-lookup"><span data-stu-id="6a258-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="6a258-p105">これは重要なポイントです。ユーザーからライセンスを削除する場合は、実際にライセンスを *削除*  する必要があります。サービスをすべて無効にすると、ユーザーは Office 365 にログオンできなくなりますが、ライセンスが解放されるわけではありません。ユーザーに現在割り当てられているライセンスを削除する場合は、次のようなコマンドを実行する必要があります。このコマンドでは、 _RemoveLicenses_ パラメーターを使用して、以前に Belinda に割り当てたライセンスを実際に削除します。</span><span class="sxs-lookup"><span data-stu-id="6a258-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="6a258-142">このコマンドを実行すると、Belinda Newman に Office 365 を使用するライセンスが付与された状態ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="6a258-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6a258-p106">ご覧のように、_RemoveLicenses_ パラメーターを使用する場合は、削除するライセンスの名前を指定する必要があります。どのライセンス プランを使用してライセンスをユーザーに割り当てたのかわからない場合は、次のようなコマンドを実行します。`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="6a258-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="6a258-145">ライセンスが本当に削除されていることを確認するには、Get-MsolUser を使用して対象のユーザー アカウントを確認します。</span><span class="sxs-lookup"><span data-stu-id="6a258-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="6a258-146">すべてが予定どおりであれば、Belinda の **isLicensed** プロパティは `False` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="6a258-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="6a258-p107">別の方法として、ユーザー アカウントを削除してライセンスを解放することもできます。詳細については、「[Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a258-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6a258-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a258-149">See also</span></span>

<span data-ttu-id="6a258-150">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6a258-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="6a258-151">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="6a258-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6a258-152">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="6a258-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6a258-153">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="6a258-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6a258-154">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="6a258-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="6a258-155">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6a258-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="6a258-156">Get-Content</span><span class="sxs-lookup"><span data-stu-id="6a258-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="6a258-157">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="6a258-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="6a258-158">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="6a258-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="6a258-159">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="6a258-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="6a258-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="6a258-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="6a258-161">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="6a258-161">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

