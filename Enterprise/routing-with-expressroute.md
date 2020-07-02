---
title: Office 365 向け ExpressRoute でのルーティング
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Azure ExpressRoute を使用して Office 365 へのルーティングトラフィックを適切に理解するには、コア ExpressRoute ルーティング要件と ExpressRoute 回線およびルーティングドメインをしっかりと理解している必要があります。 これらは、Office 365 のお客様が依存している ExpressRoute を使用するための基礎をレイアウトしています。
ms.openlocfilehash: c9d81e0823b63750a456f559855bb130a2e87b07
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998196"
---
# <a name="routing-with-expressroute-for-office-365"></a>Office 365 向け ExpressRoute でのルーティング

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Azure ExpressRoute を使用して Office 365 へのルーティングトラフィックを適切に理解するには、コア[expressroute ルーティング要件](https://azure.microsoft.com/documentation/articles/expressroute-routing/)と[expressroute 回線およびルーティングドメイン](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)をしっかりと理解している必要があります。 これらは、Office 365 のお客様が依存している ExpressRoute を使用するための基礎をレイアウトしています。
  
前述の記事で理解しておく必要がある主な項目には、次のようなものがあります。
  
- ExpressRoute の回線は特定の物理インフラストラクチャにはマッピングされていませんが、Microsoft とお客様の代わりにピアリングプロバイダーによって1つのピアリング場所で行われる論理的な接続です。

- ExpressRoute 回路とお客様の s キーとの間には、1:1 のマッピングがあります。

- 各回線は、2つの独立したピアリング関係 (Azure プライベートピアリングと Microsoft ピアリング) をサポートできます。Office 365 には、Microsoft のピアリングが必要です。

- 各回線には、すべてのピアリング関係で共有される固定帯域幅があります。

- ExpressRoute サーキットに使用されるすべてのパブリック IPv4 アドレスとパブリックアドレスは、自分が所有していることを検証するか、アドレス範囲の所有者によって排他的に割り当てられるようにする必要があります。

- 仮想 ExpressRoute の回路はグローバルに冗長性があり、標準的な BGP ルーティングプラクティスに従います。 このため、アクティブ/アクティブ構成では、プロバイダーへの出口ごとに2つの物理回路を推奨しています。

サポートされているサービス、コスト、および構成の詳細については、 [FAQ ページ](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)を参照してください。 Microsoft ピアリングサポートを提供する接続プロバイダーの一覧については、「 [ExpressRoute の場所](https://azure.microsoft.com/documentation/articles/expressroute-locations/)」を参照してください。 また、詳細について説明するために、Channel 9 で[Office 365 用の10個の Azure ExpressRoute の](https://channel9.msdn.com/series/aer)シリーズを記録しています。
  
## <a name="ensuring-route-symmetry"></a>ルート対称の保証

Office 365 フロントエンドサーバーは、インターネットと ExpressRoute の両方でアクセスできます。 これらのサーバーは、両方のが利用可能な場合に、ExpressRoute 回線を介してオンプレミスにルートし直すことを優先します。 このため、ネットワークからのトラフィックがインターネット回線経由でルーティングすることを希望する場合は、ルートが平均値周辺になる可能性があります。 ステートフルパケット検査を実行するデバイスは、発信パケットとは別のパスに続くリターントラフィックをブロックできるため、非対称ルートは問題になります。
  
インターネットまたは ExpressRoute 経由で Office 365 への接続を開始するかどうかに関係なく、ソースはパブリックルーティング可能なアドレスである必要があります。 多くのお客様が Microsoft と直接ピアリングを行うことで、お客様間で重複が起こり得るプライベートアドレスを持つことはできません。
  
以下に、Office 365 から社内ネットワークへの通信が開始されるシナリオを示します。 ネットワーク設計を簡素化するには、インターネットパスを使用してこれらをルーティングすることをお勧めします。
  
- SMTP サービス。 Exchange Online テナントからオンプレミスのホストまたは sharepoint Online からオンプレミスのホストに送信される SharePoint Online のメールなど。 SMTP プロトコルは、ExpressRoute 回線で共有されるルートプレフィックスと、ExpressRoute 経由でオンプレミス SMTP サーバーをアドバタイズすることより、Microsoft のネットワーク内で幅広く使用されています。これらのサービスではエラーが発生します。

- サインインのパスワードの検証中に ADFS が有効になります。

- [Exchange Server のハイブリッド展開](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。

- [SharePoint フェデレーションハイブリッド検索](https://technet.microsoft.com/library/dn197174.aspx)。

- [SharePoint ハイブリッド BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [Skype](https://technet.microsoft.com/library/jj205403.aspx) for business ハイブリッドおよび/または skype for business[フェデレーション](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype For Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx )。

このような双方向トラフィックフローに対して Microsoft がネットワークにルーティングするには、オンプレミスデバイスへの BGP ルートを Microsoft と共有する必要があります。 ExpressRoute を介して Microsoft にルートプレフィックスをアドバタイズする場合は、次のベストプラクティスに従う必要があります。

1) パブリック IP アドレスルートプレフィックスをパブリックインターネットと ExpressRoute にアドバタイズしないようにします。 ExpressRoute の IP BGP ルートプレフィックスは、インターネットにまったくアドバタイズされていない範囲からのものであることが強く推奨されます。 使用可能な IP アドレス空間によってこれを達成できない場合は、すべてのインターネット回線よりも、ExpressRoute よりも具体的な範囲を提供することが重要です。

2) ExpressRoute 回線ごとに別々の NAT IP プールを使用し、インターネット回線とは別のものにします。

3) Microsoft にアドバタイズされたすべてのルートによって、Microsoft のネットワーク内の任意のサーバーからのネットワークトラフィックが提供されることに注意してください。これには、ExpressRoute を介してネットワークにアドバタイズされているルートだけではありません。 ルーティングのシナリオが定義され、チームにとってよく理解されているサーバーにのみルートをアドバタイズします。 ネットワークからの複数の ExpressRoute 回路で、それぞれの IP アドレスルートプレフィックスをアドバタイズします。
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>ExpressRoute を経由してルーティングするアプリケーションと機能を決定する

Microsoft ピアリングルーティングドメインを使用してピアリング関係を構成し、適切なアクセスに対して承認されると、ExpressRoute で利用可能なすべての PaaS および SaaS サービスを表示できるようになります。 ExpressRoute 用に設計された Office 365 サービスは、 [BGP コミュニティ](https://aka.ms/bgpexpressroute365)または[ルートフィルター](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)で管理できます。
  
Office 365 ビデオなどのその他のアプリケーションは、Office 365 アプリケーションです。ただし、Office 365 のビデオは、ポータル、ストリーミングサービス、およびコンテンツ配信ネットワークの3つの異なるコンポーネントで構成されています。 ポータルは SharePoint Online 内に存在し、ストリーミングサービスは Azure メディアサービス内に存在し、コンテンツ配信ネットワークは Azure CDN 内に存在します。 次の表に、これらのコンポーネントの概要を示します。

|**コンポーネント**|**基になるアプリケーション**|**SharePoint Online BGP コミュニティに含まれていますか?**|**使用法**|
|:-----|:-----|:-----|:-----|
|Office 365 のビデオポータル  <br/> |SharePoint Online  <br/> |はい  <br/> |構成、アップロード  <br/> |
|Office 365 Video streaming service  <br/> |Azure Media Services  <br/> |いいえ  <br/> |ビデオが CDN で利用できないイベントで使用されるストリーミングサービス  <br/> |
|Office 365 ビデオコンテンツ配信ネットワーク  <br/> |Azure CDN  <br/> |いいえ  <br/> |ビデオダウンロード/ストリーミングの主要なソース。 [詳細については、「Office 365 のビデオネットワーク](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e)」を参照してください。  <br/> |

Microsoft ピアリングを使用して利用できる Office 365 の各機能の一覧については、「アプリケーションの種類と FQDN 別の[office 365 エンドポイント](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)」の記事を参照してください。 テーブルで FQDN を使用する理由は、ユーザーが PAC ファイルまたは他のプロキシ構成を使用してトラフィックを管理できるようにするためです。 .PAC ファイルなどの[Office 365 エンドポイントの管理](https://aka.ms/manageo365endpoints)に関するガイドを参照してください。
  
状況によっては、1つ以上のサブ Fqdn が上位レベルのワイルドカードドメインと異なる方法で通知されるワイルドカードドメインを使用しています。 これは通常、すべてのサーバーが ExpressRoute およびインターネットにアドバタイズされているサーバーの長いリストをワイルドカードで表している場合に発生します。また、宛先の小さなサブセットはインターネットにのみ通知されます。 相違点については、以下の表を参照してください。
  
この表には、インターネットにのみ提供されるサブ Fqdn と共にインターネットと Azure ExpressRoute の両方に通知されるワイルドカード Fqdn が表示されます。

|**ExpressRoute およびインターネット回路にアドバタイズされたワイルドカードドメイン**|**インターネット回線のみにアドバタイズされたサブ FQDN**|
|:-----|:-----|
|\*. microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*. officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

通常、PAC ファイルは、ExpressRoute のアドバタイズされたエンドポイントに、ネットワーク要求をサーキットに直接送信すること、およびプロキシに対する他のすべてのネットワーク要求を送信することを目的としています。 このような PAC ファイルを構成している場合は、PAC ファイルを次の順序で作成します。
  
1. PAC ファイルの先頭にある上記の表の2列目のサブ Fqdn を含め、プロキシにトラフィックを送信します。 [Office 365 エンドポイントの管理](https://aka.ms/manageexpressroute365)に関する記事で使用するサンプルの PAC ファイルを作成しました。

2. [この記事](https://aka.ms/o365endpoints)の最初のセクションの下にある expressroute にアドバタイズされているすべての fqdn を含め、expressroute 回線にトラフィックを直接送信します。

3. その他のネットワークエンドポイントまたはその他の規則をこの2つのエントリの下に含め、プロキシにトラフィックを送信します。

この表には、Azure ExpressRoute とインターネット回線にアドバタイズされたサブコンメールと一緒に、インターネット回線にアドバタイズされるワイルドカードドメインが表示されます。 上記の PAC ファイルでは、次の表の列2の Fqdn が、参照されているリンクの ExpressRoute にアドバタイズされていると表示されています。これは、ファイル内のエントリの2番目のグループに含まれることを意味します。

|**インターネット回線のみにアドバタイズされたワイルドカードドメイン**|**ExpressRoute およびインターネット回路にアドバタイズされたサブ FQDN**|
|:-----|:-----|
|\*. office.com  <br/> |\*. outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> <div style="display: inline">www.office.com</div>  <br/> |
|\*. office.net  <br/> |agent.office.net  <br/> |
|\*. office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*. outlook.com  <br/> |\*. protection.outlook.com  <br/> \*. mail.protection.outlook.com  <br/> 自動検出- \<tenant\> outlook.com  <br/> |
|\*. windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>インターネットおよび ExpressRoute で Office 365 のトラフィックをルーティングする

選択した Office 365 アプリケーションにルーティングするには、いくつかの重要な要因を決定する必要があります。
  
1. アプリケーションに必要な帯域幅の量。 既存の使用法をサンプリングすることは、組織内でこれを決定する唯一の信頼できる方法です。

2. ネットワークトラフィックがネットワークのどこから離れているのかを示します。 これはパフォーマンスに影響するため、Office 365 への接続のネットワーク待ち時間を最小限に抑えるように計画する必要があります。 Skype for Business はリアルタイムの音声とビデオを使用するため、ネットワークの遅延が低下する可能性が特にあります。

3. ネットワークの場所のすべてまたは一部を使用して ExpressRoute を活用したい場合。

4. 選択したネットワークプロバイダーが ExpressRoute を提供する場所。

これらの質問に対する回答を決定したら、帯域幅と場所のニーズを満たす ExpressRoute サーキットをプロビジョニングできます。 ネットワーク計画の詳細については、「 [Office 365 ネットワークチューニングガイド」](https://aka.ms/tune)および「 [Microsoft がネットワークパフォーマンス計画をどのように処理するかについてのケーススタディ](https://aka.ms/tunemsit)」を参照してください。
  
### <a name="example-1-single-geographic-location"></a>例 1: 単一の地理的な場所
  
この例は、1つの地理的な場所を持つ、Trey Research という架空の会社のシナリオを示しています。
  
Trey Research の従業員は、企業ネットワークと ISP の間に配置される送信プロキシのペアで明示的にセキュリティ部門が許可する、インターネット上のサービスおよび web サイトへの接続のみが許可されています。
  
Trey Research は Office 365 用の Azure ExpressRoute を使用するように計画し、コンテンツ配信ネットワーク宛てのトラフィックなど、一部のトラフィックは Office 365 接続の ExpressRoute ではルーティングできないことを認識します。 既定では、すべてのトラフィックがプロキシデバイスにルーティングされているため、これらの要求は以前と同じように動作し続けます。 Trey Research は、Azure ExpressRoute のルーティング要件を満たすことができることを確認した後、回線の作成、ルーティングの構成、および新しい ExpressRoute 回線の仮想ネットワークへのリンクに進みます。 基礎的な Azure ExpressRoute 構成が設定されると、Trey Research は[公開した #2 PAC ファイル](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)を使用して、Office 365 接続用の direct ExpressRoute の顧客固有のデータによるトラフィックのルーティングを行います。
  
次の図に示されているように、Trey Research は、ルーティングと送信プロキシ構成の変更の組み合わせを使用して、Office 365 のトラフィックをインターネット経由でルーティングするための要件と ExpressRoute のトラフィックのサブセットを満たすことができます。
  
1. [#2 PAC ファイル](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)を使用して、Office 365 用の Azure ExpressRoute の別のインターネット出口ポイントを経由してトラフィックをルーティングするように公開します。

2. クライアントは、Trey Research のプロキシに向かって既定のルートを使用して構成されます。

このシナリオ例では、Trey Research は送信プロキシデバイスを使用しています。 同様に、Office 365 用の Azure ExpressRoute を使用していないお客様は、この手法を使用して、既知の高ボリュームエンドポイントに宛てたトラフィックを検査するコストに基づいてトラフィックをルーティングすることができます。
  
Exchange Online、SharePoint Online、Skype for Business Online の最大ボリューム Fqdn は次のとおりです。
  
![ExpressRoute 顧客エッジネットワーク](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com、outlook.office.com

- \<tenant-name\>. sharepoint.com、 \<tenant-name\> -my.sharepoint.com、 \<tenant-name\> - \<app\> sharepoint.com

- \*.TCP 以外のトラフィックの IP 範囲と共に Lync.com

- \*broadcast.officeapps.live.com、 \* excel.officeapps.live.com、 \* onenote.officeapps.live.com、 \* powerpoint.officeapps.live.com、 \* view.officeapps.live.com、 \* visio.officeapps.live.com、 \* word-edit.officeapps.live.com、 \* word-view.officeapps.live.com、office.live.com

[Windows 8 でプロキシ設定を展開および管理する](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx)方法と、 [Office 365 がプロキシによって制限](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx)されないようにする方法について説明します。
  
1つの ExpressRoute 回線では、Trey Research の高可用性はありません。 ExpressRoute 接続にサービスを提供しているエッジデバイスのイベント Trey の冗長ペアのペアでは、フェールオーバーに追加の ExpressRoute サーキットはありません。 これにより、predicament の Trey Research は、インターネットへのフェールオーバーとして、手動による再構成と、場合によっては新しい IP アドレスを必要とする場合があります。 Trey が高可用性を追加する必要がある場合、最も簡単なソリューションは、各場所に対して ExpressRoute 回路を追加し、アクティブ/アクティブな方法で回線を構成することです。
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>複数の場所を使用する Office 365 用の ExpressRoute をルーティングする

最後のシナリオでは、ExpressRoute での Office 365 トラフィックのルーティングは、さらに複雑なルーティングアーキテクチャの基礎となります。 場所の数、場所が存在する大陸数、ExpressRoute 回路の数などに関係なく、一部のトラフィックをインターネットにルーティングでき、ExpressRoute を介したトラフィックが必要になります。
  
複数の地域に所在する顧客に対して回答する必要がある追加の質問には、次のようなものがあります。
  
1. すべての場所に ExpressRoute 回路を必要としていますか? Skype for Business Online を使用している場合、または SharePoint Online または Exchange Online の待機時間の違いを懸念している場合は、それぞれの場所でアクティブ/アクティブの ExpressRoute 回線の冗長ペアが推奨されます。 詳細については、「Skype for Business のメディア品質およびネットワーク接続ガイド」を参照してください。

2. 特定の地域で ExpressRoute 回路を使用できない場合、Office 365 の送信トラフィックをルーティングする方法を教えてください。

3. 多数の小さな場所を持つネットワークの場合、トラフィックを統合するために推奨される方法は何ですか。

これらのそれぞれには、独自のネットワークを評価する必要がある独自の課題があります。また、Microsoft から利用可能なオプションもあります。

|**十分**|**評価するネットワークコンポーネント**|
|:-----|:-----|
|複数の場所にある回路  <br/> |アクティブ/アクティブな方法で構成された、少なくととして2つの回線を構成することをお勧めします。  <br/> コスト、待機時間、および帯域幅のニーズを比較する必要があります。  <br/> BGP route のコスト、PAC ファイル、および NAT を使用して、複数の回線を使用したルーティングを管理します。  <br/> |
|ExpressRoute サーキットを使用しない場所からのルーティング  <br/> |Office 365 の要求を開始するユーザーの近くに、出口と DNS 解決をお勧めします。  <br/> DNS 転送を使用して、リモートオフィスが適切なエンドポイントを検出できるようにすることができます。  <br/> リモートオフィスのクライアントは、ExpressRoute 回線へのアクセスを提供するルートを使用できる必要があります。  <br/> |
|小規模オフィスの統合  <br/> |使用可能な帯域幅とデータの使用状況を慎重に比較する必要があります。  <br/> |

> [!NOTE]
> Microsoft は、物理的な場所に関係なくルートを使用できる場合は、インターネット経由で ExpressRoute を優先します。
  
それぞれの一意のネットワークについて、これらの考慮事項を考慮する必要があります。 次に例を示します。
  
### <a name="example-2-multi-geographic-locations"></a>例 2: 複数地域の場所
  
この例は、複数の地理的な場所を持つ Humongous 保険という架空の会社のシナリオを示しています。
  
Humongous の保険は、世界中のオフィスと地理的に分散しています。 Office 365 用の Azure ExpressRoute を実装して、大部分の Office 365 トラフィックを直接ネットワーク接続に保持したいとします。 Humongous の保険には、2つの大陸に事務所もあります。 ExpressRoute が実現できないリモートオフィスの従業員は、ExpressRoute 接続を使用するためにプライマリ機能の1つまたは両方にもう一度ルーティングする必要があります。
  
指針として、Office 365 で送信されたトラフィックを可能な限り迅速に Microsoft データセンターに取得することがあります。 この例では、Humongous の保険を使用して、遠隔地のオフィスがインターネットを介して接続されているかどうかを判断し、可能な限り迅速に Microsoft データセンターに接続するか、またはリモートオフィスが内部ネットワークを経由して、ExpressRoute 接続を介して Microsoft データセンターにすばやく到達できるようにする必要があります。
  
Microsoft のデータセンター、ネットワーク、およびアプリケーションアーキテクチャは、世界的に異なる方法で通信し、それらを最も効率的な方法で処理するように設計されています。 これは、世界最大規模のネットワークの1つです。 必要以上に長期間お客様のネットワーク上に残っている Office 365 宛ての要求では、このアーキテクチャを利用することはできません。
  
Humongous 保険の状況では、ExpressRoute で使用する予定のアプリケーションに応じて、これらの手順を続行する必要があります。 たとえば、Skype for business Online のお客様、または外部の Skype for Business Online 会議に接続する際に ExpressRoute 接続を活用することを計画している場合、Skype for Business Online メディア品質およびネットワーク接続ガイドで推奨される設計は、3番目の場所に対して追加の ExpressRoute 回路をプロビジョニングすることです。 これは、ネットワークの観点から見ると、より高価になることがあります。ただし、Microsoft データセンターへの配信前に、ある大陸から別の大陸への要求をルーティングすると、Skype for Business Online の会議やコミュニケーション時に、低品質または使用不能な状態になる可能性があります。
  
Humongous 保険を使用していないか、または Skype for Business Online の利用を計画していない場合は、ExpressRoute 接続を使用している大陸に対して Office 365 の送信ネットワークトラフィックを戻すことができる場合があります。これにより、不要な遅延や TCP 輻輳が発生する可能性があります。 どちらの場合も、Office 365 が依存しているコンテンツ配信ネットワークを利用するには、ローカルサイトでインターネットへのインターネット宛てのトラフィックをルーティングすることをお勧めします。
  
![ExpressRoute 複数地域](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Humongous 保険で複数地域戦略を計画している場合は、サーキットのサイズ、回線数、フェールオーバーなどについて考慮する必要がある事項がいくつかあります。
  
ExpressRoute を複数の地域が回線を使用して1か所に配置している場合、Humongous 保険は、リモートオフィスからの Office 365 への接続が、本社と本社のオフィスの365データセンターに送信されるようにしたいと考えています。 そのためには、Humongous 保険は DNS 転送を実装して、本社のインターネット出口ポイントに最も近い Office 365 環境との適切な接続を確立するために必要なラウンドトリップと DNS 参照の数を減らします。 これにより、クライアントがローカルフロントエンドサーバーを解決しないようにし、ユーザーが接続するフロントエンドサーバーが、Humongous 保険が Microsoft とピアリングされている本社の近くにあるようにします。 [ドメイン名に条件付きフォワーダーを割り当てる](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx)方法についても学習できます。
  
このシナリオでは、リモートオフィスからのトラフィックは、北アメリカの Office 365 フロントエンドインフラストラクチャを解決し、office 365 を利用して、office 365 アプリケーションのアーキテクチャに従ってバックエンドサーバーに接続します。 たとえば、Exchange Online は北米で接続を終了し、そのフロントエンドサーバーは、テナントが存在する場所でバックエンドメールボックスサーバーに接続します。 すべてのサービスには、ユニキャストとエニーキャストの宛先で構成される、広く分散されたフロントドアサービスがあります。
  
Humongous に複数の大陸の主要なオフィスがある場合は、Skype for Business Online などの機密性の高いアプリケーションの待機時間を減らすために、少なくとも2つのアクティブ/アクティブ回路を地域ごとに使用することをお勧めします。 すべてのオフィスが1つの大陸に含まれている場合、またはリアルタイムコラボレーションを使用していない場合は、統合または分散された出口があります。 複数の回線が使用可能な場合、BGP ルーティングによって、1つの回線が利用できなくなった場合にフェールオーバーが行われます。
  
サンプルの[ルーティング構成](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/)との詳細について説明し [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/) ます。
  
## <a name="selective-routing-with-expressroute"></a>ExpressRoute での選択ルーティング

テストなどのさまざまな理由で、ExpressRoute での選択ルーティングが必要になることがあります。これは、ユーザーのサブセットに ExpressRoute をロールアウトするためです。 さまざまなツールを使用して、ExpressRoute で Office 365 ネットワークトラフィックを選択的にルーティングすることができます。
  
1. **Route filtering/分掌**-BGP 経由で ExpressRoute を Office 365 に転送できるようにして、ExpressRoute をサブネットまたはルーターのサブセットにします。 これは、顧客のネットワークセグメントまたは物理的なオフィスの場所によって選択的にルーティングされます。 これは、Office 365 用の ExpressRoute のロールアウトを調整するための一般的な方法であり、BGP デバイス上に構成されています。

2. **PAC ファイル/url** -特定の fqdn が特定のパスでルーティングされるように、Office 365 に指定されたネットワークトラフィックを指示します。 これは、 [PAC ファイルの展開](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)によって識別されるクライアントコンピューターで選択的にルーティングされます。

3. **ルートフィルター**  - [ルートフィルター](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)は、Microsoft ピア経由でサポートされているサービスのサブセットを使用する方法です。

4. **Bgp コミュニティ**- [bgp community タグ](https://aka.ms/bgpexpressroute365)に基づくフィルタリングを使用すると、ExpressRoute をスキャンする Office 365 アプリケーションを特定し、それをインターネットでスキャンすることができます。

ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>関連項目

[Office 365 のネットワーク接続の評価](assessing-network-connectivity.md)
  
[Office 365 向け Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)
  
[Office 365 向け ExpressRoute でのネットワーク計画](network-planning-with-expressroute.md)
  
[Office 365 向け ExpressRoute の実装](implementing-expressroute.md)
  
[Skype for Business Online でのメディア品質とネットワーク接続のパフォーマンス](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype for Business Online 向けのネットワークの最適化](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype for Business Online での ExpressRoute および QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute を使用したコール フロー](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 シナリオで ExpressRoute の BGP コミュニティを使用する](bgp-communities-in-expressroute.md)
  
[ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)
  
[Office 365 のパフォーマンスに関するトラブルシューティングの計画](performance-troubleshooting-plan.md)
  
[Office 365 の URL および IP アドレスの範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 のネットワークとパフォーマンスのチューニング](network-planning-and-performance.md)
