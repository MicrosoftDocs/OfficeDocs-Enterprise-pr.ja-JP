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
# <a name="monitor-microsoft-365-connectivity"></a>Microsoft 365 の接続を監視する

Microsoft 365 を展開した後は、次に示すツールと方法を使用して、Microsoft 365 の接続を維持できます。 この記事では、サービスの[正常性と継続性](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity)に関するオフィシャルガイドライン、および[低速ネットワーク上で Microsoft 365 を使用するためのベストプラクティス](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)について説明します。 また、 [microsoft 365 admin アプリ](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)を入手して、 [microsoft 365 For Business-管理者向けヘルプ](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)にブックマークを追加することもできます。
  
## <a name="monitoring-microsoft-365-connectivity"></a>Microsoft 365 接続の監視

|||
|:-----|:-----|
|**新しい Microsoft 365 エンドポイントの通知を取得する** <br/> |[Microsoft 365 エンドポイントを管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)している場合は、新しいエンドポイントを公開したときに通知を受信する必要があります。お気に入りの rss リーダーを使用して、rss フィードを購読することができます。 [Outlook を使用](https://go.microsoft.com/fwlink/p/?LinkId=532416)して購読する方法、または[RSS フィードの更新をメール](https://go.microsoft.com/fwlink/p/?LinkId=532417)で受信する方法を説明します。  <br/> |
|**System Center を使用して Microsoft 365 を監視する** <br/> |Microsoft System Center を使用している場合は、 [Office 365 用の System Center 管理パック](https://www.microsoft.com/download/details.aspx?id=43708)をダウンロードして、microsoft 365 の監視を開始することができます。 詳細については、「 [System Centre Operations Manager を使用して 365](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)の管理パック操作ガイドまたはこのブログを投稿する」を参照してください。 <br/> |
|**Azure ExpressRoute の正常性の監視** <br/> |Microsoft 365 に microsoft 365 用の Azure ExpressRoute を使用して接続している場合は、microsoft 365 Service 正常性ダッシュボードと azure[リソース正常性によるトラブルシューティング時間](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)の両方を使用していることを確認する必要があります。 <br/> |
|**AD FS を使って Azure AD Connect Health を使用する** <br/> |Microsoft 365 でシングルサインオン用に AD FS を使用している場合は、 [AZURE Ad Connect Health を使用して AD fs インフラストラクチャを監視](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)することをお勧めします。  <br/> |
|**Microsoft 365 をプログラムで監視する** <br/> |[Microsoft 365 MANAGEMENT API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)のガイダンスを参照してください。  <br/> |

ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="related-topics"></a>関連トピック

[Microsoft 365 Enterprise サービスおよびアプリケーションを構成する](configure-services-and-applications.md)
  
[Microsoft 365 Enterprise の準備が整っている組織を取得する](get-your-organization-ready-for-office-365.md)
  
[Microsoft 365 のネットワーク計画とパフォーマンス チューニング](network-planning-and-performance.md)
  
[Microsoft 365 とオンプレミス環境との統合](office-365-integration.md)
  
[Microsoft 365 エンドポイントの管理](managing-office-365-endpoints.md)
