---
title: Office 365 の接続の監視をする
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Office 365 の展開後は、以下のツールや方法を使用して Office 365 の接続を維持することができます。公式の「サービスの正常性および継続性のガイドライン」と「低速のネットワークで Office 365 を使用するためのベスト プラクティス」を確認しておくようにしてください。また、 Office 365 管理者アプリを入手し、「Office 365 for Business - 管理者ヘルプ」をブックマークしておくことをお勧めします。
ms.openlocfilehash: 385aef73173ea6bab421fae6d10622d7a8fe3c80
ms.sourcegitcommit: 9c39ba0c21fbe86343f825bb589a108ec5f176bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2019
ms.locfileid: "37931695"
---
# <a name="monitor-office-365-connectivity"></a><span data-ttu-id="c32d6-105">Office 365 の接続の監視をする</span><span class="sxs-lookup"><span data-stu-id="c32d6-105">Monitor Office 365 connectivity</span></span>

<span data-ttu-id="c32d6-p102">Office 365 の展開後は、以下で説明するツールや方法を使用して、Office 365 の接続を維持することができます。公式の「[サービスの正常性および継続性のガイドライン](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity)」と「[低速のネットワークで Office 365 を使用するためのベスト プラクティス](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)」を確認しておくようにしてください。また、 [Office 365 管理者アプリ](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)を入手し、「[Office 365 for Business - 管理者ヘルプ](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)」をブックマークしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c32d6-p102">Once you've deployed Office 365, you can maintain Office 365 connectivity using some of the tools and techniques below. You'll want to understand the official [Service Health and Continuity](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) guidelines as well as our [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). You'll also want to grab the [Office 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Office 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-office-365-connectivity"></a><span data-ttu-id="c32d6-109">Office 365 の接続の監視</span><span class="sxs-lookup"><span data-stu-id="c32d6-109">Monitoring Office 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="c32d6-110">**新しい Office 365 エンドポイントについて通知を受信する**</span><span class="sxs-lookup"><span data-stu-id="c32d6-110">**Getting notified of new Office 365 endpoints**</span></span> <br/> |<span data-ttu-id="c32d6-p103">[Office 365 エンドポイントを管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)する場合、新しいエンドポイントが公開されたときに通知を受信できると便利なので、お使いの RSS リーダーを使用して Microsoft の RSS フィードを登録することをお勧めします。「[Outlook 経由で登録](https://go.microsoft.com/fwlink/p/?LinkId=532416)」する手順と、「[RSS フィードの更新をメールで通知](https://go.microsoft.com/fwlink/p/?LinkId=532417)」する手順をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c32d6-p103">If you're [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader. Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span></span><br/> |
|<span data-ttu-id="c32d6-113">**System Center を使って Office 365 を監視する**</span><span class="sxs-lookup"><span data-stu-id="c32d6-113">**Use System Center to Monitor Office 365**</span></span> <br/> |<span data-ttu-id="c32d6-p104">Microsoft System Center を使っている場合、[Office 365 用 System Center 管理パック](https://www.microsoft.com/download/details.aspx?id=43708)をダウンロードして、今すぐ Office 365 の監視を開始できます。 ガイダンスの詳細については、管理パックの操作ガイド、または [System Centre Operations Manager を使った Office 365 の監視](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)に関するブログ投稿を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c32d6-p104">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Office 365 today. For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="c32d6-116">**Azure ExpressRoute の正常性の監視**</span><span class="sxs-lookup"><span data-stu-id="c32d6-116">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="c32d6-117">Azure ExpressRoute for Office 365 を使って Office 365 に接続している場合、Office 365 サービス正常性ダッシュボードと Azure の両方を使用していることを確認することをお勧めします。[Azure リソースの正常性を使ったトラブルシューティング時間の短縮](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span><span class="sxs-lookup"><span data-stu-id="c32d6-117">If you are connecting to Office 365 using Azure ExpressRoute for Office 365, you'll want to ensure that you're using both the Office 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="c32d6-118">**AD FS を使って Azure AD Connect Health を使用する**</span><span class="sxs-lookup"><span data-stu-id="c32d6-118">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="c32d6-119">Office 365 のシングル サインオン用に AD FS を使用している場合、[Azure AD Connect Health を使った AD FS インフラストラクチャの監視](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)を開始することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c32d6-119">If you're using AD FS for Single Sign-On with Office 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="c32d6-120">**プログラムを使って Office 365 を監視する**</span><span class="sxs-lookup"><span data-stu-id="c32d6-120">**Programmatically monitor Office 365**</span></span> <br/> |<span data-ttu-id="c32d6-121">[Office 365 管理 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) に関するマイクロソフトのガイダンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c32d6-121">Refer to our guidance on the [Office 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="c32d6-122">ここに戻る場合は、次のショート リンクをご利用ください: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="c32d6-122">Here's a short link you can use to come back: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c32d6-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c32d6-123">See also</span></span>

[<span data-ttu-id="c32d6-124">Office 365 Enterprise のサービスとアプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="c32d6-124">Configure Office 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="c32d6-125">組織で Office 365 Enterprise を使えるようにする</span><span class="sxs-lookup"><span data-stu-id="c32d6-125">Get your organization ready for Office 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="c32d6-126">Office 365 のネットワーク計画とパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="c32d6-126">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="c32d6-127">Office 365 とオンプレミス環境との統合</span><span class="sxs-lookup"><span data-stu-id="c32d6-127">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="c32d6-128">Office 365 エンドポイントを管理する</span><span class="sxs-lookup"><span data-stu-id="c32d6-128">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
