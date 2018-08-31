---
title: Office 365 のビデオ ネットワークのよく寄せられる質問
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2016
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
description: Office 365 のビデオのリポジトリとサービスをストリーミングを使用する保存して、組織内のビデオのストリーミング簡単です。Office 365 ビデオに関する情報が多いネットワークこのよく寄せられる質問は、帯域幅の計画、暗号化、およびサービスがコンテンツ配信ネットワーク (Cdn) を活用する方法を最も一般的な質問に回答するよう設計されています。
ms.openlocfilehash: bea9838277b5752e4c9905162c0e8525e8aded04
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541583"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Office 365 のビデオ ネットワークのよく寄せられる質問

Office 365 のビデオのリポジトリとサービスをストリーミングを使用する保存して、組織内のビデオのストリーミング簡単です。多くの便利な[Office 365 のビデオについての情報](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)です。ネットワークこのよく寄せられる質問は、帯域幅の計画、暗号化、およびサービスが[コンテンツ配信ネットワーク (Cdn)](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)を活用する方法を最も一般的な質問に回答するよう設計されています。
  
既にビデオがアップロードされたときの動作の理解や再生、このビデオを見てについてまとめてみました、[ビデオ ファイルを Office 365 のビデオをアップロードするときに動作](https://www.youtube.com/watch?v=HXSZ0jYBKlM)します。
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Office 365 のビデオ帯域幅の要件は?

さまざまな[ビデオ形式がサポートされている](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817)Office 365 にアップロードできます。各ビデオ ファイルは、再生するためのいくつかのさまざまなビデオ品質の標準の形式にエンコードされます。Office 365 のビデオでは、アダプティブ ・ ビットレートが利用可能なネットワーク帯域幅とビデオ プレーヤーのサイズに基づいて、高品質なビデオ再生を選択するのにはストリーミングを使用します。これを行うには、プレーヤーは最初に最下位の再生品質を要求します。サービスは、ビデオ プレーヤーに 2 秒のビデオのセグメントの送信を開始します。プレイヤーは、各セグメントの配信速度に基づいて上位または下位の再生品質を要求します。
  
アダプティブ ・ ビットレートのストリームはすべてバック グラウンドでビデオが最小限の中断またはバッファーの再生中にします。ビデオの再生中は、ビデオ プレーヤーは、特定のビデオの再生品質を選択するのには、自動再生の品質を手動でオーバーライドするビューアーを使用できます。
  
ここでは、各ビデオの再生品質のネットワーク要件をまとめたクイック テーブルです。1 人のビデオを再生するために必要な最小の帯域幅は、802 Kbps です。
  
|||
|:-----|:-----|
|**再生品質** <br/> |**ネットワーク速度** <br/> |
|288 p  <br/> |802 kbps  <br/> |
|360 p  <br/> |1.2 Mbps  <br/> |
|576 p  <br/> |2.5 Mbps  <br/> |
|720 p  <br/> |3.8 Mbps  <br/> |

([先頭に戻る](office-365-video-networking-faq.md))
  
## <a name="how-do-cdns-help-video-playback"></a>Cdn がビデオの再生に役立つでしょうか。

同じ地理的な場所にある同じ組織で複数の人には、同じビデオをストリーミングは、Cdn は、その地域に近い場所にこれらのビデオのコピーが格納されます。ビデオと格納されている、または最も近い場所にあるキャッシュされた各ユーザー、離れた場所をさらにではなくそれらに最も近い場所からのビデオにストリームします。Office 365 のビデオは、どのようなキャッシュで Azure Cdn、および時間を管理するために、Azure のメディア サービスを使用します。Azure のメディア サービスは、ビデオの断片と、数日の目録をキャッシュするのには、 [Azure CDN の場所](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/)のいずれかを使用できます。組織内のユーザーがキャッシュされているビデオを見ながら引き続きキャッシュのままになります。数日、ビデオのビデオが最終的にはない 1 つのアクセスの場合は、ドロップがキャッシュから削除されます。次回のビデオを見るときにもう一度キャッシュに最も近い CDN の場所です。
  
すべてのコンテンツの中にビデオを視聴しようとする人が、近くにある CDN のメリットが近づき、ビデオからホップ離れたところ、以下のほとんどの場合にキャッシュされます。これがビデオの再生速度を向上します。ただし、ビデオを再生するネットワークの要件は変更されません。
  
> [!NOTE]
> 容量制限に達したことを 3 日に達した前にビデオを削除することがありますなど、いくつかの状況があります。
  
([先頭に戻る](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>ローカル再生が高速にビデオをキャッシュできますか。

うん。Office 365 もできないローカルの CDN やキャッシュ プロキシを使用して高速アクセスのためのローカル ネットワーク内にビデオ、またはその他の Office 365 のコンテンツを表示します。ネットワーク上のローカル ・ キャッシュ ・ ソリューションを実装するためにいくつかの方法がある、最も一般的な方法は、コンテンツをローカルにキャッシュするプロキシ ソリューションを使用します。プロキシまたはプライベートの CDN は、ビデオの断片とマニフェストをキャッシュは、1 回プロキシまたはプライベートの CDN を経由してルーティングするこれらのファイルの将来の要求がローカル キャッシュから取得し、インターネット上の場所からプルしていません。このようなソリューションの計画時に、ネットワーク帯域幅、容量、およびビデオの再生の同時実行を検討してください。
  
([先頭に戻る](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>どのビデオが暗号化され、セキュリティで保護しますか。

Office 365 のビデオでは、データの安全性とプライバシーを維持することがいかに重要である認識しています。[[Office 365 の信頼センター](https://products.office.com/business/office-365-trust-center-cloud-computing-security)では、コンテンツのセキュリティとプライバシーへの取り組みについて説明します。ビデオの再生速度は、環境は良好ですただし、速度と引き換えにプライバシー、セキュリティを侵害しません。速度、セキュリティ、プライバシー対応する方法を次に示します。
  
または他の組織では、新しいビデオをアップロード、そのビデオは、トランス コード、aes-128 暗号化で暗号化され、Azure のメディア サービスに格納されているです。これは、ビデオは両方で転送中に暗号化を意味します。
  
組織のだれかが新しいビデオを見るしようとすると、これらの手順に従います。
  
1. SharePoint のオンライン ビデオを表示するアクセス許可があるかどうかを確認します。

2. SharePoint Online は、ユーザーがビデオを見ることができるかどうかを決定するのにファイルのアクセス許可を使用します。

3. 許可されている場合は、SharePoint Online トークンを取得、ビデオ プレーヤーにするための Azure からです。

4. ビデオ プレーヤーは、トークンを使用して、Azure から復号化キーを要求します。

5. 手で復号化キー、ビデオ プレーヤーは、ビデオをストリーム配信することです。

![O365 ビデオの再生](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([先頭に戻る](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Office 365 のビデオを再生するための要件を挙げてください。

Office 365 のビデオには、オペレーティング システムがサポートされているし、web ブラウザーでは、SharePoint Online の要件では、 [Office 365 のシステム要件](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)と同じです。によって、どのオペレーティング システムと web ブラウザーの設定がある場合は、ビデオ プレーヤーの特定のニーズを決定します。[ビデオ再生の要件](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)の詳細については、ここで。
  
([先頭に戻る](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>Office 365 ビデオには、開始する必要があります場所が表示されることはできませんか。

Office 365 のビデオへの接続のトラブルシューティングには、ネットワーク、ISP(s)、および Office 365 の構成をトラブルシューティングする必要があります。開始する最初の場所は、サービス正常性ダッシュ ボードです。これは、により、Office 365 のビデオの問題が発生してかが示されます。すべてすばらしいが、いくつかに役立つその他のリソースです。
  
- [Office 365 のビデオに必要なネットワークのエンドポイント](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)に接続できることを確認します。

- マイクロソフトの[Office 365 のネットワーク トラブルシューティング ガイド](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)を使用して、ネットワーク接続を確認してください。

- [低速のネットワーク上の Office 365 を使用するためのベスト プラクティス](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)を参照してください。

- [Office 365 のビデオの構成についてのヘルプ](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)を検索します。

([先頭に戻る](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Office 365 のビデオ リソース

トピックを評価し、ご連絡ください、質問の答えは場合、または回答が探している場合にコメントを記入します。正常に展開し、Office 365 のビデオを使用するため、他のリソースのいくつかを以下に示します。
  
[Office 365 のビデオの構成に関するヘルプを検索](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)します。
  
[Office 365 のビデオに対応します。](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[作成し、Office 365 のビデオでは、チャンネルの管理](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[Office 365 のビデオのポータルを管理します。](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Office 365 のビデオで動作しているビデオの形式](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([先頭に戻る](office-365-video-networking-faq.md))
  
戻るを使用することができます短いリンクを以下に示します。[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
