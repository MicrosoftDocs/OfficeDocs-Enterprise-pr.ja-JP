---
title: Exchange Online のパフォーマンスをチューニングする
ms.author: krowley
author: kccross
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
description: この資料には、一般的なヒントとオンラインの Exchange のパフォーマンスを向上させる方法については、その他のリソースへのリンクが含まれています。
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541879"
---
# <a name="tune-exchange-online-performance"></a>Exchange Online のパフォーマンスをチューニングする

この資料には、一般的なヒントとオンラインの Exchange のパフォーマンスを向上させる方法については、その他のリソースへのリンクが含まれています。この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)のプロジェクトの一部です。
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Exchange のオンライン パフォーマンスを向上させるために考慮すべき事項

移行の速度が向上し、Exchange online 組織の帯域幅の制約を軽減、次の手順を検討します。
  
- **メールボックスのサイズを減らす。** メールボックスのサイズが小さいと、移行速度が上昇します。 
    
- **Exchange のハイブリッド展開でメールボックスの移行機能を使用する。** Exchange ハイブリッド展開では、オフライン メール (.OST ファイル形式) は、Exchange Online への移行時に再ダウンロードを必要としません。これは大幅にダウンロード帯域幅の要件を軽減します。 
    
- **インターネット トラフィックが低く、オンプレミスの Exchange があまり使用されていない場合にメールボックスの移動が実行されるようにスケジュールする。** スケジュールの移動時に、移行要求がメールボックスのレプリケーション プロキシに送信されますが、すぐには実行されない場合があります。 
    
- **Web 上で Outlook の無駄のない popouts を使用しています**。無駄のない popouts をサーバー上のいくつかのコンポーネントをレンダリングすることによってマイクロソフトのエッジまたは Internet Explorer で特定の電子メール メッセージのバージョンがメモリを消費するより小さい、提供します。詳細については、[メール メッセージを読むときに使用されるメモリを減らすために無駄のない popouts を使用して](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)参照してください。
    
Exchange 移行時のパフォーマンスの詳細については、 [Office 365 移行時のパフォーマンスとベスト ・ プラクティス](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)を参照してください。
  

