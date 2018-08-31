---
title: Office 365 のディレクトリ同期の状態を表示する
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: ディレクトリ同期を無効にする方法を説明します。ステータスを表示することもできます。
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541821"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="6f41a-104">Office 365 のディレクトリ同期の状態を表示する</span><span class="sxs-lookup"><span data-stu-id="6f41a-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="6f41a-105">Azure AD を Office 365 で、オンプレミス環境を同期することにより、オンプレミスの Active Directory を統合した場合は、同期のステータスを確認することも。</span><span class="sxs-lookup"><span data-stu-id="6f41a-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="6f41a-106">ディレクトリ同期の状態の表示</span><span class="sxs-lookup"><span data-stu-id="6f41a-106">View directory synchronization status</span></span>
- <span data-ttu-id="6f41a-107">Office 365 の管理センターにサインインし、[ホーム] ページで、**ディレクトリ同期のステータス**を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f41a-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="6f41a-p102">代わりに、**ユーザー**に情報を移動することができます\>**アクティブなユーザー**の**詳細**を選択して [**アクティブ ユーザ**] ページで、 \> **ディレクトリ同期**します。**ディレクトリ同期**] ウィンドウで、[**ディレクトリ同期の管理に移動します**を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f41a-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="6f41a-110">ディレクトリ同期の管理] ページの情報</span><span class="sxs-lookup"><span data-stu-id="6f41a-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="6f41a-111">次の表は、ページ上の情報を確認する機能を一覧します。</span><span class="sxs-lookup"><span data-stu-id="6f41a-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="6f41a-p103">ディレクトリ同期によって、問題がある、このページにも同様のエラーの一覧が表示されます。さまざまなエラーが発生する可能性の詳細については、 [Office 365 のディレクトリ同期エラーを識別する](identify-directory-synchronization-errors.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f41a-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="6f41a-114">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="6f41a-114">**Item**</span></span>|<span data-ttu-id="6f41a-115">**何**</span><span class="sxs-lookup"><span data-stu-id="6f41a-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6f41a-116">**ドメインの確認**</span><span class="sxs-lookup"><span data-stu-id="6f41a-116">**Domains verified**</span></span> | <span data-ttu-id="6f41a-117">所有することを確認した場合、Office 365 テナント内のドメインの数。</span><span class="sxs-lookup"><span data-stu-id="6f41a-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="6f41a-118">**ドメインが確認されていません**</span><span class="sxs-lookup"><span data-stu-id="6f41a-118">**Domains not verified**</span></span> | <span data-ttu-id="6f41a-119">ドメインを追加するが確認されていません。</span><span class="sxs-lookup"><span data-stu-id="6f41a-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="6f41a-120">**ディレクトリ同期が有効になっています。**</span><span class="sxs-lookup"><span data-stu-id="6f41a-120">**Directory sync enabled**</span></span> |<span data-ttu-id="6f41a-p104">True または false を指定します。ディレクトリ同期を有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f41a-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="6f41a-123">**最新のディレクトリ同期**</span><span class="sxs-lookup"><span data-stu-id="6f41a-123">**Latest directory sync**</span></span> | <span data-ttu-id="6f41a-p105">前回のディレクトリ同期を実行します。表示されます警告リンク トラブルシューティング ツールを前回の同期が 3 日以上前である場合。</span><span class="sxs-lookup"><span data-stu-id="6f41a-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="6f41a-126">**パスワード同期が有効になっています。**</span><span class="sxs-lookup"><span data-stu-id="6f41a-126">**Password sync enabled**</span></span> | <span data-ttu-id="6f41a-p106">True または false を指定します。設置と、Office 365 テナント間でのパスワード ハッシュの同期があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f41a-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="6f41a-129">**最後のパスワード同期**</span><span class="sxs-lookup"><span data-stu-id="6f41a-129">**Last Password Sync**</span></span> | <span data-ttu-id="6f41a-p107">前回のパスワード ハッシュの同期を実行します。表示されます警告リンク トラブルシューティング ツールを前回の同期が 3 日以上前である場合。</span><span class="sxs-lookup"><span data-stu-id="6f41a-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="6f41a-132">**ディレクトリ同期クライアントのバージョン**</span><span class="sxs-lookup"><span data-stu-id="6f41a-132">**Directory sync client version**</span></span> | <span data-ttu-id="6f41a-133">Azure AD 接続の新しいバージョンがリリースされている場合は、ダウンロードのリンクに含まれています。</span><span class="sxs-lookup"><span data-stu-id="6f41a-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="6f41a-134">**IDFix ツール**</span><span class="sxs-lookup"><span data-stu-id="6f41a-134">**IDFix Tool**</span></span> | <span data-ttu-id="6f41a-135">[IDFix](install-and-run-idfix.md)、ローカルの Active Directory をチェックすることができますを使用するツールへのリンクをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="6f41a-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="6f41a-136">**ディレクトリ同期サービス アカウント**</span><span class="sxs-lookup"><span data-stu-id="6f41a-136">**Directory sync service account**</span></span> | <span data-ttu-id="6f41a-137">Office 365 のディレクトリ同期サービス アカウントの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="6f41a-137">Displays the name of you Office 365 directory sync service account.</span></span> |