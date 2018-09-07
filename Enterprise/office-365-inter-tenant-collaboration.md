---
title: Office 365 テナント間コラボレーション
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/28/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: テナントおよび組織間での Office 365 の共同作業のしくみについて説明します。
ms.openlocfilehash: 932c837f9dc09dd0469a17ad4e6a05f09966d29c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541577"
---
# <a name="office-365-inter-tenant-collaboration"></a><span data-ttu-id="1368a-103">Office 365 テナント間コラボレーション</span><span class="sxs-lookup"><span data-stu-id="1368a-103">Office 365 inter-tenant collaboration</span></span>

<span data-ttu-id="1368a-p101">この資料では、2 つの Office 365 テナント間での共同作業のいくつかの方法について説明します。Office 365 管理者のものです。</span><span class="sxs-lookup"><span data-stu-id="1368a-p101">This article describes several ways to collaborate between two Office 365 tenants. It is intended for Office 365 Administrators.</span></span>
  
<span data-ttu-id="1368a-p102">想定すると、Office 365 のテナントのビジネスがあるそれぞれ 2 つの組織、Fabrikam と contoso 社では、いくつかのプロジェクトで共同作業します。限られた時間のうちいくつかを実行し、継続的です。方法が Fabrikam と Contoso を有効にするセキュリティで保護された方法で、別の Office 365 テナント間でより効率的に共同作業を行うには、人やチームでしょうか。Azure Active Directory の B2B の共同作業と連携して、office 365 には、いくつかのオプションが用意されています。この資料では、Fabrikam と contoso 社が検討できるいくつかの主要なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1368a-p102">Suppose that two organizations, Fabrikam and Contoso, each have an Office 365 for business tenant and they want to work together on several projects; some of which run for a limited time and some of which are ongoing. How can Fabrikam and Contoso enable their people and teams to collaborate more effectively across their different Office 365 tenants in a secure manner? Office 365, in conjunction with Azure Active Directory B2B collaboration, provides several options. This article describes several key scenarios that Fabrikam and Contoso can consider.</span></span>
  
<span data-ttu-id="1368a-p103">Office 365 のテナントの間の共同作業オプションは、ファイルや予定表の共有、im の会話の中心的な場所を使用して、オーディオとビデオでは、通信およびリソースとアプリケーションへのアクセスをセキュリティで保護します。ソリューションを選択し、詳細については、次の表を使用します。</span><span class="sxs-lookup"><span data-stu-id="1368a-p103">Office 365 inter-tenant collaboration options include using a central location for files and conversations, sharing calendars, using IM, audio/video calls for communication, and securing access to resources and applications. Use the following tables to select solutions and learn more.</span></span>
  
## <a name="exchange-online-collaboration-options"></a><span data-ttu-id="1368a-112">Exchange オンラインの共同作業オプション</span><span class="sxs-lookup"><span data-stu-id="1368a-112">Exchange Online collaboration options</span></span>

|<span data-ttu-id="1368a-113">**共有目標**</span><span class="sxs-lookup"><span data-stu-id="1368a-113">**Sharing goal**</span></span>|<span data-ttu-id="1368a-114">**管理操作**</span><span class="sxs-lookup"><span data-stu-id="1368a-114">**Administrative action**</span></span>|<span data-ttu-id="1368a-115">**操作方法に関する情報**</span><span class="sxs-lookup"><span data-stu-id="1368a-115">**How-to information**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="1368a-116">別の Office 365 組織と予定表を共有する</span><span class="sxs-lookup"><span data-stu-id="1368a-116">Share calendars with another Office 365 organization</span></span>  <br/> |<span data-ttu-id="1368a-117">管理者を設定できますカレンダーへのアクセスのさまざまなレベルでは、Exchange オンライン他のユーザーとスケジュール (空き時間情報) を共有できるようにするのには他の企業との共同作業を可能に</span><span class="sxs-lookup"><span data-stu-id="1368a-117">Administrators can set up different levels of calendar access in Exchange Online to allow businesses to collaborate with other businesses and to let users share the schedules (free/busy information) with others</span></span>  <br/> |[<span data-ttu-id="1368a-118">Exchange Online での共有</span><span class="sxs-lookup"><span data-stu-id="1368a-118">Sharing in Exchange Online</span></span>](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-119">Exchange online 組織との関係</span><span class="sxs-lookup"><span data-stu-id="1368a-119">Organization relationships in Exchange Online</span></span>](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-120">Exchange Online で組織の関係を作成する</span><span class="sxs-lookup"><span data-stu-id="1368a-120">Create an organization relationship in Exchange Online</span></span>](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-121">変更および Exchange online 組織の関係</span><span class="sxs-lookup"><span data-stu-id="1368a-121">Modify and organization relationship in Exchange Online</span></span>](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-122">Exchange Online で、組織の関係を削除します。</span><span class="sxs-lookup"><span data-stu-id="1368a-122">Remove an organization relationship in Exchange Online</span></span>](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-123">外部ユーザーと予定表を共有します。</span><span class="sxs-lookup"><span data-stu-id="1368a-123">Share calendars with external users</span></span>](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|<span data-ttu-id="1368a-124">ユーザーが組織外のユーザーとカレンダーを共有する方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="1368a-124">Control how users share their calendars with people outside your organization</span></span>  <br/> |<span data-ttu-id="1368a-125">管理者は、共有していると許可されているアクセスのレベルを制御するユーザーのメールボックスに共有ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="1368a-125">Administrators apply sharing policies to users mailboxes to control who it can be shared with and the level of access granted</span></span>  <br/> |[<span data-ttu-id="1368a-126">Exchange Online 内のポリシーを共有します。</span><span class="sxs-lookup"><span data-stu-id="1368a-126">Sharing policies in Exchange Online</span></span>](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-127">Exchange Online で共有ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1368a-127">Create a sharing policy in Exchange Online</span></span>](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-128">Exchange Online のメールボックスに共有ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="1368a-128">Apply a sharing policy to mailboxes in Exchange Online</span></span>](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-129">変更、無効化、または Exchange Online で共有ポリシーを削除します。</span><span class="sxs-lookup"><span data-stu-id="1368a-129">Modify, disable, or remove a sharing policy in Exchange Online</span></span>](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|<span data-ttu-id="1368a-130">電子メールをセキュリティで保護されたチャネルを構成し、パートナー組織とのメールの流れを制御します。</span><span class="sxs-lookup"><span data-stu-id="1368a-130">Configure secure email channels and control mail flow with partner organizations</span></span>  <br/> |<span data-ttu-id="1368a-p104">管理者は、取引先組織またはサービス プロバイダーとのやり取りはメールにセキュリティを適用するためのコネクタを作成します。コネクタがドメイン名の制限を許可すると、トランスポート層セキュリティ (TLS) 経由での暗号化を強制するか、IP アドレスの範囲をパートナーにメールを送信からです。</span><span class="sxs-lookup"><span data-stu-id="1368a-p104">Administrators create connectors to apply security to mail exchanges with a partner organization or service provider. The connectors enforce encryption via transport layer security (TLS) as well as allowing restrictions on domain names or IP address ranges your partners send email from.</span></span>  <br/> |[<span data-ttu-id="1368a-133">Exchange Online で電子メール接続をセキュリティで保護するために Office 365 で TLS を使用する方法</span><span class="sxs-lookup"><span data-stu-id="1368a-133">How Exchange Online uses TLS to secure email connections in Office 365</span></span>](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [<span data-ttu-id="1368a-134">Configure mail flow using connectors in Office 365</span><span class="sxs-lookup"><span data-stu-id="1368a-134">Configure mail flow using connectors in Office 365</span></span>](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-135">Exchange Online のリモート ドメイン</span><span class="sxs-lookup"><span data-stu-id="1368a-135">Remote domains in Exchange Online</span></span>](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-136">パートナー組織とセキュリティで保護されたメール フローにコネクタを設定します</span><span class="sxs-lookup"><span data-stu-id="1368a-136">Set up connector for secure mail flow with a partner organization</span></span>](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [<span data-ttu-id="1368a-137">Exchange Online および Office 365 でのメール フローのベスト プラクティス (概要)</span><span class="sxs-lookup"><span data-stu-id="1368a-137">Mail flow best practices for Exchange Online and Office 365 (overview)</span></span>](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a><span data-ttu-id="1368a-138">SharePoint Online およびビジネスの共同作業のオプションの OneDrive</span><span class="sxs-lookup"><span data-stu-id="1368a-138">SharePoint Online and OneDrive for Business collaboration options</span></span>

|<span data-ttu-id="1368a-139">**ゴールの共有**</span><span class="sxs-lookup"><span data-stu-id="1368a-139">**Sharing goals**</span></span>|<span data-ttu-id="1368a-140">**管理操作**</span><span class="sxs-lookup"><span data-stu-id="1368a-140">**Administrative action**</span></span>|<span data-ttu-id="1368a-141">**操作方法に関する情報**</span><span class="sxs-lookup"><span data-stu-id="1368a-141">**How-to information**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="1368a-142">外部ユーザーとサイトとドキュメントを共有します。</span><span class="sxs-lookup"><span data-stu-id="1368a-142">Share sites and documents with external users</span></span>  <br/> |<span data-ttu-id="1368a-143">管理者が、テナントで共有を構成するか、Microsoft アカウントの認証、職場または学校のサイト コレクション レベルのアカウントの認証、またはゲスト アカウント</span><span class="sxs-lookup"><span data-stu-id="1368a-143">Administrators configure sharing at the tenant, or site collection level for Microsoft account authenticated, work or school account authenticated or guest accounts</span></span>  <br/> |<span data-ttu-id="1368a-144">
  [SharePoint Online 環境の外部共有を管理する](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US)</span><span class="sxs-lookup"><span data-stu-id="1368a-144">[Manage external sharing for your SharePoint Online environment](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US)</span></span> <br/> [<span data-ttu-id="1368a-145">制限されたドメインのビジネスのオンラインの SharePoint と OneDrive を Office 365 の共有</span><span class="sxs-lookup"><span data-stu-id="1368a-145">Restricted Domains Sharing in Office 365 SharePoint Online and OneDrive for Business</span></span>](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [<span data-ttu-id="1368a-146">SharePoint Online を使用して、企業間 (B2B) エクストラネット ソリューションとして</span><span class="sxs-lookup"><span data-stu-id="1368a-146">Use SharePoint Online as a business-to-business (B2B) extranet solution</span></span>](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|<span data-ttu-id="1368a-147">進捗管理とエンド ・ ユーザー向けの外部共有を制御します。</span><span class="sxs-lookup"><span data-stu-id="1368a-147">Tracking and controlling external sharing for end users</span></span>  <br/> |<span data-ttu-id="1368a-148">OneDrive ファイルの所有者のビジネスとエンド ・ ユーザーの SharePoint Online のサイトおよびドキュメントの共有を構成し、共有を追跡するための通知を確立</span><span class="sxs-lookup"><span data-stu-id="1368a-148">OneDrive for Business file owners and SharePoint Online end users configure site and document sharing and establish notifications to track sharing</span></span>  <br/> |[<span data-ttu-id="1368a-149">ビジネスの OneDrive の外部で共有するための通知を構成します。</span><span class="sxs-lookup"><span data-stu-id="1368a-149">Configure notifications for external sharing for OneDrive for Business</span></span>](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [<span data-ttu-id="1368a-150">Office 365 で SharePoint のファイルやフォルダーを共有する</span><span class="sxs-lookup"><span data-stu-id="1368a-150">Share SharePoint files or folders in Office 365</span></span>](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a><span data-ttu-id="1368a-151">Skype ビジネス コラボレーションのオプションについて</span><span class="sxs-lookup"><span data-stu-id="1368a-151">Skype for Business collaboration options</span></span>

|<span data-ttu-id="1368a-152">**共有目標**</span><span class="sxs-lookup"><span data-stu-id="1368a-152">**Sharing goal**</span></span>|<span data-ttu-id="1368a-153">**管理操作**</span><span class="sxs-lookup"><span data-stu-id="1368a-153">**Administrative action**</span></span>|<span data-ttu-id="1368a-154">**操作方法に関する情報**</span><span class="sxs-lookup"><span data-stu-id="1368a-154">**How-to information**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="1368a-155">ビジネス オンラインの IM、通話、およびプレゼンスのビジネス ユーザー向けの他の Skype での Skype</span><span class="sxs-lookup"><span data-stu-id="1368a-155">Skype for Business Online - IM, calls, and presence with other Skype for Business users</span></span>  <br/> |<span data-ttu-id="1368a-156">管理者はビジネス オンライン ユーザーが IM、Skype を有効にする、オーディオとビデオ通話、および別の Office 365 テナント内のユーザーとのプレゼンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1368a-156">Administrators can enable their Skype for Business Online users to IM, make audio/video calls, and see presence with users in another Office 365 tenant.</span></span>  <br/> |[<span data-ttu-id="1368a-157">ビジネス ユーザー向けの外部の Skype の連絡先ユーザーを許可します。</span><span class="sxs-lookup"><span data-stu-id="1368a-157">Allow users to contact external Skype for Business users</span></span>](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|<span data-ttu-id="1368a-158">Skype ビジネス オンラインの IM、通話、および Skype (コンシューマー) のユーザーとのプレゼンスの</span><span class="sxs-lookup"><span data-stu-id="1368a-158">Skype for Business Online - IM, calls, and presence with Skype (consumer) users</span></span>  <br/> |<span data-ttu-id="1368a-159">管理者ことができます IM をオンライン ビジネスのユーザーに、Skype を有効にする呼び出しを行い、(コンシューマー) の Skype ユーザーとのプレゼンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1368a-159">Administrators can enable their Skype for Business Online users to IM, make calls, and see presence with Skype (consumer) users.</span></span>  <br/> |[<span data-ttu-id="1368a-160">Skype 連絡先を追加、ビジネス ・ ユーザーの Skype を使用します。</span><span class="sxs-lookup"><span data-stu-id="1368a-160">Let Skype for Business users add Skype contacts</span></span>](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a><span data-ttu-id="1368a-161">Azure AD B2B の共同作業オプション</span><span class="sxs-lookup"><span data-stu-id="1368a-161">Azure AD B2B Collaboration options</span></span>

|<span data-ttu-id="1368a-162">**共有目標**</span><span class="sxs-lookup"><span data-stu-id="1368a-162">**Sharing goal**</span></span>|<span data-ttu-id="1368a-163">**管理操作**</span><span class="sxs-lookup"><span data-stu-id="1368a-163">**Administrative action**</span></span>|<span data-ttu-id="1368a-164">**操作方法に関する情報**</span><span class="sxs-lookup"><span data-stu-id="1368a-164">**How-to information**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="1368a-165">Azure AD B2B コラボレーション ・ コンテンツが組織のディレクトリ内のグループに外部ユーザーを追加することで共有</span><span class="sxs-lookup"><span data-stu-id="1368a-165">Azure AD B2B collaboration - Content sharing by adding external users to a group in an organization's directory</span></span>  <br/> |<span data-ttu-id="1368a-166">グループにこれらの外部ユーザーを追加する Office 365 テナントの 1 つのグローバル管理者は、そのディレクトリに参加する別の Office 365 テナントに人を招待でき、SharePoint サイトとグループのライブラリなどのコンテンツへのアクセスを付与します。</span><span class="sxs-lookup"><span data-stu-id="1368a-166">A global admin for one Office 365 tenant can invite people in another Office 365 tenant to join their directory, add those external users to a group, and grant access to content, such as SharePoint sites and libraries for the group.</span></span>  <br/> |[<span data-ttu-id="1368a-167">Azure AD B2B コラボレーションのプレビューとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="1368a-167">What is Azure AD B2B collaboration preview?</span></span>](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [<span data-ttu-id="1368a-168">Azure AD の B2B: 新しい更新プログラムを作成、企業間のグループ作業を簡単に</span><span class="sxs-lookup"><span data-stu-id="1368a-168">Azure AD B2B: New updates make cross-business collab easy</span></span>](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [<span data-ttu-id="1368a-169">Office 365 の外部の共有と Azure Active Directory B2B コラボレーション</span><span class="sxs-lookup"><span data-stu-id="1368a-169">Office 365 external sharing and Azure Active Directory B2B collaboration</span></span>](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [<span data-ttu-id="1368a-170">Azure Active Directory の B2B コラボレーション API とカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="1368a-170">Azure Active Directory B2B collaboration API and customization</span></span>](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [<span data-ttu-id="1368a-171">Azure AD および識別情報の表示: Azure AD B2B (企業間のコラボレーション</span><span class="sxs-lookup"><span data-stu-id="1368a-171">Azure AD and Identity Show: Azure AD B2B Collaboration (Business to Business</span></span>](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a><span data-ttu-id="1368a-172">Office 365 の共同作業オプション</span><span class="sxs-lookup"><span data-stu-id="1368a-172">Office 365 collaboration options</span></span>

|<span data-ttu-id="1368a-173">**共有目標**</span><span class="sxs-lookup"><span data-stu-id="1368a-173">**Sharing goal**</span></span>|<span data-ttu-id="1368a-174">**管理操作**</span><span class="sxs-lookup"><span data-stu-id="1368a-174">**Administrative action**</span></span>|<span data-ttu-id="1368a-175">**操作方法に関する情報**</span><span class="sxs-lookup"><span data-stu-id="1368a-175">**How-to information**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="1368a-176">Office 365 のグループの電子メール、予定表、OneNote、および中央の場所のファイル共有</span><span class="sxs-lookup"><span data-stu-id="1368a-176">Office 365 Groups - Email, calendar, OneNote, and shared files in a central place</span></span>  <br/> |<span data-ttu-id="1368a-p105">ビジネス プレミアム、ビジネスに関する重要事項、教育、およびエンタープライズ E1、E3、E5 の計画では、グループがサポートされています。1 つの Office 365 テナント内のユーザーは、グループを作成し、ゲスト ユーザーとして、別の Office 365 テナントに人を招待します。Dynamics CRM にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="1368a-p105">Groups are supported in Business Essentials, Business Premium, Education, and the Enterprise E1, E3, and E5 plans. People in one Office 365 tenant can create a group and invite people in another Office 365 tenant as guest users. Applies to Dynamics CRM as well.</span></span>  <br/> |[<span data-ttu-id="1368a-180">Office 365 グループについてください。</span><span class="sxs-lookup"><span data-stu-id="1368a-180">Learn about Office 365 groups</span></span>](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [<span data-ttu-id="1368a-181">Office 365 のグループでのゲスト アクセス</span><span class="sxs-lookup"><span data-stu-id="1368a-181">Guest access in Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [<span data-ttu-id="1368a-182">Office 365 のグループを展開します。</span><span class="sxs-lookup"><span data-stu-id="1368a-182">Deploy Office 365 Groups</span></span>](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a><span data-ttu-id="1368a-183">Yammer の共同作業オプション</span><span class="sxs-lookup"><span data-stu-id="1368a-183">Yammer collaboration options</span></span>

|<span data-ttu-id="1368a-184">**共有目標**</span><span class="sxs-lookup"><span data-stu-id="1368a-184">**Sharing goal**</span></span>|<span data-ttu-id="1368a-185">**管理操作**</span><span class="sxs-lookup"><span data-stu-id="1368a-185">**Administrative action**</span></span>|<span data-ttu-id="1368a-186">**操作方法に関する情報**</span><span class="sxs-lookup"><span data-stu-id="1368a-186">**How-to information**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="1368a-187">Yammer の企業のソーシャル メディアを介しての共同作業</span><span class="sxs-lookup"><span data-stu-id="1368a-187">Yammer - Collaboration through an enterprise social medium</span></span>  <br/> |<span data-ttu-id="1368a-188">Yammer の管理者が外部のグループを作成する機能が無効な場合を除き、ユーザーは、会話をするように次の投稿、ファイルの共有、およびオンライン チャット機能を通じて、Yammer に共同作業を行う外部のグループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1368a-188">Unless the ability to create external groups is disabled by a Yammer admin, users can create external groups to collaborate in Yammer through conversations, the ability to like and follow posts, share files, and chat online.</span></span>  <br/> |[<span data-ttu-id="1368a-189">作成し、Yammer に外部のグループの管理</span><span class="sxs-lookup"><span data-stu-id="1368a-189">Create and manage external groups in Yammer</span></span>](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a><span data-ttu-id="1368a-190">チームの共同作業オプション</span><span class="sxs-lookup"><span data-stu-id="1368a-190">Teams collaboration options</span></span>

|<span data-ttu-id="1368a-191">**共有目標**</span><span class="sxs-lookup"><span data-stu-id="1368a-191">**Sharing goal**</span></span>|<span data-ttu-id="1368a-192">**管理操作**</span><span class="sxs-lookup"><span data-stu-id="1368a-192">**Administrative action**</span></span>|<span data-ttu-id="1368a-193">**操作方法に関する情報**</span><span class="sxs-lookup"><span data-stu-id="1368a-193">**How-to information**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="1368a-194">組織外部のユーザーと、チームで共同作業します。</span><span class="sxs-lookup"><span data-stu-id="1368a-194">Collaborate in Teams with users external to the organization</span></span>  <br/> |<span data-ttu-id="1368a-p106">招待側の Office 365 テナントのグローバル管理者は、チームの外部の共同作業を有効にする必要があります。グローバル管理者とチームの所有者はチームで共同作業するのには電子メール アドレスを持つユーザーを招待することになります。</span><span class="sxs-lookup"><span data-stu-id="1368a-p106">A global admin for the inviting Office 365 tenant needs to enable external collaboration in Teams. Global admins and team owners will now be able to invite anyone with an email address to collaborate in Teams.</span></span>  <br/> <span data-ttu-id="1368a-197">管理者は、管理し、来園者が、テナント内に既に存在を編集することができますもします。</span><span class="sxs-lookup"><span data-stu-id="1368a-197">Admins can also manage and edit Guests already present in their tenant.</span></span>  <br/> |[<span data-ttu-id="1368a-198">ゲスト アクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="1368a-198">Authorize Guest Access</span></span>](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [<span data-ttu-id="1368a-199">チームでゲスト アクセスを有効または無効に</span><span class="sxs-lookup"><span data-stu-id="1368a-199">Turn Guest Access On or Off in Teams</span></span>](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [<span data-ttu-id="1368a-200">PowerShell を使用して、ゲスト アクセスを制御する</span><span class="sxs-lookup"><span data-stu-id="1368a-200">Use PowerShell to control Guest Access</span></span>](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [<span data-ttu-id="1368a-201">ゲスト アクセスのチェックリスト</span><span class="sxs-lookup"><span data-stu-id="1368a-201">Guest Access Checklist</span></span>](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [<span data-ttu-id="1368a-202">ゲスト ユーザーを表示します。</span><span class="sxs-lookup"><span data-stu-id="1368a-202">View Guest Users</span></span>](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [<span data-ttu-id="1368a-203">ゲスト ユーザー情報を編集します。</span><span class="sxs-lookup"><span data-stu-id="1368a-203">Edit guest user information</span></span>](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|<span data-ttu-id="1368a-204">チームの所有者は、招待し、来園者が、チーム内で共同作業する方法を管理できます。</span><span class="sxs-lookup"><span data-stu-id="1368a-204">Team owners can invite and manage how guests collaborate within their teams.</span></span>  <br/> |<span data-ttu-id="1368a-205">チームの所有者には、チーム内で実行できる、来園者にその他のコントロールがあります。</span><span class="sxs-lookup"><span data-stu-id="1368a-205">Team owners have additional controls on what the guests can do within their teams.</span></span>  <br/> |[<span data-ttu-id="1368a-206">来園者を追加します。</span><span class="sxs-lookup"><span data-stu-id="1368a-206">Add Guests</span></span>](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [<span data-ttu-id="1368a-207">チームにゲストを追加します。</span><span class="sxs-lookup"><span data-stu-id="1368a-207">Add a guest to a team</span></span>](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [<span data-ttu-id="1368a-208">チームでのゲスト アクセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="1368a-208">Manage Guest Access in Teams</span></span>](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [<span data-ttu-id="1368a-209">チームまたはチャネルでは、ユーザーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1368a-209">See who's on a Team or in a Channel</span></span>](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|<span data-ttu-id="1368a-210">他のテナントには、来園者はチームの内容を表示でき、他のメンバーとの共同作業</span><span class="sxs-lookup"><span data-stu-id="1368a-210">Guests from other tenants can view contents in Teams and collaborate with other members</span></span>  <br/> |<span data-ttu-id="1368a-211">なし。</span><span class="sxs-lookup"><span data-stu-id="1368a-211">None.</span></span>  <br/> |[<span data-ttu-id="1368a-212">ゲスト アクセスの操作性</span><span class="sxs-lookup"><span data-stu-id="1368a-212">The guest access experience</span></span>](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |
   
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a><span data-ttu-id="1368a-213">Office 365 のテナントの間の共同作業についての注意点</span><span class="sxs-lookup"><span data-stu-id="1368a-213">Points to be aware of about Office 365 inter-tenant collaboration</span></span>

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a><span data-ttu-id="1368a-214">ユーザー アカウント、ライセンス、サブスクリプション、およびストレージの共有</span><span class="sxs-lookup"><span data-stu-id="1368a-214">Sharing of user accounts, licenses, subscriptions, and storage</span></span>

<span data-ttu-id="1368a-p107">各組織は、独自のユーザー アカウント、ユーザー、セキュリティ グループ、サブスクリプション、ライセンス、および記憶域を管理します。人は、会社の資産の制御を維持しながら必要な情報へのアクセスを提供するのに共有ポリシーおよびセキュリティの設定と Office 365 での共同作業機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="1368a-p107">Each organization maintains its own user accounts, identities, security groups, subscriptions, licenses, and storage. People use the collaboration features in Office 365 together with sharing policies and security settings to provide access to needed information while maintaining control of company assets.</span></span>
  
- <span data-ttu-id="1368a-217">**ユーザー アカウント:** アカウントを共有することはできませんし、テナントまたはオンプレミスの Active Directory ディレクトリ サービス内のパーティション間でアカウントを複製することはできません。</span><span class="sxs-lookup"><span data-stu-id="1368a-217">**User accounts:** Accounts cannot be shared and accounts cannot be duplicated between the tenants or partitions in the on-premises Active Directory Directory Services.</span></span> 
    
- <span data-ttu-id="1368a-218">**ライセンス&amp;のサブスクリプション:**、Office 365 では、計画のライセンスからライセンス (も呼び出された Sku または Office 365 プラン) ユーザーにそれらの計画に定義されている Office 365 サービスへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="1368a-218">**Licenses &amp; subscriptions:** In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans.</span></span> 
    
- <span data-ttu-id="1368a-p108">**ストレージ:** Office 365 のプランでソフトウェアの境界と SharePoint Online の制限とは切り離して管理メールボックス格納域の制限です。メールボックス格納域の制限を設定し、Exchange Online を使用して管理します。両方のシナリオでは、テナント間のストレージを共有できません。</span><span class="sxs-lookup"><span data-stu-id="1368a-p108">**Storage:** In Office 365 plans, software boundaries and limits for SharePoint Online are managed separately from mailbox storage limits. Mailbox storage limits are set up and managed by using Exchange Online. In both scenarios storage can't be shared cross tenants.</span></span> 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a><span data-ttu-id="1368a-222">Office 365 のテナント間でのドメインの名前空間をご</span><span class="sxs-lookup"><span data-stu-id="1368a-222">Can we share domain namespaces across Office 365 tenants?</span></span>

<span data-ttu-id="1368a-p109">違います。Fabrikam.com、tailspintoys.com などの修飾のドメインのみ関連付けられているし、使用できる 1 つのテナントに。各テナントが独自の名前空間にいる必要があります。UPN、SMTP、および SIP 名前空間は、テナントの間で共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="1368a-p109">No. Vanity domains, such as fabrikam.com or tailspintoys.com, can only be associated and used with one tenant at the time. Each tenant must have its own namespace; UPN, SMTP and SIP namespaces cannot be shared across tenants.</span></span>
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a><span data-ttu-id="1368a-226">ハイブリッド コンポーネントと Office 365 のテナントの間の共同作業について説明します。</span><span class="sxs-lookup"><span data-stu-id="1368a-226">What about hybrid components and Office 365 inter-tenant collaboration?</span></span>

<span data-ttu-id="1368a-227">など、Exchange 組織と Azure の AD 接続、設置型ハイブリッド コンポーネントは、複数のテナントの間で分割できません。</span><span class="sxs-lookup"><span data-stu-id="1368a-227">On-premises hybrid components, such as an Exchange organization and Azure AD Connect, cannot be split across multiple tenants.</span></span>
  
