---
title: Exchange Multi-Geo
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Exchange Online の複数地域機能について説明します。
ms.openlocfilehash: 60d25cab08ada195d1b189b30bdce8ea505f1d19
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931776"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="4b9af-103">Exchange Online の複数地域機能</span><span class="sxs-lookup"><span data-stu-id="4b9af-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="4b9af-104">複数地域環境では、ユーザーごとに Exchange Online メールボックスコンテンツ (rest のデータ) の場所を選択できます。</span><span class="sxs-lookup"><span data-stu-id="4b9af-104">In a multi-geo environment, you can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="4b9af-105">メールボックスは、次の方法でサテライトの場所に配置できます。</span><span class="sxs-lookup"><span data-stu-id="4b9af-105">You can place mailboxes in satellite locations by:</span></span>

- <span data-ttu-id="4b9af-106">サテライトの場所に新しい Exchange Online メールボックスを直接作成する</span><span class="sxs-lookup"><span data-stu-id="4b9af-106">Creating a new Exchange Online mailbox directly in a satellite location</span></span>

- <span data-ttu-id="4b9af-107">ユーザーの優先するデータの場所を変更することにより、既存の Exchange Online メールボックスをサテライトの場所に移動する</span><span class="sxs-lookup"><span data-stu-id="4b9af-107">Moving an existing Exchange Online mailbox to a satellite location by changing the user's preferred data location</span></span>

- <span data-ttu-id="4b9af-108">オンプレミスの Exchange 組織からメールボックスを直接サテライトの場所にオンボードする</span><span class="sxs-lookup"><span data-stu-id="4b9af-108">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="4b9af-109">メールボックスの配置と移動</span><span class="sxs-lookup"><span data-stu-id="4b9af-109">Mailbox placement and moves</span></span>
<span data-ttu-id="4b9af-110">Microsoft が前提条件となる複数地域構成手順を完了すると、Exchange Online は Azure AD のユーザーオブジェクトに対して**PreferredDataLocation**属性を優先します。</span><span class="sxs-lookup"><span data-stu-id="4b9af-110">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="4b9af-111">exchange online は、 **PreferredDataLocation**プロパティを Azure AD から exchange online ディレクトリサービスの**MailboxRegion**プロパティに同期します。</span><span class="sxs-lookup"><span data-stu-id="4b9af-111">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service.</span></span> <span data-ttu-id="4b9af-112">**MailboxRegion**の値は、ユーザーのメールボックスと、関連付けられたアーカイブメールボックスが配置される地域を決定します。</span><span class="sxs-lookup"><span data-stu-id="4b9af-112">The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed.</span></span> <span data-ttu-id="4b9af-113">ユーザーのプライマリメールボックスとアーカイブメールボックスを異なる地域の場所に配置するように構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="4b9af-113">It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations.</span></span> <span data-ttu-id="4b9af-114">ユーザーオブジェクトごとに構成できる geo の場所は1つだけです。</span><span class="sxs-lookup"><span data-stu-id="4b9af-114">Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="4b9af-115">既存のメールボックスを持つユーザーに対して**PreferredDataLocation**が構成されている場合、メールボックスは再配置キューに入れられ、指定した地域の場所に自動的に移動されます。</span><span class="sxs-lookup"><span data-stu-id="4b9af-115">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="4b9af-116">既存のメールボックスがないユーザーに対して**PreferredDataLocation**が構成されている場合、メールボックスのプロビジョニング時に、指定された地理的位置にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="4b9af-116">When **PreferredDataLocation** is configured on a user without an existing mailbox, when you provision the mailbox, it will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="4b9af-117">**PreferredDataLocation**がユーザーに対して指定されていない場合、メールボックスを準備すると、そのメールボックスは中央の場所にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="4b9af-117">When **PreferredDataLocation** is not specified on a user, when you provision the mailbox, it will be provisioned in the central location.</span></span>

- <span data-ttu-id="4b9af-118">**PreferredDataLocation**のコードが正しくない場合 (たとえば、タイプが NAN ではなく NAN)、メールボックスは中央の場所にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="4b9af-118">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be provisioned in the central location.</span></span>

<span data-ttu-id="4b9af-119">**注**: 複数地域機能と Skype for business Online 地域的 hosted 会議の両方で、ユーザーオブジェクトの**PreferredDataLocation**プロパティを使用してサービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="4b9af-119">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services.</span></span> <span data-ttu-id="4b9af-120">地域的でホストされている会議のユーザーオブジェクトに対して**PreferredDataLocation**値を構成すると、そのユーザーのメールボックスは、Office 365 テナントで複数地域を有効にした後、指定した地域の場所に自動的に移動されます。</span><span class="sxs-lookup"><span data-stu-id="4b9af-120">If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="4b9af-121">Exchange Online の複数地域における機能上の制限</span><span class="sxs-lookup"><span data-stu-id="4b9af-121">Feature limitations for multi-geo in Exchange Online</span></span>

1. <span data-ttu-id="4b9af-122">Exchange 管理センター (EAC) で使用可能なセキュリティおよびコンプライアンス機能 (監査、電子情報開示など) は、複数地域の組織では使用できません。</span><span class="sxs-lookup"><span data-stu-id="4b9af-122">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations.</span></span> <span data-ttu-id="4b9af-123">代わりに、 [Office 365 security & コンプライアンスセンター](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)を使用して、セキュリティとコンプライアンスの機能を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b9af-123">Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

2. <span data-ttu-id="4b9af-124">Outlook for Mac のユーザーは、自分のメールボックスを新しい地域の場所に移動している間、オンラインアーカイブフォルダーへのアクセスが一時的に失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4b9af-124">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location.</span></span> <span data-ttu-id="4b9af-125">この条件は、ユーザーのプライマリメールボックスとアーカイブメールボックスが異なる地域の場所にある場合に発生します。これは、異なる地域間メールボックスの移動が異なる時間に完了する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="4b9af-125">This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-geo mailbox moves may complete at different times.</span></span>

3. <span data-ttu-id="4b9af-126">ユーザーが*メールボックスフォルダー*を web 上の outlook (旧称 outlook web App または OWA) の地理的な場所の間で共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="4b9af-126">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA).</span></span> <span data-ttu-id="4b9af-127">たとえば、欧州連合のユーザーは、Outlook on the web を使用して、米国にあるメールボックス内の共有フォルダーを開くことができません。</span><span class="sxs-lookup"><span data-stu-id="4b9af-127">For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States.</span></span> <span data-ttu-id="4b9af-128">ただし、Web 上の outlook では、「[別のユーザーのメールボックスを outlook Web App の別のブラウザーウィンドウで開く](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)」の説明に従って、別の geo で*他のメールボックス*を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="4b9af-128">However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="4b9af-129">**注**: 地域間メールボックスフォルダーの共有は、Outlook on Windows でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4b9af-129">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

