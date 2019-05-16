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
ms.openlocfilehash: ce307e01a3d7da4a24a06e58d293b9598c684d8f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070053"
---
# <a name="monitor-office-365-connectivity"></a>Office 365 の接続の監視をする

Office 365 の展開後は、以下で説明するツールや方法を使用して、Office 365 の接続を維持することができます。公式の「[サービスの正常性および継続性のガイドライン](https://technet.microsoft.com/library/office-365-service-health.aspx)」と「[低速のネットワークで Office 365 を使用するためのベスト プラクティス](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)」を確認しておくようにしてください。また、 [Office 365 管理者アプリ](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)を入手し、「[Office 365 for Business - 管理者ヘルプ](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)」をブックマークしておくことをお勧めします。
  
## <a name="monitoring-office-365-connectivity"></a>Office 365 の接続の監視

|||
|:-----|:-----|
|**新しい Office 365 エンドポイントについて通知を受信する** <br/> |[Office 365 エンドポイントを管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)する場合、新しいエンドポイントが公開されたときに通知を受信できると便利なので、お使いの RSS リーダーを使用して Microsoft の RSS フィードを登録することをお勧めします。「[Outlook 経由で登録](https://go.microsoft.com/fwlink/p/?LinkId=532416)」する手順と、「[RSS フィードの更新をメールで通知](https://go.microsoft.com/fwlink/p/?LinkId=532417)」する手順をご覧ください。<br/> |
|**System Center を使って Office 365 を監視する** <br/> |Microsoft System Center を使っている場合、[Office 365 用 System Center 管理パック](https://www.microsoft.com/download/details.aspx?id=43708)をダウンロードして、今すぐ Office 365 の監視を開始できます。 ガイダンスの詳細については、管理パックの操作ガイド、または [System Centre Operations Manager を使った Office 365 の監視](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)に関するブログ投稿を参照してください。 <br/> |
|**Azure ExpressRoute の正常性の監視** <br/> |Azure ExpressRoute for Office 365 を使って Office 365 に接続している場合、Office 365 サービス正常性ダッシュボードと Azure の両方を使用していることを確認することをお勧めします。[Azure リソースの正常性を使ったトラブルシューティング時間の短縮](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**AD FS を使って Azure AD Connect Health を使用する** <br/> |Office 365 のシングル サインオン用に AD FS を使用している場合、[Azure AD Connect Health を使った AD FS インフラストラクチャの監視](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)を開始することをお勧めします。  <br/> |
|**プログラムを使って Office 365 を監視する** <br/> |[Office 365 管理 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) に関するマイクロソフトのガイダンスを参照してください。  <br/> |

ここに戻る場合は、次のショート リンクをご利用ください: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>関連項目

[Office 365 Enterprise のサービスとアプリケーションを構成する](configure-services-and-applications.md)
  
[組織で Office 365 Enterprise を使えるようにする](get-your-organization-ready-for-office-365.md)
  
[Office 365 のネットワーク計画とパフォーマンスのチューニング](network-planning-and-performance.md)
  
[Office 365 とオンプレミス環境との統合](office-365-integration.md)
  
[Office 365 エンドポイントを管理する](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
