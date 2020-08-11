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
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: この記事では、Office 365 でディレクトリ同期の状態を確認する方法について説明します。
ms.openlocfilehash: 9aaad085854326ebb6542f03256ae851b27f0980
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605863"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="157a4-103">Microsoft 365 でのディレクトリ同期状態の表示</span><span class="sxs-lookup"><span data-stu-id="157a4-103">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="157a4-104">オンプレミス環境を Microsoft 365 と同期させることによって、オンプレミスの Active Directory を Azure AD と統合した場合は、同期の状態を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="157a4-104">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="157a4-105">ディレクトリ同期の状態を表示する</span><span class="sxs-lookup"><span data-stu-id="157a4-105">View directory synchronization status</span></span>

- <span data-ttu-id="157a4-106">[Microsoft 365 管理センター](https://admin.microsoft.com)にサインインし、ホームページの [ **DirSync Status** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="157a4-106">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="157a4-107">または、[アクティブなユーザー] ページ**に移動**し、[ \> **Active users\*\*\*\*アクティブなユーザー** ] ページで、[ディレクトリ同期の**追加**] を選択し \> **Directory synchronization**ます。</span><span class="sxs-lookup"><span data-stu-id="157a4-107">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="157a4-108">[**ディレクトリ同期**] ウィンドウで、[ **DirSync management に移動] を**選択します。</span><span class="sxs-lookup"><span data-stu-id="157a4-108">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="157a4-109">[ディレクトリ同期の管理] ページの情報</span><span class="sxs-lookup"><span data-stu-id="157a4-109">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="157a4-110">次の表に、ページの情報を取得できる機能を示します。</span><span class="sxs-lookup"><span data-stu-id="157a4-110">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="157a4-111">ディレクトリ同期に問題がある場合は、このページにもエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="157a4-111">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="157a4-112">発生する可能性のあるさまざまなエラーの詳細については、「 [Microsoft 365 でのディレクトリ同期エラーの識別](identify-directory-synchronization-errors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="157a4-112">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="157a4-113">**項目**</span><span class="sxs-lookup"><span data-stu-id="157a4-113">**Item**</span></span>|<span data-ttu-id="157a4-114">**目的**</span><span class="sxs-lookup"><span data-stu-id="157a4-114">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="157a4-115">**確認されたドメイン**</span><span class="sxs-lookup"><span data-stu-id="157a4-115">**Domains verified**</span></span> | <span data-ttu-id="157a4-116">自分が所有していることを確認した Microsoft 365 テナント内のドメインの数。</span><span class="sxs-lookup"><span data-stu-id="157a4-116">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="157a4-117">**確認されていないドメイン**</span><span class="sxs-lookup"><span data-stu-id="157a4-117">**Domains not verified**</span></span> | <span data-ttu-id="157a4-118">追加されたが確認されていないドメイン。</span><span class="sxs-lookup"><span data-stu-id="157a4-118">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="157a4-119">**ディレクトリ同期の有効化**</span><span class="sxs-lookup"><span data-stu-id="157a4-119">**Directory sync enabled**</span></span> |<span data-ttu-id="157a4-120">True または False。</span><span class="sxs-lookup"><span data-stu-id="157a4-120">True or False.</span></span> <span data-ttu-id="157a4-121">ディレクトリ同期を有効にしたかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="157a4-121">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="157a4-122">**最新のディレクトリ同期**</span><span class="sxs-lookup"><span data-stu-id="157a4-122">**Latest directory sync**</span></span> | <span data-ttu-id="157a4-123">ディレクトリ同期が最後に実行した時刻。</span><span class="sxs-lookup"><span data-stu-id="157a4-123">Last time directory sync ran.</span></span> <span data-ttu-id="157a4-124">前回の同期が3日以上前の場合は、警告とトラブルシューティングツールへのリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="157a4-124">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="157a4-125">**パスワード同期の有効化**</span><span class="sxs-lookup"><span data-stu-id="157a4-125">**Password sync enabled**</span></span> | <span data-ttu-id="157a4-126">True または False。</span><span class="sxs-lookup"><span data-stu-id="157a4-126">True or False.</span></span> <span data-ttu-id="157a4-127">オンプレミスと Microsoft 365 テナント間でパスワードハッシュを同期するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="157a4-127">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="157a4-128">**前回のパスワード同期**</span><span class="sxs-lookup"><span data-stu-id="157a4-128">**Last Password Sync**</span></span> | <span data-ttu-id="157a4-129">前回のパスワードハッシュ同期を実行した時刻。</span><span class="sxs-lookup"><span data-stu-id="157a4-129">Last time password hash sync ran.</span></span> <span data-ttu-id="157a4-130">前回の同期が3日以上前の場合は、警告とトラブルシューティングツールへのリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="157a4-130">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="157a4-131">**ディレクトリ同期クライアントバージョン**</span><span class="sxs-lookup"><span data-stu-id="157a4-131">**Directory sync client version**</span></span> | <span data-ttu-id="157a4-132">Azure AD Connect の新しいバージョンがリリースされた場合のダウンロードリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="157a4-132">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="157a4-133">**ディレクトリ同期サービスアカウント**</span><span class="sxs-lookup"><span data-stu-id="157a4-133">**Directory sync service account**</span></span> | <span data-ttu-id="157a4-134">Microsoft 365 ディレクトリ同期サービスアカウントの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="157a4-134">Displays the name of your Microsoft 365 directory sync service account.</span></span> |