---
title: コンテンツ配信ネットワーク
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
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
description: この情報を使用すると、コンテンツ配信ネットワーク (Cdn)、および Office 365 での活用方法について説明します。Cdn は、エンド ・ ユーザーの Office 365 を高速かつ信頼性を保ちます。Cdn と Office 365 のようなクラウド サービスは迅速に web クライアントを使用して、サービスを使用しているときに、ユーザーのブラウザーに、アイコンのように、汎用的なコンテンツをダウンロードします。
ms.openlocfilehash: bcbab3256a0c1ce601abaf3f8b80e998db4bcece
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541773"
---
# <a name="content-delivery-networks"></a>コンテンツ配信ネットワーク

この情報を使用すると、コンテンツ配信ネットワーク (Cdn)、および Office 365 での活用方法について説明します。Cdn は、エンド ・ ユーザーの Office 365 を高速かつ信頼性を保ちます。Cdn と Office 365 のようなクラウド サービスは迅速に web クライアントを使用して、サービスを使用しているときに、ユーザーのブラウザーに、アイコンのように、汎用的なコンテンツをダウンロードします。
  
 **戻りましょう。**[ネットワークを計画し Office 365 のパフォーマンスをチューニング](https://aka.ms/tune)します。
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>必要がありますの設定方法ネットワーク Cdn は Office 365 で最適に動作できるようにしますか。

[Office 365 へのネットワーク接続](network-connectivity.md)を計画している場合は、Cdn の動作を理解することをお勧めします。IP アドレスを使用して、Cdn への接続をフィルターすることはできませんを理解する必要もします。Exchange Online などの Office 365 のサービスの ip アドレスの最適な作業一覧を説明します。[Office 365 の管理するエンドポイント](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)の推奨事項について説明します。
  
## <a name="how-do-cdns-make-services-work-faster"></a>CDN はどのようにしてサービスの速度を速くするのですか?

アイコンのような共通のものを何度もダウンロードは、電子メールやドキュメントなど、重要な個人的なコンテンツをダウンロードするためより使用できるネットワーク帯域幅をかかります。Office 365 は、アーキテクチャを使用しているため Cdn では、アイコン、スクリプトが含まれていますが、他の汎用的なコンテンツは、ダウンロードを高速化する、クライアント コンピューターに近い場所にサーバーからダウンロードできます。これは、Office 365 のデータ センターで安全に格納されている個人用のコンテンツをより高速なアクセスを意味します。
  
## <a name="what-exactly-is-a-cdn"></a>CDN とは正確には何ですか?

Cdn は、ほとんどのエンタープライズ ・ クラウド ・ サービスによって使用されます。Office 365 のようなクラウド サービスでは、(e メール) などの独自のコンテンツと (アイコン) などの汎用的なコンテンツの両方を同時にダウンロードするユーザーの数百万があります。可能なユーザーのコンピューターにすべてのユーザーを使用して、アイコン、イメージを配置する方が効率的です。まだ、これら Cdn のいくつかが共有されるため、すべての大都市圏、または、世界中のすべての主要なインターネット ハブの場合でもこの汎用的なコンテンツを格納する CDN のデータ センターを構築するすべてのクラウド サービスの実際的でないです。
  
Cdn には、プライベートまたはパブリックを指定できます。プライベート Cdn が所有し、1 つの会社によって運営されて、その会社のアプリケーションとサービスのみを使用します。パブリックの Cdn は、複数の会社の使用状況をリースする企業によって実行されます。存在している、によっては、Office 365 を所有している CDN と実行、公開 CDN では、2 つの組み合わせからの一般的なイメージをダウンロードするのには Office 365 の最も効率的な場合があります。CDN の種類を使用すると、データを取得する手順は、同じです。
  
1. クライアントは、Office 365 からデータを要求します。

2. Office 365 は、クライアントに直接データを返すか、または CDN するようにクライアントに指示します。

3. 場合は、CDN では、データが既にキャッシュされて、クライアントは、インターネット上のクライアントに最も近い CDN の場所から直接データをダウンロードします。

4. データは、CDN にキャッシュされていない場合は、CDN ノードでは、Office 365 のデータを要求し、し、キャッシュのデータをクライアントがデータをダウンロードした後の期間。

Cdn ファイルと Office 365 最も近いデータ センターからの画像を取り出して、クライアントがファイルとイメージを最も近い CDN からプル。ユーザーが Outlook Web App に電子メールを読むように、クラウド サービスにアクセスするとき、ユーザーのブラウザーは Office 365 のデータ センターからのファイルとイメージを取得しようとします。ファイルを提供する帯域幅と時間を費やす、代わりには、Office 365 は、CDN にブラウザーをリダイレクトします。CDN では、ユーザーのブラウザーに最も近いデータ センターをし、そこから汎用の画像をダウンロードする、リダイレクトを使用しています。この CDN のリダイレクトを使用する場合はすぐに、およびユーザーに多くのダウンロード時間を節約します。
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Cdn を活用しているすべての Fqdn の一覧はありますか。

Fqdn と Cdn の変更、時間の経過を活用する方法の一覧は、Cdn を活用している最新の Fqdn を最新の状態を取得するのには、公開されている[Office 365 エンドポイント] ページ](https://go.microsoft.com/fwlink/p/?LinkID=293744)を参照してください。
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Office 365 を使用するすべての Cdn のリストはありますか。

Office 365 で使用している Cdn は、常に変更されることがありますように構成されていない場合に複数の CDN パートナーは、多くの場合です。使用中の 2 つの最も一般的な Cdn は、 [akamai 社](https://www.akamai.com/us/en/cdn.jsp)と[Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)です。CDN ソリューションの両方の世界の多くのコーナーにサービスの利用範囲の拡張のグローバル展開があります。保管されているコンテンツには、Office 365 の一般的なスクリプト、ファイル、および画像が含まれています。たとえば、portal.office.com にログオンするとき、ページの読み込み時間をスピードアップするために最も近い CDN からイメージが引き出されます。Office 365 に用リソースの Office の最新バージョンをダウンロードするのにかかる時間を短縮するのには CDN のインストールのビットを格納する他の例が含まれます。Office 365 のビデオのビデオ ファイルなどの Cdn に格納されているいくつかの独自コンテンツもあります。ビデオをアップロードすると後のファイルが暗号化され、Azure のメディア サービスを使用して暗号化された形式で格納されます。Office 365 のビデオ プレーヤーでビデオを取得するとき最初にキャッシュされてに最も近い CDN のビデオをダウンロードするのにかかる時間を高速化をダウンロードする前にします。
  
## <a name="does-office-365-offer-a-cdn-that-i-can-use-for-my-own-files"></a>Office 365 は、自分のファイルを使用している CDN を提供しますか。

うん！Office 365 のサブスクリプションに今すぐには、Azure 用の SharePoint Online の資産に使用できるとは別にしている CDN が含まれています。Office 365 の CDN を使用する方法については、 [SharePoint Online を使用して Office 365 コンテンツ配信ネットワークを使用して](use-office-365-cdn-with-spo.md)参照してください。
  
## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>ローカル ネットワーク上に自分の CDN とキャッシュのコンテンツを使用できますか。

当社のお客様のニーズをサポートする新しい方法を継続的に検索してキャッシュ プロキシ ソリューションおよびその他の設置型 CDN ソリューションの使用方法を模索して現在です。
  
## <a name="is-my-data-safe"></a>データは安全ですか?

我々 は、お客様のビジネスを実行しているデータを保護することを確実に十分な注意をとる。コンテンツ配信ネットワーク パートナーに格納されている項目は暗号化されますか。次のように[Office 365 のビデオ](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e)、またはお客様固有のものではありませんOffice 365 用リソースのインストール ファイルです。書店で、データとプライバシーを保護するために詳細な取り組みの詳細については[Office 365 の信頼の中心](https://go.microsoft.com/fwlink/p/?LinkId=397383)にします。
  
## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>これらすべてのサード パーティ サービスを自分のネットワークのセキュリティを保護する方法は?

スケールし可用性要件を満たすし、Office 365 を使用する場合は、ユーザー エクスペリエンスを強化するのには Office 365 は、広範囲にわたるパートナーのサービスを活用することできます。Office 365 を利用してサード パーティのサービスは、両方の証明書失効リストです。などは、crl.microsoft.com または sa.symcb.com、および Cdn。など r3.res.outlook.com。すべて CDN FQDN の Office 365 は Office 365 にカスタムの FQDN は、Office 365 の要求時に送信している場合を保証する FQDN と基になるコンテンツを制御その場所にことです。
  
お客様をします、サード ・ パーティ製宛ての要求からか、Microsoft Office 365 のデータ センターに送信される要求を分離するのには[Office 365 の管理するエンドポイント](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)のガイダンスを作成しました。
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Office 365 の Azure ExpressRoute を使用して、処理が変更されることでしょうか。

[Office 365 の azure ExpressRoute](azure-expressroute.md)は、パブリック インターネットから分離されている Office 365 のインフラストラクチャに専用の接続を提供します。これは、クライアントが Cdn と ExpressRoute でサポートされているサービスの一覧に明示的に含まれていないその他のマイクロソフトのインフラストラクチャに接続する ExpressRoute ではない接続経由で接続する必要があることを意味します。Cdn 宛ての要求などの特定のトラフィックをルーティングする方法の詳細については、 [Office 365 のネットワーク トラフィックの管理](routing-with-expressroute.md)を参照してください。
  
戻るを使用することができます短いリンクを以下に示します。[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>関連項目

[Office 365 エンドポイントに関する FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
