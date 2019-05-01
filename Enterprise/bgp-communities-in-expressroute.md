---
title: Office 365 シナリオで ExpressRoute の BGP コミュニティを使用する
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
description: Azure ExpressRoute を使用した office 365 への接続は、office 365 エンドポイントが展開されているネットワークを表す特定の IP サブネットの BGP 広告に基づいています。 office 365 のグローバルな性質と、office 365 を構成するサービスの数により、多くの場合、お客様はネットワークで受け入れる広告を管理する必要があります。 IP サブネットの数を減らす。この記事の残りの部分では IP プレフィックスと呼ばれ、BGP ネットワーク管理の用語と整合するために、次のようなお客様の目標を達成しています。
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490923"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Office 365 シナリオで ExpressRoute の BGP コミュニティを使用する

Azure ExpressRoute を使用した office 365 への接続は、office 365 エンドポイントが展開されているネットワークを表す特定の IP サブネットの BGP 広告に基づいています。 office 365 のグローバルな性質と、office 365 を構成するサービスの数により、多くの場合、お客様はネットワークで受け入れる広告を管理する必要があります。 IP サブネットの数を減らす。この記事の残りの部分では IP プレフィックスと呼ばれ、BGP ネットワーク管理の用語と整合するために、次のようなお客様の目標を達成しています。
  
- **承認された ip プレフィックスの数を管理**する-制限された数の ip プレフィックスのみをサポートする内部ネットワークインフラストラクチャまたはネットワークキャリアを備えているお客様と、プレフィックスの受け入れを請求するネットワークキャリアを所有している顧客制限された数を超えると、ネットワークに既にアドバタイズされているプレフィックスの合計数を評価して、ExpressRoute に最適な Office 365 アプリケーションを選択します。

- **Azure ExpressRoute 回線で必要な帯域幅の量を管理**する-お客様は、ExpressRoute のパスとインターネットパスを介して Office 365 サービスの帯域幅エンベロープを制御する必要がある場合があります。 これにより、お客様は Skype for business などの特定のアプリケーションに対して ExpressRoute の帯域幅を予約し、残りの Office 365 アプリケーションをインターネットパスを介してルーティングすることができます。

このような目標をお客様に提供するために、次の例に示されているように、Office 365 のサービス固有の BGP community 値を使用してタグ付けされています。
  
> [!NOTE]
> 他のアプリケーションに関連付けられているネットワークトラフィックは、コミュニティの値に含まれていることが予想されます。 これは、共有サービスとデータセンターを使用したサービスとしてのグローバルソフトウェアに想定される動作です。 これは、上の2つの目的で、プレフィックスの数や帯域幅を考慮することで最小化されています。

|**サービス**|**BGP コミュニティの値**|**メモ**|
|:-----|:-----|:-----|
|変換\*  <br/> |12076:5010  <br/> |Exchange および EOP サービスが含まれています。\*  <br/> |
|sharepoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|skype for business\*  <br/> |12076:5030  <br/> |Skype for Business Online  <br/> |
|その他の Office 365 サービス\*  <br/> |12076:5100  <br/> |Azure Active Directory (認証およびディレクトリ同期のシナリオ) と Office 365 ポータルサービスが含まれています。  <br/> |
|\*ExpressRoute に含まれるサービスシナリオの範囲については、「 [Office 365 エンドポイント](https://aka.ms/o365endpoints)」の記事に記載されています。  <br/> \*\*今後、追加サービスと BGP コミュニティの値を追加することができます。 [BGP コミュニティの現在の一覧を参照してください](https://azure.microsoft.com/documentation/articles/expressroute-routing/)。  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>BGP コミュニティを使用するための最も一般的なシナリオは何ですか。

お客様は、BGP コミュニティを使用して、Azure ExpressRoute を介してネットワークに受け入れられる ip プレフィックスのグループを規制することができます。そのため、特定の Office 365 サービスの合計 ip プレフィックス数と予想帯域幅エンベロープに影響します。 すべての Office 365 で、Azure ExpressRoute または BGP コミュニティの使用に関係なく、インターネットにバインドされたトラフィックが必要になることを理解しておくことが重要です。 この機能は、次の3つのシナリオで最も一般的に使用されます。
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>シナリオ 1: Office 365 IP プレフィックスの数を最小限に抑える

Contoso Corporation は、現在 Office 365 を使用して Exchange online と SharePoint online を使用している5万の個人企業です。 「ExpressRoute の要件を確認する」では、Contoso 社のネットワークデバイスでは、多くの地域の場所にあるルーティングテーブルのサイズを処理できません100追加のルートエントリ。 Contoso 社のレビュー ExpressRoute が Office 365 サービスの完全なセットに対して提供する IP プレフィックスの合計数です。これは100を超えたことを示しています。 100の追加ルートエントリの下に留まるため、Contoso 社は、Office 365 用の expressroute の使用を、expressroute Microsoft ピアリング経由で受信した SharePoint Online BGP community value (12076:5020) だけに範囲を置いています。

|**使用される BGP コミュニティタグ**|**Azure ExpressRoute 経由でルーティング可能な機能**|**必要なインターネットルート**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp;の OneDrive for business  <br/> | DNS、CRL、 &amp; CDN 要求  <br/>  Azure ExpressRoute で特にサポートされていないその他のすべての Office 365 サービス  <br/>  その他のすべての Microsoft クラウドサービス  <br/>  office 365 ポータル、office 365 認証、 &amp; office Online  <br/>  exchange online、exchange online Protection、および Skype for business online  <br/> |

> [!NOTE]
> 各サービスに対してより低いプレフィックス数を実現するために、サービス間で最小限の重複が保持されます。 これは予想どおりの動作です。
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>シナリオ 2: 特定の Office 365 サービスに対して ExpressRoute および内部帯域幅を使用する場合

分散異種ネットワークを使用する大規模な多国籍企業の Fabrikam Inc は、多くの Office 365 サービスのサブスクライバーです。これには以下が含まれます。Exchange online、SharePoint online、Skype for business online。 Fabrikam の内部ルーティングインフラストラクチャは、ルーティングテーブルで数千の IP プレフィックスを処理できます。ただし、Fabrikam は、ネットワークパフォーマンスに最も敏感で、その他すべての office 365 アプリケーションで既存のインターネット帯域幅を使用する Office 365 アプリケーションに対して、ExpressRoute と内部帯域幅をプロビジョニングすることのみを希望しています。
  
そのため、Fabrikam は Azure expressroute 帯域幅を、ExpressRoute Microsoft ピアリング経由で受信した Skype for business Online BGP Community 値12076:5030 にのみスコープします。 Office 365 に関連付けられている残りのネットワークトラフィックでは、引き続きインターネット出口ポイントが使用されます。

|**使用される BGP コミュニティタグ**|**Azure ExpressRoute 経由でルーティング可能な機能**|**必要なインターネットルート**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype SIP 信号、ダウンロード、音声、ビデオ、デスクトップ共有  <br/> | DNS、CRL、 &amp; CDN 要求  <br/>  Azure ExpressRoute で特にサポートされていないその他のすべての Office 365 サービス  <br/>  その他のすべての Microsoft クラウドサービス  <br/>  office 365 ポータル、office 365 認証、 &amp; office Online  <br/>  skype for business テレメトリ、skype クライアントのクイックヒント、パブリック IM 接続  <br/>  exchange online、exchange online Protection、および SharePoint online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>シナリオ 3: Office 365 サービス用にのみ Azure ExpressRoute のスコープを限定する

Woodgrove bank は、Office 365 を含むいくつかの Microsoft クラウドサービスのお客様です。 ネットワーク容量と消費を評価した後、Woodgrove bank は、サポートされている Office 365 サービスの優先パスとして Azure ExpressRoute を展開することを決定します。 ルーティングテーブルは、すべての Office 365 IP プレフィックスと、プロビジョニングされた Azure ExpressRoute のすべてのセットをサポートできます。すべての予測される帯域幅と待機時間のニーズがサポートされます。
  
office 365 以外の Microsoft cloud services に関連付けられているネットワークトラフィックを確実にするために、Woodgrove bank は、office 365 の ExpressRoute を office 365 固有の BGP community 値、12076:5010、12076:5020、12076:5030、12076:5100

|**使用される BGP コミュニティタグ**|**Azure ExpressRoute 経由でルーティング可能な機能**|**必要なインターネットルート**|
|:-----|:-----|:-----|
|Exchange、Skype for business、SharePoint、 &amp;その他のサービス  <br/> (12076:5010、12076:5020、12076:5030、12076:5100)  <br/> |exchange online &amp; exchange online Protection  <br/> SharePoint Online &amp;の OneDrive for business  <br/> Skype SIP 信号、ダウンロード、音声、ビデオ、デスクトップ共有  <br/> office 365 ポータル、office 365 認証、 &amp; office Online  <br/> | DNS、CRL、 &amp; CDN 要求  <br/>  Azure ExpressRoute で特にサポートされていないその他のすべての Office 365 サービス  <br/>  その他のすべての Microsoft クラウドサービス  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>BGP コミュニティを使用するための主要な計画に関する考慮事項

お客様が BGP コミュニティを利用して、ExpressRoute を宣伝してお客様のネットワーク経由で伝達する方法に影響を与える場合は、以下の点を考慮してください。
  
- ネットワーク設計で BGP コミュニティを使用する場合は、ルート対称が引き続き維持されることが重要です。 場合によっては、BGP コミュニティの追加または削除によって、対称ルーティングが中断され、対称ルーティングを再確立するために、ルーティング構成を更新する必要があります。

- BGP community の値で Azure ExpressRoute のスコープを指定することは、顧客のアクションです。 Microsoft は、顧客によって構成されたスコープに関係なく、ピアリング関係に関連付けられているすべての IP プレフィックスを通知します。

- Azure ExpressRoute は、お客様が割り当てられた BGP コミュニティに基づく Microsoft のネットワーク上でのアクションをサポートしていません。

- Office 365are 使用される IP プレフィックスは、サービス固有の bgp コミュニティ値でのみマークされています。場所固有の bgp コミュニティはサポートされていません。 office 365 サービスはグローバルな性質を持っているため、テナントの場所または office 365 クラウド内のデータに基づくフィルター処理プレフィックスはサポートされていません。 推奨されるアプローチは、Office 365 サービスの IP アドレスの物理的な場所に関係なく、ユーザーのネットワークの場所から Microsoft グローバルネットワークへの最短または最も優先されるネットワークパスを調整するようにネットワークを構成することです。要求しています。

- 各 BGP community 値に含まれる ip プレフィックスは、値に関連付けられた Office 365 アプリケーションの ip アドレスを含むサブネットを表します。 場合によっては、複数の Office 365 アプリケーションがサブネット内に複数の ip アドレスを持ち、その結果、ip プレフィックスが複数のコミュニティ値に存在することがあります。 これは、割り当ての断片化が原因であると想定されていますが、プレフィックス数や帯域幅管理の目標に影響を与えることはありません。 Office 365 の BGP コミュニティを活用して影響を最小限に抑えるには、「必要な機能を拒否する」を使用するのではなく、「必要な機能を許可する」というアプローチを使用することをお勧めします。

- BGP コミュニティを使用しても、基盤となるネットワーク接続の要件や、Office 365 を使用するために必要な構成は変更されません。 Office 365 にアクセスする必要があるお客様は、引き続きインターネットにアクセスできるようにする必要があります。

- BGP コミュニティによる Azure ExpressRoute の範囲指定は、内部ネットワークが Microsoft ピアリング関係を介して参照できるルートにのみ影響します。 スコープルーティングと共に、PAC または WPAD 構成の使用など、追加のアプリケーションレベルの構成を行う必要がある場合があります。

- Microsoft によって割り当てられた bgp コミュニティを使用することに加えて、お客様は、内部ルーティングに影響を与えるために Azure ExpressRoute で学んだ Office 365 の IP プレフィックスに独自の bgp コミュニティを割り当てることもできます。 よく使用されるユースケースとして、特定の ExpressRoute ピアの場所で学習したすべてのルートに位置ベースの BGP コミュニティを割り当て、顧客ネットワークの下流の情報を使用して、最も短いまたは最も優先されるネットワークパスを次のように調整します。Microsoft のネットワーク。 Office 365 シナリオで ExpressRoute を使用して、顧客が割り当てられている BGP コミュニティを使用することは、Microsoft control または visibility の範囲外です。

次[https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365)の短いリンクを使用して、に戻ることができます。
  
## <a name="related-topics"></a>関連項目

[Office 365 へのネットワーク接続](network-connectivity.md)
  
[Office 365 向け Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)
  
[Office 365 向け ExpressRoute でのルーティング](routing-with-expressroute.md)
  
[Office 365 向け ExpressRoute でのネットワーク計画](network-planning-with-expressroute.md)
  
[Skype for Business Online でのメディア品質とネットワーク接続のパフォーマンス](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype for business Online の ExpressRoute および QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute を使用したコールフロー](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 向け ExpressRoute の実装](implementing-expressroute.md)
  
[BGP コミュニティのサポート](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)
  
[Office 365 のパフォーマンスに関するトラブルシューティングの計画](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute for Office 365 のトレーニング](https://channel9.msdn.com/series/aer)
