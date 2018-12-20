---
title: Office 365 のセッションのタイムアウト
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
description: Securtiy と Office 365 クライアント アプリケーションでのアクセスの容易さのバランスをとるには、セッションのタイムアウトが使用されます。
ms.openlocfilehash: 4ef50b876fd97e2de2449d324464b466243a6691
ms.sourcegitcommit: fd7a56f38ba2c2d2e7fcd6e165ec58b31be299d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "27378493"
---
# <a name="session-timeouts-for-office-365"></a><span data-ttu-id="2c045-103">Office 365 のセッションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="2c045-103">Session timeouts for Office 365</span></span>

<span data-ttu-id="2c045-104">セッションの有効期間は、Office 365 の認証の重要な部分であり、セキュリティと資格情報のユーザーが表示されたら回数のバランスの重要なコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="2c045-104">Session lifetimes are an important part of authentication for Office 365 and are an important component in balancing security and the number of times users are prompted for their credentials.</span></span>
  
## <a name="session-times-for-office-365-services"></a><span data-ttu-id="2c045-105">Office 365 サービスのセッション時間</span><span class="sxs-lookup"><span data-stu-id="2c045-105">Session times for Office 365 services</span></span>

<span data-ttu-id="2c045-p101">ユーザーは、Office 365 の web アプリケーションやモバイル アプリケーションのいずれかで認証、セッションが確立されます。セッションが終了するまで、ユーザーは再認証する必要はありません。セッションは、ブラウザーやタブを閉じるとき、またはなど、パスワードをリセットすると、他の理由により、認証トークンの有効期限が切れると、ユーザーがアクティブになっている場合に期限が切れることができます。Office 365 サービスでは、各サービスの一般的な使用に対応する別のセッションのタイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="2c045-p101">When users authenticate in any of the Office 365 web apps or mobile apps, a session is established. For the duration of the session, users won't need to re-authenticate. Sessions can expire when users are inactive, when they close the browser or tab, or when their authentication token expires for other reasons such as when their password has been reset. The Office 365 services have different session timeouts to correspond with the typical use of each service.</span></span>
  
<span data-ttu-id="2c045-110">次の表に、Office 365 サービスのセッションの有効期間を示します。</span><span class="sxs-lookup"><span data-stu-id="2c045-110">The following table lists the session lifetimes for Office 365 services:</span></span>
  
|<span data-ttu-id="2c045-111">**Office 365 サービス**</span><span class="sxs-lookup"><span data-stu-id="2c045-111">**Office 365 service**</span></span>|<span data-ttu-id="2c045-112">**セッションのタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="2c045-112">**Session timeout**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2c045-113">Office 365 管理センター</span><span class="sxs-lookup"><span data-stu-id="2c045-113">Office 365 Admin center</span></span>  <br/> |<span data-ttu-id="2c045-114">8 時間ごとに管理センターの資格情報を提供するように求められます。</span><span class="sxs-lookup"><span data-stu-id="2c045-114">You are asked to provide credentials for the admin center every 8 hours.</span></span>  <br/> |
|<span data-ttu-id="2c045-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2c045-115">SharePoint Online</span></span>  <br/> |<span data-ttu-id="2c045-p102">5 日間のアクティブでない限り、ユーザーは、**サインインを維持**するかを選択します。ユーザーがアクセスする SharePoint Online 再度前のサインインから 24 以上の時間が経過した後、タイムアウト値は 5 日にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="2c045-p102">5 days of inactivity as long as the users chooses **Keep me signed in**. If the user accesses SharePoint Online again after 24 or more hours have passed from the previous sign-in, the timeout value is reset to 5 days.  </span></span><br/> |
|<span data-ttu-id="2c045-118">Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="2c045-118">Outlook Web App</span></span>  <br/> |<span data-ttu-id="2c045-119">6 時間です。</span><span class="sxs-lookup"><span data-stu-id="2c045-119">6 hours.</span></span>  <br/> <span data-ttu-id="2c045-120">[セット OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378)コマンドレットの_ActivityBasedAuthenticationTimeoutInterval_パラメーターを使用して、この値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="2c045-120">You can change this value by using the  _ActivityBasedAuthenticationTimeoutInterval_ parameter in the [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet.</span></span>  <br/> |
|<span data-ttu-id="2c045-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="2c045-121">Azure Active Directory</span></span>  <br/> <span data-ttu-id="2c045-122">(現代の認証が有効になっているとは、Office 2013 の Windows クライアントで使用)</span><span class="sxs-lookup"><span data-stu-id="2c045-122">(Used by Office 2013 Windows clients with modern authentication enabled)</span></span>  <br/> | <span data-ttu-id="2c045-p103">現代の認証では、アクセス ・ トークンとトークンの更新を使用して、Azure Active Directory を使用して Office 365 リソースへのユーザー アクセスを許可します。アクセス トークンは JSON Web トークン認証に成功した後、有効な 1 時間です。更新トークンの有効期間が長くなりますがも用意されています。アクセス トークンが期限切れに、Office クライアントは新しいアクセス トークンを取得するのには有効な更新トークンを使用します。ユーザーの最初の認証が有効の場合、この交換が成功します。</span><span class="sxs-lookup"><span data-stu-id="2c045-p103">Modern authentication uses access tokens and refresh tokens to grant user access to Office 365 resources using Azure Active Directory. An access token is a JSON Web Token provided after a successful authentication and is valid for 1 hour. A refresh token with a longer lifetime is also provided. When access tokens expire, Office clients use a valid refresh token to obtain a new access token. This exchange succeeds if the user's initial authentication is still valid.</span></span>  <br/>  <span data-ttu-id="2c045-128">リフレッシュ トークンは 90 日間、有効期間は、継続的な使用は、失効するまで有効なことができます。</span><span class="sxs-lookup"><span data-stu-id="2c045-128">Refresh tokens are valid for 90 days, and with continuous use, they can be valid until revoked.</span></span>  <br/>  <span data-ttu-id="2c045-129">更新トークンは、次のようにいくつかのイベントによって無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2c045-129">Refresh tokens can be invalidated by several events such as :</span></span>  <br/>  <span data-ttu-id="2c045-130">リフレッシュ トークンが発行されてから、ユーザーのパスワードが変更されました。</span><span class="sxs-lookup"><span data-stu-id="2c045-130">User's password has changed since the refresh token was issued.</span></span>  <br/>  <span data-ttu-id="2c045-131">管理者は、ユーザーがアクセスしようとしてリソースへのアクセスを制限する条件付きのアクセス ポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="2c045-131">An administrator can apply conditional access policies which restrict access to the resource the user is trying to access.</span></span>  <br/> |
|<span data-ttu-id="2c045-132">Android、iOS、および Windows の 10 のモバイル アプリケーションを SharePoint と OneDrive</span><span class="sxs-lookup"><span data-stu-id="2c045-132">SharePoint and OneDrive mobile apps for Android, iOS, and Windows 10</span></span>  <br/> |<span data-ttu-id="2c045-p104">アクセス トークンの既定の有効期間は、1 時間です。更新トークンの既定の最大使用頻度の低い時間は、90 日間です。</span><span class="sxs-lookup"><span data-stu-id="2c045-p104">The default lifetime for the access token is 1 hour. The default max inactive time of the refresh token is 90 days.  </span></span><br/> [<span data-ttu-id="2c045-135">トークンおよびトークンの有効期間を構成する方法の詳細についてください。</span><span class="sxs-lookup"><span data-stu-id="2c045-135">Learn more about tokens and how to configure token lifetimes</span></span>](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> <span data-ttu-id="2c045-136">更新を取り消すにはトークンがパスワードをリセットするユーザーの Office 365</span><span class="sxs-lookup"><span data-stu-id="2c045-136">To revoke the refresh token, you can reset the user's Office 365 password</span></span>  <br/> |
|<span data-ttu-id="2c045-137">Yammer を Office 365 にサインイン</span><span class="sxs-lookup"><span data-stu-id="2c045-137">Yammer with Office 365 Sign-In</span></span>  <br/> |<span data-ttu-id="2c045-p105">ブラウザーの有効期間。ユーザーがブラウザーを閉じるし、Yammer に新しいブラウザーでアクセス、Yammer を再認証に Office 365 にします。ユーザーは、サード ・ パーティ製のブラウザーをキャッシュ cookie を使用している場合、ブラウザーを再度開き、ときに再認証する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c045-p105">Lifetime of the browser. If users close the browser and access Yammer in a new browser, Yammer will re-authenticate them with Office 365. If users use third-party browsers that cache cookies, they may not need to re-authenticate when they reopen the browser.  </span></span><br/> <span data-ttu-id="2c045-141">> [!NOTE]> これは、Yammer の Office 365 にサインインを使用してネットワークでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="2c045-141">> [!NOTE]> This is valid only for networks using Office 365 Sign-In for Yammer.</span></span>           |
   

