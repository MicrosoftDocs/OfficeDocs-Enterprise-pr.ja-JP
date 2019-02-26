---
title: ユーザーのメールボックスで削除済みアイテムを復元する - 管理者ヘルプ
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: 'この記事は、管理者を対象としています。ユーザーが Outlook メールボックスからアイテムを完全に削除したかどうか。ユーザーはそれらを回復することはできません。削除されたアイテムがユーザーのメールボックスから完全に削除されていない場合は、それらを回復できることがあります。 '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541576"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="80dd2-106">ユーザーのメールボックスで削除済みアイテムを復元する - 管理者ヘルプ</span><span class="sxs-lookup"><span data-stu-id="80dd2-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="80dd2-p102">**この記事は、管理者を対象としています。自分のメールボックス内の削除済みアイテムを復元しようとしていますか?** 次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p102">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?** Try one of the following:</span></span>
- [<span data-ttu-id="80dd2-109">Windows 版 Outlook で削除済みのアイテムを復元する</span><span class="sxs-lookup"><span data-stu-id="80dd2-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="80dd2-110">Outlook Web App で削除済みのアイテムやメールを復元する</span><span class="sxs-lookup"><span data-stu-id="80dd2-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="80dd2-111">Outlook on the web で削除されたメールメッセージを復元する</span><span class="sxs-lookup"><span data-stu-id="80dd2-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="80dd2-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="80dd2-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="80dd2-p103">ユーザーが Outlook メールボックスからアイテムを完全に削除したかどうか。ユーザーはそれらを回復することはできません。削除されたアイテムがユーザーのメールボックスから完全に削除されていない場合は、それらを回復できることがあります。これを行うには、Exchange Online のインプレース電子情報開示ツールを使用して、ユーザーのメールボックスで、削除されたメールやその他のアイテム (連絡先、予定表の予定、タスクなど) を検索します。削除済みアイテムが見つかった場合は、そのアイテムを PST ファイル (Outlook データファイルとも呼ばれます) にエクスポートし、ユーザーがそのアイテムをメールボックスに復元するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p103">Did a user permanently delete items from their Outlook mailbox? The user wants them back but can't recover them. You may be able recover the purged items if they haven't been permanently removed from the user's mailbox. You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox. If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="80dd2-p104">ユーザーのメールボックス内の削除済みアイテムを復元する手順を次に示します。これにはどのくらい時間がかかりますか?最初に、回復しようとしているアイテムの数に応じて、すべての手順を完了するのに20分または30分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p104">Here are the steps for recovering deleted items in a user's mailbox. How long will this take? The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="80dd2-p105">この記事の手順を実行するには、Office 365 の**exchange 管理**者または**全体管理者**であるか、または exchange Online の Organization Management 役割グループのメンバーである必要があります。詳細については、「 [Office 365 管理者ロールについ](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p105">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article. For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="80dd2-123">手順 1: 自分自身に電子情報開示のアクセス許可を割り当てる</span><span class="sxs-lookup"><span data-stu-id="80dd2-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="80dd2-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="80dd2-124"></span></span>

<span data-ttu-id="80dd2-p106">最初の手順として、インプレース電子情報開示ツールを使用してユーザーのメールボックスを検索できるように、Exchange Online で必要なアクセス許可を自分自身に割り当てます。これを行う必要があるのは1回だけです。今後、別のメールボックスを検索する必要がある場合は、この手順を省略できます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p106">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox. You only have to do this once. If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="80dd2-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="80dd2-129">左上隅にある Office ![365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)のアプリ起動ツールのアイコンを選択し、[**管理者**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="80dd2-130">Office 365 管理センターの左側のナビゲーションで、[**管理センター**] を展開し、[ **Exchange**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![管理センターの一覧](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="80dd2-132">Exchange 管理センターで、[**アクセス許可**] をクリックし、[**管理役割**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="80dd2-133">リストビューで、[**探索管理**] を選択し、[編集アイコン](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)の**編集**![] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![EAC の "Discovery Management/検出の管理" 役割グループに自分を追加します。](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="80dd2-135">[**役割グループ**] の [**メンバー**] \*\*\*\*![で、[](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)追加] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="80dd2-136">[**メンバーの選択**] で、名前のリストから [自分自身] を選択し、[**追加**] をクリックして、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="80dd2-p107">また、組織の管理や tenantadmins など、メンバーとなっているグループを追加することもできます。グループを追加すると、そのグループの他のメンバーに、インプレース電子情報開示ツールを実行するために必要なアクセス許可が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p107">You can also add a group that you are a member of, such as Organization Management or TenantAdmins. If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="80dd2-139">**[役割グループ]** で、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="80dd2-140">Office 365 からサインアウトします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="80dd2-141">新しいアクセス許可が有効になるように、次の手順を開始する前に、サインアウトする必要があります。</span><span class="sxs-lookup"><span data-stu-id="80dd2-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="80dd2-p108">Discovery Management 役割グループのメンバーは、機密メッセージコンテンツにアクセスできます。これには、組織内のすべてのメールボックスの検索、検索結果 (およびその他のメールボックスアイテム) のプレビュー、探索メールボックスへの結果のコピー、および検索結果を PST ファイルにエクスポートすることが含まれます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p108">Members of the Discovery Management role group can access sensitive message content. This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="80dd2-144">Return to top</span><span class="sxs-lookup"><span data-stu-id="80dd2-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="80dd2-145">手順 2: ユーザーのメールボックスで削除済みアイテムを検索する</span><span class="sxs-lookup"><span data-stu-id="80dd2-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="80dd2-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="80dd2-146"></span></span>

<span data-ttu-id="80dd2-p109">インプレース電子情報開示検索を実行すると、検索するメールボックス内の [回復可能なアイテム] フォルダーが自動的に検索に含められます。回復可能なアイテムフォルダーは、完全に削除されたアイテムがメールボックスから削除 (完全に削除) されるまで保存されます。そのため、アイテムが削除されていない場合は、インプレース電子情報開示ツールを使用して見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p109">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search. The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox. So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="80dd2-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="80dd2-151">左上隅にある Office ![365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)のアプリ起動ツールのアイコンを選択し、[**管理者**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="80dd2-152">Office 365 管理センターの左側のナビゲーションで、[**管理者**] を展開し、[ **Exchange**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="80dd2-153">Exchange 管理センターで、[**コンプライアンス管理**] をクリックし、[**インプレース&amp;電子情報開示の保持**] をクリック](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)して、[**新規**![追加] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![EAC の [コンプライアンス管理] ページで、[インプレースの電子情報開示と保持] をクリックします。](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="80dd2-155">[**名前と説明**] ページで、検索の名前 (電子メールを回復するユーザーの名前など) を入力し、オプションの説明を入力して、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="80dd2-156">[**メールボックス**] ページで、[**検索するメールボックスを指定する**] を](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)クリックし、[追加] アイコンをクリック\*\*\*\*![します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![[検索するメールボックスを指定する] をクリックして表面化メールボックスを検索する](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="80dd2-158">削除されたメールを回復するユーザーの名前を検索して選択し、[**追加**] をクリックして、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="80dd2-159">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-159">Click **Next**.</span></span>
    
    <span data-ttu-id="80dd2-p110">[**検索クエリ**] ページが表示されます。ここでは、ユーザーのメールボックス内の不足しているアイテムを検索するために使用できる検索条件を定義します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p110">The **Search query** page is displayed. This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="80dd2-162">**[検索クエリ]** ページで、以下のフィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="80dd2-p111">**すべてのコンテンツを含める**ユーザーのメールボックス内のすべてのコンテンツを検索結果に含めるには、このオプションを選択します。このオプションを選択した場合、追加の検索条件を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p111">**Include all content** Select this option to include all content in the user's mailbox in the search results. If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="80dd2-165">**条件に基づいてフィルターを**適用するこのオプションを選択すると、キーワード、開始日と終了日、送信者および受信者のアドレス、メッセージの種類などの検索条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![キーワード、日付の範囲、受信者、メッセージの種類などの条件に基づいて、検索を作成します。](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="80dd2-167">**フィールド**</span><span class="sxs-lookup"><span data-stu-id="80dd2-167">**Field**</span></span>|<span data-ttu-id="80dd2-168">**使用する方法...**</span><span class="sxs-lookup"><span data-stu-id="80dd2-168">**Use this to...**</span></span>|
|:-----|:-----|
|![ピンクの丸の番号 1](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="80dd2-170">キーワード、日付の範囲、受信者、メッセージの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![ピンクの丸の番号 2](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="80dd2-172">キーワードまたは語句を含むメッセージを検索し、 **and**や**or**などの論理演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![ピンクの丸の番号 3](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="80dd2-174">日付範囲内で送受信されたメッセージを検索します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![ピンクの丸の番号 4](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="80dd2-176">特定のユーザーとの間で受信または送信されたメッセージを検索します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![ピンクの丸の5番目の数字。](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="80dd2-178">すべてのメッセージの種類を検索するか、特定の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="80dd2-p112">[**インプレース保持の設定**] ページで、[**完了**] をクリックして検索を開始します。削除されたメールを回復するために、ユーザーのメールボックスを保留にする理由はありません。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p112">On the **In-Place Hold settings** page, click **Finish** to start the search. To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="80dd2-181">検索を開始すると、指定した条件に基づいて検索によって返されるアイテムの合計サイズと数の推定値が Exchange に表示されます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="80dd2-p113">作成したばかりの検索を選択\*\*\*\*![し、](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) [更新の更新] をクリックして、詳細ウィンドウに表示される情報を更新します。**推定**の状態は、検索が完了したことを示します。また、Exchange には、手順9で指定した検索条件に基づいて、検索によって検出されたアイテムの総数 (およびそのサイズ) の推定値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p113">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane. The status of **Estimate Succeeded** indicates that the search has finished. Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="80dd2-p114">詳細ウィンドウで、[**検索結果のプレビュー** ] をクリックして、見つかったアイテムを表示します。これは、探しているアイテムを特定するのに役立つことがあります。回復しようとしているアイテムが見つかった場合は、手順4に進み、検索結果を PST ファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p114">In the details pane, click **Preview search results** to view the items that were found. This might help you identify the item(s) that you're looking for. If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![[検索結果のプレビュー] をクリックして、回復しようとしているアイテムを表示します。](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="80dd2-p115">探している内容が見つからない場合は、検索を選択し、[ \*\*\*\*![編集] 編集アイコンをクリックして、](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)[**検索クエリ**] をクリックすると、検索条件を変更できます。検索条件を変更してから、検索を再実行してください。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p115">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**. Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="80dd2-191">Return to top</span><span class="sxs-lookup"><span data-stu-id="80dd2-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="80dd2-192">オプション手順 3: 検索結果を探索メールボックスにコピーする</span><span class="sxs-lookup"><span data-stu-id="80dd2-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="80dd2-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="80dd2-193"></span></span>

<span data-ttu-id="80dd2-p116">検索結果をプレビューしてアイテムが見つからない場合や、ユーザーの回復可能なアイテムフォルダーにあるアイテムを確認する場合は、検索結果を特別なメールボックス (探索メールボックスと呼ばれます) にコピーし、そのメールボックスを web 上の Outlook で開くことができます。o 実際のアイテムを表示します。検索結果をコピーする最善の理由は、ユーザーの回復可能なアイテムフォルダー内のアイテムを表示できるようにするためです。多くの場合、回復しようとしているアイテムがパージサブフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p116">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items. The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder. More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="80dd2-197">Exchange 管理センターで、[**コンプライアンス管理** \> ]**の [インプレース電子情報&amp;開示の保持**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="80dd2-198">検索の一覧で、手順2で作成した検索を選択します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="80dd2-199">[検索検索](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)] をクリックし、ドロップダウンリストから [**検索結果のコピー** ] をクリックします。 \*\*\*\*![</span><span class="sxs-lookup"><span data-stu-id="80dd2-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![[検索] をクリックし、[検索結果のコピー] をクリックします。](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="80dd2-201">[**検索結果のコピー** ] ページで、[**参照**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![削除済みアイテムを復元するときはチェックボックスをオフのままにする](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="80dd2-203">[**表示名**] で [**探索検索メールボックス**] をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![検索結果を既定の探索検索メールボックスにコピーする](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="80dd2-205">探索検索メールボックスは、Office 365 組織に自動的に作成される既定の証拠開示用メールボックスです。</span><span class="sxs-lookup"><span data-stu-id="80dd2-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="80dd2-206">[**検索結果のコピー** ] ページに戻り、[**コピー** ] をクリックして、検索結果を探索検索メールボックスにコピーするプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![検索結果を探索検索メールボックスにコピーするには、[コピー] をクリックします。](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="80dd2-208">[更新の](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)更新] をクリックして、詳細ウィンドウに表示されるコピー状態に関する情報を更新します。 \*\*\*\*![</span><span class="sxs-lookup"><span data-stu-id="80dd2-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="80dd2-209">コピーが完了したら、[**開く**] をクリックして探索検索メールボックスを開き、検索結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![[開く] をクリックして探索検索メールボックスに移動し、検索結果を表示します。](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="80dd2-p117">探索検索メールボックスにコピーされた検索結果は、インプレース電子情報開示検索と同じ名前のフォルダーに配置されます。フォルダーをクリックすると、そのフォルダー内のアイテムを表示できます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p117">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search. You can click a folder to display the items in that folder.</span></span>
    
    ![探索検索メールボックス内の検索結果。削除フォルダー内のアイテムは、管理者のみが復元できます。](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="80dd2-p118">検索を実行すると、ユーザーの回復可能なアイテムフォルダーも検索されます。つまり、回復可能なアイテムフォルダーのアイテムが検索条件を満たしていれば、それらは検索結果に含まれます。削除フォルダー内のアイテムは、削除済みアイテムフォルダーからアイテムを削除するか、またはそれを選択して Shift キーを押し**ながら del**キーを押すことによって、ユーザーが完全に削除したアイテムです。ユーザーは、outlook または web 上の outlook の削除済みアイテムの回復ツールを使用して、削除フォルダー内のアイテムを復元できます。削除フォルダー内のアイテムは、削除済みアイテムの復元ツールまたはメールボックスに適用されたポリシーによって自動的に削除されたアイテムを使用してユーザーが削除したアイテムです。どちらの場合も、管理者のみが [削除] フォルダー内のアイテムを復元できます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p118">When you run a search, the user's Recoverable Items folder is also searched. That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results. Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**. A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder. Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox. In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="80dd2-p119">回復可能なアイテムツールを使用して削除されたアイテムをユーザーが見つけられない場合でも、そのアイテムはまだ回復可能である (メールボックスから完全に削除されていないことを意味します) ので、パージフォルダーに配置される可能性が高くなります。そのため、ユーザーに対して回復しようとしている削除済みのアイテムの [削除] フォルダーを確認してください。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p119">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder. So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="80dd2-222">Return to top</span><span class="sxs-lookup"><span data-stu-id="80dd2-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="80dd2-223">手順 4: 検索結果を PST ファイルにエクスポートする</span><span class="sxs-lookup"><span data-stu-id="80dd2-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="80dd2-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="80dd2-224"></span></span>

<span data-ttu-id="80dd2-p120">ユーザーの回復を試行しているアイテムが見つかったら、次の手順では、手順2で実行した検索結果を PST ファイルにエクスポートします。ユーザーは、次の手順でこの PST ファイルを使用して、削除されたアイテムをメールボックスに復元します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p120">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file. The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="80dd2-227">Exchange 管理センターで、[**コンプライアンス管理** \> ]**の [インプレース電子情報&amp;開示の保持**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="80dd2-228">検索の一覧で、手順2で作成した検索を選択します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="80dd2-229">[ **PST ファイルへのエクスポート] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-229">Click **Export to a PST file**.</span></span>
    
    ![[PST ファイルへのエクスポート] をクリックします。](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="80dd2-231">電子情報開示エクスポートツールをインストールするように求めるメッセージが表示されたら、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="80dd2-232">電子情報開示の pst エクスポートツールで、[**参照**] をクリックして、PST ファイルをダウンロードする場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![電子情報開示の PST エクスポートツール](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="80dd2-234">重複除去を有効にし、検索不能アイテムを含めるには、オプションを無視します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="80dd2-235">[**スタート**] をクリックして、PST ファイルをコンピューターにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="80dd2-p121">**電子情報開示 PST エクスポートツール**は、エクスポート処理に関する状態情報を表示します。エクスポートが完了すると、ファイルはダウンロードされた場所でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p121">The **eDiscovery PST Export Tool** displays status information about the export process. When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="80dd2-238">Return to top</span><span class="sxs-lookup"><span data-stu-id="80dd2-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="80dd2-239">手順 5: 回復されたアイテムをユーザーのメールボックスに復元する</span><span class="sxs-lookup"><span data-stu-id="80dd2-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="80dd2-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="80dd2-240"></span></span>

<span data-ttu-id="80dd2-p122">最後の手順では、手順4でエクスポートした PST ファイルを使用して、回復されたアイテムをユーザーのメールボックスに復元します。pst ファイルをユーザーに送信した後、この手順の残りの部分は、ユーザーが pst ファイルを開き、回復されたアイテムを自分のメールボックス内の別のフォルダーに移動することによって実行されます。詳細な手順については、このトピック「 [Outlook データファイル (.pst) を開いて閉じる](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2)」のリンクをユーザーに送信することもできます。または、以下の「PST ファイル」セクションを[使用して、削除済みアイテムをメールボックスに復元](recover-deleted-items-in-a-mailbox.md#restoredeleteditems)するためのリンクをユーザーに送信し、これらの手順を実行するように依頼することもできます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p122">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox. After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox. For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="80dd2-245">**ユーザーに PST ファイルを送信する**</span><span class="sxs-lookup"><span data-stu-id="80dd2-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="80dd2-p123">最後の手順として、手順4でエクスポートした PST ファイルをユーザーに送信する必要があります。これを行うには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p123">The final step that you need to perform is sending the PST file that was exported in step 4 to the user. There are a few ways to do this:</span></span>
  
- <span data-ttu-id="80dd2-p124">PST ファイルを電子メールメッセージに添付します。Outlook が PST ファイルをブロックするように構成されている場合は、ファイルを圧縮してからメッセージに添付する必要があります。方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p124">Attach the PST file to an email message. If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message. Here's how:</span></span>
    
1. <span data-ttu-id="80dd2-251">エクスプローラーまたはエクスプローラーで、PST ファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="80dd2-p125">ファイルを右クリックし、[ \> **圧縮 (zip 形式) フォルダー\*\*\*\*に送信**] を選択します。Windows によって新しい zip ファイルが作成され、PST ファイルと同じ名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p125">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**. Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="80dd2-254">圧縮された PST ファイルを電子メールメッセージに添付し、ユーザーに送信します。その後、ファイルをクリックするだけでそのファイルを展開できます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="80dd2-255">ユーザーがアクセスして取得できる共有フォルダーに PST ファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="80dd2-256">次のセクションの手順は、削除されたアイテムをメールボックスに復元するためにユーザーによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <span data-ttu-id="80dd2-257">**PST ファイルを使用して削除済みアイテムをメールボックスに復元する**</span><span class="sxs-lookup"><span data-stu-id="80dd2-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="80dd2-p126">PST ファイルを使用して削除済みのアイテムを復元するには、Outlook デスクトップアプリを使用する必要があります。outlook web App または outlook on the web を使用して PST ファイルを開くことはできません。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p126">You have to use the Outlook desktop app to restore a deleted item by using a PST file. You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="80dd2-260">outlook 2013 または outlook 2016 で、[**ファイル**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="80dd2-261">[**エクスポート&amp;を開く**] をクリックし、[ **Outlook データファイルを開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="80dd2-262">管理者が送信した PST ファイルを保存した場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="80dd2-263">PST を選択し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="80dd2-264">PST ファイルは、Outlook の左側のナビゲーションバーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![PST ファイルは、Outlook の左側のナビゲーションバーに表示されます。](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="80dd2-266">矢印をクリックして、PST ファイルとその下のフォルダーを展開し、復元するアイテムを見つけます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![回復するアイテムの [削除] フォルダーを確認する](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="80dd2-p127">復元するアイテムの [削除] フォルダーを調べます。これは、削除されたアイテムの移動先となる隠しフォルダーです。管理者が復元したアイテムは、このフォルダーにある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p127">Look in the Purges folder for the item you want to recover. This is a hidden folder that purged items are moved to. It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="80dd2-271">回復する項目を右クリックし、[**他のフォルダーの\*\*\*\*移動** \> ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![[移動] をクリックし、[その他のフォルダー] を選択します。](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="80dd2-273">アイテムを受信トレイに移動するには、[**受信トレイ**] をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="80dd2-274">**ヒント:** その他の種類のアイテムを復元するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="80dd2-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="80dd2-275">予定表アイテムを回復するには、そのアイテムを右クリックして、[**その他のフォルダー** \>の**予定表**を**移動** \> ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="80dd2-276">連絡先を回復するには、連絡先を右クリックして、[**その他のフォルダー** \>の**連絡先**を**移動** \>する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="80dd2-277">タスクを回復するには、タスクを右クリックして、[**その他のフォルダー** \> **タスク**を**移動** \> ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dd2-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![他の種類のアイテムを移動するフォルダーを選択する](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="80dd2-279">削除済みアイテムの復元が終了したら、左側のナビゲーションバーで pst ファイルを右クリックし、[ **pst ファイルの名前を閉じる**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="80dd2-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="80dd2-280">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="80dd2-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="80dd2-281">詳細情報</span><span class="sxs-lookup"><span data-stu-id="80dd2-281">More information</span></span>
<span data-ttu-id="80dd2-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="80dd2-282"></span></span>

- <span data-ttu-id="80dd2-p128">アイテムの削除済みアイテムの保存期間の期限が切れていない場合、ユーザーは完全に削除されたアイテムを回復できる可能性があります。管理者として、回復可能なアイテムフォルダー内のアイテムを回復に使用できる期間を指定している可能性があります。たとえば、ユーザーの削除済みアイテムフォルダーに含まれていたものを30日間削除するポリシーがあり、さらにユーザーが回復可能なアイテムフォルダー内のアイテムを別の14日まで復元できるようにするポリシーがあるとします。ただし、この14日を過ぎると、このトピックの手順を使用して、ユーザーのメールボックス内のアイテムを復元することができます。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p128">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired. As an admin you may have specified how long items in the Recoverable Items folder are available for recovery. For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days. However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="80dd2-p129">削除されていないアイテムの削除済みアイテムの保存期間が切れていない場合、ユーザーは削除済みアイテムを復元できます。ユーザーが自分のメールボックス内の削除済みアイテムを復元できるようにするには、次のいずれかのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="80dd2-p129">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired. To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="80dd2-289">Windows 版 Outlook で削除済みのアイテムを復元する</span><span class="sxs-lookup"><span data-stu-id="80dd2-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="80dd2-290">Outlook 2010 で削除済みのアイテムを復元する</span><span class="sxs-lookup"><span data-stu-id="80dd2-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="80dd2-291">Outlook Web App で削除済みのアイテムやメールを復元する</span><span class="sxs-lookup"><span data-stu-id="80dd2-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="80dd2-292">Outlook on the web で削除されたメールメッセージを復元する</span><span class="sxs-lookup"><span data-stu-id="80dd2-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="80dd2-293">Outlook で削除された連絡先を復元する</span><span class="sxs-lookup"><span data-stu-id="80dd2-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="80dd2-294">Outlook.com で削除されたメールメッセージを復元する</span><span class="sxs-lookup"><span data-stu-id="80dd2-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="80dd2-295">Return to top</span><span class="sxs-lookup"><span data-stu-id="80dd2-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

