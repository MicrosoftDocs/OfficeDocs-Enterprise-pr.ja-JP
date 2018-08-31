---
title: ExpressRoute に BGP のコミュニティを使用して Office 365 シナリオ
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
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
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: Office 365 に接続する Azure ExpressRoute を使用するは、Office 365 エンドポイントが展開されているネットワークを表す特定の IP サブネットの BGP の提供情報に基づきます。Office 365 および Office 365 を構成するサービスの数のグローバル性質上、お客様多くの場合、ネットワーク上で使用する提供情報を管理する必要があります。IP サブネットの数を減らすIP プレフィックス BGP ネットワーク管理の用語に合わせて自動的に、この資料の残りの部分、お客様には次の最終目標と呼ばれます。
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541536"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>ExpressRoute に BGP のコミュニティを使用して Office 365 シナリオ

Office 365 に接続する Azure ExpressRoute を使用するは、Office 365 エンドポイントが展開されているネットワークを表す特定の IP サブネットの BGP の提供情報に基づきます。Office 365 および Office 365 を構成するサービスの数のグローバル性質上、お客様多くの場合、ネットワーク上で使用する提供情報を管理する必要があります。IP サブネットの数を減らすIP プレフィックス BGP ネットワーク管理の用語に合わせて自動的に、この資料の残りの部分、お客様には次の最終目標と呼ばれます。
  
- **管理提供された IP プレフィックス付きの番号が受け入れ**を内部ネットワーク インフラストラクチャや IP プレフィックスの限られた数のみをサポートするネットワークのキャリアをしているお客様とプレフィックスを許可するため、その費用のネットワークのキャリアをしているお客様限られた数の上は、ネットワークには既にプレフィックスの合計数を評価するし、Office 365 アプリケーションは、ExpressRoute に最適ですを選択します。

- **Azure ExpressRoute 回路に必要な帯域幅の量を管理**- お客様は、インターネット パスと ExpressRoute のパス上で Office 365 サービスの帯域幅の封筒を制御する必要があります。これにより、ビジネスの Skype などの特定のアプリケーション用の ExpressRoute の帯域幅を予約し、インターネットのパスで残りの Office 365 アプリケーションにルーティングします。

これらの目標を持つお客様を支援するために Office 365 IP プレフィックス ExpressRoute 経由で提供されているタグが付けられたサービス BGP コミュニティ値を指定して次の例で示すようにします。
  
> [!NOTE]
> コミュニティ値に含まれる他のアプリケーションに関連付けられているいくつかのネットワーク トラフィックが予想されます。これは、共有サービスやデータ センターで提供するサービスとしてグローバル ソフトウェアの正常な動作です。プレフィックスの数や帯域幅の点を管理する 2 つの目標、上で可能な限りこの最小化されています。

|**サービス**|**BGP コミュニティの値**|**メモ**|
|:-----|:-----|:-----|
|交換\*  <br/> |12076:5010  <br/> |Exchange および EOP サービスが含まれています\*  <br/> |
|sharepoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|ビジネス用の skype\*  <br/> |12076:5030  <br/> |Skype for Business Online  <br/> |
|その他の Office 365 サービス\*  <br/> |12076:5100  <br/> |Office 365 ポータルのサービスと、Azure Active Directory (認証とディレクトリの同期のシナリオ) が含まれています  <br/> |
|\*ExpressRoute に含まれているサービスのシナリオの範囲は、 [Office 365 の端点](https://aka.ms/o365endpoints)の資料に記載されています。  <br/> \*\*追加サービスと BGP コミュニティの値は、将来的に追加可能性があります。[BGP コミュニティの現在のリストを参照してください](https://azure.microsoft.com/documentation/articles/expressroute-routing/)。<br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>BGP コミュニティを使用する最も一般的なシナリオを挙げてください。

お客様は、IP プレフィックスの有効な IP プレフィックスの合計数と予想される帯域幅の封筒の特定の Office 365 サービスに影響を与えるので、Azure ExpressRoute 経由でのネットワークのグループを制御するのに BGP のコミュニティを使用することがあります。Azure ExpressRoute や BGP コミュニティの使用に関係なくトラフィックがインターネットにバインドされているすべての Office 365 を要求することを理解する重要です。次の 3 つのシナリオは、この機能の最も一般的な使用です。
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>シナリオ 1: Office 365 IP プレフィックスの数を最小限に抑える

コントソ株式会社は、現在 Exchange Online と SharePoint Online に Office 365 を使用している 50,000 人の会社です。ExpressRoute を確認するのには、Contoso が多くの地域では、そのネットワーク デバイスを指定は 100 のエントリの追加の経路上のルーティング テーブル サイズを処理できません。Contoso 社では、ExpressRoute を選択し、Office 365 サービスの完全なセットの広告が 100 を超えていることを確認したうえ IP プレフィックスの合計数を確認します。100 の別のルート エントリの下に、contoso 社のスコープ Office 365 用に、SharePoint のオンライン BGP コミュニティの値だけ、12076:5020、ExpressRoute のマイクロソフトのピアリング経由で受信した ExpressRoute を使用します。

|**BGP コミュニティのタグが使用されます。**|**Azure ExpressRoute 経由でルーティング可能な機能**|**インターネットのルートが必要です。**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint オンライン&amp;ビジネスの OneDrive  <br/> | DNS、CRL は、 &amp; CDN の要求  <br/>  Azure ExpressRoute 経由でサポートされていない具体的には他のすべての Office 365 サービス  <br/>  他のすべての Microsoft クラウド サービス  <br/>  Office 365 ポータル、Office 365 認証では、 &amp; Office オンライン  <br/>  オンラインの交換、Exchange オンライン保護、および Skype のビジネス オンライン  <br/> |

> [!NOTE]
> 各サービスの下の接頭辞数を達成するため、最小限のサービス間の重複が保持されます。これは、予想される動作です。
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>シナリオ 2: スコープの ExpressRoute および内部帯域幅を使用していくつかの Office 365 サービス

Fabrikam Inc、分散型の異機種混在ネットワークでの大規模な多国籍企業などを含む多くの Office 365 サービスのサブスクリプション サーバーではExchange オンライン、オンラインでの SharePoint とオンライン ビジネスの Skype。Fabrikam 社の内部のルーティング インフラストラクチャは、そのルーティング テーブル内の IP プレフィックスの数千を処理できます。ただし、fabrikam 社のみを必要と ExpressRoute とは、最も機密性の高いネットワーク パフォーマンスと他のすべての Office 365 アプリケーション用の既存のインターネットの帯域幅を使用する Office 365 アプリケーションの内部帯域幅を提供します。
  
そのため、Fabrikam の BGP コミュニティのオンライン ビジネスの値、12076:5030、ExpressRoute のマイクロソフトのピアリング経由で受信した Skype だけに、Azure の ExpressRoute の帯域幅のスコープです。Office 365 に関連する他のネットワーク トラフィックは、インターネットの出口ポイントを使用し続けます。

|**BGP コミュニティのタグが使用されます。**|**Azure ExpressRoute 経由でルーティング可能な機能**|**インターネットのルートが必要です。**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype は SIP シグナリングでは、ダウンロード、音声、ビデオ、およびデスクトップの共有  <br/> | DNS、CRL は、 &amp; CDN の要求  <br/>  Azure ExpressRoute 経由でサポートされていない具体的には他のすべての Office 365 サービス  <br/>  他のすべての Microsoft クラウド サービス  <br/>  Office 365 ポータル、Office 365 認証では、 &amp; Office オンライン  <br/>  ビジネスの遠隔測定、Skype クライアントの簡単なヒント、パブリック IM 接続の Skype  <br/>  オンラインの交換、Exchange オンライン保護、および SharePoint オンライン  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>シナリオ 3: Office 365 のサービスのみの Azure ExpressRoute のスコープ

Woodgrove Bank は、Office 365 を含むいくつかのマイクロソフトのクラウド サービスのお客様です。ネットワークを評価した後、容量と消費 Woodgrove Bank がサポートされている Office 365 サービスの優先パスとしての Azure ExpressRoute の展開を決定しました。ルーティング テーブルは、Office 365 IP プレフィックスの完全なセットをサポートできるし、Azure ExpressRoute 回路が提供するすべての予想される帯域幅と遅延のニーズをサポートします。
  
ネットワーク トラフィックを Office 365、Woodgrove Bank のスコープと IP のすべての接頭番号を Office 365 に ExpressRoute を使用する以外に、マイクロソフトのクラウド サービスに関連付けられていることを確認するのには、特定の BGP コミュニティの値を Office 365、12076:5010、12076:5020、12076:5030 でタグ付けされました。12076:5100。

|**BGP コミュニティのタグが使用されます。**|**Azure ExpressRoute 経由でルーティング可能な機能**|**インターネットのルートが必要です。**|
|:-----|:-----|:-----|
|Exchange、SharePoint では、ビジネス用の Skype&amp;その他のサービス  <br/> (12076:5010、12076:5020、12076:5030、12076:5100)  <br/> |オンライン交換&amp;オンライン保護を交換します。  <br/> SharePoint オンライン&amp;ビジネスの OneDrive  <br/> Skype は SIP シグナリングでは、ダウンロード、音声、ビデオ、およびデスクトップの共有  <br/> Office 365 ポータル、Office 365 認証では、 &amp; Office オンライン  <br/> | DNS、CRL は、 &amp; CDN の要求  <br/>  Azure ExpressRoute 経由でサポートされていない具体的には他のすべての Office 365 サービス  <br/>  他のすべての Microsoft クラウド サービス  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>BGP コミュニティを使用しての考慮事項を検討

ExpressRoute が提供され、お客様のネットワークを通じて伝達される方法に影響を与える BGP のコミュニティを活用することを選択したお客様は、次、点を考慮する必要があります。
  
- BGP コミュニティを使用して、ネットワークの設計を確認することが重要でルートの対称性が維持されます。場合によっては、追加または BGP コミュニティの削除は、対称ルーティングとは、壊れた対称ルーティングを再確立するために、ルーティングの構成を更新する必要がある場合を作成できます。

- BGP コミュニティの値を持つ Azure ExpressRoute スコープの設定は、お客様の操作です。マイクロソフトでは、お客様が構成されているスコープに関係なくピアリング関係を持つすべての IP プレフィックスが関連付けられているを通知します。

- Azure ExpressRoute は、BGP のコミュニティを割り当てられている顧客に基づくマイクロソフトのネットワークのすべてのアクションをサポートしていません。

- Office 365are で使用される IP プレフィックスは、サービス BGP コミュニティ値を指定して、場所の特定の BGP コミュニティはサポートされていませんのみマークします。Office 365 のサービスはグローバルであり、テナントの場所に基づくプレフィックスをフィルター処理、または、Office 365 のクラウド内のデータはサポートされていません。推奨されるアプローチは、最も短いを調整するためのネットワークまたは Office 365 サービスの IP アドレスの物理的な場所に関係なく、Microsoft のグローバル ネットワークに、ユーザーのネットワーク上の場所から、最優先されるネットワーク パスを構成するのには、します。要求しています。

- BGP コミュニティの各値に含まれている IP プレフィックスは、値に関連付けられている Office 365 アプリケーションの IP アドレスを含むサブネットを表します。、場合によっては、複数の Office 365 アプリケーションは、既存のコミュニティの 1 つ以上の値で、IP プレフィックスのサブネット内の IP アドレスを持ちます。これは、予想もめったにありませんが、割り当ての断片化のための動作とプレフィックスの数や帯域幅の管理の目標に影響を与えません。お客様は、許可が必要] を使用することをお勧め拒否機能は必要ありません」ではなくアプローチの影響を最小限に抑えるため、Office 365 コミュニティで BGP を利用するとします。

- BGP のコミュニティを使用すると、基になるネットワーク接続の要件または Office 365 を使用するために必要な構成は変更されません。Office 365 にアクセスしたい顧客する必要がありますインターネットにアクセスできるようにします。

- BGP コミュニティと Azure ExpressRoute スコープの設定は、マイクロソフトのピアリング関係を表示、内部ネットワークのルートにのみ影響します。スコープ ベースのルーティングと組み合わせて、PAC または WPAD 構成の使用など・その他のアプリケーション レベルの構成を確認する必要があります。

- BGP コミュニティを割り当てられている Microsoft を使用するには、こともできます、自身の BGP コミュニティを内部ルーティングに影響を与える Azure ExpressRoute を介して Office 365 IP プレフィックスに割り当てるには。ピアリングの場所とし、お客様のネットワークのダウン ストリーム情報を使用する、最短を調整するための指定された各 ExpressRoute で学習したすべてのルートに BGP コミュニティ ベースの場所を割り当てることが一般的な使用例や、最も優先されるネットワークのパスにマイクロソフトのネットワークです。BGP コミュニティでは ExpressRoute と Office 365 シナリオを割り当てられている顧客の使用は、Microsoft の制御と可視性の範囲外です。

戻るを使用することができます短いリンクを次のとおりです: [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365)。
  
## <a name="related-topics"></a>関連項目

[Office 365 へのネットワーク接続](network-connectivity.md)
  
[Office 365 向け Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)
  
[Office 365 向け ExpressRoute でのルーティング](routing-with-expressroute.md)
  
[Office 365 向け ExpressRoute でのネットワーク計画](network-planning-with-expressroute.md)
  
[メディアの品質とオンライン ビジネスの Skype でのネットワーク接続のパフォーマンス](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute とオンライン ビジネスの Skype での QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute を使用して通話フロー](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 向け ExpressRoute での実装](implementing-expressroute.md)
  
[BGP コミュニティのサポート](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)
  
[Office 365 のパフォーマンスに関するトラブルシューティングの計画](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute for Office 365 のトレーニング](https://channel9.msdn.com/series/aer)
