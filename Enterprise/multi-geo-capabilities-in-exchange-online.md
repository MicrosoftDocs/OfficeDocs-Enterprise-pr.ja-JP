---
title: Exchange Multi-Geo
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Exchange Online の Multi-Geo 機能について説明します。
ms.openlocfilehash: d518121c69ee29ee246c6947e361a74a3933310f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069933"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="1bc4a-103">Exchange Online の Multi-Geo 機能</span><span class="sxs-lookup"><span data-stu-id="1bc4a-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="1bc4a-104">Multi-Geo の環境では、Exchange Online メールボックスのコンテンツ (保管中のデータ) の場所をユーザー別に選択できます。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-104">In a multi-geo environment, you can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="1bc4a-105">次の方法でメールボックスをサテライトの地理的位置に配置できます。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-105">You can place mailboxes in satellite geo locations by:</span></span>

- <span data-ttu-id="1bc4a-106">サテライトの地理的位置に新しい Exchange Online メールボックスを直接作成します。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-106">Creating a new Exchange Online mailbox directly in a satellite geo location.</span></span>

- <span data-ttu-id="1bc4a-107">ユーザーが希望するデータの場所を変更することで、既存の Exchange Online メールボックスをサテライトの地理的位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-107">Moving an existing Exchange Online mailbox to a satellite geo location by changing the user's preferred data location.</span></span>

- <span data-ttu-id="1bc4a-108">メールボックスをオンプレミスの Exchange 組織から、サテライトの地理的位置に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-108">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite geo location.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="1bc4a-109">メールボックスの配置と移動</span><span class="sxs-lookup"><span data-stu-id="1bc4a-109">Mailbox placement and moves</span></span>

<span data-ttu-id="1bc4a-110">Microsoft が事前に必要な複数地域の構成手順を完了すると、Exchange Online は Azure AD のユーザーオブジェクトで **PreferredDataLocation** 属性を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-110">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="1bc4a-111">Exchange online は、\*\* PreferredDataLocation\*\* プロパティを、Azure AD から Exchange online ディレクトリサービスの\*\* MailboxRegion\*\* プロパティに同期します。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-111">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service.</span></span> <span data-ttu-id="1bc4a-112">**MailboxRegion**の値は、ユーザーのメールボックスと、関連付けられている アーカイブ メールボックス が配置されている地理的位置を決定します。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-112">The value of **MailboxRegion** determines the geo location where user mailboxes and any associated archive mailboxes will be placed.</span></span> <span data-ttu-id="1bc4a-113">別の地理的位置に存在するユーザーの プライマリ メールボックス と アーカイブ メールボックス を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-113">It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations.</span></span> <span data-ttu-id="1bc4a-114">ユーザーオブジェクトごとに構成できる地理的位置は1つだけです。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-114">Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="1bc4a-115">ユーザーの既存のメールボックスを使用して **PreferredDataLocation** を構成した場合、メールボックスは再配置キューに入れられ、指定された地理的位置に自動的に移動されます。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-115">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span>

- <span data-ttu-id="1bc4a-116">既存のメールボックスを持たないユーザーに\*\* PreferredDataLocation\*\* を構成したてメールボックスをプロビジョンする場合、そのメールボックスは指定された地理的位置にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-116">When **PreferredDataLocation** is configured on a user without an existing mailbox, when you provision the mailbox, it will be provisioned into the specified geo location.</span></span>

- <span data-ttu-id="1bc4a-117">**PreferredDataLocation**がユーザーに指定されていない場合、メールボックスは中央の地理的位置にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-117">When **PreferredDataLocation** is not specified on a user, when you provision the mailbox, it will be provisioned in the central geo location.</span></span>

- <span data-ttu-id="1bc4a-118">**PreferredDataLocation**コードが誤っている場合 (たとえば、NAMでなくNANと入力した場合)、メールボックスは中央の 地理的位置にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-118">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be provisioned in the central geo location.</span></span>

<span data-ttu-id="1bc4a-119">**注**: 複数地域の機能と Skype for Business Online が地域的にホストする会議のいずれの場合も、ユーザーオブジェクトの **PreferredDataLocation** プロパティがサービスを見つけます。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-119">**Note**: Multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services.</span></span> <span data-ttu-id="1bc4a-120">地域的に管理されている会議用のユーザーオブジェクトに\*\* PreferredDataLocation\*\* の値を構成すると、そのユーザーのメールボックスは、Office 365 テナントで複数地域が有効になった後、指定した地理的位置に自動的に移動します。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-120">If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="1bc4a-121">Exchange Online における複数地域の機能に関する制限</span><span class="sxs-lookup"><span data-stu-id="1bc4a-121">Feature limitations for multi-geo in Exchange Online</span></span>

- <span data-ttu-id="1bc4a-122">Exchange 管理センター (EAC) で利用できるセキュリティ機能およびコンプライアンス機能（たとえば、監査や電子情報開示）は、複数地域の組織では利用できません。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-122">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations.</span></span> <span data-ttu-id="1bc4a-123">セキュリティとコンプライアンスの機能を構成するには、[Office 365 セキュリティ/コンプライアンス センター](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-123">Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

- <span data-ttu-id="1bc4a-124">Outlook for Mac を使用している場合は、メールボックスを新しい地理的位置に移動する際、オンラインアーカイブ フォルダーに一時的にアクセスできなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-124">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location.</span></span> <span data-ttu-id="1bc4a-125">この状態は、ユーザーのプライマリメールボックスとアーカイブメールボックスが異なる地理的位置にある場合に発生します。これは、複数地域のメールボックスの移動が異なる時刻に完了する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-125">This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-geo mailbox moves may complete at different times.</span></span>

- <span data-ttu-id="1bc4a-126">ユーザーは、Outlook on the web (旧 Outlook web App または OWA) の地理的位置を跨いで*メールボックスフォルダー*を共有できません。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-126">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA).</span></span> <span data-ttu-id="1bc4a-127">たとえば、欧州連合のユーザーが Outlook on the web を使用して、米国にあるメールボックス内の共有フォルダーを開くことはできません。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-127">For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States.</span></span> <span data-ttu-id="1bc4a-128">ただし、Outlook on the web では、 *「Outlook Web App の別のブラウザーウィンドウで他のユーザーのメールボックスを開く」* の説明に従って、別のブラウザーウィンドウを使って異なる地理的位置にある[他のメールボックス](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-128">However, Outlook on the Web users can open *other mailboxes* in different geo locations by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

  <span data-ttu-id="1bc4a-129">**注**: 地域間のメールボックスフォルダーの共有は、Outlook on the Windows でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-129">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

- <span data-ttu-id="1bc4a-130">複数地域にある組織では、パブリックフォルダーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-130">Public folders are supported in multi-geo organizations.</span></span> <span data-ttu-id="1bc4a-131">ただし、パブリックフォルダーは中央の地理的位置に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-131">However, the public folders must remain in the central geo location.</span></span> <span data-ttu-id="1bc4a-132">パブリックフォルダーをサテライトの地理的位置に移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="1bc4a-132">You can't move public folders to satellite geo locations.</span></span>
