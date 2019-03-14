---
title: Exchange Online のパフォーマンスをチューニングする
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: この記事には、Exchange Online のパフォーマンスを向上させる方法を説明する一般的なヒントとその他のリソースへのリンクが含まれています。
ms.openlocfilehash: f75869ba6d83a92b1e19743c8b38c4bcbb6762cf
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372854"
---
# <a name="tune-exchange-online-performance"></a>Exchange Online のパフォーマンスをチューニングする

この記事では、特に移行の前に Exchange Online のパフォーマンスを向上させる方法を説明する一般的なヒントとその他のリソースへのリンクを掲載しています。 この記事は、 [Office 365 プロジェクトのネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Exchange Online のパフォーマンスを向上させるための考慮事項

移行速度を向上させ、Exchange Online の帯域幅制限を減らすには、次の点を考慮してください。
  
- **メールボックスのサイズを小さくします。** メールボックスのサイズが小さくなると、移行速度が向上します。 
    
- **Exchange ハイブリッド展開でメールボックスの移動機能を使用します。** Exchange ハイブリッド展開では、オフラインメール (の形式) を使用します。OST ファイル) は、Exchange Online に移行するときに再ダウンロードする必要はありません。 これにより、ダウンロード帯域幅の要件を大幅に削減できます。 
    
- **メールボックスの移動は、インターネットトラフィックが少ない時間帯やオンプレミスの Exchange の使用中に発生するようにスケジュールします。** 移動をスケジュールするとき、メールボックスレプリケーションプロキシに移行要求が送信され、すぐには実行されない場合があります。 
    
- **web 上の Outlook のリーンポップアウトを使用します。** リーンポップアウトは、サーバー上にいくつかのコンポーネントをレンダリングすることによって、Microsoft Edge または Internet Explorer で特定の電子メールメッセージのより小さなメモリを消費するバージョンを少なくします。 詳細については、「[リーンポップアウトを使用してメールメッセージの読み取り時に使用されるメモリを減らす](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)」を参照してください。


## <a name="general-advice"></a>一般的なアドバイス

- outlook.office.com の DNS 参照が、場所の論理的なエントリの場所で MS データセンターに入力されていることを確認します。

- メールボックスのキャッシュを調査し、適切なオプション (re を選択します。 キャッシュ期間、共有メールボックスのキャッシュ、et cetera)。

- インターネット経由に移行する前に、Outlook データが VPN 接続 (中央オフィスへ) を通過しないようにします。

- メールボックスデータがフォルダー、アイテム、量の制限に準拠していることを確認してください。
    
Exchange の移行のパフォーマンスの詳細については、「 [Office 365 移行のパフォーマンスとベストプラクティス](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)」を参照してください。
  

