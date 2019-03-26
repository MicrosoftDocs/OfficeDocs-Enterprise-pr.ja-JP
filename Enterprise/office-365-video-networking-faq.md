---
title: Office 365 のビデオネットワークについてよく寄せられる質問
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: Office 365 のビデオリポジトリおよびストリーミングサービスを使用すると、組織内のビデオを簡単に保存およびストリーミングすることができます。 Office 365 ビデオについて多くの重要な情報があります。このネットワーク FAQ は、帯域幅の計画、暗号化、およびサービスがコンテンツ配信ネットワーク (cdns) を活用する方法に関してよく寄せられる質問に回答するように設計されています。
ms.openlocfilehash: f11bd8baff7c2527287f6e1249ad4dae1928bdd2
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "30641524"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Office 365 のビデオネットワークについてよく寄せられる質問

Office 365 のビデオリポジトリおよびストリーミングサービスを使用すると、組織内のビデオを簡単に保存およびストリーミングすることができます。 [Office 365 ビデオについて](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)多くの重要な情報があります。このネットワーク FAQ は、帯域幅の計画、暗号化、およびサービスが[コンテンツ配信ネットワーク](content-delivery-networks.md)(cdns) を活用する方法に関してよく寄せられる質問に回答するように設計されています。
  
ビデオをアップロードまたは再生したときに何が起こるかを十分に理解していない場合は、このビデオをまとめたものとして、 [Office 365 のビデオにアップロードしたときにビデオファイル](https://www.youtube.com/watch?v=HXSZ0jYBKlM)がどうなるかを確認してください。
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Office 365 のビデオ帯域幅の要件を教えてください。

Office 365 にアップロードできる[サポートされているビデオ形式](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817)は多数あります。 各ビデオファイルは、再生にさまざまなビデオ品質を持つ標準形式にエンコードされます。 Office 365 video は、アダプティブビットレートのストリーミングを使用して、使用可能なネットワーク帯域幅とビデオプレーヤーのサイズに基づいて、最適なビデオ再生品質を選択します。 これを行うために、player は最初に最小の再生品質を要求します。 その後、サービスは、2秒間のビデオセグメントをビデオプレーヤーに送信します。 プレーヤーは、各セグメントが配信される速度に基づいて、より高いまたは低い再生品質を要求できます。
  
アダプティブビットレートストリーミングでは、ビデオの再生が最小限に抑えられている間、バックグラウンドでこれらすべてが実行されます。 ビデオの再生中に、ビデオプレーヤーでは、視聴者が自動再生の品質を手動で上書きして、特定のビデオ再生品質を選択することができます。
  
ビデオ再生の各品質のネットワーク要件の概要を示すクイックテーブルを次に示します。 ビデオの再生に必要なユーザーあたりの最小帯域幅は802kbps です。
  
|||
|:-----|:-----|
|**再生品質** <br/> |**ネットワークの速度** <br/> |
|288 p  <br/> |802kbps  <br/> |
|360p  <br/> |1.2 Mbps  <br/> |
|576p  <br/> |2.5 Mbps  <br/> |
|プログレッシブ  <br/> |3.8 Mbps  <br/> |

([トップに戻る](office-365-video-networking-faq.md))
  
## <a name="how-do-content-delivery-networks-cdns-help-video-playback"></a>コンテンツ配信ネットワーク (cdns) はどのようにビデオの再生をサポートしますか?

同じ地理的位置にある同じ組織の複数のユーザーが同じビデオをストリーミングしている場合、cdns はその地域に近い場所にこれらのビデオのコピーを保存します。 ビデオが保存されているか、最も近い場所にキャッシュされていると、各ユーザーは、その場所から離れた場所ではなく、最も近い場所からビデオをストリームします。 Office 365 Video は、azure メディアサービスを使用して azure cdns にキャッシュされているものと、期間を管理します。 azure Media Services では、任意の[azure CDN の場所](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/)を使用して、ビデオフラグメントとマニフェストを数日間キャッシュできます。 組織内のユーザーがキャッシュされたビデオを引き続き視聴する場合は、キャッシュに残ります。 何度もビデオにアクセスできない場合、ビデオは最終的にキャッシュから削除されます。 次回、ユーザーがビデオを視聴しようとしたときに、それが最も近い CDN の場所で再びキャッシュされます。
  
ビデオを視聴しようとしているすべてのユーザーは、ビデオの近くにある CDN の利点で、ビデオが近い場所にあることを示しています。 これにより、ビデオの再生速度が向上します。ただし、ビデオを再生するためにネットワーク要件が変更されることはありません。
  
> [!NOTE]
> 容量の制限に達しているなど、状況によっては、3日が経過する前にビデオが削除されることがあります。
  
([トップに戻る](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>再生を高速化するためにビデオをローカルにキャッシュすることはできますか?

はい。 office 365 では、ローカル CDN またはキャッシュプロキシを使用して、アクセスを高速化するためにビデオやその他の Office 365 コンテンツをローカルネットワークに格納することはできません。 ネットワークにローカルキャッシュソリューションを実装する方法はいくつかありますが、最も一般的な方法は、コンテンツをローカルにキャッシュするプロキシソリューションを使用する方法です。 プロキシまたはプライベート cdn によってビデオフラグメントとマニフェストがキャッシュされた後、プロキシまたはプライベート cdn を経由してルーティングされるこれらのファイルへの要求は、インターネット上の場所から引き出されずにローカルキャッシュから取得されます。 このようなソリューションを計画する際には、ネットワーク帯域幅、容量、ビデオ再生の同時実行を考慮します。
  
([トップに戻る](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>ビデオを暗号化してセキュリティで保護する方法

Office 365 Video は、データのセキュリティを確保し、プライベートにすることが重要であることを認識しています。 [Microsoft Trust Center](https://products.office.com/business/office-365-trust-center-welcome)は、コンテンツのプライバシーとセキュリティに対するコミットメントについて説明します。 ビデオの再生では、パフォーマンスを向上させるには速度が重要です。しかし、exchange のセキュリティやプライバシーをスピードアップすることはありません。 スピード、セキュリティ、プライバシーに対応する方法を次に示します。
  
組織内のユーザーが新しいビデオをアップロードすると、そのビデオはトランスコードされ、AES-128 暗号化によって暗号化され、Azure Media Services に格納されます。 これは、送信中と保存中の両方のビデオが暗号化されることを意味します。
  
組織内の誰かが新しいビデオを視聴しようとすると、次の手順に従います。
  
1. ビデオを表示する権限がある場合は、SharePoint Online にお問い合わせください。

2. SharePoint Online は、ファイルのアクセス許可を使用して、ユーザーがビデオを視聴できるかどうかを判断します。

3. 許可されている場合、SharePoint Online は、ビデオプレーヤーに提供するために Azure からトークンを取得します。

4. その後、ビデオプレーヤーは、トークンを使用して Azure の復号化キーを要求します。

5. 復号キーが手元にある場合、ビデオプレーヤーはビデオをストリームできます。

![O365 ビデオの再生](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([トップに戻る](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Office 365 ビデオを再生するための要件

office 365 のビデオサポートされているオペレーティングシステムと web ブラウザーは、 [office 365 のシステム要件](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)である SharePoint Online の要件と同じです。 使用しているオペレーティングシステムと web ブラウザーの構成に応じて、ビデオプレーヤーの特定のニーズが決まります。 [ビデオ再生の要件](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)の詳細については、以下を参照してください。
  
([トップに戻る](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>Office 365 ビデオをご利用いただけません。どこから始めるべきですか?

office 365 ビデオへの接続のトラブルシューティングでは、ネットワーク、ISP、および office 365 の構成に関するトラブルシューティングを行います。 最初に開始する場所は、サービス正常性ダッシュボードです。 これにより、Office 365 のビデオで問題が発生しているかどうかがわかります。 すべてがすばらしいのであれば、次のような追加のリソースを参照してください。
  
- [Office 365 のビデオに必要なネットワークエンドポイント](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)に接続できることを確認してください。

- [Office 365 ネットワークトラブルシューティングガイド](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)を使用して、ネットワーク接続を確認します。

- [低速のネットワークで Office 365 を使用するためのベストプラクティス](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)を参照してください。

- [Office 365 のビデオ構成に関するヘルプを参照して](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)ください。

([トップに戻る](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Office 365 のビデオリソース

Office 365 ビデオを正常に展開して使用するために役立つその他のリソースを以下に示します。
  
[Office 365 のビデオ構成に関するヘルプを参照する](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)
  
[Office 365 ビデオを利用する](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[Office 365 でチャネルを作成および管理するビデオ](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  

  [Office 365 ビデオ ポータルを管理する](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Office 365 のビデオで使用できるビデオ形式](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([トップに戻る](office-365-video-networking-faq.md))
  
ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
