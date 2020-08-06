---
title: Microsoft 365 でのディレクトリ同期状態の表示
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: ディレクトリ同期を非アクティブ化する方法について説明します。 その状態を表示することもできます。
ms.openlocfilehash: 4c2f0baf6d3657e3eb9974ff7d4f8109e52e603b
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571040"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="7b7d6-104">Microsoft 365 でのディレクトリ同期状態の表示</span><span class="sxs-lookup"><span data-stu-id="7b7d6-104">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="7b7d6-105">オンプレミス環境を Microsoft 365 と同期させることによって、オンプレミスの Active Directory を Azure AD と統合した場合は、同期の状態を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="7b7d6-106">ディレクトリ同期の状態を表示する</span><span class="sxs-lookup"><span data-stu-id="7b7d6-106">View directory synchronization status</span></span>

- <span data-ttu-id="7b7d6-107">[Microsoft 365 管理センター](https://admin.microsoft.com)にサインインし、ホームページの [ **DirSync Status** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="7b7d6-108">または、[アクティブなユーザー] ページ**に移動**し、[ \> **Active users\*\*\*\*アクティブなユーザー** ] ページで、[ディレクトリ同期の**追加**] を選択し \> **Directory synchronization**ます。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="7b7d6-109">[**ディレクトリ同期**] ウィンドウで、[ **DirSync management に移動] を**選択します。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="7b7d6-110">[ディレクトリ同期の管理] ページの情報</span><span class="sxs-lookup"><span data-stu-id="7b7d6-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="7b7d6-111">次の表に、ページの情報を取得できる機能を示します。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="7b7d6-112">ディレクトリ同期に問題がある場合は、このページにもエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="7b7d6-113">発生する可能性のあるさまざまなエラーの詳細については、「 [Microsoft 365 でのディレクトリ同期エラーの識別](identify-directory-synchronization-errors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="7b7d6-114">**項目**</span><span class="sxs-lookup"><span data-stu-id="7b7d6-114">**Item**</span></span>|<span data-ttu-id="7b7d6-115">**目的**</span><span class="sxs-lookup"><span data-stu-id="7b7d6-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7b7d6-116">**確認されたドメイン**</span><span class="sxs-lookup"><span data-stu-id="7b7d6-116">**Domains verified**</span></span> | <span data-ttu-id="7b7d6-117">自分が所有していることを確認した Microsoft 365 テナント内のドメインの数。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-117">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="7b7d6-118">**確認されていないドメイン**</span><span class="sxs-lookup"><span data-stu-id="7b7d6-118">**Domains not verified**</span></span> | <span data-ttu-id="7b7d6-119">追加されたが確認されていないドメイン。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="7b7d6-120">**ディレクトリ同期の有効化**</span><span class="sxs-lookup"><span data-stu-id="7b7d6-120">**Directory sync enabled**</span></span> |<span data-ttu-id="7b7d6-121">True または False。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-121">True or False.</span></span> <span data-ttu-id="7b7d6-122">ディレクトリ同期を有効にしたかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="7b7d6-123">**最新のディレクトリ同期**</span><span class="sxs-lookup"><span data-stu-id="7b7d6-123">**Latest directory sync**</span></span> | <span data-ttu-id="7b7d6-124">ディレクトリ同期が最後に実行した時刻。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-124">Last time directory sync ran.</span></span> <span data-ttu-id="7b7d6-125">前回の同期が3日以上前の場合は、警告とトラブルシューティングツールへのリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="7b7d6-126">**パスワード同期の有効化**</span><span class="sxs-lookup"><span data-stu-id="7b7d6-126">**Password sync enabled**</span></span> | <span data-ttu-id="7b7d6-127">True または False。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-127">True or False.</span></span> <span data-ttu-id="7b7d6-128">オンプレミスと Microsoft 365 テナント間でパスワードハッシュを同期するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-128">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="7b7d6-129">**前回のパスワード同期**</span><span class="sxs-lookup"><span data-stu-id="7b7d6-129">**Last Password Sync**</span></span> | <span data-ttu-id="7b7d6-130">前回のパスワードハッシュ同期を実行した時刻。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-130">Last time password hash sync ran.</span></span> <span data-ttu-id="7b7d6-131">前回の同期が3日以上前の場合は、警告とトラブルシューティングツールへのリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="7b7d6-132">**ディレクトリ同期クライアントバージョン**</span><span class="sxs-lookup"><span data-stu-id="7b7d6-132">**Directory sync client version**</span></span> | <span data-ttu-id="7b7d6-133">Azure AD Connect の新しいバージョンがリリースされた場合のダウンロードリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="7b7d6-134">**ディレクトリ同期サービスアカウント**</span><span class="sxs-lookup"><span data-stu-id="7b7d6-134">**Directory sync service account**</span></span> | <span data-ttu-id="7b7d6-135">Microsoft 365 ディレクトリ同期サービスアカウントの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="7b7d6-135">Displays the name of your Microsoft 365 directory sync service account.</span></span> |