---
title: Multgeo 環境でのユーザー エクスペリエンス
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: マルチ geo 環境で SharePoint と OneDrive のユーザー エクスペリエンスについて説明します。
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="09430-103">マルチ地域環境でのユーザー エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="09430-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="09430-104">ここでは、OneDrive の複数の地域の構成では、ユーザーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="09430-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="09430-105">業務の場所のユーザーの OneDrive</span><span class="sxs-lookup"><span data-stu-id="09430-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="09430-p101">ユーザーには、希望するデータの場所を提供するビジネス用の OneDrive があります。場合は、正しくない地理的な場所 (以前の地理的な場所からブックマーク) などが含まれている OneDrive の URL にユーザーが移動した、適切な地理的な場所に OneDrive を自動的にリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="09430-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="09430-108">共有</span><span class="sxs-lookup"><span data-stu-id="09430-108">Sharing</span></span>

<span data-ttu-id="09430-p102">ユーザー選択ウィンドウの操作性は、その地域の場所に関係なくすべてのユーザーを示します。これにより、ユーザーは、同じ地域でも、他のテナントの geo の場所の他のユーザーと共有できます。場所、**自分と共有**ビューでのビジネス ユーザーの OneDrive が表示され、アクセスするのには、シングル ・ サインオン環境でホストされている地理的な場所に関係なく、異なる地域からのコンテンツします。</span><span class="sxs-lookup"><span data-stu-id="09430-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="09430-112">Office アプリケーション</span><span class="sxs-lookup"><span data-stu-id="09430-112">Office applications</span></span>

<span data-ttu-id="09430-p103">Word、Excel、PowerPoint などの Office アプリケーションにログインするとき、各ユーザーのビジネスの地理的な場所に適切な OneDrive が自動的に検出します。ユーザーは、OneDrive の地域に固有の URL を入力する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="09430-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="09430-115">同期クライアントのビジネスの OneDrive</span><span class="sxs-lookup"><span data-stu-id="09430-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="09430-116">同期クライアントのビジネスの OneDrive (バージョン 17.3.6943.0625 以降では)、ユーザーの業務地域の場所の正しい OneDrive を自動的に検出されます。</span><span class="sxs-lookup"><span data-stu-id="09430-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="09430-117">Office 365 アプリ起動ツール</span><span class="sxs-lookup"><span data-stu-id="09430-117">Office 365 app launcher</span></span>

<span data-ttu-id="09430-p104">アプリケーション起動プログラムは複数の地域に注意してください、作業負荷の適切な地域の場所には、各タイルを紹介OneDrive では、ユーザーの OneDrive ライブラリをホストしている、SharePoint のタイルのすべてのユーザーを指す中央の場所では、チーム サイトは引き続きホストされているが、中に地域の正しい場所を並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="09430-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="09430-120">ユーザー プロファイルを説明します。</span><span class="sxs-lookup"><span data-stu-id="09430-120">Delve User profiles</span></span>

<span data-ttu-id="09430-p105">ユーザー プロファイル情報はユーザーの地域の場所で習得します。ユーザーを選択すると、表示される、適切な地域の場所に、ユーザーの場所の完全なプロファイルの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="09430-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="09430-123">Delve がオフの場合は、複数地域の対応ではありませんが発生する SharePoint で、従来のプロファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="09430-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="09430-124">Delve</span><span class="sxs-lookup"><span data-stu-id="09430-124">Delve</span></span>

<span data-ttu-id="09430-125">Office 365 ユーザーに対しては衛星の場合に、複数の地域の説明はサポートされて Delve が SharePoint の SharePoint ブログ サイトにのみ、その他の地域のユーザーが作成したブログの投稿にリンクしないこと。</span><span class="sxs-lookup"><span data-stu-id="09430-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="09430-126">検索</span><span class="sxs-lookup"><span data-stu-id="09430-126">Search</span></span>

<span data-ttu-id="09430-p106">各地域の場所では、独自の検索インデックスと検索センターがあります。ユーザーが検索するときに、すべての場所の地域では、クエリが送信されると返される結果がマージされ、ユーザーは統一された結果を取得するために、ランク付けします。ユーザーは、独自の地域の場所に関係なくすべての地域の場所からの結果を取得します。詳細については、 [OneDrive 複数の地域のビジネスを検索する構成](configure-search-for-multi-geo.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09430-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="09430-131">次の検索クライアントがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="09430-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="09430-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="09430-132">OneDrive for Business</span></span>

-   <span data-ttu-id="09430-133">Delve</span><span class="sxs-lookup"><span data-stu-id="09430-133">Delve</span></span>

-   <span data-ttu-id="09430-134">SharePoint ホーム</span><span class="sxs-lookup"><span data-stu-id="09430-134">SharePoint Home</span></span>

-   <span data-ttu-id="09430-135">検索センター</span><span class="sxs-lookup"><span data-stu-id="09430-135">The Search Center</span></span>

-   <span data-ttu-id="09430-136">SharePoint 検索 API を使用するカスタムの検索アプリケーション</span><span class="sxs-lookup"><span data-stu-id="09430-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="09430-137">OneDrive iOS および Android</span><span class="sxs-lookup"><span data-stu-id="09430-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="09430-p107">OneDrive iOS および Android モバイル アプリケーションが表示されます、OneDrive ファイルとファイルを共有する地域の保存場所を問わない。OneDrive のモバイル アプリケーションからの検索には、地域のすべての場所から関連する検索結果が表示されます。これらのアプリケーションの最新バージョンをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="09430-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="09430-141">詳細については、 [iOS の OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)の使用と[アプリの使用 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09430-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="09430-142">チームの経験</span><span class="sxs-lookup"><span data-stu-id="09430-142">Teams Experience</span></span>

<span data-ttu-id="09430-p108">チームは、複数の地域に注意してください。OneDrive ファイルおよび最近表示したファイルは、ユーザーの地域の場所に関係なく表示されます。@ すべての地域の場所からユーザーの作業を参照。</span><span class="sxs-lookup"><span data-stu-id="09430-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
