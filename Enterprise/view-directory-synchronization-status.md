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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: ディレクトリ同期を非アクティブ化する方法について説明します。その状態を表示することもできます。
ms.openlocfilehash: 4803cbadd17dbc1ee23d019f39144ff1ffaefd9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085056"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="e73f8-104">Office 365 のディレクトリ同期の状態を表示する</span><span class="sxs-lookup"><span data-stu-id="e73f8-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="e73f8-105">オンプレミス環境と Office 365 を同期することによって、オンプレミスの Active Directory を Azure AD に統合している場合は、同期の状態を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="e73f8-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="e73f8-106">ディレクトリ同期の状態を表示する</span><span class="sxs-lookup"><span data-stu-id="e73f8-106">View directory synchronization status</span></span>
- <span data-ttu-id="e73f8-107">Office 365 管理センターにサインインし、ホームページの [ **DirSync Status** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e73f8-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="e73f8-p102">または、[**アクティブ**な\*\*\*\* \>ユーザー] ページに移動し、 **[アクティブなユーザー** ] ページで、[**ディレクトリ同期**の**追加** \> ] を選択します。[**ディレクトリ同期**] ウィンドウで、[ **DirSync management に移動] を**選択します。</span><span class="sxs-lookup"><span data-stu-id="e73f8-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="e73f8-110">[ディレクトリ同期の管理] ページの情報</span><span class="sxs-lookup"><span data-stu-id="e73f8-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="e73f8-111">次の表に、ページの情報を取得できる機能を示します。</span><span class="sxs-lookup"><span data-stu-id="e73f8-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="e73f8-p103">ディレクトリ同期に問題がある場合は、このページにもエラーが表示されます。発生する可能性のあるさまざまなエラーの詳細については、「 [Office 365 でのディレクトリ同期エラーの識別](identify-directory-synchronization-errors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e73f8-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="e73f8-114">**項目**</span><span class="sxs-lookup"><span data-stu-id="e73f8-114">**Item**</span></span>|<span data-ttu-id="e73f8-115">**目的**</span><span class="sxs-lookup"><span data-stu-id="e73f8-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e73f8-116">**確認されたドメイン**</span><span class="sxs-lookup"><span data-stu-id="e73f8-116">**Domains verified**</span></span> | <span data-ttu-id="e73f8-117">自分が所有していることが確認された Office 365 テナント内のドメインの数。</span><span class="sxs-lookup"><span data-stu-id="e73f8-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="e73f8-118">**確認されていないドメイン**</span><span class="sxs-lookup"><span data-stu-id="e73f8-118">**Domains not verified**</span></span> | <span data-ttu-id="e73f8-119">追加されたが確認されていないドメイン。</span><span class="sxs-lookup"><span data-stu-id="e73f8-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="e73f8-120">**ディレクトリ同期の有効化**</span><span class="sxs-lookup"><span data-stu-id="e73f8-120">**Directory sync enabled**</span></span> |<span data-ttu-id="e73f8-p104">True または False。ディレクトリ同期を有効にしたかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e73f8-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="e73f8-123">**最新のディレクトリ同期**</span><span class="sxs-lookup"><span data-stu-id="e73f8-123">**Latest directory sync**</span></span> | <span data-ttu-id="e73f8-p105">ディレクトリ同期が最後に実行した時刻。前回の同期が3日以上前の場合は、警告とトラブルシューティングツールへのリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e73f8-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="e73f8-126">**パスワード同期の有効化**</span><span class="sxs-lookup"><span data-stu-id="e73f8-126">**Password sync enabled**</span></span> | <span data-ttu-id="e73f8-p106">True または False。オンプレミスと Office 365 テナント間でパスワードハッシュを同期するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e73f8-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="e73f8-129">**前回のパスワード同期**</span><span class="sxs-lookup"><span data-stu-id="e73f8-129">**Last Password Sync**</span></span> | <span data-ttu-id="e73f8-p107">前回のパスワードハッシュ同期を実行した時刻。前回の同期が3日以上前の場合は、警告とトラブルシューティングツールへのリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e73f8-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="e73f8-132">**ディレクトリ同期クライアントバージョン**</span><span class="sxs-lookup"><span data-stu-id="e73f8-132">**Directory sync client version**</span></span> | <span data-ttu-id="e73f8-133">Azure AD Connect の新しいバージョンがリリースされた場合のダウンロードリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e73f8-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="e73f8-134">**idfix ツール**</span><span class="sxs-lookup"><span data-stu-id="e73f8-134">**IDFix Tool**</span></span> | <span data-ttu-id="e73f8-135">ローカルの Active Directory を確認するためのツールである[idfix](install-and-run-idfix.md)へのリンクをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="e73f8-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="e73f8-136">**ディレクトリ同期サービスアカウント**</span><span class="sxs-lookup"><span data-stu-id="e73f8-136">**Directory sync service account**</span></span> | <span data-ttu-id="e73f8-137">Office 365 ディレクトリ同期サービスアカウントの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e73f8-137">Displays the name of you Office 365 directory sync service account.</span></span> |