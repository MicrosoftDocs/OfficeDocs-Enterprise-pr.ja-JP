---
title: Office 365 での管理アクセス制御
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- NOCSH
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: '概要: Office 365 の管理アクセス制御とデータ分類の概要について説明します。'
ms.openlocfilehash: f902b123b26f2c71cb6597f66fc47142e2f2b44c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844538"
---
# <a name="administrative-access-controls-in-office-365"></a><span data-ttu-id="3c0b1-103">Office 365 での管理アクセス制御</span><span class="sxs-lookup"><span data-stu-id="3c0b1-103">Administrative Access Controls in Office 365</span></span> 

<span data-ttu-id="3c0b1-104">Microsoft は、Microsoft によってお客様のコンテンツへのアクセスを意図的に制限する一方で、ほとんどの Office 365 操作を自動化するシステムと管理に多大な投資を行ってきました。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-104">Microsoft has invested heavily in systems and controls that automate most Office 365 operations while intentionally limiting access to customer content by Microsoft.</span></span> <span data-ttu-id="3c0b1-105">人間がサービスを制御し、ソフトウェアがサービスを運用します。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-105">Humans govern the service, and software operates the service.</span></span> <span data-ttu-id="3c0b1-106">これにより、Microsoft は Office 365 をスケールで管理し、お客様のコンテンツに対する内部の脅威のリスクを管理することができます。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-106">This enables Microsoft to manage Office 365 at scale and manage the risks of internal threats to customer content.</span></span>

<span data-ttu-id="3c0b1-107">既定では、Microsoft のエンジニアには継続的な管理者権限も、Office 365 の顧客コンテンツへのアクセス権もありません。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-107">By default, Microsoft engineers have zero standing administrative privileges and zero standing access to customer content in Office 365.</span></span> <span data-ttu-id="3c0b1-108">Microsoft のエンジニアは、限られた期間、お客様のコンテンツへのアクセスを制限、監査、およびセキュリティで保護することができます。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-108">A Microsoft engineer can have limited, audited, and secured access to a customer's content for a limited amount of time.</span></span> <span data-ttu-id="3c0b1-109">アクセスは、サービス操作に必要な場合と、Microsoft シニアマネージメントのメンバーによって承認された場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-109">Access is only when necessary for service operations and only when approved by a member of Microsoft senior management.</span></span> <span data-ttu-id="3c0b1-110">お客様がライセンスを供与されたお客様の場合、お客様は Office 365 でホストされているコンテンツへのアクセスを承認します。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-110">For Customer Lockbox licensed customers, the customer provides access approval to their content hosted on Office 365.</span></span>

<span data-ttu-id="3c0b1-111">Microsoft では、複数の形式のクラウド配信を使用したオンラインサービスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-111">Microsoft provides online services using multiple forms of cloud delivery:</span></span>

- <span data-ttu-id="3c0b1-112">**パブリッククラウド:** Office 365、Azure、および北アメリカ、南米、ヨーロッパ、アジア、オーストラリアなどでホストされているその他のサービスのマルチテナントバージョンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-112">**Public Clouds:** Includes multi-tenant versions of Office 365, Azure, and other services hosted in North America, South America, Europe, Asia, Australia, etc.</span></span>
- <span data-ttu-id="3c0b1-113">**国立雲:** 米国外のすべての独立およびサードパーティ製のクラウド (前述のものを除く) (中国で運用されている 365)、ドイツの office 365 (Microsoft が運用している、ドイツのデータを含むモデルの下で、ドイツのデータが含まれるお客様のデータとシステムに対する Microsoft のアクセスを制御し、監視します)。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-113">**National Clouds:** Includes all sovereign and third party-operated clouds outside of the United States (except ones noted previously), such as Office 365 in China (operated by 21Vianet), and Office 365 in Germany (operated by Microsoft, but under a model in which a German data trustee, Deutsche Telekom, controls and monitors Microsoft's access to Customer Data and systems that contain Customer Data).</span></span>
- <span data-ttu-id="3c0b1-114">**行政機関向けクラウド:** 米国政府機関のお客様が利用できる Office 365 および Azure サービスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-114">**Government Clouds:** Includes Office 365 and Azure services that are available to United States government customers.</span></span>

<span data-ttu-id="3c0b1-115">この記事の目的として、Office 365 サービスには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-115">For purposes of this article, Office 365 services include:</span></span>

- [<span data-ttu-id="3c0b1-116">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3c0b1-116">Exchange Online</span></span>](https://docs.microsoft.com/Exchange/exchange-online)
- [<span data-ttu-id="3c0b1-117">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="3c0b1-117">Exchange Online Protection</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [<span data-ttu-id="3c0b1-118">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3c0b1-118">SharePoint Online</span></span>](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [<span data-ttu-id="3c0b1-119">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="3c0b1-119">OneDrive for Business</span></span>](https://docs.microsoft.com/OneDrive/onedrive)
- [<span data-ttu-id="3c0b1-120">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="3c0b1-120">Skype for Business</span></span>](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [<span data-ttu-id="3c0b1-121">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3c0b1-121">Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [<span data-ttu-id="3c0b1-122">Yammer</span><span class="sxs-lookup"><span data-stu-id="3c0b1-122">Yammer</span></span>](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a><span data-ttu-id="3c0b1-123">Office 365 のアクセス制御</span><span class="sxs-lookup"><span data-stu-id="3c0b1-123">Office 365 Access Controls</span></span>

<span data-ttu-id="3c0b1-124">アクセス制御を目的として、Microsoft では Office 365 データを顧客データまたはその他の種類のデータとして分類しています。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-124">For access control purposes, Microsoft categorizes Office 365 data as Customer data or other types of data.</span></span>

### <a name="customer-data"></a><span data-ttu-id="3c0b1-125">顧客データ</span><span class="sxs-lookup"><span data-stu-id="3c0b1-125">Customer data</span></span>

<span data-ttu-id="3c0b1-126">顧客データとは、Office 365 サービスを使用している場合に、お客様によって提供される、または代理となるデータのことです。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-126">Customer data is all data provided by or on behalf of a customer when using Office 365 services.</span></span> <span data-ttu-id="3c0b1-127">これは、次のような Office 365 ユーザーによって直接作成またはアップロードされるお客様向けコンテンツです。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-127">This is customer content directly created or uploaded by Office 365 users, including:</span></span>

- <span data-ttu-id="3c0b1-128">メール</span><span class="sxs-lookup"><span data-stu-id="3c0b1-128">Emails</span></span>
- <span data-ttu-id="3c0b1-129">SharePoint Online のコンテンツ</span><span class="sxs-lookup"><span data-stu-id="3c0b1-129">SharePoint Online content</span></span>
- <span data-ttu-id="3c0b1-130">インスタントメッセージ</span><span class="sxs-lookup"><span data-stu-id="3c0b1-130">Instant messages</span></span>
- <span data-ttu-id="3c0b1-131">予定表アイテム</span><span class="sxs-lookup"><span data-stu-id="3c0b1-131">Calendar items</span></span>
- <span data-ttu-id="3c0b1-132">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="3c0b1-132">Documents</span></span>
- <span data-ttu-id="3c0b1-133">連絡先</span><span class="sxs-lookup"><span data-stu-id="3c0b1-133">Contacts</span></span>
- <span data-ttu-id="3c0b1-134">エンドユーザー識別情報 (EUII) (ユーザーに固有のデータ、または個別のユーザーに linkable されていても、顧客コンテンツは含まれません)。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-134">End-user identifiable information (EUII) (data that is unique to a user or that is linkable to an individual user but does not include customer content).</span></span>

### <a name="other-types-of-data"></a><span data-ttu-id="3c0b1-135">その他の種類のデータ</span><span class="sxs-lookup"><span data-stu-id="3c0b1-135">Other types of data</span></span>

<span data-ttu-id="3c0b1-136">その他の種類のデータは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-136">Other types of data include:</span></span>

- <span data-ttu-id="3c0b1-137">**アカウントデータ:** 管理データ (管理者がサインアップまたはサービスを購入するときに提供される情報) と支払いデータ (クレジットカードの詳細などの支払い手段に関する情報) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-137">**Account data:** Includes administrative data (information provided by administrators when they sign-up or purchase services), and payment data (information about payment instruments, such as credit card details).</span></span>
- <span data-ttu-id="3c0b1-138">**組織的に識別できる情報:** テナントを識別するために使用されるデータ、使用状況データ、個々のユーザーに linkable していないこと、または顧客コンテンツに含まれているデータを含みます。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-138">**Organizationally identifiable information:** Includes data used to identify a tenant, usage data, and not linkable to an individual user or included in customer content.</span></span>
- <span data-ttu-id="3c0b1-139">**システムのメタデータ:** 構成設定、システム状態、Microsoft IP アドレス、およびサブスクリプションとテナントに関する技術情報を含むサービスログが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-139">**System metadata:** Includes service logs that contain configuration settings, system status, Microsoft IP addresses, and technical information about subscriptions and tenants.</span></span>

<span data-ttu-id="3c0b1-140">Microsoft は、お客様のデータまたはアクセスコントロールのデータへのアクセスが許可されていないことを確認するためのアクセス制御メカニズムを確立しています。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-140">Microsoft has established access control mechanisms to ensure that no one has unapproved access to Customer Data or access control data.</span></span> <span data-ttu-id="3c0b1-141">Access control データは、お客様のコンテンツや EUII、Microsoft のパスワード、セキュリティ証明書、およびその他の認証関連データへのアクセスを含む、環境内の他の種類のデータまたは機能へのアクセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-141">Access control data manages access to other types of data or functions within the environment, including access to customer content or EUII, Microsoft passwords, security certificates, and other authentication-related data.</span></span> <span data-ttu-id="3c0b1-142">アクセス制御メカニズムは、Office 365 運用環境への許可されていない物理、論理、またはリモートアクセスに対する保護も行います。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-142">Access control mechanisms also guard against unapproved physical, logical, or remote access to the Office 365 production environment.</span></span>

<span data-ttu-id="3c0b1-143">Microsoft では、次の3つのカテゴリのアクセス制御を Office 365 用に使用しています。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-143">There are three categories of access controls used by Microsoft for operating Office 365:</span></span>

- <span data-ttu-id="3c0b1-144">分離コントロール</span><span class="sxs-lookup"><span data-stu-id="3c0b1-144">Isolation Controls</span></span>
- <span data-ttu-id="3c0b1-145">人事管理</span><span class="sxs-lookup"><span data-stu-id="3c0b1-145">Personnel Controls</span></span>
- <span data-ttu-id="3c0b1-146">テクノロジコントロール</span><span class="sxs-lookup"><span data-stu-id="3c0b1-146">Technology Controls</span></span>

<span data-ttu-id="3c0b1-147">これらのコントロールを組み合わせると、Office 365 の悪意のあるアクションを防ぎ、検出することができます。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-147">When combined, these controls help prevent and detect malicious actions in Office 365.</span></span> <span data-ttu-id="3c0b1-148">Microsoft によって使用される分離、人物、およびテクノロジの各コントロールに加えて、ユーザーによって実装されるコントロールには、次の4つのカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-148">In addition to the isolation, personnel, and technology controls used by Microsoft, there is a fourth category of controls: those implemented by customers.</span></span>

<span data-ttu-id="3c0b1-149">Office 365 では、オンプレミス環境でのデータ管理と同じ方法でデータを管理できます。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-149">Office 365 allows you to manage data the same way data is managed in on-premises environments.</span></span> <span data-ttu-id="3c0b1-150">Office 365 の組織をサインアップするユーザーは、自動的にグローバル管理者になります。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-150">The person who signs up an organization for Office 365 automatically becomes a global administrator.</span></span> <span data-ttu-id="3c0b1-151">グローバル管理者は、管理ポータルのすべての機能にアクセスでき、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-151">The global admin has access to all features in Management Portals and can:</span></span>

- <span data-ttu-id="3c0b1-152">ユーザーを作成または編集する</span><span class="sxs-lookup"><span data-stu-id="3c0b1-152">Create or edit users</span></span>
- <span data-ttu-id="3c0b1-153">他のユーザーに管理者ロールを割り当てる</span><span class="sxs-lookup"><span data-stu-id="3c0b1-153">Assign admin roles to others</span></span>
- <span data-ttu-id="3c0b1-154">ユーザーのパスワードをリセットする</span><span class="sxs-lookup"><span data-stu-id="3c0b1-154">Reset user passwords</span></span>
- <span data-ttu-id="3c0b1-155">ユーザーライセンスを管理する</span><span class="sxs-lookup"><span data-stu-id="3c0b1-155">Manage user licenses</span></span>
- <span data-ttu-id="3c0b1-156">ドメインの管理</span><span class="sxs-lookup"><span data-stu-id="3c0b1-156">Manage domains</span></span>
- <span data-ttu-id="3c0b1-157">顧客のロックボックス要求を承認する</span><span class="sxs-lookup"><span data-stu-id="3c0b1-157">Approve Customer Lockbox requests</span></span>

<span data-ttu-id="3c0b1-158">各組織で少なくとも2人の管理者アカウントを構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-158">We recommend that each organization configure at least two admin accounts.</span></span> <span data-ttu-id="3c0b1-159">大規模な企業組織の場合、さまざまな機能を提供する特別な管理者アカウントをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-159">For large enterprise organizations, we recommend specialized admin accounts that serve different functions.</span></span>

<span data-ttu-id="3c0b1-160">管理者の役割とアクセス許可の割り当てについては、「 [office 365 での管理者ロールの割り当て](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504)」および「 [office 365 管理者ロールについ](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c0b1-160">For information about assigning admin roles and permissions, see [Assigning admin roles in Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) and [About Office 365 admin roles](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).</span></span>

## <a name="related-links"></a><span data-ttu-id="3c0b1-161">関連リンク</span><span class="sxs-lookup"><span data-stu-id="3c0b1-161">Related Links</span></span>

- [<span data-ttu-id="3c0b1-162">分離コントロール</span><span class="sxs-lookup"><span data-stu-id="3c0b1-162">Isolation Controls</span></span>](office-365-isolation-controls.md)
- [<span data-ttu-id="3c0b1-163">人事管理</span><span class="sxs-lookup"><span data-stu-id="3c0b1-163">Personnel Controls</span></span>](office-365-personnel-controls.md)
- [<span data-ttu-id="3c0b1-164">テクノロジコントロール</span><span class="sxs-lookup"><span data-stu-id="3c0b1-164">Technology Controls</span></span>](office-365-technology-controls.md)
- [<span data-ttu-id="3c0b1-165">アクセス制御の監視と監査</span><span class="sxs-lookup"><span data-stu-id="3c0b1-165">Monitoring and Auditing Access Controls</span></span>](office-365-monitoring-and-auditing-access-controls.md)
- [<span data-ttu-id="3c0b1-166">Yammer Enterprise でのアクセス制御</span><span class="sxs-lookup"><span data-stu-id="3c0b1-166">Yammer Enterprise Access Controls</span></span>](office-365-yammer-enterprise-access-controls.md)