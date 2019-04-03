---
title: コンテンツ配信ネットワーク
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: この情報を使用して、Office 365 がコンテンツ配信ネットワーク (cdns) を使用してパフォーマンスを向上させる方法について説明します。
ms.openlocfilehash: 5d02b28fad0e47473cc6a75948c9dd27e6728bb5
ms.sourcegitcommit: 43d2b7e1d9932182c6cca5164d4d9096dcf4ed36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "31039484"
---
# <a name="content-delivery-networks-cdns"></a>コンテンツ配信ネットワーク (cdns)

cdns は、エンドユーザーにとって Office 365 を高速かつ信頼性の高い状態に保つことができます。 Office 365 などのクラウドサービスでは、cdns を使用して、ダウンロードを高速化し、エンドユーザーの潜在期間を短縮するために、静的なアセットをブラウザーの近くにキャッシュします。 このトピックの情報は、コンテンツ配信ネットワーク (cdns) と、それらが Office 365 でどのように使用されるかについて理解するのに役立ちます。

## <a name="what-exactly-is-a-cdn"></a>完全に CDN とは何ですか。

CDN は、高速バックボーンネットワークによって接続されるデータセンター内のプロキシサーバーとファイルサーバーで構成される、地理的に分散したネットワークです。 cdns は、web サイトまたはサービス内の指定した一連のファイルとオブジェクトの待機時間と読み込み時間を短縮するために使用されます。 CDN には、任意の場所からの着信要求を最適に処理するために、数千のエンドポイントが存在する場合があります。

通常、cdns は、javascript ファイル、アイコン、画像などの web サイトまたはサービスの汎用コンテンツのダウンロードを高速化するために使用されます。また、ファイルなどのユーザーコンテンツへのプライベートアクセスを SharePoint Online ドキュメントライブラリ、ストリーミングメディアファイルなどに提供することもできます。、およびカスタムコード。

cdns は、ほとんどのエンタープライズクラウドサービスで使用されます。 Office 365 のようなクラウドサービスには、多数のユーザーが所有するコンテンツ (メールなど) と汎用コンテンツ (アイコンなど) を同時にダウンロードします。 ユーザーのコンピューターにできるだけ近づけるように、すべてのユーザーがアイコンを使用して、画像を追加する方が効率的です。 すべてのクラウドサービスで、この汎用コンテンツをすべての大都市エリアに保存する CDN データセンターや、世界中の主要なインターネットハブのすべてにおいて使用することは現実的ではありません。一部の cdns は共有されています。

## <a name="how-do-cdns-make-services-work-faster"></a>cdns を使用してサービスを高速化する方法

アイコンなどの一般的なオブジェクトをもう一度にダウンロードすると、電子メールやドキュメントなどの重要な個人コンテンツをダウンロードするために使用できるネットワーク帯域幅が必要になることがあります。 Office 365 は cdns を含むアーキテクチャを使用しているため、アイコン、スクリプト、およびその他の汎用コンテンツをサーバーからクライアントコンピューターに近い場所にダウンロードして、ダウンロードを高速化することができます。 これは、Office 365 データセンターに安全に格納されている個人コンテンツへのアクセスが高速になることを意味します。

cdns は、クラウドサービスのパフォーマンスを次のように改善するために役立ちます。

- cdns は、ネットワークの一部を移行し、クラウドサービスからのファイルダウンロードの負荷を軽減し、ユーザーコンテンツやその他のサービスにサービスを提供するためにクラウドサービスリソースを解放します。これにより、静的アセットの要求を処理する必要性が減少します。
- cdns は、高パフォーマンスのネットワークとファイルサーバーを実装することにより遅延のないファイルアクセスを実現する目的で構築されており、 [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2)などの更新されたネットワークプロトコルを使用して高効率の圧縮と要求多重化を行うことを目的としています。
- CDN ネットワークは、グローバルに分散されたエンドポイントを多数使用して、コンテンツを可能な限り近くで利用できるようにします。

## <a name="the-office-365-cdn"></a>Office 365 CDN

組み込みの office 365 のコンテンツ配信ネットワーク (CDN) を使用すると、office 365 管理者は、それを要求するブラウザーに近い静的なアセットをキャッシュすることによって、組織の SharePoint Online ページのパフォーマンスを向上させることができます。ダウンロードして待機時間を短縮します。 Office 365 CDN は、強化された圧縮およびダウンロード速度を実現するために、 [HTTP/2 プロトコル](https://en.wikipedia.org/wiki/HTTP/2)を使用します。

Office 365 CDN は静的資産を複数の場所 _(元の場所)_ でホストできる複数の CDN で構成されているため、静的資産をグローバルな高速ネットワークから提供することができます。 Office 365 CDN でホストするコンテンツの種類に応じて、**公開**、**非公開**、またはその両方の元の場所を追加できます。

![Office 365 CDN の概念図](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN の概念図")

Office 365 CDN 内で**公開されている**元の場所のコンテンツは匿名でのアクセスが可能で、ホストされた資産への URL があれば誰でもアクセスできます。 公開されている元の場所のコンテンツへのアクセスは匿名になるため、アクセスしたコンテンツは、機密データ以外の一般的なコンテンツ (JavaScript ファイル、スクリプト、アイコン、画像など) をキャッシュする場合にのみ使用するようにしてください。 Office 365 CDN は、Office 365 クライアント アプリケーションのような一般リソースを、公開されている元の場所からダウンロードする際に既定で使用します。

Office 365 CDN 内の**非公開**の元の場所は、SharePoint Online ドキュメント ライブラリ、サイト、メディア (例: 動画) など、ユーザー コンテンツへのプライベート アクセスを行う場合に使用します。 公開されている元のファイルのコンテンツへのアクセスは、動的に生成されたトークンで保護されているため、元のドキュメント ライブラリまたは保存場所へのアクセス許可を持つユーザーのみがアクセスできます。 Office 365 CDN で公開されている元の場所は SharePoint Online コンテンツに対してのみ使用することができ、SharePoint Online テナントからのリダイレクトによってのみ資産にアクセスすることができます。

Office 365 CDN サービスは、SharePoint Online サブスクリプションの一部として含まれます。

office 365 CDN の使用方法の詳細については、「 [SharePoint Online で office 365 コンテンツ配信ネットワークを使用](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)する」を参照してください。

## <a name="other-microsoft-cdns"></a>その他の Microsoft cdns

office 365 cdn の一部ではありませんが、これらの cdns を office 365 テナントで使用して、SharePoint 開発ライブラリ、カスタムコード、および office 365 CDN の範囲外にあるその他の目的にアクセスすることができます。

### <a name="azure-cdn"></a>Azure CDN

**Azure CDN**を使用すると、カスタム web パーツ、ライブラリ、およびその他のリソースアセットをホストするための独自の cdn インスタンスを展開できます。これにより、アクセスキーを cdn ストレージに適用し、cdn 構成をより細かく制御することができます。 azure CDN の使用は無料であり、azure サブスクリプションが必要です。

azure cdn インスタンスを構成する方法の詳細については、「[クイックスタート: azure storage アカウントと azure cdn を統合](https://docs.microsoft.com/en-us/azure/cdn/cdn-create-a-storage-account-with-cdn)する」を参照してください。

sharepoint web パーツをホストするために azure cdn を使用する方法の例については、「 [sharepoint のクライアント側 web パーツを Azure CDN に展開](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn)する」を参照してください。

azure cdn PowerShell モジュールの詳細については、「 [PowerShell を使用して azure cdn を管理](https://docs.microsoft.com/en-us/azure/cdn/cdn-manage-powershell)する」を参照してください。

### <a name="microsoft-ajax-cdn"></a>Microsoft Ajax CDN

Microsoft の**Ajax cdn**は読み取り専用の cdn で、jQuery (およびその他のすべてのライブラリ)、ASP.NET Ajax、ブートストラップ、ノックアウトなどの多くの一般的な開発ライブラリを提供します。
  
これらのスクリプトをプロジェクトに含めるには、プロジェクト自体に含めるのではなく、これらのパブリックなライブラリへの参照を CDN アドレスへの参照に置き換えます。 たとえば、次のコードを使用して jQuery にリンクします。

``` html
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

microsoft ajax cdn の使用方法の詳細については、「 [microsoft ajax cdn](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview)」を参照してください。

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Office 365 で CDN からのコンテンツを使用する方法

Office 365 テナントに対して構成する CDN に関係なく、基本的なデータ取得プロセスは同じです。

1. クライアント (ブラウザーまたは office クライアントアプリケーション) は、Office 365 のデータを要求します。

2. Office 365 は、クライアントにデータを直接返すか、またはデータが cdn によってホストされるコンテンツセットの一部である場合、クライアントを cdn URL にリダイレクトします。

    a: データが_パブリック_の配信元で既にキャッシュされている場合、クライアントは、最も近い CDN の場所からクライアントにデータを直接ダウンロードします。

    b: データが既に_プライベート_の配信元でキャッシュされている場合、CDN サービスは、元の Office 365 ユーザーアカウントのアクセス許可を確認します。 アクセス許可がある場合、SharePoint Online は CDN および2つのアクセストークン内のアセットへのパスで構成されるカスタム url を動的に生成し、クライアントにカスタム url を返します。 その後、クライアントは、カスタム URL を使用して、最も近い CDN の場所からクライアントにデータを直接ダウンロードします。

3. cdn でデータがキャッシュされていない場合、cdn ノードは Office 365 のデータを要求し、クライアントがデータをダウンロードした後、しばらくの間データをキャッシュします。

CDN は、ユーザーのブラウザーに最も近いデータセンターを特定し、リダイレクトを使用して、そこから要求されたデータをダウンロードします。 CDN リダイレクトは短時間で、ユーザーはダウンロード時間を大幅に短縮できます。

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Office 365 で cdns が最適に機能するように、どのようにネットワークをセットアップする必要がありますか?

ネットワーク上のクライアント間の遅延を最小限に抑え、CDN エンドポイントは、最適なパフォーマンスを確保するための重要な考慮事項です。 「 [Office 365 エンドポイントの管理](managing-office-365-endpoints.md)」に記載されているベストプラクティスを使用すると、クライアントブラウザーが中央のプロキシ経由で cdn トラフィックをルーティングするのではなく、直接 cdn にアクセスできるようになります。不要な待機時間。

また、「office [365 のネットワーク接続の原則](https://aka.ms/o365networkingprinciples)」を参照して、office 365 のネットワークパフォーマンスの最適化の背後にある概念を理解することもできます。

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Office 365 で使用されるすべての cdns の一覧はありますか。

Office 365 で使用されている cdns は常に変更される可能性があり、多くの場合、イベント1に構成されている複数の CDN パートナーが利用できなくなっています。 Office 365 で使用されるプライマリの cdns は次のとおりです。

|CDN  |Company  |使用方法  |リンク  |
|---------|---------|---------|---------|
|Office 365 CDN     |Akamai         |一般に公開される出所の汎用アセット、プライベートオリジンでの SharePoint ユーザーコンテンツ         |[SharePoint Online での Office 365 コンテンツ配信ネットワークの使用](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)         |
|Azure CDN     |Microsoft         |カスタムコード、SharePoint Framework ソリューション         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Microsoft Ajax CDN (読み取り専用)     |Microsoft         |Ajax、jQuery、ASP.NET、ブートストラップ、ノックアウトなどの共通ライブラリ。         |[Microsoft Ajax CDN](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>CDN によって得られるパフォーマンスの向上

Office 365 から直接ダウンロードされたデータと、特定の cdn からダウンロードされたデータとの間のパフォーマンスの違いを測定する要因は多数あります。たとえば、テナントへの相対位置や、最も近い cdn エンドポイントに対する特定の数、CDN によって提供されるページ上のアセット、およびネットワークの待ち時間と帯域幅の一時的な変化。 ただし、単純な a/B テストでは、特定のファイルのダウンロード時間の違いを表示するのに役立ちます。

次のスクリーンショットは、Office 365 のネイティブファイルの場所と、 [Microsoft Ajax コンテンツ配信ネットワーク](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview)上でホストされている同じファイルの間でのダウンロード速度の違いを示しています。 これらのスクリーンショットは、Internet Explorer 11 開発者ツールの [**ネットワーク**] タブにあります。 これらのスクリーンショットは、人気のあるライブラリ jQuery の待機時間を示しています。 この画面を表示するには、Internet Explorer で**F12**キーを押して、wi-fi アイコンで認識されている [**ネットワーク**] タブを選択します。
  
![F12 ネットワークのスクリーンショット](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
このスクリーンショットは、SharePoint Online サイト自体のマスターページギャラリーにアップロードされたライブラリを示しています。 ライブラリのアップロードにかかった時間は1.51 秒です。
  
![読み込み時間 1.51 秒のスクリーン ショット](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
2番目のスクリーンショットは、Microsoft の CDN によって配信された同じファイルを示しています。 この時間が経過すると、遅延は約496ミリ秒になります。 これは大規模な改善で、1秒間にオブジェクトをダウンロードする合計時間が短縮されることを示しています。
  
![読み込み時間 469 ミリ秒のスクリーンショット](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>データは安全ですか?

当社では、ビジネスを実行するデータを保護するために十分な注意を払っています。 office 365 cdn に格納されているデータは、移行中と保存時の両方で暗号化され、office 365 のデータへのアクセスは office 365 のユーザー権限とトークン認証によって保護されます。 office 365 SharePoint CDN のデータに対する要求は、office 365 テナントから参照 (リダイレクト) する必要があります。または、認証トークンは生成されません。

データを安全な状態に保つために、ユーザーコンテンツやその他の機密データをパブリック CDN に保存しないことをお勧めします。 パブリック CDN のデータへのアクセスは匿名であるため、パブリック cdns は、web スクリプトファイル、アイコン、画像、その他の機密でないアセットなどの汎用コンテンツをホストする場合にのみ使用してください。

> [!NOTE]
> サードパーティの CDN プロバイダーは、Office 365 セキュリティセンターによって規定されているコミットメントとは異なるプライバシーとコンプライアンス標準を備えている場合があります。 CDN サービスを使用してキャッシュされたデータは、Microsoft データ処理条件 (DPT) に準拠していない可能性があり、Office 365 セキュリティセンターのコンプライアンス境界の外にある場合があります。

Office 365 CDN プロバイダーのプライバシーとデータ保護の詳細については、以下を参照してください。  

- office 365 のプライバシーとデータ保護の詳細については、「 [Microsoft Trust Center」](https://www.microsoft.com/trustcenter)を参照してください。
- akamai のプライバシーとデータ保護の詳細については、「 [akamai privacy セキュリティセンター」](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)を参照してください。
- azure のプライバシーとデータ保護の詳細については、「 [azure のセキュリティセンター」](https://azure.microsoft.com/en-us/overview/trusted-cloud/)を参照してください。

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>これらのサードパーティ製サービスを使用してネットワークをセキュリティで保護するにはどうすればよいですか?

一連のパートナーサービスを活用することにより、office 365 は、office 365 を使用しているときに、可用性の要件を拡大縮小し、ユーザーの利便性を向上させることができます。 サードパーティ製サービスの Office 365 では、両方の証明書失効リストが含まれています。crl.microsoft.com、sa.symcb.com、cdns など。r3.res.outlook.com など。 office 365 によって生成されるすべての CDN fqdn は、office 365 のカスタム fqdn です。 Office 365 の要求で fqdn に送信した場合は、CDN プロバイダーが fqdn およびその場所の基になるコンテンツを制御することができます。
  
サードパーティに対する要求から、Microsoft または office 365 データセンター宛ての要求を分離する必要があるお客様のために、 [office 365 エンドポイントの管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)に関するガイダンスを作成しました。

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>cdns を利用する fqdn の一覧はありますか。

fqdn の一覧と、時間の経過による cdns の変更の活用方法。 cdns を利用する最新の fqdn で最新の情報を得るには、「公開された[Office 365 の url と IP アドレスの範囲](https://go.microsoft.com/fwlink/p/?LinkID=293744)」ページを参照してください。

[office 365 の ip アドレスと URL Web サービス](https://docs.microsoft.com/en-us/office365/enterprise/office-365-ip-web-service)を使用して、現在の office 365 の url と IP アドレス範囲を CSV または JSON として書式設定して要求することもできます。

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>自分の CDN を使用して、ローカルネットワーク上でコンテンツをキャッシュすることはできますか。

お客様のニーズに対応するための新しい方法が絶えず模索されており、現在、キャッシュプロキシソリューションやその他のオンプレミスの CDN ソリューションの使用方法について調査しています。

Office 365 cdn の一部ではありませんが、 **Azure cdn**を使用してカスタム web パーツ、ライブラリ、およびその他のリソースアセットをホストすることができます。これにより、アクセスキーを cdn ストレージに適用して、cdn 構成をより細かく制御することができます。 azure CDN の使用は無料であり、azure サブスクリプションが必要です。 azure cdn インスタンスを構成する方法の詳細については、「[クイックスタート: azure storage アカウントと azure cdn を統合](https://docs.microsoft.com/en-us/azure/cdn/cdn-create-a-storage-account-with-cdn)する」を参照してください。

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Office 365 用の Azure ExpressRoute を使用していますが、変更はありますか?

[office 365 用の Azure ExpressRoute](azure-expressroute.md)は、パブリックインターネットから分離された office 365 インフラストラクチャへの専用の接続を提供します。 この場合も、クライアントは、expressroute 以外の接続を介して接続して、expressroute でサポートされているサービスの一覧に明示的に含まれていない他の Microsoft インフラストラクチャに接続する必要があります。 cdns に対する要求など、特定のトラフィックをルーティングする方法の詳細については、「 [Office 365 ネットワークトラフィック管理](routing-with-expressroute.md)」を参照してください。

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>オンプレミスの SharePoint Server で cdns を使用できますか?

cdns の使用は sharepoint Online のコンテキストでのみ有効であり、sharepoint Server で回避する必要があります。 これは、サーバーが社内に設置されている場合や、地理的に閉じている場合は、地理的な場所に関するすべての利点が true を保持しないためです。 また、ホストされているサーバーへのネットワーク接続がある場合は、インターネット接続を使用せずにサイトが使用される可能性があるため、CDN ファイルを取得することはできません。 それ以外の場合は、使用可能で、サイトに必要なライブラリおよびファイルに対して安定したものがある場合は、CDN を使用する必要があります。
  
ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>関連項目

[Office 365 ネットワーク接続の原則](https://aka.ms/o365networkingprinciples)

[Office 365 へのネットワーク接続](network-connectivity.md)

[Office 365 エンドポイントを管理する](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[Office 365 の URL と IP アドレスの範囲](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[SharePoint Online での Office 365 コンテンツ配信ネットワークの使用](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Microsoft Trust Center](https://www.microsoft.com/trustcenter)