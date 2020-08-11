---
title: Microsoft 365 の接続を監視する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: この記事では、Microsoft 365 の接続を監視および管理するために使用できるツールと手法について説明します。
ms.openlocfilehash: 791352910cf82bf4d43543166cb4b1e974f9a238
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606863"
---
# <a name="monitor-microsoft-365-connectivity"></a><span data-ttu-id="d9917-103">Microsoft 365 の接続を監視する</span><span class="sxs-lookup"><span data-stu-id="d9917-103">Monitor Microsoft 365 connectivity</span></span>

<span data-ttu-id="d9917-104">Microsoft 365 を展開した後は、次に示すツールと方法を使用して、Microsoft 365 の接続を維持できます。</span><span class="sxs-lookup"><span data-stu-id="d9917-104">Once you've deployed Microsoft 365, you can maintain Microsoft 365 connectivity using some of the tools and techniques below.</span></span> <span data-ttu-id="d9917-105">この記事では、サービスの[正常性と継続性](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity)に関するオフィシャルガイドライン、および[低速ネットワーク上で Microsoft 365 を使用するためのベストプラクティス](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9917-105">You'll want to understand the official [Service Health and Continuity](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) guidelines as well as our [Best practices for using Microsoft 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166).</span></span> <span data-ttu-id="d9917-106">また、 [microsoft 365 admin アプリ](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)を入手して、 [microsoft 365 For Business-管理者向けヘルプ](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)にブックマークを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="d9917-106">You'll also want to grab the [Microsoft 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Microsoft 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-microsoft-365-connectivity"></a><span data-ttu-id="d9917-107">Microsoft 365 接続の監視</span><span class="sxs-lookup"><span data-stu-id="d9917-107">Monitoring Microsoft 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="d9917-108">**新しい Microsoft 365 エンドポイントの通知を取得する**</span><span class="sxs-lookup"><span data-stu-id="d9917-108">**Getting notified of new Microsoft 365 endpoints**</span></span> <br/> |<span data-ttu-id="d9917-109">[Microsoft 365 エンドポイントを管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)している場合は、新しいエンドポイントを公開したときに通知を受信する必要があります。お気に入りの rss リーダーを使用して、rss フィードを購読することができます。</span><span class="sxs-lookup"><span data-stu-id="d9917-109">If you're [Managing Microsoft 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader.</span></span> <span data-ttu-id="d9917-110">[Outlook を使用](https://go.microsoft.com/fwlink/p/?LinkId=532416)して購読する方法、または[RSS フィードの更新をメール](https://go.microsoft.com/fwlink/p/?LinkId=532417)で受信する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d9917-110">Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>  <br/> |
|<span data-ttu-id="d9917-111">**System Center を使用して Microsoft 365 を監視する**</span><span class="sxs-lookup"><span data-stu-id="d9917-111">**Use System Center to Monitor Microsoft 365**</span></span> <br/> |<span data-ttu-id="d9917-112">Microsoft System Center を使用している場合は、 [Office 365 用の System Center 管理パック](https://www.microsoft.com/download/details.aspx?id=43708)をダウンロードして、microsoft 365 の監視を開始することができます。</span><span class="sxs-lookup"><span data-stu-id="d9917-112">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Microsoft 365 today.</span></span> <span data-ttu-id="d9917-113">詳細については、「 [System Centre Operations Manager を使用して 365](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)の管理パック操作ガイドまたはこのブログを投稿する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9917-113">For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="d9917-114">**Azure ExpressRoute の正常性の監視**</span><span class="sxs-lookup"><span data-stu-id="d9917-114">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="d9917-115">Microsoft 365 に microsoft 365 用の Azure ExpressRoute を使用して接続している場合は、microsoft 365 Service 正常性ダッシュボードと azure[リソース正常性によるトラブルシューティング時間](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)の両方を使用していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9917-115">If you are connecting to Microsoft 365 using Azure ExpressRoute for Microsoft 365, you'll want to ensure that you're using both the Microsoft 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="d9917-116">**AD FS を使って Azure AD Connect Health を使用する**</span><span class="sxs-lookup"><span data-stu-id="d9917-116">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="d9917-117">Microsoft 365 でシングルサインオン用に AD FS を使用している場合は、 [AZURE Ad Connect Health を使用して AD fs インフラストラクチャを監視](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d9917-117">If you're using AD FS for Single Sign-On with Microsoft 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="d9917-118">**Microsoft 365 をプログラムで監視する**</span><span class="sxs-lookup"><span data-stu-id="d9917-118">**Programmatically monitor Microsoft 365**</span></span> <br/> |<span data-ttu-id="d9917-119">[Microsoft 365 MANAGEMENT API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)のガイダンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9917-119">Refer to our guidance on the [Microsoft 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="d9917-120">ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="d9917-120">Here's a short link you can use to come back: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="d9917-121">関連トピック</span><span class="sxs-lookup"><span data-stu-id="d9917-121">Related topics</span></span>

[<span data-ttu-id="d9917-122">Microsoft 365 Enterprise サービスおよびアプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="d9917-122">Configure Microsoft 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="d9917-123">Microsoft 365 Enterprise の準備が整っている組織を取得する</span><span class="sxs-lookup"><span data-stu-id="d9917-123">Get your organization ready for Microsoft 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="d9917-124">Microsoft 365 のネットワーク計画とパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="d9917-124">Network planning and performance tuning for Microsoft 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="d9917-125">Microsoft 365 とオンプレミス環境との統合</span><span class="sxs-lookup"><span data-stu-id="d9917-125">Microsoft 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="d9917-126">Microsoft 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="d9917-126">Managing Microsoft 365 endpoints</span></span>](managing-office-365-endpoints.md)
