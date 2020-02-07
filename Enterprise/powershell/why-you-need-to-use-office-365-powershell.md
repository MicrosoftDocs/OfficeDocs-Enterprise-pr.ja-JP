---
title: Office 365 PowerShell を使用する必要がある理由
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: '概要: 管理者が Office 365 PowerShell を使って Office 365 を管理すべき理由を説明します。ある場合は効率のため、他の場合は必要であるためです。'
ms.openlocfilehash: f7854888db563b932567200db0d24708d59f9969
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841254"
---
# <a name="why-you-need-to-use-office-365-powershell"></a><span data-ttu-id="e1b99-103">Office 365 PowerShell を使用する必要がある理由</span><span class="sxs-lookup"><span data-stu-id="e1b99-103">Why you need to use Office 365 PowerShell</span></span>

<span data-ttu-id="e1b99-104">Microsoft 365 管理センターを使用すると、Office 365 のユーザーアカウントとライセンスを管理できるだけでなく、Exchange Online、Teams、SharePoint Online などの Office 365 サービスを管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-104">With the Microsoft 365 admin center, you can not only manage your Office 365 user accounts and licenses, but you can also manage your Office 365 services such as Exchange Online, Teams, and SharePoint Online.</span></span> <span data-ttu-id="e1b99-105">しかし、これらの管理は Office 365 PowerShell コマンドでも行うことができ、そうするなら、コマンド ラインやスクリプト言語環境を活用して処理の高速化や自動化を実現させ、機能性が向上する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-105">However, you can also manage these elements with Office 365 PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="e1b99-106">この記事では、Office 365 PowerShell を使用して Office 365 を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-106">In this article, we'll show you these ways in which you can use Office 365 PowerShell to manage Office 365:</span></span>
  
- <span data-ttu-id="e1b99-107">Microsoft 365 管理センターでは表示できない追加情報を確認する</span><span class="sxs-lookup"><span data-stu-id="e1b99-107">Reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>
    
- <span data-ttu-id="e1b99-108">Office 365 PowerShell でのみ機能と設定を構成する</span><span class="sxs-lookup"><span data-stu-id="e1b99-108">Configure features and settings only possible with Office 365 PowerShell</span></span>
    
- <span data-ttu-id="e1b99-109">一括操作を実行する</span><span class="sxs-lookup"><span data-stu-id="e1b99-109">Perform bulk operations</span></span>
    
- <span data-ttu-id="e1b99-110">データのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="e1b99-110">Filtering data</span></span>
    
- <span data-ttu-id="e1b99-111">データを印刷または保存する</span><span class="sxs-lookup"><span data-stu-id="e1b99-111">Print or save data</span></span>
    
- <span data-ttu-id="e1b99-112">サービス間で管理する</span><span class="sxs-lookup"><span data-stu-id="e1b99-112">Manage across services</span></span>
    
<span data-ttu-id="e1b99-p102">最初に、Office 365 PowerShell が、Windows ベースのサービスとプラットフォームのコマンド ライン環境である Windows PowerShell のモジュールのセットであることを理解してください。この環境によって作成されるコマンド シェル言語は、追加モジュールによって拡張することができ、それによって単純または複雑なコマンドやスクリプトが実行できるようになります。たとえば、Office 365 PowerShell モジュールをインストールして Office 365 サブスクリプションに接続した後、次のコマンドを実行して Microsoft Exchange Online のすべてのユーザー メールボックスの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p102">Before you begin, understand that Office 365 PowerShell is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms. This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts. For example, after you install the Office 365 PowerShell modules and connect to your Office 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```powershell
Get-Mailbox
```

<span data-ttu-id="e1b99-116">メールボックスのリストを取得することも、Microsoft 365 管理センターを使用して簡単に行うことができますが、すべての web アプリのすべてのサイトについて、すべてのリストのアイテム数をカウントすることは簡単に行えません。</span><span class="sxs-lookup"><span data-stu-id="e1b99-116">Getting the list of mailboxes can also be easily done using the Microsoft 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="e1b99-117">Office 365 PowerShell は、Microsoft 365 管理センターを置き換えるのではなく、Office 365 を管理する機能を強化し、強化するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e1b99-117">Please note that Office 365 PowerShell is designed to augment and enhance your ability to manage Office 365, not to replace the Microsoft 365 admin center.</span></span> <span data-ttu-id="e1b99-118">Office 365 の管理者は、office 365 PowerShell コマンドでしか実行できない構成手順があるため、Office 365 PowerShell の使用に関しては、少なくとも使い慣れてはなりません。</span><span class="sxs-lookup"><span data-stu-id="e1b99-118">As an Office 365 administrator, you must become at least comfortable with using Office 365 PowerShell because there are some configuration procedures that can only be done with Office 365 PowerShell commands.</span></span> <span data-ttu-id="e1b99-119">このような場合は、次の方法を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-119">In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="e1b99-120">Office 365 PowerShell モジュールをインストールする (管理者のコンピューターごとに 1 回のみ行います)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-120">Install the Office 365 PowerShell modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="e1b99-121">Office 365 サブスクリプションに接続する (PowerShell セッションごとに 1 回行います)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-121">Connect to your Office 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="e1b99-122">必要な Office 365 PowerShell コマンドを実行するのに必要な情報を収集する。</span><span class="sxs-lookup"><span data-stu-id="e1b99-122">Gather the information needed to run the required Office 365 PowerShell commands.</span></span>
    
- <span data-ttu-id="e1b99-123">Office 365 PowerShell コマンドを正常に実行する。</span><span class="sxs-lookup"><span data-stu-id="e1b99-123">Run the Office 365 PowerShell commands successfully.</span></span>
    
<span data-ttu-id="e1b99-p104">これらの基本的なスキルを習得すれば、 **Get-mailbox** コマンドを使用してメールボックス ユーザーの一覧を作成する必要もなければ、すべての Web アプリ用のすべてのサイトのすべての一覧に含まれるすべてのアイテムをカウントするための前述のコマンドのような新しいコマンドを作成する方法を理解する必要もありません。Microsoft や Office 365 管理者のコミュニティが、こうした事柄を必要に応じて実行する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p104">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps. Microsoft and the community of Office 365 administrators can help you with that as needed.</span></span>
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a><span data-ttu-id="e1b99-126">Office 365 PowerShell では、Microsoft 365 管理センターでは表示できない追加情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-126">Office 365 PowerShell can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>

<span data-ttu-id="e1b99-127">Microsoft 365 管理センターでは、多くの有益な情報が表示されますが、これは、ユーザー、ライセンス、メールボックス、サイトに Office 365 が保存する可能性がある情報をすべて表示するという意味ではありません。</span><span class="sxs-lookup"><span data-stu-id="e1b99-127">The Microsoft 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Office 365 stores on users, licenses, mailboxes, and sites.</span></span> <span data-ttu-id="e1b99-128">Microsoft 365 管理センターの**ユーザーとグループ**の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-128">Here is an example for **users and groups** in the Microsoft 365 admin center:</span></span>
  
![Microsoft 365 管理センターでのユーザーとグループの表示例。](media/o365-powershell-users-and-groups.png)
  
<span data-ttu-id="e1b99-130">ここには、さまざまな理由で把握すべき情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-130">For many purposes, this displays the information you need to know.</span></span> <span data-ttu-id="e1b99-131">しかし、もっと多くの情報が必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-131">However, there are times when you need more.</span></span> <span data-ttu-id="e1b99-132">たとえば、Office 365 ライセンス (およびユーザーが使用できる Office 365 機能) は、そのユーザーの地理的な場所によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-132">For example, Office 365 licensing (and the Office 365 features available to a user) depend in part on that user's geographic location.</span></span> <span data-ttu-id="e1b99-133">米国内に在住しているユーザーに対して拡張可能なポリシーと機能は、インドやベルギー在住のユーザーに対して拡張可能なポリシーと機能と同じではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-133">The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium.</span></span> <span data-ttu-id="e1b99-134">Microsoft 365 管理センターを使用して、ユーザーの地理的な場所を確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-134">You can use the Microsoft 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="e1b99-135">ユーザーの **表示名** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-135">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="e1b99-136">ユーザーのプロパティを表示するウィンドウで、 **[詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-136">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="e1b99-137">詳細表示で、 **[追加情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-137">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="e1b99-138">**[国/地域]** という見出しが表示されるまでスクロールダウンします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-138">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Microsoft 365 管理センター内のユーザーの地域情報の例。](media/o365-powershell-usage-location.png)
  
5. <span data-ttu-id="e1b99-140">ユーザーの表示名と場所を紙に書き留めるか、コピーしてメモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-140">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="e1b99-p107">この手順をユーザーごとに繰り返す必要があります。これは多くのユーザーにとって、面倒な作業でしょう。Office 365 PowerShell で、次のコマンドを使用して、すべてのユーザーについてのこの情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p107">You must repeat this procedure for each user. For many users, this can be a tedious task. With Office 365 PowerShell, you can display this information for all of your users with the following command:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```


>[!Note]
><span data-ttu-id="e1b99-144">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e1b99-144">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e1b99-145">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-145">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="e1b99-146">表示例:</span><span class="sxs-lookup"><span data-stu-id="e1b99-146">Here is an example of the display:</span></span>
  
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
>  <span data-ttu-id="e1b99-147">この Office 365 PowerShell コマンドの説明: 現在の Office 365 サブスクリプション内のすべてのユーザーを取得し (**Get-MsolUser**)、各ユーザーの名前と場所だけを表示します (**Select DisplayName, UsageLocation**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-147">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription ( **Get-MsolUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="e1b99-p109">Office 365 PowerShell はコマンド シェル言語をサポートしているので、 **Get-MSolUser** コマンドで取得した情報をさらに処理できます。たとえば、場所を基準にユーザーを並べ替えて、ブラジルのユーザー、米国のユーザーなどをそれぞれグループ化できます。コマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p109">Because Office 365 PowerShell supports a command shell language, you can further manipulate the information obtained from the **Get-MSolUser** command. For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="e1b99-150">表示例:</span><span class="sxs-lookup"><span data-stu-id="e1b99-150">Here is an example of the display:</span></span>
  
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
>  <span data-ttu-id="e1b99-151">この Office 365 PowerShell コマンドの説明:  現在の Office 365 サブスクリプション内のユーザーすべてを取得し、各ユーザーの名前と場所のみを表示します。それらのユーザーを、場所を第一基準、名前を第二基準にして並べ替えます (**Sort UsageLocation, DisplayName**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-151">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="e1b99-p110">また、フィルター処理を追加することもできます。たとえば、ブラジル在住のユーザーに関する情報のみを表示する場合には、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p110">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="e1b99-154">表示例:</span><span class="sxs-lookup"><span data-stu-id="e1b99-154">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="e1b99-155">この Office 365 PowerShell コマンドの説明:  現在の Office 365 サブスクリプション内のユーザーのうち、ブラジルに在住しているすべてのユーザーを取得します (**Where {$\_.UsageLocation -eq "BR"}**)。次に、各ユーザーの名前と場所を表示します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-155">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="e1b99-156">**規模の大きいドメインに関する注意事項**</span><span class="sxs-lookup"><span data-stu-id="e1b99-156">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="e1b99-p111">ドメインの規模が非常に大きい場合 (たとえば、何万人ものユーザーが属している場合)、この記事に記載する一部の例で、「スロットリング」が発生する場合があります。これはつまり、計算能力や使用可能なネットワーク帯域幅などを上回る操作を、一度に実行しようとしていることを意味します。このため、大規模な組織の場合は、これらの Office 365 PowerShell コマンドを 2 つのコマンドに分けることができます。たとえば、次の 1 つのコマンドはすべてのユーザー アカウントを返し、それぞれの名前と場所を示します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p111">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling." That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time. Because of that, larger organizations might want to split some of these Office 365 PowerShell commands into two commands. For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="e1b99-p112">このコマンドは、規模が小さいドメインには最適に機能します。しかし大規模な組織では、これを 2 つのコマンドに分けて、一方のコマンドでユーザー アカウント情報を変数に格納し、もう一方のコマンドで必要な情報を表示することが必要になる可能性があります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p112">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```powershell
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```

<span data-ttu-id="e1b99-164">この Office 365 PowerShell コマンド セットの説明:</span><span class="sxs-lookup"><span data-stu-id="e1b99-164">The interpretation of this set of Office 365 PowerShell commands is:</span></span>
- <span data-ttu-id="e1b99-165">現在の Office 365 サブスクリプション内のすべてのユーザーを取得し、その情報を $x という名前の変数に格納します (**$x = Get-MsolUser**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-165">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="e1b99-166">変数 $x の内容のうち、各ユーザーの名前と場所のみを表示します (**$x | Select DisplayName, UsageLocation**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-166">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a><span data-ttu-id="e1b99-167">Office 365 には Office 365 PowerShell でのみ構成可能な機能がある</span><span class="sxs-lookup"><span data-stu-id="e1b99-167">Office 365 has features that you can only configure with Office 365 PowerShell</span></span>

<span data-ttu-id="e1b99-168">Microsoft 365 管理センターは、ほとんどのユーザーに適用される最も一般的な管理タスクまたは意味のある管理タスクへのアクセスを提供することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="e1b99-168">The Microsoft 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people.</span></span> <span data-ttu-id="e1b99-169">つまり、Microsoft 365 管理センターは、一般的な管理者がツールを使用して最も一般的な管理タスクを実行できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e1b99-169">In other words, the Microsoft 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks.</span></span> <span data-ttu-id="e1b99-170">この定義により、Microsoft 365 管理センターを使用して完了できないタスクがいくつかあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-170">By this definition, that means that there are some tasks that can't be completed by using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="e1b99-171">たとえば、Skype for Business Online 管理センターにはカスタムの会議出席依頼を作成するためのいくつかのオプションが備わっています。</span><span class="sxs-lookup"><span data-stu-id="e1b99-171">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![Skype for Business Online 管理センターでカスタムの会議出席依頼を表示する例です。](media/o365-powershell-meeting-invitation.png)
  
<span data-ttu-id="e1b99-p114">これらの設定を使用すると、会議出席依頼にパーソナルでプロフェッショナルな風合いを加えることができます。しかし、会議の構成設定には、カスタムの会議出席依頼を作成する以上の事柄が関係します。たとえば、既定では会議に関して以下の事柄が許可されています。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p114">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="e1b99-176">匿名ユーザーが、各会議に自動的に参加すること。</span><span class="sxs-lookup"><span data-stu-id="e1b99-176">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="e1b99-177">参加者が、会議を記録すること。</span><span class="sxs-lookup"><span data-stu-id="e1b99-177">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="e1b99-178">組織のすべてのユーザーが、会議に参加するときに発表者として指定されること。</span><span class="sxs-lookup"><span data-stu-id="e1b99-178">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="e1b99-p115">これらの設定に関しては、Skype for Business Online 管理センターからは行うことができません。ただし、Office 365 PowerShell からは制御が可能です。これらの 3 つの設定を無効にするコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p115">These settings are not available from the Skype for Business Online Admin center. However, you can control them from Office 365 PowerShell. Here is a command that disables these three settings:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="e1b99-182">このコマンドを実行するには、[Skype for Business Online PowerShell モジュール](https://www.microsoft.com/download/details.aspx?id=39366)をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-182">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="e1b99-183">この Office 365 PowerShell コマンドの説明: 新たな Skype for Business Online 会議の設定 (**Set-CsMeetingConfiguration**) に関して、匿名ユーザーが会議に自動的に参加する許可を無効にし (**-AdmitAnonymousUsersByDefault $False**)、出席者が会議を記録する機能を無効にし (**-AllowConferenceRecording $False**)、組織内のどのユーザーも発表者として指定しません (**-DesignateAsPresenter "None"**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-183">The interpretation of this Office 365 PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="e1b99-184">方針を変えて既定の設定に戻す (これらすべてを有効にする) 場合には、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-184">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="e1b99-p116">これは一例に過ぎません。Office 365 管理者が Office 365 PowerShell コマンドの実行方法をよく理解しているべき理由は他にもあります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p116">This is just one example. There are others, which is why you, as an Office 365 administrator, need to be comfortable with running Office 365 PowerShell commands.</span></span>
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="e1b99-187">Office 365 PowerShell は一括操作の実行の点で優れている</span><span class="sxs-lookup"><span data-stu-id="e1b99-187">Office 365 PowerShell is great at carrying out bulk operations</span></span>

<span data-ttu-id="e1b99-188">従来は、単一の操作を実行すると、Microsoft 365 管理センターのようなビジュアルインターフェイスが最も重要になります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-188">Historically, visual interfaces like the Microsoft 365 admin center are most valuable when you have a single operation to perform.</span></span> <span data-ttu-id="e1b99-189">たとえば、1つのユーザーアカウントを無効にする必要がある場合は、Microsoft 365 管理センターを使用して、チェックボックスをすばやく見つけてクリアすることができます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-189">For example, if you need to disable one user account, you can use the Microsoft 365 admin center to quickly locate and clear a checkbox.</span></span> <span data-ttu-id="e1b99-190">こちらのほうが、Office 365 PowerShell で同様の操作を行うよりも簡単な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-190">This can be simpler than performing a similar operation in Office 365 PowerShell.</span></span>
  
<span data-ttu-id="e1b99-191">しかし、その他の多くの場合に、多数の項目や選択したものを変更する必要がある場合は、Microsoft 365 管理センターがお客様の時間を最適に使用しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-191">But if you have to change many things or some selected things within a large set of other things, the Microsoft 365 admin center might not be the best use of your time.</span></span> <span data-ttu-id="e1b99-192">たとえば、数千人の電話番号のプレフィックスを変更する必要がある場合や、特定のユーザー (Ken Myer) をすべての SharePoint Online サイトから削除する必要がある場合は、Microsoft 365 管理センターでどうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="e1b99-192">For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Microsoft 365 admin center?</span></span>
  
<span data-ttu-id="e1b99-193">後者の例の場合、何百もの SharePoint Online サイトがあり、Ken Meyer がメンバーのサイトも判断できません。</span><span class="sxs-lookup"><span data-stu-id="e1b99-193">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member.</span></span> <span data-ttu-id="e1b99-194">そのため、Microsoft 365 管理センターから開始して、各サイトでこの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-194">That means you'll have to start at the Microsoft 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="e1b99-195">サイトの **URL** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-195">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="e1b99-196">[ **サイト コレクションのプロパティ** ] ボックスで、[ **Web サイトのアドレス** ] リンクをクリックしてサイトを開きます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-196">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="e1b99-197">サイトの [ **共有** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-197">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="e1b99-198">[ **共有** ] ダイアログ ボックスで、サイトへのアクセス権限を持つすべてのユーザーを表示するリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-198">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![SharePoint Online 管理センターの SharePoint Online サイトのメンバーを表示する例です。](media/o365-powershell-view-permissions.png)
  
5. <span data-ttu-id="e1b99-200">[ **共有相手** ] ダイアログ ボックスで、[ **詳細設定** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-200">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="e1b99-201">ユーザーの一覧をスクロール ダウンし、Ken Myer (サイトへのアクセス権限を持っていることが前提) を見つけて選択してから、[ **ユーザー権限の削除** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-201">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="e1b99-202">何百ものサイトがある場合、長時間かかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-202">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="e1b99-203">これに代わる方法として、Office 365 PowerShell で次のコマンドを使って、すべてのサイトから Ken Myer を削除できます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-203">The alternative is to use Office 365 PowerShell and the following command to remove Ken Myer from all of your sites:</span></span>
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="e1b99-204">このコマンドを実行するには、 [SharePoint Online PowerShell モジュール](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-204">This command requires that you install the [SharePoint Online PowerShell module](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="e1b99-205">この Office 365 PowerShell コマンドの説明: 現在の Office 365 サブスクリプションのすべての SharePoint サイトを取得し (**Get-SPOSite**)、各サイトにアクセス可能なユーザーの一覧から Ken Meyer を削除します (**ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-205">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="e1b99-206">ユーザーがアクセス権を持っていないものも含めて、すべてのサイトから Ken Meyer を削除するよう Office 365 に指示しているため、このコマンドの表示では、現在アクセスできないサイトに関するエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-206">Because we are telling Office 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access.</span></span> <span data-ttu-id="e1b99-207">このコマンドで追加の条件を使用して、彼がログインリストにあるサイトからのみキー Meyer のみを削除することができますが、リストされているエラーによってサイト自体に悪影響が生じることはありません。</span><span class="sxs-lookup"><span data-stu-id="e1b99-207">We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves.</span></span> <span data-ttu-id="e1b99-208">このコマンドは、Microsoft 365 管理センターで作業する時間ではなく、数百のサイトに対して実行されるまでに数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-208">This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="e1b99-p121">別の一括操作の例を次に示します。このコマンドを使用して、新しい SharePoint 管理者である Bonnie Kearney を組織内のすべてのサイトに追加します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p121">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="e1b99-211">この Office 365 PowerShell コマンドの説明: 現在の Office 365 サブスクリプションのすべての SharePoint サイトを取得し、各サイトで Bonnie Kearney のログイン名をサイトの Members グループに追加して Bonnie Kearney にアクセスを許可します (**ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-211">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a><span data-ttu-id="e1b99-212">Office 365 PowerShell はデータのフィルター処理に優れている</span><span class="sxs-lookup"><span data-stu-id="e1b99-212">Office 365 PowerShell is great at filtering data</span></span>

<span data-ttu-id="e1b99-213">Microsoft 365 管理センターでは、データをフィルター処理して、対象となる情報のサブセットを迅速かつ簡単に見つけられるように、さまざまな方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-213">The Microsoft 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information.</span></span> <span data-ttu-id="e1b99-214">たとえば、Exchange では、ユーザー メールボックスのほとんどすべてのプロパティに対するフィルターを簡単に適用できます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-214">For example, Exchange makes it easy to filter on practically any property of a user mailbox.</span></span> <span data-ttu-id="e1b99-215">たとえば、以下は、Bloomington 市に在住のすべてのユーザーのメールボックスを一覧表示する例です。</span><span class="sxs-lookup"><span data-stu-id="e1b99-215">For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![ブルーミントンの市区町村に居住しているすべてのユーザーのメールボックスの一覧については、Microsoft 365 管理センターで高度な検索を実行する例を示します。](media/o365-powershell-advanced-search.png)
  
<span data-ttu-id="e1b99-p123">Exchange 管理センターでは、フィルター条件を組み合わせることもできます。たとえば、ブルーミントン市に住み、経理部で働いているすべての住民のメールボックスを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p123">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="e1b99-p124">しかし、Exchange 管理センターで行えることには限界があります。たとえば、ブルーミントンかサンディエゴに住んでいる住民のメールボックスを検索したい場合や、ブルーミントンに住んでいないすべての住民のメールボックスを検索したい場合もあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p124">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="e1b99-221">Office 365 PowerShell では、ブルーミントン市やサンディエゴ市に住んでいるすべての住民のメールボックスの一覧を取得するために、次のコマンドを使うことができます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-221">With Office 365 PowerShell, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="e1b99-222">表示例:</span><span class="sxs-lookup"><span data-stu-id="e1b99-222">Here is an example of the display:</span></span>
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  <span data-ttu-id="e1b99-223">この Office 365 PowerShell コマンドの説明: 現在の Office 365 サブスクリプションのユーザーのうち、サンディエゴ市またはブルーミントン市にメールボックスを持つすべてのユーザーを取得し ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($$\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** )、各ユーザーの名前と都市を表示します (**Select DisplayName, City**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-223">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="e1b99-224">ブルーミントン以外に居住しているユーザーのメールボックスをすべて一覧表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-224">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="e1b99-225">表示例:</span><span class="sxs-lookup"><span data-stu-id="e1b99-225">Here is an example of the display:</span></span>
  
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
>  <span data-ttu-id="e1b99-226">この Office 365 PowerShell コマンドの説明: 現在の Office 365 サブスクリプションのユーザーのうち、ブルーミントン市以外の場所にあるメールボックスを持つユーザーすべてを取得し ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** )、各ユーザーの名前と都市を表示します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-226">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="e1b99-p125">Office 365 PowerShell フィルターでワイルドカード文字を使って、名前の一部が一致している項目を検出することもできます。たとえば、あるユーザー アカウントを探しているものの、名字が Anderson か Henderson であることしか思い出せず、もしかすると Jorgenson だったかもしれないとします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p125">You can also use wildcard characters in your Office 365 PowerShell filters to match part of a name. For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="e1b99-229">検索ツールを使用して、次の3つの異なる検索を実行することによって、Microsoft 365 管理センターでそのユーザーを追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-229">You could track down that user in the Microsoft 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="e1b99-230">*Anderson*  用のもの</span><span class="sxs-lookup"><span data-stu-id="e1b99-230">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="e1b99-231">*Henderson*  用のもの</span><span class="sxs-lookup"><span data-stu-id="e1b99-231">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="e1b99-232">*Jorgenson*  用のもの</span><span class="sxs-lookup"><span data-stu-id="e1b99-232">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="e1b99-p126">これら 3 つの名前の最後はどれも「son」で終わっているので、Office 365 PowerShell に、名前の末尾が「son」のユーザーすべてを表示するよう指示できます。コマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p126">Because all three of these names end in "son", you can tell Office 365 PowerShell to display all the users whose name ends in "son". Here is the command:</span></span>
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="e1b99-p127">この Office 365 PowerShell コマンドの説明: 現在の Office 365 サブスクリプションのすべてのユーザーを取得します。ただし、名前の最後が「son」のユーザーのみを一覧表示するフィルターを使用します ( **-Filter '{LastName -like "\*son"}'** )。\* は任意の文字セット (ユーザーのラスト ネームの場合は文字列) を表します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p127">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ). The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="e1b99-237">Office 365 PowerShell を使用するとデータの印刷や保存が簡単にできる</span><span class="sxs-lookup"><span data-stu-id="e1b99-237">Office 365 PowerShell makes it easy to print or save data</span></span>

<span data-ttu-id="e1b99-238">Microsoft 365 管理センターでは、データの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-238">The Microsoft 365 admin center lets you view lists of data.</span></span> <span data-ttu-id="e1b99-239">以下に、skype for business online 管理センターの例を示します。このリストには、Skype for business Online が有効になっているユーザーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-239">Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![Skype for Business Online 管理センターで、Skype for Business Online に対して有効になっているユーザーの一覧を表示する例です。](media/o365-powershell-lync-users.png)
  
<span data-ttu-id="e1b99-241">この情報をファイルに保存するには、コピーしてドキュメントまたは Excel に貼り付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-241">To save that information to a file, you must copy and paste it into a document or Excel.</span></span> <span data-ttu-id="e1b99-242">どちらの場合も、コピー操作には追加の書式設定が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-242">In either case, the copy might require additional formatting.</span></span> <span data-ttu-id="e1b99-243">また、Microsoft 365 管理センターでは、表示されている一覧を直接印刷する方法は提供されていません。</span><span class="sxs-lookup"><span data-stu-id="e1b99-243">Additionally, the Microsoft 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="e1b99-p130">幸い、Office 365 PowerShell を使えば、一覧を表示するだけでなく、ファイルに保存してそれを簡単に Excel にインポートできます。次に示すコマンド例を実行すると、Skype for Business Online ユーザー データがコンマ区切り値 (CSV) ファイルに保存されます。このファイルは、Excel ワークシート内にテーブルとして簡単にインポートできます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p130">Fortunately, you can use Office 365 PowerShell to not only display the list, but save it to a file that can be easily imported into Excel. Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="e1b99-246">表示例:</span><span class="sxs-lookup"><span data-stu-id="e1b99-246">Here is an example of the display:</span></span>
  
![Excel ワークシートにインポートされている、コンマ区切り値 (CSV) ファイルに保存された Skype for Business Online ユーザー データに関するテーブルの例です。](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  <span data-ttu-id="e1b99-248">この Office 365 PowerShell コマンドの説明: 現在の Office 365 サブスクリプションのすべての Skype for Business Online ユーザーを取得し (**Get-CsOnlineUser**)、ユーザー名、UPN、場所のみを取り出します (**Select DisplayName, UserPrincipalName, UsageLocation**)。次に、その情報を C:\\Logs\\SfBUsers.csv という名前の CSV ファイルに保存します (**Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-248">The interpretation of this Office 365 PowerShell command is: Get all of the Skype for Business Online users in the current Office 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="e1b99-p131">また、オプションを使って、この一覧を XML ファイルや HTML ページとして保存できます。実際、追加の PowerShell コマンドを使い、必要なカスタム書式設定で直接 Excel ファイルとして保存できます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p131">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="e1b99-p132">さらに、一覧を表示する Office 365 PowerShell コマンドの出力を、Windows の既定のプリンターに直接送信することもできます。コマンド例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p132">You can also send the output of an Office 365 PowerShell command that displays a list directly to the default printer in Windows. Here is an example command:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="e1b99-253">印刷されたドキュメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e1b99-253">Here's what your printed document will look like:</span></span>
  
![直接 Windows の既定のプリンターに一覧表示された、Office 365 PowerShell コマンドの出力の印刷されたドキュメントの例です。](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  <span data-ttu-id="e1b99-255">この Office 365 PowerShell コマンドの説明: 現在の Office 365 サブスクリプションのすべての Skype for Business Online ユーザーを取得し、ユーザー名、UPN、場所のみを取り出し、その情報を既定の Windows プリンターに送信します (**Out-Printer**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-255">The interpretation of this Office 365 PowerShell command is:  Get all of the Skype for Business Online users in the current Office 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="e1b99-256">印刷されるドキュメントの書式は Office 365 PowerShell コマンド ウィンドウでの表示と同じ単純なものですが、必要なデータの一覧を表示する Office 365 PowerShell コマンドを作成すると、そのコマンドの最後に **| Out-Printer** を追加するだけで、ハードコピーを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-256">The printed document has the same simple formatting as the display within the Office 365 PowerShell command window, but once you have created an Office 365 PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a><span data-ttu-id="e1b99-257">Office 365 PowerShell を使用すると複数のサーバー製品を管理できる</span><span class="sxs-lookup"><span data-stu-id="e1b99-257">Office 365 PowerShell lets you manage across server products</span></span>

<span data-ttu-id="e1b99-p133">Office 365 を構成する各種のコンポーネントは連動するように設計されています。たとえば、Office 365 に新しいユーザーを追加し、そのときにユーザーの部署や電話番号などの情報を指定したとします。この情報は、Office 365 サーバー製品 (Skype for Business Online、Exchange、SharePoint Online) のいずれかを使用してユーザーの情報にアクセスすれば入手できます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p133">The different components that make up Office 365 are designed to work together. For example, suppose you add a new user to Office 365 and, when you do, you specify such information as the user's department and phone number. That information will then be available if you access the user's information using any of the Office 365 server products: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="e1b99-p134">ただし、これは製品のスイートに共通する一般情報の場合です。製品固有の情報 (たとえば、ユーザーの Exchange メールボックスに関する情報など) は基本的にはスイートのすべての製品で入手できるようにはなっていません。たとえば、ユーザーのメールボックスが有効になっているかどうかを把握したい場合などには、Exchange 管理センターにおいてのみこの情報が取得できます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p134">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="e1b99-264">すべてのユーザーに関する次のような情報を示すレポートを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="e1b99-264">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="e1b99-265">ユーザーの表示名</span><span class="sxs-lookup"><span data-stu-id="e1b99-265">The user's display name</span></span>
    
- <span data-ttu-id="e1b99-266">ユーザーが Office 365 のライセンスを所有しているかどうか</span><span class="sxs-lookup"><span data-stu-id="e1b99-266">Whether the user is licensed for Office 365</span></span>
    
- <span data-ttu-id="e1b99-267">ユーザーの Exchange メールボックスが有効になっているかどうか</span><span class="sxs-lookup"><span data-stu-id="e1b99-267">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="e1b99-268">ユーザーが Skype for Business Online に対して有効になっているかどうか</span><span class="sxs-lookup"><span data-stu-id="e1b99-268">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="e1b99-269">現時点では、Microsoft 365 管理センターを使用してこのようなレポートを簡単に作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="e1b99-269">You currently cannot use the Microsoft 365 admin center to easily produce such a report.</span></span> <span data-ttu-id="e1b99-270">代わりに、Excel ワークシートなどの情報を格納する別のドキュメントを作成し、Microsoft 365 管理センターからすべてのユーザー名とライセンス情報を取得する必要があります。また、Exchange 管理センターからメールボックス情報を取得して、Skype for Business を取得することもできます。Skype for Business Online 管理センターからのビジネスオンライン情報を入力し、その情報を照合して結合します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-270">Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Microsoft 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="e1b99-271">これに代わる方法として、Office 365 PowerShell スクリプトを使ってレポートをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="e1b99-271">The alternative is to use an Office 365 PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="e1b99-p136">次のスクリプト例は、この記事でこれまでに示したコマンドの中で最も複雑です。しかし、この例は、他の方法では作成の難しい情報のビューも Office 365 PowerShell を使用すれば作成できる場合があることを示しています。必要な一覧をコンパイルして表示するスクリプトを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e1b99-p136">The following example script is more complicated than the commands you have seen so far in this article. But, it shows the potential of using Office 365 PowerShell to create views of information that are very difficult to do otherwise. Here is the script that can compile and display the needed list:</span></span>
  
```powershell
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

<span data-ttu-id="e1b99-275">表示例:</span><span class="sxs-lookup"><span data-stu-id="e1b99-275">Here is an example of the display:</span></span>
  
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

<span data-ttu-id="e1b99-276">この Office 365 PowerShell スクリプトの説明:</span><span class="sxs-lookup"><span data-stu-id="e1b99-276">The interpretation of this Office 365 PowerShell script is:</span></span>  
- <span data-ttu-id="e1b99-277">現在の Office 365 サブスクリプション内のすべてのユーザーを取得し、その情報を $x という名前の変数に格納します (**$x = Get-MsolUser**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-277">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="e1b99-278">$x という変数内のすべてのユーザーに対して実行されるループを開始します (**foreach ($i in $x)**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-278">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="e1b99-279">$y という名前の変数を定義し、ユーザーのメールボックス情報をその変数に格納します (**$y = Get-Mailbox -Identity $i.UserPrincipalName**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-279">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="e1b99-280">ユーザー情報に IsMailBoxEnabled という新しいプロパティを追加し、このプロパティの値に、ユーザーのメールボックスの IsMailBoxEnabled プロパティの値を設定します (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-280">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="e1b99-281">$y という変数を定義し、ユーザーの Skype for Business Online 情報をその変数に格納します (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-281">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="e1b99-282">EnabledForSfB という名前の新しいプロパティをユーザー情報に追加し、このプロパティの値に、ユーザーの Skype for Business Online 情報の Enabled プロパティの値を設定します (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-282">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="e1b99-283">ユーザーの一覧を表示します。ただし、含めるのは、ユーザー名、ライセンス認定されているかどうか、およびメールボックスが使用可能かどうかと Skype for Business Online に対して有効かどうかを示す 2 つの新たなプロパティのみとします (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**)。</span><span class="sxs-lookup"><span data-stu-id="e1b99-283">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e1b99-284">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1b99-284">See also</span></span>

[<span data-ttu-id="e1b99-285">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="e1b99-285">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="e1b99-286">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="e1b99-286">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e1b99-287">Windows PowerShell を使用して Office 365 でレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="e1b99-287">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

