---
title: Office 365 エンドポイントの管理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/11/2019
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
description: 一部のエンタープライズネットワークは、一般的なインターネットの場所へのアクセスを制限するか、またはネットワークトラフィックの処理を大幅に行います。このようなネットワーク上のコンピューターが office 365 にアクセスできるようにするには、ネットワークおよびプロキシ管理者が、office 365 エンドポイントの一覧を構成する fqdn、url、IP アドレスの一覧を管理する必要があります。ネットワーク要求が Office 365 に到達できるようにするには、これらのルールを直接ルート、プロキシバイパス、またはファイアウォールルールおよび PAC ファイルに追加する必要があります。
ms.openlocfilehash: ed3a64ad3cd840987d105ae99a5ba5cbf41567e9
ms.sourcegitcommit: a8aedcfe0d6a6047a622fb3f68278c81c1e413bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "30053001"
---
# <a name="managing-office-365-endpoints"></a>Office 365 エンドポイントの管理

複数のオフィスの場所を持ち、WAN を接続する多くの企業組織では、office 365 のネットワーク接続の構成が必要です。すべての信頼された Office 365 ネットワーク要求をファイアウォール経由で直接送信することにより、ネットワークを最適化することができます。これには、追加のすべてのパケットレベルの検査または処理を省略しますこれにより、遅延と境界容量の要件が減少します。Office 365 のネットワークトラフィックを特定することは、ユーザーに最適なパフォーマンスを提供するための最初の手順です。office 365 のネットワーク接続の詳細については、「 [office 365 のネットワーク接続の原則](office-365-network-connectivity-principles.md)」を参照してください。

office 365 ネットワークエンドポイントにアクセスして、 [office 365 の IP アドレスと URL Web サービス](office-365-ip-web-service.md)を使用して変更することをお勧めします。

office 365 の重要なネットワークトラフィックを管理する方法に関係なく、office 365 ではインターネット接続が必要です。接続が必要なその他のネットワークエンドポイントは[、Office 365 の IP アドレスと URL Web サービスに含まれていない追加のエンドポイント](additional-office365-ip-addresses-and-urls.md)に一覧表示されます。

Office 365 のネットワークエンドポイントの使用方法は、エンタープライズ組織のネットワークアーキテクチャによって異なります。この記事では、エンタープライズネットワークアーキテクチャが Office 365 の IP アドレスと url と統合できるいくつかの方法について説明します。信頼するネットワーク要求を選択する最も簡単な方法は、各オフィスの場所で自動 Office 365 構成をサポートする sdwan デバイスを使用することです。 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>重要な Office 365 ネットワークトラフィックのローカルブランチ出口の sdwan

各支社の場所には、office 365 の [エンドポイントの最適化] カテゴリのトラフィックをルーティングするように構成された sdwan デバイス、または Microsoft のネットワークに直接カテゴリを最適化して許可することができます。オンプレミスのデータセンタートラフィック、一般的なインターネット web サイトトラフィック、および Office 365 へのトラフィックを含むその他のネットワークトラフィックには、より大きなネットワーク境界を持つ別の場所に送信されます。

Microsoft は、自動構成を有効にするために sdwan プロバイダーと協力しています。詳細については、「 [Office 365 のネットワーキングパートナープログラム](office-365-networking-partner-program.md)」を参照してください。

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>重要な Office 365 トラフィックの直接ルーティングに PAC ファイルを使用する

PAC または WPAD ファイルを使用して、Office 365 に関連付けられているが IP アドレスを持っていないネットワーク要求を管理します。プロキシまたは境界デバイス経由で送信される一般的なネットワーク要求は、待機時間が増加します。SSL ブレークと調査によって最大の待機時間が作成されますが、プロキシ認証や評価の参照などのサービスによって、パフォーマンスが低下し、ユーザーの作業が正しくない可能性があります。さらに、これらの境界ネットワークデバイスには、すべてのネットワーク接続要求を処理するのに十分な容量が必要です。ダイレクト Office 365 のネットワーク要求には、プロキシまたは検査デバイスをバイパスすることをお勧めします。
  
[powershell Gallery の Get-pacfile](https://www.powershellgallery.com/packages/Get-PacFile)は powershell スクリプトで、Office 365 の IP アドレスと URL Web サービスから最新のネットワークエンドポイントを読み取り、サンプル PAC ファイルを作成します。スクリプトを変更して、既存の PAC ファイル管理と統合できるようにすることができます。 

![ファイアウォールとプロキシを介して Office 365 に接続します。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**図 1-単純なエンタープライズネットワーク境界**

PAC ファイルは、図1のポイント1の web ブラウザーに展開されます。重要な Office 365 ネットワークトラフィックの直接出口に PAC ファイルを使用する場合は、ネットワーク境界ファイアウォール上のこれらの url の背後にある IP アドレスへの接続も許可する必要があります。これは、PAC ファイルで指定されているものと同じ Office 365 エンドポイントカテゴリの IP アドレスを取得し、それらのアドレスに基づいてファイアウォール acl を作成することによって行われます。ファイアウォールは図1のポイント3です。 

別の方法として、最適化カテゴリエンドポイントに対して直接ルーティングのみを選択した場合は、プロキシサーバーに送信する必要のある許可カテゴリエンドポイントがプロキシサーバーに表示され、それ以降の処理をバイパスする必要があります。たとえば、SSL ブレーク、検査、プロキシ認証は、[最適化] および [許可] カテゴリエンドポイントと互換性がありません。プロキシサーバーは図1のポイント2です。

一般的な構成では、プロキシサーバーにヒットする Office 365 ネットワークトラフィックの宛先 IP アドレスについて、プロキシサーバーからのすべての送信トラフィックを処理することなく許可されます。SSL ブレークおよび検査に関する問題の詳細については、「 [Office 365 でサードパーティ製のネットワークデバイスまたはソリューションを使用する](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)」を参照してください。

pacfile スクリプトによって生成される PAC ファイルには、次の2種類があります。

|**型**|**説明**|
|:-----|:-----|
|**1** <br/> |プロキシサーバーに対して、最適化エンドポイントトラフィックの直接送信およびその他すべてを送信します。 <br/> |
|**2** <br/> |[最適化] および [エンドポイントのトラフィックを直接送信する] およびその他のすべてのプロキシサーバーを送信します。この型を使用して、Office 365 トラフィックに対してサポートされているすべての expressroute を expressroute ネットワークセグメントに、その他すべてをプロキシサーバーに送信することもできます。 <br/> |

次に、PowerShell スクリプトを呼び出す簡単な例を示します。

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

スクリプトに渡すことのできるパラメーターはいくつかあります。

|**パラメーター**|**説明**|
|:-----|:-----|
|**ClientRequestId** <br/> |これは必須であり、呼び出しを行うクライアントコンピューターを表す web サービスに渡される GUID です。 <br/> |
|**Instance** <br/> |既定では、Office 365 service インスタンスが世界に設定されています。web サービスにも渡されます。 <br/> |
|**TenantName** <br/> |Office 365 テナント名。web サービスに渡され、一部の Office 365 の url で置き換え可能なパラメーターとして使用されます。 <br/> |
|**型** <br/> |生成するプロキシ PAC ファイルの種類。 <br/> |

追加のパラメーターを使用して PowerShell スクリプトを呼び出す別の例を次に示します。

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Office 365 ネットワークトラフィックのプロキシサーバーのバイパス処理 

PAC ファイルが直接送信トラフィックに使用されていない場合でも、プロキシサーバーを構成してネットワーク境界での処理をバイパスする必要があります。プロキシサーバーのベンダーによっては、 [Office 365 ネットワークパートナープログラム](office-365-networking-partner-program.md)で説明されているように、この機能の自動構成が有効になっている場合があります。 

これを手動で実行する場合は、Office 365 の IP アドレスと URL Web サービスから、[最適化] と [エンドポイントのカテゴリ] データを取得し、これらの処理をバイパスするようにプロキシサーバーを構成する必要があります。SSL ブレークを回避し、カテゴリエンドポイントの最適化と許可の認証とプロキシ認証を行うことが重要です。 
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Office 365 の IP アドレスおよび url の変更管理

ネットワーク境界に適切な構成を選択することに加えて、Office 365 エンドポイントの変更管理プロセスを採用することが重要です。これらのエンドポイントは定期的に変更され、変更を管理していない場合は、新しい IP アドレスまたは URL が追加された後にユーザーがブロックされたり、パフォーマンスが低下したりする可能性があります。 

Office 365 の IP アドレスと url への変更は、通常、毎月の最終日付近に公開されます。運用、サポート、またはセキュリティ要件によって、そのスケジュールの外部で変更が公開されることがあります。

IP アドレスまたは URL が追加されたために処理を必要とする変更が公開されている場合は、そのエンドポイントに Office 365 サービスが存在するまで、変更を公開するまでに30日の通知が表示されるはずです。この通知期間を対象としていますが、運用、サポート、またはセキュリティの要件によっては常に可能であるとは限りません。削除された IP アドレスや url、重要な変更の削減など、直ちに接続を維持する必要がない変更には、事前通知は含まれません。通知の種類に関係なく、各変更に対して予想されるサービスのアクティブな日付を一覧表示します。

### <a name="change-notification-using-the-web-service"></a>Web サービスを使用して通知を変更する

Office 365 の IP アドレスと URL Web サービスを使用して、変更通知を取得することができます。Office 365 への接続に使用しているエンドポイントのバージョンを確認するには、 **/version** web メソッドを1時間ごとに呼び出すことをお勧めします。使用しているバージョンと比較してこのバージョンが変更された場合は、 **/エンドポイント**web メソッドから最新のエンドポイントデータを取得し、必要に応じて**変更/変更**web メソッドとの相違点を取得する必要があります。検索したバージョンが変更されていない場合は、/**エンドポイント**または **/変更**web メソッドを呼び出す必要はありません。 

詳細については、「 [Office 365 の IP アドレスと URL Web サービス](office-365-ip-web-service.md)」を参照してください。

### <a name="change-notification-using-rss-feeds"></a>RSS フィードを使用した変更通知

Office 365 の IP アドレスと URL Web サービスには、Outlook で購読できる RSS フィードが用意されています。各 Office 365 サービスインスタンス固有のページに、IP アドレスと url に関する RSS url へのリンクがあります。詳細については、「 [Office 365 の IP アドレスと URL Web サービス](office-365-ip-web-service.md)」を参照してください。

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Microsoft Flow を使用して通知と承認レビューを変更する

各月に発生するネットワークエンドポイントの変更については、手動での処理が必要になる可能性があることを理解しています。Microsoft flow を使用して、電子メールで通知するフローを作成できます。 Office 365 ネットワークエンドポイントが変更されたときに、必要に応じて変更の承認プロセスを実行することもできます。レビューが完了すると、そのフローによって、ファイアウォールとプロキシサーバーの管理チームへの変更が自動的に電子メールで送信されるようになります。 

microsoft flow のサンプルとテンプレートについては、「 [microsoft flow を使用して Office 365 の IP アドレスおよび url の変更に関する電子メールを受信する](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)」を参照してください。
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 ネットワークエンドポイントに関する FAQ

Office 365 の接続に関してよく寄せられる管理者の質問:
  
### <a name="how-do-i-submit-a-question"></a>質問を送信するにはどうすればよいですか?

下部にあるリンクをクリックして、記事が役に立ったかどうかを示し、追加の質問を送信します。フィードバックを監視し、よく寄せられる質問にお答えします。
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>テナントの場所を決定するにはどうすればよいですか?

 **テナントの場所**は、[データセンターマップ](http://aka.ms/datamaps)を使用して決定することをお勧めします。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Microsoft に対して適切にピアリングを行いますか?

 **ピアリングの場所**の詳細については、「 [Microsoft とのピアリング](https://www.microsoft.com/peering)」を参照してください。
  
2500を超える ISP ピアリング関係をグローバルおよび70のプレゼンス状態で使用すると、ネットワークから私たちをシームレスに取得する必要があります。数分で、ISP のピアリング関係が最も最適であることを確認するのには、[次の](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)ようにしておくことができます。これは、良好なピアツーリングのネットワークへの最適な使用例です。 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>IP アドレスへのネットワーク要求が公開されたリストにないことを確認しました。それらへのアクセスを提供する必要がありますか。
<a name="bkmk_MissingIP"> </a>

ここでは、に直接ルーティングする必要がある Office 365 サーバーの IP アドレスのみを提供しています。これは、ネットワーク要求を表示するすべての IP アドレスの包括的なリストではありません。Microsoft およびサードパーティが所有する、公開されていない、IP アドレスへのネットワーク要求が表示されます。これらの IP アドレスは、変更されたときに適切な通知が行われないように動的に生成または管理されます。ファイアウォールがこれらのネットワーク要求の fqdn に基づいてアクセスを許可できない場合は、PAC または WPAD ファイルを使用して要求を管理します。
  
詳細については、「Office 365 に関連付けられている IP について」を参照してください。
  
1. [CIDR 計算機](http://jodies.de/ipcalc)を使用して、IP アドレスがより大きな公開範囲に含まれているかどうかを確認します。
2. パートナーが[whois クエリ](https://dnsquery.org/)を使用して IP を所有しているかどうかを確認します。Microsoft が所有している場合は、内部パートナーである可能性があります。
3. 証明書を確認するブラウザーで*HTTPS://\<\> *を使用して ip アドレスに接続するには、証明書に一覧表示されているドメインを調べて、ip アドレスに関連付けられているドメインを理解します。office 365 の ip アドレスの一覧ではなく、microsoft が所有する ip アドレスである場合は、ip アドレスが*MSOCDN.NET*などの microsoft CDN または公開された ip 情報を持たない別の microsoft ドメインに関連付けられている可能性があります。証明書に記載されているドメインが、IP アドレスの一覧を取得することを要求している場合は、お知らせください。

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>nsatc.net や akadns.net などの名前が Microsoft ドメイン名に表示されるのはなぜですか?
<a name="bkmk_akamai"> </a>

office 365 およびその他の Microsoft サービスでは、office 365 の動作を向上させるために、akamai や markmonitor などのサードパーティ製のサービスをいくつか使用します。最高の経験を常に提供できるように、今後これらのサービスを変更することがあります。そのため、多くの場合、所有しているサードパーティのドメイン、レコード、または IP アドレスを指す CNAME レコードを公開します。サードパーティのドメインは、CDN などのコンテンツをホストしたり、地理的トラフィック管理サービスなどのサービスをホストしたりすることができます。これらのサードパーティとの接続が表示されている場合、クライアントからの最初の要求ではなく、リダイレクトまたは紹介の形式になっています。お客様によっては、潜在的な fqdn サードパーティのサービスで使用される可能性のある長いリストを明示的に追加せずに、この形式の紹介とリダイレクトを確実に通過できるようにする必要があります。
  
サービスの一覧は、いつでも変更される可能性があります。現在使用中のサービスには、次のようなものがあります。
  
* \*nsatc.net*を含む要求を表示するときに、 [markmonitor](https://www.markmonitor.com/)が使用されています。このサービスは、悪意のある動作から保護するためのドメイン名の保護と監視を提供します。
  
[](https://www.marketingcloud.com/) exacttarget.com へ* \** の要求が表示されている場合は、ExactTarget が使用されています。このサービスは、悪意のある動作からの電子メールリンクの管理と監視を提供します。
  
次の fqdn のいずれかを含む要求がある場合は、 [akamai](https://www.akamai.com/)が使用されています。このサービスは、geo DNS およびコンテンツ配信ネットワークサービスを提供します。
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Office 365 で最低限の接続を可能にする必要があります。
<a name="bkmk_thirdparty"> </a>

Office 365 は、インターネット上で機能するように構築された一連のサービスで、信頼性と可用性の約束は、利用可能な多くの標準インターネットサービスに基づいています。たとえば、DNS、CRL、および cdns などの標準インターネットサービスは、最新のインターネットサービスを使用するためにアクセスできるようにするために、Office 365 を使用するために到達可能である必要があります。

Office 365 スイートは、主なサービス領域に分割されています。接続に対して選択的に有効にすることができます。また、すべてのに依存する共通領域があり、常に必須です。

|**サービスエリア**|**説明**|
|:-----|:-----|
|**Exchange** <br/> |exchange online および exchange online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online と OneDrive for Business <br/> |
|**Skype for Business Online および Microsoft Teams** <br/> |Skype for business と Microsoft Teams <br/> |
|**一般的な** <br/> |office 365 Pro Plus、office Online、Azure AD、その他の一般的なネットワークエンドポイント <br/> |

基本的なインターネットサービスに加えて、機能の統合にのみ使用されるサードパーティのサービスがあります。これらは統合のために必要ですが、Office 365 エンドポイントの記事ではオプションとしてマークされていますが、エンドポイントにアクセスできない場合にもサービスのコア機能が引き続き機能することを意味します。必要なネットワークエンドポイントには、必須属性が true に設定されます。任意のネットワークエンドポイント (省略可能) には、必須属性が false に設定され、notes 属性には、接続がブロックされている場合に期待する必要がある不足している機能が詳細に表示されます。
  
Office 365 を使用しようとしていて、サードパーティのサービスにアクセスできないことが検出された場合は[、この記事に記載されている必須またはオプションとしてマークされたすべての fqdn を、プロキシとファイアウォール経由で許可](urls-and-ip-address-ranges.md)する必要があります。
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Microsoft のコンシューマーサービスへのアクセスをどのようにブロックするか。
<a name="bkmk_consumer"> </a>

コンシューマーサービスへのアクセスを制限することは、自己責任で行う必要があります。コンシューマーサービスをブロックする唯一の信頼できる方法は、 *login.live.com*の FQDN へのアクセスを制限することです。この FQDN は、MSDN、TechNet などの非コンシューマーサービスを含む広範なサービスセットによって使用されます。この FQDN は microsoft サポートのセキュリティで保護されたファイル Exchange プログラムによっても使用され、microsoft 製品のトラブルシューティングを容易にするためにファイルを転送するために必要です。 この FQDN へのアクセスを制限すると、これらのサービスに関連付けられているネットワーク要求のルールに対する例外も含める必要があります。
  
Microsoft のコンシューマーサービスのみにアクセスをブロックしても、ネットワーク上のユーザーが Office 365 テナントまたはその他のサービスを使用して情報を exfiltrate することはできないことに注意してください。
  
## <a name="related-topics"></a>関連トピック

[Office 365 IP アドレスと URL の Web サービス ](office-365-ip-web-service.md)

[Microsoft Azure データ センターの IP 範囲](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft パブリック IP スペース](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune のネットワークインフラストラクチャの要件](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute と power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 の URL と IP アドレス範囲](urls-and-ip-address-ranges.md)
  
[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)
  
[Office 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)
