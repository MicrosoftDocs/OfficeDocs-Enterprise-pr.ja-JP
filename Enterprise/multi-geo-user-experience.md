---
title: 複数地域環境でのユーザー エクスペリエンス
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 複数地域環境での SharePoint および OneDrive のユーザー エクスペリエンスについて説明します。
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="ec7e3-103">複数地域環境でのユーザー エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="ec7e3-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="ec7e3-104">ここでは、OneDrive 複数地域構成でユーザーが確認できる内容について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="ec7e3-105">ユーザーの OneDrive for Business の場所</span><span class="sxs-lookup"><span data-stu-id="ec7e3-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="ec7e3-p101">ユーザーには、そのユーザーの優先されるデータの場所にプロビジョニングされた OneDrive for Business が提供されます。ユーザーが不適切な地域の場所を含む OneDrive URL に移動すると (以前の地域の場所からのブックマークなど)、適切な地域の場所にある OneDrive に自動的にリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="ec7e3-108">共有</span><span class="sxs-lookup"><span data-stu-id="ec7e3-108">Sharing</span></span>

<span data-ttu-id="ec7e3-p102">ユーザー選択ウィンドウのエクスペリエンスでは、ユーザーの地域の場所に関係なく、すべてのユーザーが示されます。これにより、ユーザーは同じ地域またはテナントの地域の場所が異なる他のユーザーとの共有が可能になります。別の地域の場所からのコンテンツは、ユーザーの OneDrive for Business の **[共有相手]** ビューに表示され、そのコンテンツがホストされている地域の場所に関係なく、シングルサインオン エクスペリエンスに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="ec7e3-112">Office アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ec7e3-112">Office applications</span></span>

<span data-ttu-id="ec7e3-p103">Office アプリケーション (Word、Excel、PowerPoint など) は、ユーザーがログインしたときに、ユーザーごとの適切な OneDrive for Business の地域の場所を自動的に検出します。ユーザーは、自分の OneDrive の地域固有の URL を入力する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="ec7e3-115">OneDrive for Business 同期クライアント</span><span class="sxs-lookup"><span data-stu-id="ec7e3-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="ec7e3-116">OneDrive for Business 同期クライアント (バージョン 17.3.6943.0625 以降) は、ユーザーにとって適切な OneDrive for Business の地域の場所を自動的に検出します。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="ec7e3-117">Office 365 アプリ起動ツール</span><span class="sxs-lookup"><span data-stu-id="ec7e3-117">Office 365 app launcher</span></span>

<span data-ttu-id="ec7e3-p104">アプリ起動ツールは、複数地域に対応していて、各タイルをワークロードの適切な地域の場所に差し向けます。OneDrive タイルは、ユーザーの OneDrive ライブラリがホストされている適切な地域の場所をポイントします。その一方で、SharePoint タイルは、すべてのユーザーを中央の場所に差し向けます (チーム サイトは引き続き中央の場所でホストされるため)。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="ec7e3-120">Delve のユーザー プロファイル</span><span class="sxs-lookup"><span data-stu-id="ec7e3-120">Delve User profiles</span></span>

<span data-ttu-id="ec7e3-p105">ユーザー プロファイル情報は、ユーザーの地域の場所でマスター管理されます。ユーザーを選択すると、そのユーザーにとって適切な地域の場所に転送され、完全なプロファイルの詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="ec7e3-123">Delve がオフの場合、SharePoint の従来の (複数地域に対応していない) プロファイル エクスペリエンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="ec7e3-124">Delve</span><span class="sxs-lookup"><span data-stu-id="ec7e3-124">Delve</span></span>

<span data-ttu-id="ec7e3-125">サテライトのインスタンスに存在する Office 365 ユーザーの場合は、Delve 複数地域がサポートされますが、別の地域に存在するユーザーの記述した SharePoint ブログ投稿へのリンクが Delve に示されないという制限があります。そのユーザーの SharePoint ブログ サイトへのリンクのみが示されます。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="ec7e3-126">検索</span><span class="sxs-lookup"><span data-stu-id="ec7e3-126">Search</span></span>

<span data-ttu-id="ec7e3-p106">各地域の場所には、独自の検索インデックスと検索センターがあります。ユーザーが検索を実行すると、クエリはすべての地域の場所に送信されます。返される結果はマージされてからランク付けされるため、ユーザーには統一された結果が示されます。ユーザーは、自分の地域の場所に関係なく、すべての地域の場所からの結果を取得します。詳細については、「[OneDrive for Business 複数地域の検索の構成](configure-search-for-multi-geo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="ec7e3-131">サポートされている検索クライアントは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="ec7e3-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="ec7e3-132">OneDrive for Business</span></span>

-   <span data-ttu-id="ec7e3-133">Delve</span><span class="sxs-lookup"><span data-stu-id="ec7e3-133">Delve</span></span>

-   <span data-ttu-id="ec7e3-134">SharePoint Home</span><span class="sxs-lookup"><span data-stu-id="ec7e3-134">SharePoint Home</span></span>

-   <span data-ttu-id="ec7e3-135">検索センター</span><span class="sxs-lookup"><span data-stu-id="ec7e3-135">The Search Center</span></span>

-   <span data-ttu-id="ec7e3-136">SharePoint 検索 API を使用するカスタムの検索アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ec7e3-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="ec7e3-137">OneDrive iOS および Android</span><span class="sxs-lookup"><span data-stu-id="ec7e3-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="ec7e3-p107">OneDrive iOS および Android モバイル アプリには、ユーザーの OneDrive ファイルと、ユーザーの地域の場所と関係なくユーザーが共有しているファイルが表示されます。OneDrive モバイル アプリからの検索では、すべての地域の場所から関連する結果が表示されます。これらのアプリの最新バージョンをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="ec7e3-141">詳細については、「[iOS で OneDrive を使う](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)」および「[Android で OneDrive を使う](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="ec7e3-142">Teams のエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="ec7e3-142">Teams Experience</span></span>

<span data-ttu-id="ec7e3-p108">Teams は、複数地域に対応しています。OneDrive ファイルとユーザーの地域の場所と関係なく最近表示したファイルが表示されます。@ は、すべての地域の場所からのユーザーと作業することを示します。</span><span class="sxs-lookup"><span data-stu-id="ec7e3-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
