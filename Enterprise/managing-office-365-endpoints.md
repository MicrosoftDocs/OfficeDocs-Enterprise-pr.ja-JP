---
title: Office 365 エンドポイントの管理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/22/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 一部のエンタープライズ ネットワークは、汎用のインターネット上の場所へのアクセスを制限またはかなり backhaul ネットワーク トラフィックの処理など。確認するのには、Office 365 にアクセスできる、ネットワークとプロキシの管理者は、Fqdn では、Url のリストを管理する必要があります、および IP アドレスなどのネットワーク上のコンピューターは、Office 365 エンドポイントの一覧を構成します。これらの必要性の直接ルート、プロキシ バイ パス、およびファイアウォール規則とネットワーク要求は、Office 365 にアクセスできないことを確認するのには、PAC ファイルに追加するには。
ms.openlocfilehash: 480d2fa1b55507187f9150d02907849178a451b5
ms.sourcegitcommit: d93f7a51e8cdefdfc9933cdf1f9e413b013bb367
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "25719021"
---
# <a name="managing-office-365-endpoints"></a>Office 365 エンドポイントの管理

複数のオフィスと WAN 接続を持つほとんどの企業は、Office 365 のネットワーク接続の構成を必要とする必要があります。すべての信頼されたファイアウォールを使用して直接 Office 365 のネットワーク要求を送信する、すべての他のパケット レベルの検査をバイパスする処理では、ネットワークを最適化できます。これにより、遅延時間と、境界領域の容量要件が削減されます。ユーザーのための最適なパフォーマンスを提供する最初の手順は、Office 365 のネットワーク トラフィックを識別します。Office 365 のネットワーク接続の詳細については、 [Office 365 のネットワーク接続性の原則](office-365-network-connectivity-principles.md)を参照してください。

Office 365 のネットワークの端点とそれらを使用して[Office 365 の IP アドレスと Web サービスの URL](office-365-ip-web-service.md)への変更にアクセスするをお勧めします。

重要な Office 365 のネットワーク トラフィックを管理する方法に関係なく Office 365 には、インターネット接続が必要です。他のネットワーク エンドポイントの接続が必要な場所は、 [Office 365 の IP アドレスおよび URL の Web サービスに含まれないその他のエンドポイント](additional-office365-ip-addresses-and-urls.md)に表示されます。

Office 365 のネットワーク エンドポイントを使用する方法は、エンタープライズ組織のネットワーク アーキテクチャによって異なります。この資料では、エンタープライズ ネットワーク アーキテクチャは、Office 365 の IP アドレスや Url と統合可能ないくつかの方法を説明します。ネットワークを信頼するように要求を選択する最も簡単な方法では、各オフィスの所在地、自動的に Office 365 構成をサポートする SDWAN デバイスを使用します。 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>重要な Office 365 のネットワーク トラフィックをローカルの分岐出口の SDWAN

各ブランチ オフィスの場所では、エンドポイント、または最適化のカテゴリを Office 365 の最適化のトラフィックをルーティングし、マイクロソフトのネットワークに直接、カテゴリを許可するように構成された SDWAN のデバイスを使用できます。大幅なネットワーク境界がある別の場所には、オンプレミス データ センターのトラフィック、一般的なインターネット web サイトのトラフィック、およびカテゴリの Office 365 の既定のエンドポイントへのトラフィックを含む他のネットワーク トラフィックが送信されます。

マイクロソフトは自動構成を有効にする SDWAN のプロバイダーと協力します。詳細については、 [Office 365 のパートナー ネットワークのプログラム](office-365-networking-partner-program.md)を参照してください。

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>PAC ファイルを使用して、Office 365 の重要なトラフィックの直接のルーティングについて

WPAD PAC ファイルを使用すると、ネットワーク要求を Office 365 に関連付けられているが、IP アドレスがないを管理できます。プロキシまたは境界デバイス経由で送信される一般的なネットワーク要求の遅延が増加します。SSL を解除し、検査は、最大待機時間を作成するときにその他のサービスなど、パフォーマンスが低下し、不正なユーザー エクスペリエンス プロキシの認証や評価の参照が発生することができます。さらに、これらの境界ネットワーク デバイスには、すべてのネットワーク接続要求を処理するために十分な容量が必要があります。Office 365 のネットワーク要求を渡すため、プロキシや検査のデバイスをバイパスすることをお勧めします。
  
[PowerShell ギャラリー Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile)は、Office 365 の IP アドレスおよび URL の Web サービスから最新のネットワーク エンドポイントを読み取るし、PAC ファイルのサンプルを作成する PowerShell スクリプトです。既存の PAC ファイルの管理を統合できるようにスクリプトを変更することができます。 

![ファイアウォールやプロキシ経由で Office 365 に接続します。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**図 1 - 単純な企業ネットワークのペリメータ**

PAC ファイルは、図 1 の 1 の時点で web ブラウザーに配置されます。重要な Office 365 のネットワーク トラフィックの直接の出口の PAC ファイルを使用している場合は、ネットワーク境界部のファイアウォールでこれらの Url の背後にある IP アドレスへの接続を許可する必要があります。これには、同じ Office 365 エンドポイント内のカテゴリとして指定した PAC ファイルの IP アドレスの取得をし、これらのアドレスに基づいて、ファイアウォールの Acl を作成します。図 1 では、ポイント 3 はファイアウォールです。 

別にする場合は直接のみ最適化カテゴリのエンドポイントをプロキシ サーバーに送信するカテゴリのエンドポイントはこれ以上の処理をバイパスするプロキシ サーバーに登録する必要があります、必要な許可用のルーティングします。たとえば、SSL の区切りと検査およびプロキシ認証と互換性がない最適化および許可の両方のカテゴリのエンドポイントです。プロキシ サーバーは、図 1 の 2 のポイントです。

一般的な構成では、プロキシ サーバーをヒットする Office 365 のネットワーク トラフィックの宛先 IP アドレスにはプロキシ サーバーからのすべての送信トラフィックを処理せずに許可します。SSL を解除し、検査の問題について[を使用するサードパーティ製のネットワーク デバイス、または Office 365 のトラフィックのソリューション](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)を参照してください。

Get PacFile スクリプトを生成する PAC ファイルの 2 種類があります。

|**種類**|**説明**|
|:-----|:-----|
|**1** <br/> |エンドポイントのトラフィックの直接の最適化、およびその他すべてをプロキシ サーバーに送信します。 <br/> |
|**2** <br/> |直接的な最適化および許可のエンドポイントのトラフィック、およびその他すべてをプロキシ サーバーに送信します。このタイプは、ExpressRoute のネットワーク セグメントへのトラフィックを Office 365 は、プロキシ サーバーにすべての ExpressRoute がサポートされているすべての送信にも使用できます。 <br/> |

PowerShell スクリプトを呼び出すための簡単な例を以下に示します。

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

いくつかのパラメーターをスクリプトに渡すことができます。

|**パラメーター**|**説明**|
|:-----|:-----|
|**ClientRequestId** <br/> |これは、必要とは、呼び出し元のクライアント マシンを表す web サービスに渡される GUID です。 <br/> |
|**Instance** <br/> |世界の検索サイトにデフォルト設定されている Office 365 のサービス インスタンスです。Web サービスに渡されます。 <br/> |
|**TenantName** <br/> |Office 365 テナントの名前です。Web サービスに渡され、いくつかの Office 365 の Url で置き換え可能パラメーターとして使用します。 <br/> |
|**種類** <br/> |生成するプロキシの PAC ファイルの種類。 <br/> |

追加のパラメーターを PowerShell スクリプトを呼び出すための別の例です。

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>プロキシ サーバーは、Office 365 のネットワーク トラフィックの処理をバイパスします。 

送信トラフィックの直接の PAC ファイルが使用できない場合か、プロキシ サーバーを構成することによって、ネットワーク境界部での処理をバイパスします。いくつかのプロキシ サーバーの製造元は、 [Office 365 のパートナー ネットワークのプログラム](office-365-networking-partner-program.md)の説明に従って、これを自動的に構成を有効にしています。 

これを手動で行う場合は、最適化を取得してから Office 365 の IP アドレスと URL の Web サービス エンドポイントのカテゴリのデータを許可してこれらの処理をバイパスするプロキシ サーバーを構成する必要があります。最適化の SSL を解除し、検査とプロキシの認証を回避し、カテゴリの端点が重要です。 
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Office 365 の IP アドレスや Url の変更管理

だけでなく、ネットワーク境界部の適切な構成を選択すると、Office 365 エンドポイントの変更管理プロセスを採用することが重要です。これらのエンドポイントを定期的に変更し、でブロックされているユーザー終了することができます、変更を管理しない場合、またはアドレスまたは URL の追加で新しい ip アドレスの後のパフォーマンスが低下します。 

Office 365 の IP アドレスおよび Url の変更は通常、各月の最終日近く公開します。変更は、その運用のためのスケジュール、サポート、またはセキュリティの要件以外で公開されます。

IP アドレスまたは URL が追加されたために動作する必要がある変更が公開されたら、そのエンドポイントが、Office 365 サービスに変更を公開してから 30 日間の通知を受け取ることが予想されます。この通知期間の開発を目指して、ある可能性がありますいない常に運用が可能なサポート、またはセキュリティ要件。変更など、接続を維持するために即時の操作を必要としない IP アドレスまたは Url を削除するか、大幅な変更は、以下 [事前通知します。どのような通知を提供するに関係なく必要なサービスの有効日を変更するたびにリストします。

### <a name="change-notification-using-the-web-service"></a>Web サービスを使用して変更通知

Office 365 の IP アドレスと Web サービスの URL を使用するには、変更通知を取得します。メソッドを呼び出すと **/version** web 1 時間に一度 Office 365 への接続を使用しているエンドポイントのバージョンを確認することをお勧めします。使用されているバージョンと比較するときにこのバージョンが変更された場合する必要があります **/endpoints**の web メソッドから最新のエンドポイントのデータを取得し、必要に応じて **/changes**の web メソッドからの相違点を取得します。**/Endpoints**または **/changes** web メソッドを呼び出しますが、バージョンが見つかった場合に何らかの変更されていない場合する必要はありません。 

詳細については、 [Office 365 の IP アドレスと Web サービスの URL](office-365-ip-web-service.md)を参照してください。

### <a name="change-notification-using-rss-feeds"></a>RSS フィードを使用して変更通知

Office 365 の IP アドレスと Web サービスの URL は、Outlook で購読する RSS フィードを提供します。各 IP アドレスを Office 365 サービスのインスタンス固有のページの RSS の Url や Url へのリンクがあります。詳細については、 [Office 365 の IP アドレスと Web サービスの URL](office-365-ip-web-service.md)を参照してください。

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>変更通知と承認は、マイクロソフトのフローを使用してを確認します。

私たちを理解する 1 か月で得られるネットワーク エンドポイントの変更の手動処理を要求することも可能性があります。マイクロソフトのフローを使用するには電子メールで通知して、Office 365 のネットワーク エンドポイントが行った変更と、必要に応じて変更の承認プロセスを実行するフローを作成します。レビューを完了すると、ファイアウォールとプロキシ サーバーの管理チームへの変更を自動的にメール フローを持つことができます。 

マイクロソフトのフローのサンプルとテンプレートについては、 [Office 365 の IP アドレスや Url の変更に電子メールを受信するのには使用して Microsoft のフロー](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)を参照してください。
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 のネットワーク エンドポイントに関する FAQ

Office 365 の接続性に関する管理者のよく寄せられる質問:
  
### <a name="how-do-i-submit-a-question"></a>質問を送信する方法は?

か、記事が役に立ちましたかどうかを示すために下部にあるリンクをクリックし、新たな質問を送信します。私たちは、フィードバックを監視し、最も頻繁に寄せられる質問をここで更新します。
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>自分のテナントの場所を確認する方法はありますか

 **テナントの場所**は、当社の[データ センターのマップ](http://aka.ms/datamaps)を使用して最適な決定されます。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Am にピアリング適切にマイクロソフトのでしょうか。

 **Peering の場所**については、[マイクロソフトとピアリング](https://www.microsoft.com/peering)で詳細に説明します。
  
2500 以上の ISP のピアリング関係を持つグローバルなプレゼンス、70 ポイントへのネットワークから取得する必要がありますシームレスです。ISP のピアリング関係では、最適です[ここでいくつかの例では](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)良好ではだめですねピアリングのやり取りに当社のネットワークのことを確認する数分を費やすのも悪くないことはできません。 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>発行済みの一覧にない IP アドレスへのネットワーク要求を表示すると、必要へのアクセスを提供するでしょうか。
<a name="bkmk_MissingIP"> </a>

のみ IP アドレスを提供する Office 365 サーバーに直接ルーティングする必要があります。すべての IP アドレスのネットワーク要求が表示されますの包括的なリストではありません。Microsoft およびサード ・ パーティ製の所有している、パブリッシュされていない場合、IP アドレスへのネットワーク要求が表示されます。これらの IP アドレスが動的に生成されるかを変更するときに、タイムリーな通知を防止する方法で管理します。場合は、ファイアウォールでは、これらのネットワーク要求の Fqdn に基づいてアクセスを許可することはできません、要求を管理するために、PAC または WPAD ファイルを使用します。
  
IP は、Office 365 の詳細情報を表示するに関連付けられているを参照してください。
  
1. [CIDR の電卓](http://jodies.de/ipcalc)を使用して大規模な公開されている範囲の IP アドレスが含まれているかどうかを確認してください。
2. パートナーが[whois クエリ](https://dnsquery.org/)を使用して ip アドレスを所有しているかどうかを参照してください。マイクロソフトが所有している場合は、内部の相手がある可能性があります。
3. 証明書をチェックし、IP アドレスへの接続をブラウザーで*HTTPS://\<と\>*、IP アドレスに関連付けられているどのようなドメインを理解する証明書に記載されているドメインを確認します。場合 IP アドレスを所有している Microsoft は、Office 365 の IP アドレスの一覧ではなく可能性があります IP アドレスは、公開されている IP 情報を使用しないで Microsoft ドメインまたは*MSOCDN.NET*などの Microsoft CDN に関連付けられます。証明書のドメインは、いずれかの IP アドレスの一覧を表示する要求は、行う場合は、知らせてください。

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Nsatc.net や akadns.net では、マイクロソフトのドメイン名などの名前を参照してください理由は?
<a name="bkmk_akamai"> </a>

Office 365 とその他の Microsoft サービスは、Office 365 のエクスペリエンスを向上させるために akamai 社、MarkMonitor などのいくつかのサードパーティのサービスを使用します。最高のエクスペリエンスを提供してください、可能な場合があります変更これらのサービス、将来的にします。操作中に、サード パーティのドメインを所有している、レコード、または IP アドレスを指す CNAME レコード多くの場合発行されます。サード パーティのドメインが、CDN などのコンテンツをホストまたは地理的なトラフィック管理サービスなどのサービスをホストすることがあります。これらのサード パーティへの接続が表示されたら、これらはリダイレクトまたは参照は、最初の要求で、クライアントからではないのです。一部のお客様がこのフォームを参照のことを確認する必要があり、潜在的な Fqdn でサード パーティのサービスの長いリストを使用して可能性がありますを明示的に追加せずにリダイレクトを許可します。
  
サービスの一覧は、いつでも変更されることがします。現在使用中のサービスの一部は次のとおりです。
  
含む要求が表示されたら、 [MarkMonitor](https://www.markmonitor.com/)を使用中は*\*です。 nsatc.net* 。このサービスは、ドメイン名の保護、悪意のある行為から保護するための監視を提供します。
  
要求が表示されたら、 [ExactTarget](https://www.marketingcloud.com/)を使用中は*\*です。 exacttarget.com* 。このサービスは、電子メールのリンクの管理し、悪意のある行為に対する監視を提供します。
  
[Akamai 社](https://www.akamai.com/)は、Fqdn を次のいずれかを含む要求が表示された場合、使用中です。このサービスでは、geo DNS、コンテンツ配信ネットワーク サービスを提供します。
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Office 365 の使用可能な最小の接続が必須であります。
<a name="bkmk_thirdparty"> </a>

Office 365 は、一連のサービスをインターネット経由で機能するように構築、使用可能な多くの標準的なインターネット サービスに基づく信頼性と可用性の約束です。などの DNS、CRL、および Cdn などの標準のインターネット サービスは、最近のほとんどのインターネット サービスを使用して到達できる必要があると同様に、Office 365 を使用するのには到達可能でなければなりません。

Office 365 製品ファミリは、主要なサービス エリアに分割します。これらが選択的に有効にする接続とすべての依存関係は、常に必要な一般的な領域があります。

|**サービス エリア**|**説明**|
|:-----|:-----|
|**Exchange** <br/> |オンラインの Exchange および Exchange のオンライン保護 <br/> |
|**SharePoint** <br/> |SharePoint Online と OneDrive for Business <br/> |
|**Skype** <br/> |Skype ビジネスおよびマイクロソフトのチーム <br/> |
|**共通** <br/> |Office 365 Pro と、Office オンライン、Azure AD やその他の一般的なネットワーク ・ エンドポイント <br/> |

基本的なインターネットのサービス、機能を統合するためにのみ使用されるサードパーティ製のサービスがあります。これらが統合に必要なときに、サービスのコア機能は、エンドポイントがアクセス可能でない場合で機能しますが、Office 365 エンドポイントの資料では省略可能としてマークしています。必要なすべてのネットワーク エンドポイントが必要な属性が true に設定します。省略可能なすべてのネットワーク エンドポイントは必須の属性が false に設定があり、ノートの属性は接続がブロックされているかどうかを想定する必要があります不足している機能の詳細を。
  
Office 365 を使用しようとするいるし、サードパーティのサービスにアクセスできない検索が[必須であるか、またはこの資料では省略可能にマークされているすべての Fqdn はプロキシとファイアウォールを通過できる](urls-and-ip-address-ranges.md)ことを確認します。
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>マイクロソフトのコンシューマー サービスへのアクセスをブロックする方法は?
<a name="bkmk_consumer"> </a>

自己の責任において、消費者サービスへのアクセス制限を行う必要があります、コンシューマー サービスをブロックする唯一確実な方法は、 *login.live.com* FQDN へのアクセスを制限します。この FQDN は、MSDN、TechNet、およびその他のユーザーなどの非消費者サービスなどのサービスの広範なセットで使用されます。この FQDN へのアクセスを制限するもこれらのサービスに関連付けられているネットワークの要求のルールの例外を含める必要がある可能性があります。
  
Exfiltrate については、Office 365 テナントまたはその他のサービスを使用するネットワーク上の他のユーザーの Microsoft コンシューマー サービスだけにアクセスをブロックしない機能しないように注意してください。
  
## <a name="related-topics"></a>関連項目

[Office 365 IP アドレスと URL の Web サービス ](office-365-ip-web-service.md)

[Microsoft Azure データ センターの IP 範囲](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft パブリック IP スペース](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune のネットワーク インフラストラクチャの要件](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[電源の BI および ExpressRoute](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 の URL と IP アドレスの範囲](urls-and-ip-address-ranges.md)
  
[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)
  
[Office 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)
