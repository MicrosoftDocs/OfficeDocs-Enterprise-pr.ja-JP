---
title: Microsoft 365 で PowerShell を使用する必要がある理由
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: '概要: PowerShell を使用して Microsoft 365 を管理する必要がある理由について説明します。場合によっては効率的で、その他の場合は必要になることがあります。'
ms.openlocfilehash: ba786acd8b5ad08bad97b11812f0180004e55cb6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229863"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a><span data-ttu-id="27415-103">Microsoft 365 で PowerShell を使用する必要がある理由</span><span class="sxs-lookup"><span data-stu-id="27415-103">Why you need to use PowerShell for Microsoft 365</span></span>

<span data-ttu-id="27415-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="27415-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="27415-105">Microsoft 365 管理センターを使用すると、Microsoft 365 のユーザーアカウントとライセンスを管理できるだけでなく、Exchange Online、Teams、SharePoint Online などの Microsoft 365 サービスを管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="27415-105">With the Microsoft 365 admin center, you can not only manage your Microsoft 365 user accounts and licenses, but you can also manage your Microsoft 365 services such as Exchange Online, Teams, and SharePoint Online.</span></span> <span data-ttu-id="27415-106">ただし、これらの要素を PowerShell コマンドで管理することもできます。これには、速度、自動化、および追加機能について、コマンドラインおよびスクリプト言語環境を利用できます。</span><span class="sxs-lookup"><span data-stu-id="27415-106">However, you can also manage these elements with PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="27415-107">この記事では、PowerShell を使用して Microsoft 365 を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="27415-107">In this article, we'll show you these ways in which you can use PowerShell to manage Microsoft 365:</span></span>
  
- <span data-ttu-id="27415-108">Microsoft 365 管理センターでは表示できない追加情報を確認する</span><span class="sxs-lookup"><span data-stu-id="27415-108">Reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>
    
- <span data-ttu-id="27415-109">PowerShell でのみ使用可能な機能と設定を構成する</span><span class="sxs-lookup"><span data-stu-id="27415-109">Configure features and settings only possible with PowerShell</span></span>
    
- <span data-ttu-id="27415-110">一括操作を実行する</span><span class="sxs-lookup"><span data-stu-id="27415-110">Perform bulk operations</span></span>
    
- <span data-ttu-id="27415-111">データのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="27415-111">Filtering data</span></span>
    
- <span data-ttu-id="27415-112">データを印刷または保存する</span><span class="sxs-lookup"><span data-stu-id="27415-112">Print or save data</span></span>
    
- <span data-ttu-id="27415-113">サービス間で管理する</span><span class="sxs-lookup"><span data-stu-id="27415-113">Manage across services</span></span>
    
<span data-ttu-id="27415-114">作業を開始する前に、「Microsoft 365 用の PowerShell」は、windows PowerShell 用のモジュールのセットで、Windows ベースのサービスとプラットフォーム用のコマンドライン環境です。</span><span class="sxs-lookup"><span data-stu-id="27415-114">Before you begin, understand that PowerShell for Microsoft 365 is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms.</span></span> <span data-ttu-id="27415-115">この環境では、コマンドシェル言語が作成されます。これにより、追加モジュールを使用して拡張することができ、単純なコマンドやスクリプトを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="27415-115">This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts.</span></span> <span data-ttu-id="27415-116">たとえば、microsoft 365 モジュールの PowerShell をインストールし、Microsoft 365 サブスクリプションに接続した後、次のコマンドを実行して Microsoft Exchange Online のすべてのユーザーメールボックスを一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="27415-116">For example, after you install the PowerShell for Microsoft 365 modules and connect to your Microsoft 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```powershell
Get-Mailbox
```

<span data-ttu-id="27415-117">メールボックスのリストを取得することも、Microsoft 365 管理センターを使用して簡単に行うことができますが、すべての web アプリのすべてのサイトについて、すべてのリストのアイテム数をカウントすることは簡単に行えません。</span><span class="sxs-lookup"><span data-stu-id="27415-117">Getting the list of mailboxes can also be easily done using the Microsoft 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="27415-118">Microsoft 365 用の PowerShell は、microsoft の365管理センターを置き換えるのではなく、Microsoft の365を管理する機能を強化し、強化するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="27415-118">Please note that PowerShell for Microsoft 365 is designed to augment and enhance your ability to manage Microsoft 365, not to replace the Microsoft 365 admin center.</span></span> <span data-ttu-id="27415-119">管理者は、microsoft 365 コマンドの PowerShell でしか実行できない構成手順があるため、Microsoft 365 での PowerShell の使用に関して、少なくとも使い慣れておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="27415-119">As an administrator, you must become at least comfortable with using PowerShell for Microsoft 365 because there are some configuration procedures that can only be done with PowerShell for Microsoft 365 commands.</span></span> <span data-ttu-id="27415-120">このような場合は、次の方法を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27415-120">In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="27415-121">Microsoft 365 モジュールの PowerShell をインストールします (管理者のコンピューターごとに1回だけ実行されます)。</span><span class="sxs-lookup"><span data-stu-id="27415-121">Install the PowerShell for Microsoft 365 modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="27415-122">Microsoft 365 サブスクリプションに接続します (PowerShell セッションごとに1回実行します)。</span><span class="sxs-lookup"><span data-stu-id="27415-122">Connect to your Microsoft 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="27415-123">Microsoft 365 コマンドに必要な PowerShell を実行するために必要な情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="27415-123">Gather the information needed to run the required PowerShell for Microsoft 365 commands.</span></span>
    
- <span data-ttu-id="27415-124">Microsoft 365 コマンドの PowerShell を正常に実行します。</span><span class="sxs-lookup"><span data-stu-id="27415-124">Run the PowerShell for Microsoft 365 commands successfully.</span></span>
    
<span data-ttu-id="27415-125">これらの基本的なスキルを習得すれば、 **Get-mailbox** コマンドを使用してメールボックス ユーザーの一覧を作成する必要もなければ、すべての Web アプリ用のすべてのサイトのすべての一覧に含まれるすべてのアイテムをカウントするための前述のコマンドのような新しいコマンドを作成する方法を理解する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="27415-125">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps.</span></span> <span data-ttu-id="27415-126">Microsoft と管理者コミュニティは、必要に応じてお手伝いします。</span><span class="sxs-lookup"><span data-stu-id="27415-126">Microsoft and the community of administrators can help you with that as needed.</span></span>
  
## <a name="powershell-for-microsoft-365-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a><span data-ttu-id="27415-127">Microsoft 365 の PowerShell では、Microsoft 365 管理センターでは表示できない追加情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="27415-127">PowerShell for Microsoft 365 can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>

<span data-ttu-id="27415-128">Microsoft 365 管理センターでは、多くの有益な情報が表示されますが、これは、ユーザー、ライセンス、メールボックス、サイトに Microsoft 365 が保存する可能性がある情報をすべて表示するという意味ではありません。</span><span class="sxs-lookup"><span data-stu-id="27415-128">The Microsoft 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Microsoft 365 stores on users, licenses, mailboxes, and sites.</span></span> <span data-ttu-id="27415-129">Microsoft 365 管理センターの**ユーザーとグループ**の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="27415-129">Here is an example for **users and groups** in the Microsoft 365 admin center:</span></span>
  
![Microsoft 365 管理センターでのユーザーとグループの表示例。](media/o365-powershell-users-and-groups.png)
  
<span data-ttu-id="27415-131">ここには、さまざまな理由で把握すべき情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="27415-131">For many purposes, this displays the information you need to know.</span></span> <span data-ttu-id="27415-132">しかし、もっと多くの情報が必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="27415-132">However, there are times when you need more.</span></span> <span data-ttu-id="27415-133">たとえば、Microsoft 365 ライセンス (およびユーザーが使用できる Microsoft 365 機能) は、そのユーザーの地理的な場所によって異なります。</span><span class="sxs-lookup"><span data-stu-id="27415-133">For example, Microsoft 365 licensing (and the Microsoft 365 features available to a user) depend in part on that user's geographic location.</span></span> <span data-ttu-id="27415-134">米国内に在住しているユーザーに対して拡張可能なポリシーと機能は、インドやベルギー在住のユーザーに対して拡張可能なポリシーと機能と同じではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="27415-134">The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium.</span></span> <span data-ttu-id="27415-135">Microsoft 365 管理センターを使用して、ユーザーの地理的な場所を確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="27415-135">You can use the Microsoft 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="27415-136">ユーザーの **表示名** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="27415-136">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="27415-137">ユーザーのプロパティを表示するウィンドウで、 **[詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27415-137">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="27415-138">詳細表示で、 **[追加情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27415-138">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="27415-139">**[国/地域]** という見出しが表示されるまでスクロールダウンします。</span><span class="sxs-lookup"><span data-stu-id="27415-139">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Microsoft 365 管理センター内のユーザーの地域情報の例。](media/o365-powershell-usage-location.png)
  
5. <span data-ttu-id="27415-141">ユーザーの表示名と場所を紙に書き留めるか、コピーしてメモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="27415-141">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="27415-142">この手順をユーザーごとに繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="27415-142">You must repeat this procedure for each user.</span></span> <span data-ttu-id="27415-143">これは多くのユーザーにとって、面倒な作業でしょう。</span><span class="sxs-lookup"><span data-stu-id="27415-143">For many users, this can be a tedious task.</span></span> <span data-ttu-id="27415-144">Microsoft 365 の PowerShell では、次のコマンドを使用して、すべてのユーザーについてこの情報を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="27415-144">With PowerShell for Microsoft 365, you can display this information for all of your users with the following command:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
><span data-ttu-id="27415-145">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="27415-145">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="27415-146">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27415-146">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="27415-147">表示例:</span><span class="sxs-lookup"><span data-stu-id="27415-147">Here is an example of the display:</span></span>
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  <span data-ttu-id="27415-148">この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプション ( **set-azureaduser** ) 内のすべてのユーザーを取得しますが、各ユーザーの名前と場所のみを表示します ( **DisplayName、使用場所の選択**)。</span><span class="sxs-lookup"><span data-stu-id="27415-148">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription ( **Get-AzureADUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="27415-149">Microsoft 365 用の PowerShell はコマンドシェル言語をサポートしているため、 **set-azureaduser**コマンドで取得した情報をさらに操作することができます。</span><span class="sxs-lookup"><span data-stu-id="27415-149">Because PowerShell for Microsoft 365 supports a command shell language, you can further manipulate the information obtained from the **Get-AzureADUser** command.</span></span> <span data-ttu-id="27415-150">たとえば、これらのユーザーを場所によって並べ替えたり、すべてのブラジルユーザーを一緒にグループ化したり、すべての米国ユーザーを一緒にグループ化したりしたい場合があります。コマンドは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="27415-150">For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="27415-151">表示例:</span><span class="sxs-lookup"><span data-stu-id="27415-151">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  <span data-ttu-id="27415-152">この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションのすべてのユーザーを取得しますが、各ユーザーの名前と場所のみを表示し、それらの名前と名前 (**並べ替えを使用した場所、DisplayName** ) を最初に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="27415-152">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="27415-p110">また、フィルター処理を追加することもできます。たとえば、ブラジル在住のユーザーに関する情報のみを表示する場合には、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="27415-p110">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="27415-155">表示例:</span><span class="sxs-lookup"><span data-stu-id="27415-155">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="27415-156">この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションで、場所がブラジルであるすべてのユーザーを取得します ( **Where {$ \_ .[使用場所]-eq "BR"}** ) で、各ユーザーの名前と場所を表示します。</span><span class="sxs-lookup"><span data-stu-id="27415-156">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="27415-157">**規模の大きいドメインに関する注意事項**</span><span class="sxs-lookup"><span data-stu-id="27415-157">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="27415-158">ドメインの規模が非常に大きい場合 (たとえば、何万人ものユーザーが属している場合)、この記事に記載する一部の例で、「スロットリング」が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="27415-158">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling."</span></span> <span data-ttu-id="27415-159">これはつまり、計算能力や使用可能なネットワーク帯域幅などを上回る操作を、一度に実行しようとしていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="27415-159">That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time.</span></span> <span data-ttu-id="27415-160">そのため、大規模な組織では、Microsoft 365 コマンド用にこれらの PowerShell の一部を2つのコマンドに分割することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="27415-160">Because of that, larger organizations might want to split some of these PowerShell for Microsoft 365 commands into two commands.</span></span> <span data-ttu-id="27415-161">たとえば、次の 1 つのコマンドはすべてのユーザー アカウントを返し、それぞれの名前と場所を示します。</span><span class="sxs-lookup"><span data-stu-id="27415-161">For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="27415-p112">このコマンドは、規模が小さいドメインには最適に機能します。しかし大規模な組織では、これを 2 つのコマンドに分けて、一方のコマンドでユーザー アカウント情報を変数に格納し、もう一方のコマンドで必要な情報を表示することが必要になる可能性があります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="27415-p112">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

<span data-ttu-id="27415-165">この PowerShell コマンドのセットは次のように解釈されます。</span><span class="sxs-lookup"><span data-stu-id="27415-165">The interpretation of this set of PowerShell commands is:</span></span>
- <span data-ttu-id="27415-166">現在の Microsoft 365 サブスクリプション内のすべてのユーザーを取得し、その情報を $x ( **$x = set-azureaduser** ) という名前の変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="27415-166">Get all of the users in the current Microsoft 365 subscription and store the information in a variable named $x ( **$x = Get-AzureADUser** ).</span></span>
- <span data-ttu-id="27415-167">変数 $x の内容のうち、各ユーザーの名前と場所のみを表示します (**$x | Select DisplayName, UsageLocation**)。</span><span class="sxs-lookup"><span data-stu-id="27415-167">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a><span data-ttu-id="27415-168">Microsoft 365 には、Microsoft 365 の PowerShell でのみ構成できる機能があります。</span><span class="sxs-lookup"><span data-stu-id="27415-168">Microsoft 365 has features that you can only configure with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="27415-169">Microsoft 365 管理センターは、ほとんどのユーザーに適用される最も一般的な管理タスクまたは意味のある管理タスクへのアクセスを提供することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="27415-169">The Microsoft 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people.</span></span> <span data-ttu-id="27415-170">つまり、Microsoft 365 管理センターは、一般的な管理者がツールを使用して最も一般的な管理タスクを実行できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="27415-170">In other words, the Microsoft 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks.</span></span> <span data-ttu-id="27415-171">この定義により、Microsoft 365 管理センターを使用して完了できないタスクがいくつかあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="27415-171">By this definition, that means that there are some tasks that can't be completed by using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="27415-172">たとえば、Skype for Business Online 管理センターにはカスタムの会議出席依頼を作成するためのいくつかのオプションが備わっています。</span><span class="sxs-lookup"><span data-stu-id="27415-172">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![Skype for Business Online 管理センターでカスタムの会議出席依頼を表示する例です。](media/o365-powershell-meeting-invitation.png)
  
<span data-ttu-id="27415-p114">これらの設定を使用すると、会議出席依頼にパーソナルでプロフェッショナルな風合いを加えることができます。しかし、会議の構成設定には、カスタムの会議出席依頼を作成する以上の事柄が関係します。たとえば、既定では会議に関して以下の事柄が許可されています。</span><span class="sxs-lookup"><span data-stu-id="27415-p114">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="27415-177">匿名ユーザーが、各会議に自動的に参加すること。</span><span class="sxs-lookup"><span data-stu-id="27415-177">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="27415-178">参加者が、会議を記録すること。</span><span class="sxs-lookup"><span data-stu-id="27415-178">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="27415-179">組織のすべてのユーザーが、会議に参加するときに発表者として指定されること。</span><span class="sxs-lookup"><span data-stu-id="27415-179">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="27415-180">これらの設定に関しては、Skype for Business Online 管理センターからは行うことができません。</span><span class="sxs-lookup"><span data-stu-id="27415-180">These settings are not available from the Skype for Business Online Admin center.</span></span> <span data-ttu-id="27415-181">ただし、Microsoft 365 については PowerShell を使用して制御できます。</span><span class="sxs-lookup"><span data-stu-id="27415-181">However, you can control them from PowerShell for Microsoft 365.</span></span> <span data-ttu-id="27415-182">これらの 3 つの設定を無効にするコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="27415-182">Here is a command that disables these three settings:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="27415-183">このコマンドを実行するには、[Skype for Business Online PowerShell モジュール](https://www.microsoft.com/download/details.aspx?id=39366)をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="27415-183">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="27415-184">この PowerShell コマンドの解釈は次のとおりです。新しい Skype for Business Online 会議 ( **AdmitAnonymousUsersByDefault $False** **) の**設定については、匿名ユーザーの会議への自動開始を許可しないようにします (- **AllowConferenceRecording $False** )。また、組織のすべてのユーザーを発表者として指定しない ( **-designateaspresenter "None"** )。</span><span class="sxs-lookup"><span data-stu-id="27415-184">The interpretation of this PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="27415-185">方針を変えて既定の設定に戻す (これらすべてを有効にする) 場合には、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="27415-185">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="27415-186">これは一例に過ぎません。</span><span class="sxs-lookup"><span data-stu-id="27415-186">This is just one example.</span></span> <span data-ttu-id="27415-187">他にもあります。このため、管理者は Microsoft 365 コマンドの PowerShell の実行に慣れている必要があります。</span><span class="sxs-lookup"><span data-stu-id="27415-187">There are others, which is why you, as an administrator, need to be comfortable with running PowerShell for Microsoft 365 commands.</span></span>
  
## <a name="powershell-for-microsoft-365-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="27415-188">Microsoft 365 の PowerShell は一括操作を実行するのに適しています。</span><span class="sxs-lookup"><span data-stu-id="27415-188">PowerShell for Microsoft 365 is great at carrying out bulk operations</span></span>

<span data-ttu-id="27415-189">従来は、単一の操作を実行すると、Microsoft 365 管理センターのようなビジュアルインターフェイスが最も重要になります。</span><span class="sxs-lookup"><span data-stu-id="27415-189">Historically, visual interfaces like the Microsoft 365 admin center are most valuable when you have a single operation to perform.</span></span> <span data-ttu-id="27415-190">たとえば、1つのユーザーアカウントを無効にする必要がある場合は、Microsoft 365 管理センターを使用して、チェックボックスをすばやく見つけてクリアすることができます。</span><span class="sxs-lookup"><span data-stu-id="27415-190">For example, if you need to disable one user account, you can use the Microsoft 365 admin center to quickly locate and clear a checkbox.</span></span> <span data-ttu-id="27415-191">これは、PowerShell で同様の操作を実行するよりも簡単になります。</span><span class="sxs-lookup"><span data-stu-id="27415-191">This can be simpler than performing a similar operation in PowerShell.</span></span>
  
<span data-ttu-id="27415-192">しかし、その他の多くの場合に、多数の項目や選択したものを変更する必要がある場合は、Microsoft 365 管理センターがお客様の時間を最適に使用しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="27415-192">But if you have to change many things or some selected things within a large set of other things, the Microsoft 365 admin center might not be the best use of your time.</span></span> <span data-ttu-id="27415-193">たとえば、数千人の電話番号のプレフィックスを変更する必要がある場合や、特定のユーザー (Ken Myer) をすべての SharePoint Online サイトから削除する必要がある場合は、Microsoft 365 管理センターでどうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="27415-193">For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Microsoft 365 admin center?</span></span>
  
<span data-ttu-id="27415-194">後者の例の場合、何百もの SharePoint Online サイトがあり、Ken Meyer がメンバーのサイトも判断できません。</span><span class="sxs-lookup"><span data-stu-id="27415-194">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member.</span></span> <span data-ttu-id="27415-195">そのため、Microsoft 365 管理センターから開始して、各サイトでこの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27415-195">That means you'll have to start at the Microsoft 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="27415-196">サイトの **URL** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27415-196">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="27415-197">[ **サイト コレクションのプロパティ** ] ボックスで、[ **Web サイトのアドレス** ] リンクをクリックしてサイトを開きます。</span><span class="sxs-lookup"><span data-stu-id="27415-197">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="27415-198">サイトの [ **共有** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27415-198">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="27415-199">[ **共有** ] ダイアログ ボックスで、サイトへのアクセス権限を持つすべてのユーザーを表示するリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="27415-199">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![SharePoint Online 管理センターの SharePoint Online サイトのメンバーを表示する例です。](media/o365-powershell-view-permissions.png)
  
5. <span data-ttu-id="27415-201">[ **共有相手** ] ダイアログ ボックスで、[ **詳細設定** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27415-201">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="27415-202">ユーザーの一覧をスクロール ダウンし、Ken Myer (サイトへのアクセス権限を持っていることが前提) を見つけて選択してから、[ **ユーザー権限の削除** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27415-202">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="27415-203">何百ものサイトがある場合、長時間かかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="27415-203">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="27415-204">別の方法として、Microsoft 365 の PowerShell を使用し、次のコマンドを使用して、すべてのサイトから Ken Myer を削除します。</span><span class="sxs-lookup"><span data-stu-id="27415-204">The alternative is to use PowerShell for Microsoft 365 and the following command to remove Ken Myer from all of your sites:</span></span>
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="27415-205">このコマンドを実行するには、 [SharePoint Online PowerShell モジュール](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="27415-205">This command requires that you install the [SharePoint Online PowerShell module](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="27415-206">この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプション ( **get-sposite** ) 内のすべての SharePoint サイトを取得し、各サイトについて、アクセス可能なユーザーのリストから Ken Meyer を削除し**ます (ForEach {Remove-Spouser-site $ \_ 。Url-ログイン "kenmyer@litwareinc.com"}** )。</span><span class="sxs-lookup"><span data-stu-id="27415-206">The interpretation of this PowerShell command is:  Get all of the SharePoint sites in the current Microsoft 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="27415-207">ユーザーがアクセス権を持っていないものも含めて、すべてのサイトから Ken Meyer を削除するよう Microsoft 365 に指示しているため、このコマンドの表示では、現在アクセスできないサイトに関するエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="27415-207">Because we are telling Microsoft 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access.</span></span> <span data-ttu-id="27415-208">このコマンドで追加の条件を使用して、彼がログインリストにあるサイトからのみキー Meyer のみを削除することができますが、リストされているエラーによってサイト自体に悪影響が生じることはありません。</span><span class="sxs-lookup"><span data-stu-id="27415-208">We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves.</span></span> <span data-ttu-id="27415-209">このコマンドは、Microsoft 365 管理センターで作業する時間ではなく、数百のサイトに対して実行されるまでに数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="27415-209">This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="27415-p121">別の一括操作の例を次に示します。このコマンドを使用して、新しい SharePoint 管理者である Bonnie Kearney を組織内のすべてのサイトに追加します。</span><span class="sxs-lookup"><span data-stu-id="27415-p121">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="27415-212">この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプション内のすべての SharePoint サイトを取得し、各サイトについて、サイトのメンバーグループにログイン名を追加して Bonnie Kearney access を許可します ( **ForEach {Add-SPOUser-site $ \_ 。Url-ログイン "bkearney@litwareinc.com"-グループ "メンバー"}** )。</span><span class="sxs-lookup"><span data-stu-id="27415-212">The interpretation of this PowerShell command is:  Get all of the SharePoint sites in the current Microsoft 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a><span data-ttu-id="27415-213">Microsoft 365 の PowerShell は、データのフィルター処理に適しています。</span><span class="sxs-lookup"><span data-stu-id="27415-213">PowerShell for Microsoft 365 is great at filtering data</span></span>

<span data-ttu-id="27415-214">Microsoft 365 管理センターでは、データをフィルター処理して、対象となる情報のサブセットを迅速かつ簡単に見つけられるように、さまざまな方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="27415-214">The Microsoft 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information.</span></span> <span data-ttu-id="27415-215">たとえば、Exchange では、ユーザー メールボックスのほとんどすべてのプロパティに対するフィルターを簡単に適用できます。</span><span class="sxs-lookup"><span data-stu-id="27415-215">For example, Exchange makes it easy to filter on practically any property of a user mailbox.</span></span> <span data-ttu-id="27415-216">たとえば、以下は、Bloomington 市に在住のすべてのユーザーのメールボックスを一覧表示する例です。</span><span class="sxs-lookup"><span data-stu-id="27415-216">For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![ブルーミントンの市区町村に居住しているすべてのユーザーのメールボックスの一覧については、Microsoft 365 管理センターで高度な検索を実行する例を示します。](media/o365-powershell-advanced-search.png)
  
<span data-ttu-id="27415-p123">Exchange 管理センターでは、フィルター条件を組み合わせることもできます。たとえば、ブルーミントン市に住み、経理部で働いているすべての住民のメールボックスを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="27415-p123">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="27415-p124">しかし、Exchange 管理センターで行えることには限界があります。たとえば、ブルーミントンかサンディエゴに住んでいる住民のメールボックスを検索したい場合や、ブルーミントンに住んでいないすべての住民のメールボックスを検索したい場合もあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="27415-p124">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="27415-222">Microsoft 365 の PowerShell では、次のコマンドを使用して、ブルーミントンまたはサンディディエゴの都市に居住しているすべてのユーザーのメールボックスの一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="27415-222">With PowerShell for Microsoft 365, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="27415-223">表示例:</span><span class="sxs-lookup"><span data-stu-id="27415-223">Here is an example of the display:</span></span>
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  <span data-ttu-id="27415-224">この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションで、メールボックスが San ディエゴまたはブルーミントン (Where {$) のいずれかの都市にあるすべてのユーザーを取得します\*\* \_ 。[受信者] Typetypedetails-eq "UserMailbox"-and ($ \_ .City-eq "サンディエゴ"-または $ \_ 。City-eq "ブルーミントン")}\*\* ) で、それぞれの名前と市区町村を表示します ( **DisplayName、City を選択**)。</span><span class="sxs-lookup"><span data-stu-id="27415-224">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="27415-225">ブルーミントン以外に居住しているユーザーのメールボックスをすべて一覧表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="27415-225">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="27415-226">表示例:</span><span class="sxs-lookup"><span data-stu-id="27415-226">Here is an example of the display:</span></span>
  
```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  <span data-ttu-id="27415-227">この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションで、メールボックスがブルーミントンの city (Where {$) にないすべてのユーザーを取得します\*\* \_ 。[受信者] Typetypedetails-eq "UserMailbox"-and $ \_ 。City-ne "ブルーミントン"}\*\* ) で、それぞれの名前と市区町村を表示します。</span><span class="sxs-lookup"><span data-stu-id="27415-227">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="27415-228">また、PowerShell フィルターでワイルドカード文字を使用して、名前の一部と一致させることもできます。</span><span class="sxs-lookup"><span data-stu-id="27415-228">You can also use wildcard characters in your PowerShell filters to match part of a name.</span></span> <span data-ttu-id="27415-229">たとえば、あるユーザー アカウントを探しているものの、名字が Anderson か Henderson であることしか思い出せず、もしかすると Jorgenson だったかもしれないとします。</span><span class="sxs-lookup"><span data-stu-id="27415-229">For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="27415-230">検索ツールを使用して、次の3つの異なる検索を実行することによって、Microsoft 365 管理センターでそのユーザーを追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="27415-230">You could track down that user in the Microsoft 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="27415-231">*Anderson*  用のもの</span><span class="sxs-lookup"><span data-stu-id="27415-231">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="27415-232">*Henderson*  用のもの</span><span class="sxs-lookup"><span data-stu-id="27415-232">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="27415-233">*Jorgenson*  用のもの</span><span class="sxs-lookup"><span data-stu-id="27415-233">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="27415-234">これらの3つの名前はすべて "son" で終わるので、名前が "son" で終わるすべてのユーザーを表示するように PowerShell に指示できます。</span><span class="sxs-lookup"><span data-stu-id="27415-234">Because all three of these names end in "son", you can tell PowerShell to display all the users whose name ends in "son".</span></span> <span data-ttu-id="27415-235">コマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="27415-235">Here is the command:</span></span>
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="27415-236">この PowerShell コマンドは、次のように解釈されます。現在の Microsoft 365 サブスクリプション内のすべてのユーザーを取得しますが、姓が "son" で終わるユーザーを一覧表示するフィルターを使用します ( **-filter ' {LastName-like " \* son"} '** )。</span><span class="sxs-lookup"><span data-stu-id="27415-236">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ).</span></span> <span data-ttu-id="27415-237">は、 \* 任意の文字セット (ユーザーの姓の場合は文字) で表します。</span><span class="sxs-lookup"><span data-stu-id="27415-237">The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="27415-238">Microsoft 365 の PowerShell を使用すると、データの印刷や保存が容易になります。</span><span class="sxs-lookup"><span data-stu-id="27415-238">PowerShell for Microsoft 365 makes it easy to print or save data</span></span>

<span data-ttu-id="27415-239">Microsoft 365 管理センターでは、データの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="27415-239">The Microsoft 365 admin center lets you view lists of data.</span></span> <span data-ttu-id="27415-240">以下に、skype for business online 管理センターの例を示します。このリストには、Skype for business Online が有効になっているユーザーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="27415-240">Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![Skype for Business Online 管理センターで、Skype for Business Online に対して有効になっているユーザーの一覧を表示する例です。](media/o365-powershell-lync-users.png)
  
<span data-ttu-id="27415-242">この情報をファイルに保存するには、コピーしてドキュメントまたは Excel に貼り付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="27415-242">To save that information to a file, you must copy and paste it into a document or Excel.</span></span> <span data-ttu-id="27415-243">どちらの場合も、コピー操作には追加の書式設定が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="27415-243">In either case, the copy might require additional formatting.</span></span> <span data-ttu-id="27415-244">また、Microsoft 365 管理センターでは、表示されている一覧を直接印刷する方法は提供されていません。</span><span class="sxs-lookup"><span data-stu-id="27415-244">Additionally, the Microsoft 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="27415-245">さいわい、PowerShell を使用してリストを表示するだけでなく、Excel に簡単にインポートできるファイルに保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="27415-245">Fortunately, you can use PowerShell to not only display the list, but save it to a file that can be easily imported into Excel.</span></span> <span data-ttu-id="27415-246">以下に、Skype for Business Online ユーザーデータをコンマ区切り値 (CSV) ファイルに保存するコマンドの例を示します。これは、Excel ワークシートのテーブルとして簡単にインポートできるファイルです。</span><span class="sxs-lookup"><span data-stu-id="27415-246">Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="27415-247">表示例:</span><span class="sxs-lookup"><span data-stu-id="27415-247">Here is an example of the display:</span></span>
  
![Excel ワークシートにインポートされている、コンマ区切り値 (CSV) ファイルに保存された Skype for Business Online ユーザー データに関するテーブルの例です。](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  <span data-ttu-id="27415-249">この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションのすべての Skype for Business Online ユーザーを取得します (**取得**します)。ユーザー名、UPN、および場所のみを取得し ( **DisplayName、UserPrincipalName、使用場所を選択**)、その情報を c: \\ Logs \\SfBUsers.csv ( **Export-csv-Path "C: \\ logs \\SfBUsers.csv"-notypeinformation** ) という名前で保存します。</span><span class="sxs-lookup"><span data-stu-id="27415-249">The interpretation of this PowerShell command is: Get all of the Skype for Business Online users in the current Microsoft 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="27415-p131">また、オプションを使って、この一覧を XML ファイルや HTML ページとして保存できます。実際、追加の PowerShell コマンドを使い、必要なカスタム書式設定で直接 Excel ファイルとして保存できます。</span><span class="sxs-lookup"><span data-stu-id="27415-p131">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="27415-252">また、Windows の既定のプリンターにリストを直接表示する PowerShell コマンドの出力を送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="27415-252">You can also send the output of a PowerShell command that displays a list directly to the default printer in Windows.</span></span> <span data-ttu-id="27415-253">コマンド例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="27415-253">Here is an example command:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="27415-254">印刷されたドキュメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="27415-254">Here's what your printed document will look like:</span></span>
  
![Windows の既定のプリンターに直接表示されている PowerShell コマンドの出力である印刷されたドキュメントの例です。](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  <span data-ttu-id="27415-256">この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションの Skype for Business Online ユーザーをすべて取得し、ユーザー名、UPN、および場所のみを取得して、その情報を既定の Windows プリンター (**出力プリンター** ) に送信します。</span><span class="sxs-lookup"><span data-stu-id="27415-256">The interpretation of this PowerShell command is:  Get all of the Skype for Business Online users in the current Microsoft 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="27415-257">印刷された文書の簡単な書式設定は PowerShell コマンドウィンドウでの表示と同じですが、必要なものを一覧表示する PowerShell コマンドを作成したら、追加するだけでも **|** コマンドの最後にプリンターを使用して、ハードコピーを取得します。</span><span class="sxs-lookup"><span data-stu-id="27415-257">The printed document has the same simple formatting as the display within the PowerShell command window, but once you have created a PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a><span data-ttu-id="27415-258">Microsoft 365 の PowerShell を使用すると、複数のサーバー製品を管理できます。</span><span class="sxs-lookup"><span data-stu-id="27415-258">PowerShell for Microsoft 365 lets you manage across server products</span></span>

<span data-ttu-id="27415-259">Microsoft 365 を構成するさまざまなコンポーネントは、連携して動作するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="27415-259">The different components that make up Microsoft 365 are designed to work together.</span></span> <span data-ttu-id="27415-260">たとえば、Microsoft 365 に新しいユーザーを追加した場合に、ユーザーの部署や電話番号などの情報を指定するとします。</span><span class="sxs-lookup"><span data-stu-id="27415-260">For example, suppose you add a new user to Microsoft 365 and, when you do, you specify such information as the user's department and phone number.</span></span> <span data-ttu-id="27415-261">この情報は、Microsoft 365 サービスのいずれかを使用してユーザーの情報にアクセスすると、Skype for Business Online、Exchange、または SharePoint Online のいずれかを使用して利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="27415-261">That information will then be available if you access the user's information using any of the Microsoft 365 services: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="27415-p134">ただし、これは製品のスイートに共通する一般情報の場合です。製品固有の情報 (たとえば、ユーザーの Exchange メールボックスに関する情報など) は基本的にはスイートのすべての製品で入手できるようにはなっていません。たとえば、ユーザーのメールボックスが有効になっているかどうかを把握したい場合などには、Exchange 管理センターにおいてのみこの情報が取得できます。</span><span class="sxs-lookup"><span data-stu-id="27415-p134">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="27415-265">すべてのユーザーに関する次のような情報を示すレポートを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="27415-265">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="27415-266">ユーザーの表示名</span><span class="sxs-lookup"><span data-stu-id="27415-266">The user's display name</span></span>
    
- <span data-ttu-id="27415-267">ユーザーが Microsoft 365 用にライセンスされているかどうか</span><span class="sxs-lookup"><span data-stu-id="27415-267">Whether the user is licensed for Microsoft 365</span></span>
    
- <span data-ttu-id="27415-268">ユーザーの Exchange メールボックスが有効になっているかどうか</span><span class="sxs-lookup"><span data-stu-id="27415-268">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="27415-269">ユーザーが Skype for Business Online に対して有効になっているかどうか</span><span class="sxs-lookup"><span data-stu-id="27415-269">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="27415-270">現時点では、Microsoft 365 管理センターを使用してこのようなレポートを簡単に作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="27415-270">You currently cannot use the Microsoft 365 admin center to easily produce such a report.</span></span> <span data-ttu-id="27415-271">その代わりに、Excel ワークシートのような情報を格納するための別のドキュメントを作成し、Microsoft 365 管理センターからすべてのユーザー名とライセンス情報を取得し、Exchange 管理センターからメールボックス情報を取得して、skype for business online 管理センターからの Skype for Business Online 情報を取得し、それらの情報を照合して組み合わせます。</span><span class="sxs-lookup"><span data-stu-id="27415-271">Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Microsoft 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="27415-272">別の方法として、PowerShell スクリプトを使用してレポートをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="27415-272">The alternative is to use a PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="27415-273">次のスクリプト例は、この記事でこれまでに示したコマンドの中で最も複雑です。</span><span class="sxs-lookup"><span data-stu-id="27415-273">The following example script is more complicated than the commands you have seen so far in this article.</span></span> <span data-ttu-id="27415-274">しかし、PowerShell を使用して情報のビューを作成することによって、そのような操作が非常に困難になる可能性があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="27415-274">But, it shows the potential of using PowerShell to create views of information that are very difficult to do otherwise.</span></span> <span data-ttu-id="27415-275">必要な一覧をコンパイルして表示するスクリプトを次に示します。</span><span class="sxs-lookup"><span data-stu-id="27415-275">Here is the script that can compile and display the needed list:</span></span>
  
```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

<span data-ttu-id="27415-276">表示例:</span><span class="sxs-lookup"><span data-stu-id="27415-276">Here is an example of the display:</span></span>
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

<span data-ttu-id="27415-277">この PowerShell スクリプトの解釈は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="27415-277">The interpretation of this PowerShell script is:</span></span>  

- <span data-ttu-id="27415-278">現在の Microsoft 365 サブスクリプション内のすべてのユーザーを取得し、その情報を $x ( **$x = set-azureaduser** ) という名前の変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="27415-278">Get all of the users in the current Microsoft 365 subscription and store the information in a variable named $x ( **$x = Get-AzureADUser** ).</span></span>
- <span data-ttu-id="27415-279">$x という変数内のすべてのユーザーに対して実行されるループを開始します (**foreach ($i in $x)**)。</span><span class="sxs-lookup"><span data-stu-id="27415-279">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="27415-280">$y という名前の変数を定義し、ユーザーのメールボックス情報をその変数に格納します (**$y = Get-Mailbox -Identity $i.UserPrincipalName**)。</span><span class="sxs-lookup"><span data-stu-id="27415-280">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="27415-281">ユーザー情報に IsMailBoxEnabled という新しいプロパティを追加し、このプロパティの値に、ユーザーのメールボックスの IsMailBoxEnabled プロパティの値を設定します (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**)。</span><span class="sxs-lookup"><span data-stu-id="27415-281">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="27415-282">$y という変数を定義し、ユーザーの Skype for Business Online 情報をその変数に格納します (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**)。</span><span class="sxs-lookup"><span data-stu-id="27415-282">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="27415-283">EnabledForSfB という名前の新しいプロパティをユーザー情報に追加し、このプロパティの値に、ユーザーの Skype for Business Online 情報の Enabled プロパティの値を設定します (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**)。</span><span class="sxs-lookup"><span data-stu-id="27415-283">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="27415-284">ユーザーの一覧を表示します。ただし、含めるのは、ユーザー名、ライセンス認定されているかどうか、およびメールボックスが使用可能かどうかと Skype for Business Online に対して有効かどうかを示す 2 つの新たなプロパティのみとします (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**)。</span><span class="sxs-lookup"><span data-stu-id="27415-284">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="27415-285">関連項目</span><span class="sxs-lookup"><span data-stu-id="27415-285">See also</span></span>

[<span data-ttu-id="27415-286">Microsoft 365 の PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="27415-286">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="27415-287">PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="27415-287">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="27415-288">Windows PowerShell を使用して Microsoft 365 でレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="27415-288">Use Windows PowerShell to create reports in Microsoft 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

