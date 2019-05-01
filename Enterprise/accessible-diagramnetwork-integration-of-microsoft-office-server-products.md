---
title: アクセス可能な図 - Microsoft Office Server 製品のネットワーク統合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: この記事は、「Microsoft Office Server 製品のネットワーク統合」という名前の図のアクセス可能なテキスト バージョンです。
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487774"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>アクセス可能な図 - Microsoft Office Server 製品のネットワーク統合

**概要:** この記事は、「Microsoft Office Server 製品のネットワーク統合」という名前の図のアクセス可能なテキスト バージョンです。
  
このポスターは Lync Server 2013、SharePoint 2013、および Exchange Server 2013 を含むネットワーク環境の概要図を示しています。また、これらの製品に共通のネットワーク要素である、リモート アクセスと内部アクセス、認証、クライアントのトラフィック、共有デバイス経由のトラフィックのルーティングについても説明しています。 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Lync、Exchange、SharePoint サーバー、および Office Web Apps の大まかな概念

### <a name="about-the-design"></a>設計について

#### <a name="streamlined-network-design"></a>効率的なネットワーク設計

このトポロジは、SharePoint 2013、Exchange Server 2013、および Lync Server 2013 のオンプレミスのネットワーク展開を示しています。また、インターネットからの簡易メール転送プロトコル (SMTP) の受信トラフィック用のスパムやマルウェア保護を提供する、マイクロソフト クラウド ベースのサービスの Exchange Online Protection の使用法も示しています。 
  
このネットワーク設計は、ネットワーク機能の最小セットになるよう合理化されています。この設計は、一部の組織が必要とするアカウント追加セキュリティやインフラストラクチャ機能は考慮していません。 
  
この図では次のようになっています。 
  
- ゲートウェイ ルーターとクライアント セッションのトラフィック (外部および内部) の負荷分散を経由し、適切な SharePoint、Exchange、および Lync サーバー階層に到達する受信および送信トラフィックを示すネットワーク トポロジの例を示しています。 
    
- ローミングやリモートの従業員に対して安全な通信を提供するための、サード パーティ製 VPN ゲートウェイや DirectAccess サーバーなどのオプションのリモート アクセス サーバーの使用を示します。 
    
- SharePoint、Exchange、および Lync のクライアントから各プラットフォーム サーバー層へのトラフィック フローの詳細を示します。 
    
- (パートナーまたは従業員などの) クライアント ベースのリモートおよび内部アクセスの接続の種類と、使用される認証方法を識別します。 
    
- フロント エンド、アプリケーション、データベース、および他のレベルを識別する、必要なサーバーの役割によって、SharePoint、Exchange、および Lync プラットフォームを分割します。 
    
SharePoint、Lync、および Exchange のためにここで使用されるアーキテクチャは、これらのプラットフォームの実装の推奨方法を示すものではありません。トポロジは固有のネットワーク要件やセキュリティ上の考慮事項に応じて異なるため、これらは単に例を示しているにすぎません。 
  
#### <a name="gateway-router"></a>ゲートウェイ ルーター

このトポロジでは、ゲートウェイ ルーターはネットワークの端にあり、イントラネットのすべての着信および発信トラフィックをルーティングしています。また、ゲートウェイ ルーターと、図の複数のレイヤーのファイアウォールなどのロード バランサーのギャップを埋める、ほかのコンポーネントが存在する可能性もあります。このトポロジは、ネットワークを展開する多数の方法の 1 つを表しているにすぎません。この構成では、ルーター インターフェイス上の IP ベースの固有の着信および発信トラフィックを許可するアクセス制御リスト (ACL) を使用して、ゲートウェイが構成されています。ACL、高度な検査、またはネットワーク アドレス変換 (NAT) も、ネットワーク全体のファイアウォールなどのほかのデバイス上で実行できます。 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>ロード バランサーとリバース プロキシ デバイス

SharePoint フロント エンド Web サーバーや Exchange クライアント アクセス サーバー (CAS) を含むセグメントのトラフィックをリダイレクトするのに、ハードウェアまたはソフトウェアの負荷分散ソリューションを使用できます。 要求内の cookie またはヘッダー情報のような情報を使用することでパフォーマンスが向上することがあるため、永続性の要件のためにレイヤー 7 のハードウェア ベースのロード バランサーを使用するのが最適な場合があります。ただし、コストと使用率の増加、ソリューションからの負荷などの要因により、特定のニーズには適さない可能性もあります。SharePoint、Exchange、および Lync での負荷分散では、次の点を検討します。 
  
- SharePoint - SharePoint 2013 では、フロント エンド Web サーバーのアフィニティを有効にする必要はありません。通常、これはスティッキー セッションの作成に使用され、各フロント エンド Web サーバーにクライアントから複数の認証要求を行うことを回避するために使用されます。SharePoint 2013 の新しい分散キャッシュ サービスは、SharePoint ファームの Web サーバー間のログオン トークンを保存して配布します。 
    
- Exchange - Exchange 2013 では、レイヤー 4 ロード バランシングを使用して、トランスポート層で要求を分散するよう CA の役割が設計されています。これにより、ロード バランサーの使用率と作業負荷を大幅に削減することができます。 
    
- Lync - Lync のプールの セッション開始プロトコル (SIP) トラフィックでは、ドメイン ネーム システム (DNS) の負荷分散が推奨されています。ハードウェア負荷分散 (HLB) は、Lync Web (HTTPS) トラフィックのために必要です。 
    
### <a name="remote-access-options"></a>リモート アクセスのオプション

イントラネット リソースをインターネット上のパートナーのために発行したり、リモート ユーザーやローミングの従業員に安全なリモート アクセスを提供したりするための、いくつかのオプションがあります。例として、リバース プロキシ、DirectAccess、サード パーティ製 VPN ゲートウェイなどがあります。このセクションで後述するリモート アクセス ソリューションを、オンプレミス展開の SharePoint、Lync、および Exchange、またはこれらのサーバーの任意の組み合わせに対して選択できます。ただし、特定のソリューションで、一部のリモートのオプションが機能しない場合があります。 
  
リバース プロキシ - リバース プロキシは、Secure Sockets Layer (SSL) などのトラフィックの暗号化をサポートし、インターネットの認証ユーザーとパートナーにイントラネット アプリケーションと Web リソースを公開できます。例として、Microsoft Forefront Unified Access Gateway (UAG) があります。 多くのハードウェア ロード バランサーは、リバース プロキシの機能もサポートします。ただし、トラフィックの分離、セキュリティ区画化、パフォーマンスの最適化などのニーズと要件に応じて、スタンドアロンのソリューションを使用するための有効なシナリオがあります。 
  
リバース プロキシのメリットと注意事項: 
  
- イントラネット リソースにアクセスするパートナーまたはユーザーに、認証およびセキュリティで保護されたアクセスを提供します (クライアントとリバース プロキシ サーバー間で SSL (TCP 443) を使用)。 
    
- Exchange では、Forefront UAG などのリバース プロキシを使用する利点は、Exchange クライアント アクセス サーバーにアクセスする前に事前認証できることです。Outlook Web Access (OWA) などの公開されたアプリケーションを使用するリモート アクセス ユーザーは、基本、NTLM、または Kerberos の方法を使用して、内部ネットワークに到達する前に認証できます。 
    
- Exchange および SharePoint では、Forefront UAG のようなソリューションが SSL 接続を終了し、内部リソースの負荷を減らしながら、証明書を一か所で管理できるようになります。 
    
- Lync では、Web (HTTPS) トラフィックはクライアント通信のためにリバース プロキシ (TCP 443) を経由します。リバース プロキシは、Lync Web Services、Exchange CAS、および Office Web Apps への HTTPS 接続のプロキシを実行します。Lync Server 2013 は UAG をサポートしていません。 
    
DirectAccess - インターネット プロトコル セキュリティ (IPsec) を DirectAccess クライアントとサーバー間の認証およびトラフィックの暗号化に使用するリモート アクセス テクノロジ。DirectAccess は接続を開始する必要性無しで、ローミングやリモートの従業員のインターネットとイントラネットの両方のリソースへの同時アクセスを提供します。 
  
DirectAccess の考慮すべき事項: 
  
- DirectAccess は、IPsec で保護されたトラフィック (プロトコル 50、51 と UDP 500) を DirectAccess クライアントとサーバー間で使用します。 
    
- Windows Server 2012 と Windows 8 用の DirectAccess では、サーバーとクライアントの認証に公開キー基盤 (PKI) の展開を必要としません。 
    
- IPsec の暗号化と復号化に関連するオーディオとビデオの遅延の問題のため、DirectAccess は Lync Server 2013 と共に使用しないことをお勧めします。 
    
    VPN ゲートウェイ - 典型的な VPN ゲートウェイは、トンネルおよびユーザーによる接続を使用してイントラネットにリモート アクセス クライアント コンピューターが論理的に投影されるリモート アクセス接続を提供します。イントラネットへのセキュリティで保護されたアクセスをローミングまたはリモートの従業員に提供するために、Windows Server 2012 のリモート アクセスの統合やサード パーティ製ソリューションを使用できます。VPN は Lync では推奨されません。Lync のリモート トラフィックは、エッジ サーバーとスプリット トンネリングを使用します。 
    
### <a name="domain-name-system-dns-considerations"></a>ドメイン ネーム システム (DNS) の考慮事項

インターネットおよびイントラネットのユーザーが DNS 名を適切な IP アドレスに解決できるように、DNS レコードのセットを計画する必要があります。 
  
- インターネット ベースのパートナー、およびローミングやリモートの従業員には、インターネット DNS サーバーに登録された DNS レコードが、ゲートウェイ ルーター、Lync エッジ サーバー、ロード バランサーの仮想 IP アドレス (VIP) のセット、および DirectAccess または VPN ゲートウェイに該当するパブリック IP アドレスのセットへの解決を、必要に応じて提供します。 
    
- イントラネット ベースのユーザーには、イントラネット DNS サーバーに登録されている DNS レコードが、SharePoint、Lync、および Exchange のリソースにアクセスするために、ロード バランサーの仮想 IP アドレス (VIP) のセットへの解決を提供します。 
    
- DirectAccess クライアントはイントラネットの DNS サーバーを該当するイントラネットの DNS 名前空間の名前に使用し、インターネット DNS サーバーをそれ以外の名前に使用します。DirectAccess の運用を簡素化するために、イントラネットおよびインターネット ベースの名前に別の DNS 名前空間を使用するよう、分割 DNS の実装の使用を検討してください。たとえば、contoso.com をインターネット名前空間に使用し、corp.contoso.com をイントラネット名前空間に使用します。 
    
- Exchange は、IP 解決のホストが、パブリック ルーティング トラフィックと企業ネットワークで異なる分割 DNS モデルを使用します。最低限、クライアント トラフィックのための OWA、自動検出、ActiveSync の URL の DNS レコードと、受信メールのための MX レコードが必要です。 
    
- Exchange Online Protection (EOP) を使用している場合、MX レコードは Exchange ファームではなく、そのサービスを指します。 
    
- Exchange では、パブリック DNS に TXT レコードの所有権の証明が必要であり、フェデレーションの共有の設定にフェデレーションの組織 ID が必要です。 
    
- リモート アクセス VPN クライアントは、リモート アクセス VPN 接続がアクティブな場合はイントラネットの DNS サーバーだけを使用するように構成できます。 
    
### <a name="diagram-description"></a>図の説明

この図は、ゲートウェイ ルーターとクライアント セッションのトラフィック (外部および内部) の負荷分散を経由し、適切な SharePoint、Exchange、および Lync サーバー階層に到達する受信および送信トラフィックを示すネットワーク トポロジの例を示しています。この図の説明は次の 2 つの部分に分かれています。 
  
- 図中のコンポーネントの説明 
    
- SharePoint、Exchange、Lync、および Office Web Apps サーバー層にコンポーネントを経由してトラフィックを移動する方法の説明。 
    
#### <a name="description-of-components-shown-in-the-diagram"></a>図中のコンポーネントの説明

#### <a name="user-types"></a>ユーザーの種類

4 つの異なる種類のユーザーがあります。ネットワークとクラウド サービスの外部にいる 3 種類のユーザーと内部にいる 1 種類のユーザーがあり、以下のようになっています。 
  
- パートナー企業 (企業間) – 外部 
    
- 個々のパートナー (SharePoint と匿名 (Lync)) – 外部 
    
- ローミングとリモートの従業員 – 外部 
    
- 内部の従業員 
    
#### <a name="cloud-based-email-traffic"></a>クラウド ベースの電子メール トラフィック

SMTP ベースの電子メール トラフィックに対して、インターネット メール ホストまたは Exchange Online Protection のいずれかのクラウド ベースのコンポーネントがあります。 
  
#### <a name="authentication-for-external-access"></a>外部アクセスの認証

それぞれの種類のユーザーに対して、Lync、SharePoint、および Exchange の認証手順の特定のセットがあります。それらについては、このドキュメントの後半で詳しく説明します。 
  
#### <a name="gateway-router-with-acls"></a>ゲートウェイ ルーターと ACL

ゲートウェイ ルーターはネットワークの端にあり、イントラネットのすべての着信および発信トラフィックをルーティングします。 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Lync と SharePoint のリモート アクセス サーバー

このトポロジには、Lync エッジ サーバーと、SharePoint の VPN ゲートウェイまたは DirectAccess サーバーが含まれます。 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>ロード バランサーとリバース プロキシ デバイス

SharePoint フロント エンド Web サーバーや Exchange クライアント アクセス サーバー (CAS) を含むセグメントのトラフィックをリダイレクトするのに、ハードウェアまたはソフトウェアの負荷分散ソリューションを使用できます。このトポロジは、ロード バランサーでの Lync の VIP、SharePoint の VIP、Exchange の VIP のコンポーネントを示します。 
  
#### <a name="servers"></a>サーバー

4 台のサーバーがあります。 Lync、SharePoint、Exchange、および Office Web Apps サーバー。 各サーバーは、フロント エンドのクライアント アクセス層、アプリケーション層、およびデータベース/ストレージ層の 3 つの層を持つことができます。
  
#### <a name="front-end-client-access-tier"></a>フロント エンドのクライアント アクセス層

この層には、4 つのすべてのサーバーのコンポーネントがあります。 
  
- Lync のプール (フロント エンド)。Lync の 2 つのデータベースを図に示します。 
    
- SharePoint フロント エンド、および分散キャッシュ。3 つの SharePoint データベースを図に示します。 
    
- Exchange CAS。2 つの SharePoint データベースを図に示します。 
    
- Office Web Apps サーバー2 つの Office Web Apps データベースを図に示します。 
    
#### <a name="application-tier"></a>アプリケーション層

この層には、SharePoint サーバーのみのコンポーネントがあります。 
  
- 検索 (クエリ、インデックス、管理)。3 つの SharePoint データベースを図に示します。 
    
- バッチ処理。3 つの SharePoint データベースを図に示します。 
    
#### <a name="databasestorage-tier"></a>データベース/ストレージ層

この層には、Lync、SharePoint、および Exchange サーバーのコンポーネントがあります。 
  
- Lync データベース (バックエンド)。Lync の 3 つのデータベースを図に示します。 
    
- SharePoint データベース。3 つの SharePoint データベースを図に示します。 
    
- Exchange メールボックス サーバー。2 つの Exchange メールボックス サーバーを図に示します。 
    
各 SharePoint サーバーにインストールされているコンポーネントの詳細については、「[SharePoint 2013 の効率化されたトポロジー](https://aka.ms/Ma5cgk)」を参照してください。 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>トラフィックがコンポーネントを経由して別のサーバー層に移動する方法の説明

このセクションでは、ユーザーの要求がネットワーク トポロジを移動する方法について説明します。 
  
#### <a name="authentication-and-routing-for-external-access"></a>外部アクセスのための認証とルーティング

ネットワークとクラウド サービスの外部に、次の 3 種類の異なるクライアントがあります。 
  
- パートナー企業 (企業間) – 外部 
    
- 個々のパートナー (SharePoint と匿名 (Lync)) – 外部 
    
- ローミングとリモートの従業員 – 外部 
    
外部ユーザーの種類ごとの認証およびルーティング プロセスを個別に説明します。 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>パートナー会社 (企業間) (https://partnerweb.contoso.com)

- Lync: 他の組織、Skype、および AOL を使用したパブリック IM 接続のフェデレーション信頼。Lync のフェデレーション トラフィックは、ゲートウェイ ルーターを介して、Lync エッジ サーバー、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Lync Server に移動します。 
    
- SharePoint:SAML 認証を使用する信頼できるパートナー ID プロバイダー。SharePoint のクライアント トラフィックは、ゲートウェイ ルーターを介して、SharePoint の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に SharePoint Server に移動します。 
    
- Exchange:メール トラフィック用の相互認証 TLS、フェデレーション共有用の SAML 認証。Exchange のクライアント トラフィックは、ゲートウェイ ルーターを介して、Exchange の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Exchange Server に移動します。 
    
- SMTP のトラフィックは、ゲートウェイ ルーターを介して、Exchange の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Exchange Server に移動します。 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>個々のパートナー (SharePoint) と匿名 (Lync) (https://partnerweb.contoso.com および https://meet.contoso.com)

- Lync: 匿名ユーザーは従業員別に整理された Lync 会議のみに参加できます。Lync のフェデレーション トラフィックは、ゲートウェイ ルーターを介して、Lync エッジ サーバー、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Lync Server に移動します。 
    
- SharePoint:SAML 認証またはフォーム ベース認証を使用する信頼できるパートナー ID プロバイダー。SharePoint のクライアント トラフィックは、ゲートウェイ ルーターを介して、SharePoint の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に SharePoint Server に移動します。 
    
- Exchange: 該当しません。 
    
- Lync の Web トラフィックは、ゲートウェイ ルーターを介して、Lync エッジ サーバー、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、ハードウェアのロード バランサー (HTTPS トラフィックで必要)、次に Lync Server に移動します。 
    
#### <a name="roaming-and-remote-employees"></a>ローミングとリモートの従業員

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* Exchange の URL は次の仮想ディレクトリを持っています:Autodiscover、ecp、EWS、Microsoft-Server-ActiveSync、OAB、owa、PowerShell 
  
- Lync:TLS-DSK または NTLM 認証。Lync のクライアント トラフィックは、ゲートウェイ ルーターを介して、Lync エッジ サーバー、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Lync Server に移動します。 
    
- SharePoint:Active Directory ドメイン サービス (AD DS)、フォームベース認証または SAML 認証。SharePoint のクライアント トラフィックは、VPN ゲートウェイまたは DirectAccess サーバーを介して、SharePoint の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に SharePoint Server に移動します。 
    
- Exchange:SSL 経由の基本認証 (ActiveSync、自動検出)、フォーム ベース認証 (OWA)。Exchange のクライアント トラフィックは、ゲートウェイ ルーターを介して、Exchange の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Exchange Server に移動します。 
    
- Lync のクライアント トラフィックは、ゲートウェイ ルーターを介して、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、ハードウェアのロード バランサー (HTTPS トラフィックで必要)、次に Lync Server に移動します。 
    
#### <a name="authentication-for-internal-access"></a>内部アクセスの認証

#### <a name="internal-employees"></a>内部の従業員

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- Lync:Kerberos、TLS-DSK、または NTLM 認証。Lync のクライアント トラフィックは、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Lync Server に移動します。 
    
- SharePoint:Active Directory ドメイン サービス (AD DS)、フォームベース認証または SAML 認証。SharePoint のクライアント トラフィックは、SharePoint の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に SharePoint Server に移動します。 
    
- Exchange:AD DS、フォーム ベース認証。Exchange のクライアント トラフィックは、Exchange の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Exchange Server に移動します。 
    
- Lync のクライアント トラフィックは、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、ハードウェアのロード バランサー (HTTPS トラフィックで必要)、次に Lync Server に移動します。 
    
#### <a name="cloud-based-email-traffic"></a>クラウド ベースの電子メール トラフィック

SMTP ベースの電子メール トラフィックのためのクラウド ベースのコンポーネントは、インターネット メール ホストまたは Exchange Online Protection のいずれかで構成されます。
  
これらのコンポーネントは、SMTP を使用してネットワーク経由で電子メール トラフィックを移動します。トラフィックは、ゲートウェイ ルーターを介して、Exchange の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Exchange Server に移動します。 
  
### <a name="network-traffic-legend"></a>ネットワーク トラフィックの凡例

凡例のボックスでは、次のように線に異なる色を付けて、各種のトラフィックをグラフィカルに示しています。 
  
- 緑色の線: Lync の SIP トラフィック 
    
- 青色の線:Lync の Web トラフィック 
    
- 紫色の線:SharePoint クライアントのトラフィック 
    
- オレンジ色の線:Exchange クライアントのトラフィック 
    
- 灰色の線:Exchange のオンプレミスと Exchange Online Protection の間の Exchange メール サーバーのトラフィック。 
    
トラフィックと使用するポートの様々な種類も、凡例のボックスに記載されています。 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Lync の SIP トラフィックと Lync の web トラフィック

Lync エッジ サーバーは、外部のユーザーの通信に次のポートを使用します。 
  
- 信号/IM トラフィック (SIP/SIMPLE):TCP ポート 443 (着信トラフィック用に開いている) 
    
- Web 会議トラフィック (PSOM):TCP 443 (着信トラフィック用に開いている) 
    
- A/V のトラフィック (SRTP):TCP 443、UDP 3478、および TCP 50000 ～ 59999 (省略可能) (受信および送信トラフィック用に開いている) 
    
Lync エッジ サーバーは、フェデレーションの通信に次のポートを使用します。 
  
- TCP ポート 5061 (SIP)、5269 (XMPP)、443、および UDP 3478 (SRTP) (受信および送信トラフィック用に開いている) 
    
#### <a name="sharepoint-client-traffic"></a>SharePoint クライアントのトラフィック

SharePoint は、クライアントとロード バランサーの間の暗号化通信のために TCP ポート 443 (SSL) を使用できます。インターネットからの外部アクセスでは、ゲートウェイ ルーター (または外部ファイアウォール) 上の送受信トラフィックに対してこのポートを開く必要があります。 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Exchange クライアントのトラフィックと Exchange メール サーバーのトラフィック

Exchange は、サーバーからサーバーへの通信に TCP ポート 25 (SMTP) を使用します。ほとんどのクライアント トラフィック (OWA、ActiveSync、自動検出、Outlook Anywhere) がポート 443 (HTTPS) 経由で処理されます。 POP または IMAP クライアントがある場合は、これらのクライアントをサポートするために、ポート 110 (POP3)、995 (暗号化された POP3)、143 (IMAP4)、993 (暗号化された IMAP4)、および 587 (SMTP) も使用されます。 
  
#### <a name="more-on-lync-network-traffic"></a>Lync ネットワーク トラフィックの詳細について

Lync Server が、インスタント メッセージング、web 会議、アプリケーション共有、および音声通信を提供する点で、組織を支援する方法を確認できます。詳細については、「[Microsoft Lync Server 2013 のプロトコル ワークロード ポスター](https://aka.ms/G5jzjo)」を参照してください。 
  
ポスターには、この情報にアクセスする QR コードもあります。 
  

