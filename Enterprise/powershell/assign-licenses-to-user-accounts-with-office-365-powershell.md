---
title: "Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる"
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。"
ms.openlocfilehash: 88628a78179605c734cd1d3f114a8a1dcb712376
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="053f2-103">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="053f2-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="053f2-104">**概要:** Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="053f2-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="053f2-p101">ユーザーは自分のアカウントにライセンスが供与されるまで Office 365 サービスを一切使用できないため、Office 365 のユーザー アカウントへのライセンス供与は重要です。Office 365 PowerShell を使用することにより、効率的にライセンスをライセンスのないアカウント、特に複数のアカウントに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="053f2-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="053f2-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="053f2-107">Before you begin</span></span>
<span data-ttu-id="053f2-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="053f2-108"><a name="RTT"> </a></span></span>

- <span data-ttu-id="053f2-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="053f2-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="053f2-p103">**Get-MsolAccountSku** コマンドレットを使用して、利用可能なライセンス プランと組織で利用可能なライセンスのプランごとの数を表示します。各プランで利用可能なライセンスの数は、**ActiveUnits** - **WarningUnits** - **ConsumedUnits** です。ライセンス プラン、ライセンス、サービスの詳細については、「[Office 365 PowerShell でライセンスとサービスを確認する](view-licenses-and-services-with-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="053f2-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="053f2-114">組織内のライセンスのないアカウントを検索するには、コマンド  `Get-MsolUser -All -UnlicensedUsersOnly` を実行します。</span><span class="sxs-lookup"><span data-stu-id="053f2-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="053f2-p104">ライセンスは、**UsageLocation** プロパティが有効な ISO 3166-1 alpha-2 の国別コードに設定されているユーザー アカウントにのみ割り当てることができます。たとえば、米国は US、フランスは FR です。一部の Office 365 サービスは特定の国では使用できません。詳細については、「[ライセンスによる使用制限について](https://go.microsoft.com/fwlink/p/?LinkId=691730)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="053f2-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="053f2-p105">**UsageLocation** 値のないアカウントを検索するには、コマンド `Get-MsolUser -All | where {$_.UsageLocation -eq $null}` を実行します。アカウントに **UsageLocation** 値を設定するには、構文 `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>` を使用します。例: `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。</span><span class="sxs-lookup"><span data-stu-id="053f2-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="053f2-122">`-All` パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="053f2-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="053f2-123">簡略版 (説明なしの手順)</span><span class="sxs-lookup"><span data-stu-id="053f2-123">The short version (instructions without explanations)</span></span>
<span data-ttu-id="053f2-124"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="053f2-124"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="053f2-p106">このセクションでは、詳細な説明を省いて手順を示します。ご質問がある場合、または詳細情報が必要な場合には、このトピックの残りの部分をお読みください。</span><span class="sxs-lookup"><span data-stu-id="053f2-p106">This section presents the procedures without detailed explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="053f2-127">ユーザーにライセンスを割り当てるには、Office 365 PowerShell で次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="053f2-127">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="053f2-128">この例では、ライセンスを `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスのないユーザー `belindan@litwareinc.com` に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="053f2-128">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="053f2-129">ライセンスのない多数のユーザーにライセンスを割り当てるには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="053f2-129">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="053f2-130">**メモ**</span><span class="sxs-lookup"><span data-stu-id="053f2-130">**Notes**</span></span>
  
- <span data-ttu-id="053f2-131">複数のライセンスを同じライセンス プランのユーザーに割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="053f2-131">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="053f2-132">十分な数の利用可能なライセンスをお持ちでない場合は、使用可能なライセンスがなくなるまで、ライセンスは **Get-MsolUser** コマンドレットによって返される順序でユーザーに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="053f2-132">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="053f2-133">この例では、ライセンスを `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスのないユーザーすべてに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="053f2-133">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="053f2-134">この例では、これらの同じライセンスを米国内にある営業部のライセンスのないユーザーに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="053f2-134">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="053f2-135">詳細版 (詳細な説明付きの手順)</span><span class="sxs-lookup"><span data-stu-id="053f2-135">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="053f2-136"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="053f2-136"><a name="LongVersion"> </a></span></span>

<span data-ttu-id="053f2-p107">「[ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する](view-licensed-and-unlicensed-users-with-office-365-powershell.md)」で説明しているように、有効な Office 365 ユーザー アカウントを所有していても、Office 365 のライセンスが発行されていないユーザーが存在する可能性があります。ライセンスのないユーザーは、有効なアカウントがあるかどうかにかかわらず、Office 365 にログオンできません。そしてログオンできなければ、Office 365 のサービスを利用できません。</span><span class="sxs-lookup"><span data-stu-id="053f2-p107">As noted in the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), it's possible to have users who have valid Office 365 user accounts, but who have not been issued an Office 365 license. That means that, valid account or no valid account, those users will not be able to log on to Office 365. And if you can't log on, you can't take advantage of any Office 365 services.</span></span>
  
<span data-ttu-id="053f2-140">前述の記事では、次のコマンドを実行すると、ライセンスのないユーザー アカウントの一覧を取得できると説明しています。</span><span class="sxs-lookup"><span data-stu-id="053f2-140">The aforementioned article also noted that we can return a list of unlicensed user accounts by running this command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="053f2-141">このコマンドは、Office 365 のライセンスを現在所有していないユーザーに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="053f2-141">That command returns information about any users who are not currently licensed for Office 365:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="053f2-p108">ご覧のように、ライセンスのないユーザーが 1 人表示されています。それは Belinda Newman です。Belinda に Office 365 のライセンスを割り当てるには、どのような方法がありますか?</span><span class="sxs-lookup"><span data-stu-id="053f2-p108">As you can see, we have one unlicensed user: Belinda Newman. So how do we go about assigning Belinda an Office 365 license?</span></span>
  
<span data-ttu-id="053f2-144">まず、「[Office 365 PowerShell でライセンスとサービスを確認する](view-licenses-and-services-with-office-365-powershell.md)」の記事で説明されている **Get-MsolAccountSku** コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="053f2-144">For starters, we're going to run the **Get-MsolAccountSku** cmdlet discussed in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="053f2-145">このコマンドを実行すると、以下のようなデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="053f2-145">That command returns data similar to this:</span></span>
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

<span data-ttu-id="053f2-p109">なぜ **Get-MsolAccountSku** を実行するのでしょうか? (念のために付け加えますが、"Sku" は "Stock Keeping Unit" (最小在庫管理単位) の略です。ここでは、"製品" に対応する業界用語だと思っていただければ十分です。) **Get-MsolAccountSku** を実行する理由は 2 つあります。まず、Belinda に割り当てるライセンスが実際にあるかどうかを確認する必要があります。Belinda に割り当てられるライセンスはありますか?これを確認するには、 **ActiveUnits** プロパティ値 (25) から、 **WarningUnits** プロパティ値 (0) と **ConsumedUnits** プロパティ値 (24) を差し引きます。</span><span class="sxs-lookup"><span data-stu-id="053f2-p109">Why did we run **Get-MsolAccountSku** ? ("Sku," in case you're wondering, is short for "stock-keeping unit." For our purposes, that's just business-speak for "product.") There are two reasons why we ran **Get-MsolAccountSku**. First, we need to make sure we actually have a license to assign Belinda. Do we have any licenses we can assign her? To determine that, we take the value of **ActiveUnits** property (25) and subtract the values of the **WarningUnits** (0) and **ConsumedUnits** (24) properties:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="053f2-p110">**ActiveUnits** プロパティは購入したライセンスの数を示し、 **WarningUnits** と **ConsumedUnits** の合計値は現在使用されているライセンスの数を示します。購入したライセンス数から配布済みのライセンス数を引くと、現在の利用可能なライセンス数が得られます。幸いにも、配布できるライセンスが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="053f2-p110">The **ActiveUnits** property tells us how many licenses we've purchased, and the combined value of **WarningUnits** and **ConsumedUnits** tells us how many licenses are currently in use. If we subtract the number of licenses already spoken for from the number of licenses we purchased, we'll know how many licenses are still available. As luck would have it, we have one license available for distribution:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="053f2-p111">次に、Belinda に新しいライセンスを割り当てるには、ライセンス プランの名前を知る必要があります (つまり、 **AccountSkuId** を知る必要があります)。これは簡単です。ライセンス プランは 1 つしかありません ( `litwareinc:ENTERPRISEPACK`)。ただし、組織が複数のライセンス プランを持っている場合もあります。この場合、 **Get-MsolAccountSku** は 2 つの異なる **AccountSkuIds** を返し、ライセンスを割り当てるときは適切なライセンス プランを選択する必要があります。ただしここでは、最も単純なケースにこだわり、1 つのライセンス プランだけを所有しているものとします。</span><span class="sxs-lookup"><span data-stu-id="053f2-p111">Second, in order to assign Belinda a new license we need to know the name of our licensing plan (that is, we need to know the **AccountSkuId** ). In this case, that's easy: we only have a single licensing plan ( `litwareinc:ENTERPRISEPACK`). Note, however, that it's possible for an organization to have multiple licensing plans. In that case, **Get-MsolAccountSku** would return two different **AccountSkuIds**, and you would need to pick the appropriate licensing plan when assigning licenses. For now, though, we're going to stick with the simplest case, and assume we have just one licensing plan.</span></span>
  
<span data-ttu-id="053f2-p112">では、Belinda Newman に新しいライセンスを割り当てるには、どうすればよいでしょうか?以下のようにします。</span><span class="sxs-lookup"><span data-stu-id="053f2-p112">So then how  *do*  we assign Belinda Newman a new license? Like this:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="053f2-162">さらに、 **Set-MsolUserLicense** コマンドレットを呼び出して、ユーザーの _UserPrincipalName_ パラメーターと適切なライセンス プランを指定していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="053f2-162">That's also you have to do: just call the **Set-MsolUserLicense** cmdlet, making sure that you specify the _UserPrincipalName_ parameter for the user and the appropriate licensing plan.</span></span>
  
<span data-ttu-id="053f2-163">**Set-MsolUserLicense** の実行が完了すると、次のような画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="053f2-163">When **Set-MsolUserLicense** finishes running, you'll see something similar to this onscreen:</span></span>
  
 `PS C:\\windows\\system32>`
  
<span data-ttu-id="053f2-p113">別の言い方をすれば、何も実行されなかったかのように見えます。ユーザーにライセンスが割り当てられていることを確認するには、次のようなコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="053f2-p113">In other words, it won't look like anything has happened. To verify that the user has been assigned a license, run a command like the following:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

<span data-ttu-id="053f2-166">すべてが想定どおりに動作した場合、Belinda の isLicensed プロパティが True に設定されていることを確認できるはずです。</span><span class="sxs-lookup"><span data-stu-id="053f2-166">If everything worked as expected, you should see that Belinda's isLicensed property is now set to True:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [!SECURITY NOTE]<span data-ttu-id="053f2-p114"> おそらく次のような疑問を抱かれるでしょう。すでにライセンスを所有しているユーザーに間違ってライセンスを割り当てようとしたらどうなりますか?1 人のユーザーに 2 つのライセンスを割り当てることになりますか? > この疑問の簡潔な答えは、「いいえ」です。Office 365 は同じユーザーに 2 つ以上のライセンスを割り当てることはありません。(同じライセンス プランから複数のライセンスを割り当てることはあります。)そうしようとすると、次のエラー メッセージが表示されてコマンドは失敗します。 >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> このエラー メッセージは、少し誤解を与える可能性があります。実際はライセンスが無効なのではなく、ライセンスをすでに *所有している*  ユーザーに割り当てようとしているだけです。エラー メッセージはともかくとして、重要な点は、1 人のユーザーに複数のライセンスが割り当てられることはないという点です。</span><span class="sxs-lookup"><span data-stu-id="053f2-p114"> Good question: what if you made a mistake and tried to assign a license to a user who already has a license? Will you end up giving two licenses to a single user? > The quick answer? No; Office 365 won't let you assign more than one license to the same user. (Well, more than one license from the same licensing plan, that is.) If you try to do that your command will fail with the following error message: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Admittedly, that error message is a tiny bit misleading: the license isn't really invalid, it's just being assigned to a user who already  *has*  a license. But, error message aside, the important thing is that one user won't end up with multiple licenses.</span></span>
  
<span data-ttu-id="053f2-p115">今確認したように、Office 365 PowerShell を使用して 1 つのライセンスを 1 人のユーザーに割り当てることはとても簡単です。しかし、次のような疑問を抱かれるでしょう。Office 365 管理センター を使用すれば、1 つのライセンスを 1 人のユーザーに割り当てる作業が同じように、あるいはもっと簡単でしょうか? そうかもしれません。それは Windows PowerShell を使い慣れているか、Office 365 管理センター を使い慣れているかによっても異なります。ただし、Windows PowerShell が本当に役に立つのは、複数のライセンスを複数のユーザーに割り当てる必要がある場合です。たとえば、次のコマンドは、まだライセンスを所有していないユーザーに、Office 365 のライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="053f2-p115">As you've just seen, it's very easy to use Office 365 PowerShell to assign a single license to a single user. And that leads to an obvious question: wouldn't it be just as easy, maybe even easier, to use the Office 365 admin center to assign a single license to a single user? Well, maybe; that depends, in part, on whether you're more comfortable using Windows PowerShell or more comfortable using the Office 365 admin center. Where Windows PowerShell really shines, however, is when you need to assign multiple licenses to multiple users. For example, this command assigns an Office 365 license to any of your users that don't already have a license:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="053f2-p116">前のコマンドでは、 **Get-MsolUser** パラメーターと _UnlicensedUsersOnly_ パラメーターを使用して、ライセンスのないすべてのユーザー アカウントのコレクションを返します。それから、このコレクションを **Set-MsolUserLicense** コマンドレットに渡します。次に、 **Set-MsolUserLicense** が ( `litwareinc:ENTERPRISEPACK` ライセンス プランから取り出した) ライセンスをコレクションの各ユーザーに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="053f2-p116">In the preceding command, we use **Get-MsolUser** and the _UnlicensedUsersOnly_ parameter to return a collection of all the unlicensed user accounts. We then pass that collection to the **Set-MsolUserLicense** cmdlet; in turn, **Set-MsolUserLicense** assigns a license (taken from the `litwareinc:ENTERPRISEPACK` licensing plan) to each user in the collection.</span></span>
  
<span data-ttu-id="053f2-p117">しかし、ライセンスのないユーザーが 5 人いるのに、利用できるライセンスが 1 つしかない場合はどうすればよいでしょうか? この場合、 **Set-MsolUserLicense** は利用可能なライセンスを **Get-MsolUser** によって返された最初のユーザーに付与します。 **Set-MsolUserLicense** は他の 4 人のユーザーにもライセンスを割り当てようとしますが、その 4 人分の試行はすべて失敗し、次のエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="053f2-p117">Ah, but what if you have 5 unlicensed users but only one available license? In that case **Set-MsolUserLicense** will give the available license to the first user returned by **Get-MsolUser**. **Set-MsolUserLicense** will then dutifully try to assign a license to the other four users, but all four of those attempts will fail along with the following error message:</span></span>
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
<span data-ttu-id="053f2-p118">言い換えると、Set-MsolUserLicense はただ失敗するだけではなく、できるだけ多くのライセンスを割り当てようとします。そのあとで、コマンドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="053f2-p118">In other words, Set-MsolUserLicense won't just fail. Instead, it will assign as many licenses as it can. Only then will it fail.</span></span>
  
<span data-ttu-id="053f2-p119">別の例を試してみましょう。セールス部門のユーザー全員にライセンスを割り当てようとすることもあるでしょう。その場合は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="053f2-p119">Let's try another example. Maybe you'd like to assign a license to all the users in the Sales department. No problem:</span></span>
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="053f2-189">あるいは、エラー メッセージとコンピューティング プロセスを最小限に抑えたい場合は、次のようにしてライセンスをセールス部門のうちライセンスのないユーザーに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="053f2-189">Or, if you want to get really fancy, and if you want to keep error messages and computing processing to a minimum, just assigned a license to unlicensed users from the Sales department:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="053f2-p120">つまり、ライセンスをすでに所有しているユーザーにライセンスを付与しようとしても意味がありません。前述のように、その操作はうまくいきません。</span><span class="sxs-lookup"><span data-stu-id="053f2-p120">After all, there's no point trying to license users who already have a license. As we've already seen, that won't work.</span></span>
  
<span data-ttu-id="053f2-p121">別の例を考えましょう。現在 Office 365 のライセンスを所有していない米国のすべてのユーザーにライセンスを付与するとします。その場合は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="053f2-p121">Here's another example. Maybe you'd like to license all the US users who don't currently have an Office 365 license. In that case:</span></span>
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="053f2-195">このようにやっていきます。</span><span class="sxs-lookup"><span data-stu-id="053f2-195">And so on and so on.</span></span>
  
> [!NOTE]
> <span data-ttu-id="053f2-p122">では、ライセンスのないのユーザーすべてにライセンスを発行するコマンドを実行するには、どのくらい時間がかかるでしょうか? これは答えるのが難しい質問です。これは、ユーザーの数からネットワーク接続の速度に至るまで、あらゆる要素に依存します。ライセンスを付与するユーザーが数百人なら、かなり短時間で終わります (1 - 2 分以下)。ライセンスを付与するユーザーが 10,000 人の場合は、明らかにもう少し時間がかかります。ただし、Office 365 管理センター を使用して 10,000 人のユーザーにライセンスを割り当てる場合ほど長くはありません。</span><span class="sxs-lookup"><span data-stu-id="053f2-p122">How long does it take to run a command that, say, issues licenses to all your unlicensed users? That's difficult to say: it depends on everything from the number of users you have to the speed of your network connection. If you have a couple hundred users to license this will go reasonably quickly (that is, it shouldn't take more than a minute or two). If you have 10,000 users to license it will obviously take a little longer. But nowhere near as long as it would take to assign licenses to 10,000 users by using the Office 365 admin center.</span></span> 
  
<span data-ttu-id="053f2-p123">この件に関する限り、ライセンスの割り当てでは次の点に注意する必要があります。ユーザーの **UsageLocation** プロパティの値が設定されていない場合、Office 365 のライセンスをそのユーザーに割り当てることはできません。代わりに、次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="053f2-p123">As long as we're on the subject, here's something you need to watch out for when assigning licenses: if a user does not have a value configured for the **UsageLocation** property you won't be able to assign that user an Office 365 license. Instead, you'll get an error message similar to this:</span></span>
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
<span data-ttu-id="053f2-p124">このエラー メッセージは、やや間接的ですが、対象のユーザーに **UsageLocation** が割り当てられていないことを示しています。ご想像のとおり、(ユーザーが通常 Office 365 を使用する地域や国を示す) **UsageLocation** プロパティは、非常に重要です。その理由は、ユーザーが利用できるサービスは、購入したライセンス パックだけでなく、ユーザーの居住地によっても異なるからです。地域の法律や規制により、一部のサービスを利用できないユーザーもいます。ユーザーの **UsageLocation** がない場合、Office 365 はそのユーザーに対してどのサービスを合法的に公開できるのかがわかりません。このため、Office 365 はそのユーザーに対して、少なくとも **UsageLocation** が指定されるまではサービスをまったく提供できません。</span><span class="sxs-lookup"><span data-stu-id="053f2-p124">In somewhat-roundabout fashion, this error message tells us that the user in question has not been assigned a **UsageLocation**. As you might have guessed, the **UsageLocation** property (which indicates the region or country where the user typically uses Office 365) is extremely important. Why? That's because the services available to a user depend not only on the licensing pack that you purchased but also on where the user lives: due to local rules and regulations, some services might not be available to some users. If a user doesn't have a **UsageLocation**, Office 365 has no way of knowing which services can legally be exposed to that user. Therefore, Office 365 can't offer any services to that user, at least not until the **UsageLocation** has been specified.</span></span>
  
> [!NOTE]
> <span data-ttu-id="053f2-p125">ユーザー アカウントを構成すると、指定した地域に関連付けられたライセンスの規制がないかどうかがすぐにわかります。たとえば、ライセンスが付与されたユーザーの **UsageLocation** をイラン ( `IR`) に変更すると、次のエラー メッセージを表示してコマンドが失敗します。`Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> これは、現在 Office 365 がイランのユーザーに提供されていないためです。詳細については、「[ライセンスによる使用制限について](https://go.microsoft.com/fwlink/p/?LinkId=691730)」を参照してください。ちなみに、Office 365 は国際標準化機構 (ISO) が作成した 2 文字の国別コードを使用しています。これらのコードについては [ISO の Web サイト](https://go.microsoft.com/fwlink/p/?LinkId=84073)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="053f2-p125">When you configure a user account you'll know immediately if there are any license restrictions associated with the specified part of the world. For example, if you change the **UsageLocation** for a licensed user to Iran ( `IR`), the command will fail with this error message: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> That's because Office 365 is not currently available to users in Iran. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidentally, Office 365 uses the two-letter country codes produced by the International Organization for Standardization (ISO). You can find those codes on the [ISO web site](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span></span> 
  
<span data-ttu-id="053f2-214">特定のユーザーに **UsageLocation** が指定されているかどうかを確認するには、次のようなコマンドを利用できます。</span><span class="sxs-lookup"><span data-stu-id="053f2-214">If you want to verify that a given user has a **UsageLocation** you can use a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

<span data-ttu-id="053f2-215">または、次のコマンドを使用して、**UsageLocation** のないすべてのユーザーの一覧を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="053f2-215">Alternatively, you can return a list of all the users who don't have a **UsageLocation** by using this command:</span></span>
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> <span data-ttu-id="053f2-p126">ユーザーにライセンスを割り当てると、既定ではそのユーザーは、所属する組織がアクセスできるすべての Office 365 サービスへのアクセス権を付与されます。たとえば、Office 365 Enterprise E3 のライセンスを購入した場合、新たにライセンスを割り当てられたユーザーは、Exchange Online、Skype for Business Online、および SharePoint Online などサービスへのアクセス権を自動的に付与されます。ユーザーが利用できるサービスを制限したい場合 (たとえば、SharePoint Online を利用できるものの、Exchange Online と Skype for Business Online を*利用できない*ようにする場合)、記事「[Office 365 PowerShell を使ったサービスへのアクセスを無効にする](disable-access-to-services-with-office-365-powershell.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="053f2-p126">When you assign a license to a user that user will, by default, be given access to all the Office 365 services that your organization has access to. For example, if you purchased licenses for Office 365 Enterprise E3, your newly-licensed user will automatically be granted access to services like Exchange Online, Skype for Business Online, and SharePoint Online. If you would prefer to limit a user's access to those services (for example, you might want a user to have access to SharePoint Online but  *not*  to Exchange Online and Skype for Business Online) then see the article [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span></span> 
  
## <a name="new-to-office-365"></a><span data-ttu-id="053f2-219">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="053f2-219">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="053f2-p127">![LinkedIn Learning の小さいアイコン](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 を初めて使用する場合は、**         LinkedIn Learning が提供する [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5) のための無料のビデオ コースをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="053f2-p127">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="053f2-222">関連項目</span><span class="sxs-lookup"><span data-stu-id="053f2-222">See Also</span></span>
<span data-ttu-id="053f2-223"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="053f2-223"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="053f2-224">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="053f2-224">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="053f2-225">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="053f2-225">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="053f2-226">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="053f2-226">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="053f2-227">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="053f2-227">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="053f2-228">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="053f2-228">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="053f2-229">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="053f2-229">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="053f2-230">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="053f2-230">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="053f2-231">Get-msoluser</span><span class="sxs-lookup"><span data-stu-id="053f2-231">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="053f2-232">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="053f2-232">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="053f2-233">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="053f2-233">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="053f2-234">Select-Object</span><span class="sxs-lookup"><span data-stu-id="053f2-234">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="053f2-235">Where-Object</span><span class="sxs-lookup"><span data-stu-id="053f2-235">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

