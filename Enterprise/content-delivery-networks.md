---
title: コンテンツ配信ネットワーク
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
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
description: この情報を使用して、コンテンツ配信ネットワーク (cdns) と、Office 365 がそれらを活用する方法について説明します。
ms.openlocfilehash: 50f28e8311a501d9bc5b3f2c709fa84b1633e418
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "30636098"
---
# <a name="content-delivery-networks"></a>Content Delivery Network

このトピックの情報は、コンテンツ配信ネットワーク (cdns) と、それらが Office 365 でどのように使用されるかについて理解するのに役立ちます。

cdns は、エンドユーザーにとって Office 365 を高速かつ信頼性の高い状態に保つことができます。 Office 365 などのクラウドサービスは、cdns を使用して、ダウンロードを高速化し、待機時間を短縮するために、静的なアセットをブラウザーの近くにキャッシュします。 パブリック cdns は、javascript ファイル、アイコン、画像などの一般的なコンテンツのダウンロードを高速にしますが、プライベート cdns は、ビデオや SharePoint Online ドキュメントライブラリなどのユーザーコンテンツに高速かつ安全にアクセスできるようにすることができます。
  
 **に戻る**[Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)。
  
## <a name="what-exactly-is-a-cdn"></a>完全に CDN とは何ですか。

cdns は、ほとんどのエンタープライズクラウドサービスで使用されます。 Office 365 のようなクラウドサービスには、多数のユーザーが所有するコンテンツ (メールなど) と汎用コンテンツ (アイコンなど) を同時にダウンロードします。 ユーザーのコンピューターにできるだけ近づけるように、すべてのユーザーがアイコンを使用して、画像を追加する方が効率的です。 それでも、すべてのクラウドサービスで、この汎用コンテンツをあらゆる大都市領域に保存する CDN データセンター、または世界中の主要なインターネットハブすべてにおいて、どのような CDN データを格納するのかは実用的ではありません。一部の cdns は共有されています。
  
cdns はプライベートまたはパブリックにすることができます。 プライベート cdns は1つの会社によって所有され、運用されており、その企業のアプリケーションとサービスだけが使用できます。 パブリック cdns は、複数の会社に使用をリースしている企業によって実行されます。 どこにいるかによっては、office 365 が office 365 が所有および実行する CDN、パブリック CDN、または両者の組み合わせを使用して、一般的な画像をダウンロードするのが最も効率的な場合があります。 使用される CDN の種類に関係なく、データを取得する手順は同じです。
  
1. クライアントは、Office 365 のデータを要求します。

2. Office 365 は、クライアントにデータを直接返すか、クライアントを CDN にします。

3. データが既に cdn でキャッシュされている場合、クライアントは、インターネット上のクライアントに、最も近い cdn の場所からデータを直接ダウンロードします。

4. データが cdn でキャッシュされていない場合、cdn ノードは Office 365 のデータを要求してから、クライアントがデータをダウンロードしてからデータをキャッシュします。

cdns は、最も近い Office 365 データセンターからファイルとイメージを取得し、クライアントは最も近い CDN からファイルとイメージを取得します。 ユーザーがクラウドサービスにアクセスしているときに、Outlook Web App での電子メールの読み取りなど、ユーザーのブラウザーは Office 365 データセンターからファイルとイメージを取得しようとします。 Office 365 は、ファイルを配信する時間と帯域幅を費やす代わりに、ブラウザーを CDN にリダイレクトします。 CDN は、ユーザーのブラウザーに最も近いデータセンターを特定し、リダイレクトを使用してそこから標準の画像をダウンロードします。 この CDN リダイレクトの使用は短時間で、ユーザーはダウンロード時間を大幅に節約できます。

## <a name="how-do-cdns-make-services-work-faster"></a>cdns を使用してサービスを高速化する方法

アイコンなどの一般的な情報をもう一度ダウンロードすると、電子メールやドキュメントなどの重要な個人コンテンツをダウンロードするために使用できるネットワーク帯域幅が必要になることがあります。 Office 365 は cdns を含むアーキテクチャを使用しているため、アイコン、スクリプト、およびその他の汎用コンテンツをサーバーからクライアントコンピューターに近い場所にダウンロードして、ダウンロードを高速化することができます。 これは、Office 365 データセンターに安全に格納されている個人コンテンツへのアクセスが高速になることを意味します。

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Office 365 で cdns が最適に機能するように、どのようにネットワークをセットアップする必要がありますか?

[Office 365 へのネットワーク接続](network-connectivity.md)を計画している場合は、一般的な cdns のしくみ、および CDN ネットワークトラフィックの管理方法を理解しておくことをお勧めします。

Office 365 テナントに対して cdn を有効にする場合は、まず、コンテンツソース (cdns のコンテキストでは**オリジン**と呼ばれます)、cdn に配布するデータ分類、またはファイルの種類を管理するポリシーを設定します。 指定したコンテンツにアクセスするユーザーは、CDN 内のファイルの最も近い場所にリダイレクトされます。 そのため、「 [Office 365 エンドポイントの管理](managing-office-365-endpoints.md)」で説明されているベストプラクティスを使用して、ネットワークの構成で、クライアントブラウザーが中央のプロキシを介して cdn トラフィックをルーティングするのではなく、直接 cdn にアクセスできるようにする必要があります。不要な待機時間の概要。

## <a name="is-my-data-safe"></a>データは安全ですか?

当社では、ビジネスを実行するデータを確実に保護するために十分に注意してください。 cdns に格納されている顧客固有のデータは、送信と保存の両方で暗号化されます。

> [!NOTE]
> CDN プロバイダーには、Office 365 セキュリティセンターで規定されているコミットメントとは異なるプライバシーとコンプライアンスの標準があります。 CDN サービスを使用してキャッシュされたデータは、Microsoft データ処理条件 (DPT) に準拠していない可能性があり、Office 365 セキュリティセンターのコンプライアンス境界の外にある場合があります。

Office 365 CDN プロバイダーのプライバシーとデータ保護の詳細については、以下を参照してください。  

+ office 365 のプライバシーとデータ保護の詳細については、「 [Microsoft Trust Center」](https://www.microsoft.com/trustcenter)を参照してください。
+ azure のプライバシーとデータ保護の詳細については、「 [azure のセキュリティセンター」](https://azure.microsoft.com/en-us/overview/trusted-cloud/)を参照してください。
+ akamai のプライバシーとデータ保護の詳細については、「 [akamai privacy セキュリティセンター」](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)を参照してください。

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>これらのサードパーティ製サービスを使用してネットワークをセキュリティで保護するにはどうすればよいですか?

一連のパートナーサービスを活用することにより、office 365 は、office 365 を使用しているときに、可用性の要件を拡大縮小し、ユーザーの利便性を向上させることができます。 サードパーティ製サービスの Office 365 では、両方の証明書失効リストが含まれています。crl.microsoft.com、sa.symcb.com、cdns など。r3.res.outlook.com など。 office 365 で使用されるすべての CDN fqdn は、office 365 のカスタム fqdn です。 Office 365 の要求で fqdn に送信した場合は、CDN プロバイダーが fqdn およびその場所の基になるコンテンツを制御することができます。
  
サードパーティに対する要求から Microsoft または office 365 データセンター宛ての要求を分離する必要があるお客様のために、 [office 365 エンドポイントの管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)に関するガイダンスを作成しました。

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Office 365 で使用されるすべての cdns の一覧はありますか。

Office 365 で使用されている cdns は常に変更される可能性があり、多くの場合、イベント1に構成されている複数の CDN パートナーが利用できなくなっています。 使用されているプライマリの cdns は次のとおりです。

+ [Office 365 (特に SharePoint Online コンテンツ用)](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)
+ [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)
+ [Akamai](https://www.akamai.com/us/en/cdn.jsp)

これらの CDN ソリューションには、世界のより多くの隅へのサービスの到達を拡張するグローバルなものがあります。 そこに格納されるコンテンツには、一般的な Office 365 スクリプト、ファイル、およびイメージが含まれています。 たとえば、portal.office.com にログオンすると、ページの読み込み時間を短縮するために、最も近い CDN から画像が送られます。 その他の例としては、office 365 ProPlus に、インストールビットを CDN に格納して、最新バージョンの office をダウンロードするのにかかる時間を短縮することがあります。

Office 365 ビデオ用のビデオファイルなど、cdns に格納されている独自のコンテンツもあります。 ビデオをアップロードすると、ファイルは暗号化され、Azure Media Services で暗号化された形式で保存されます。 Office 365 video player がビデオを取得すると、ビデオのダウンロードにかかる時間を短縮するために、ダウンロードする前に最も近い CDN にキャッシュされます。

office 365 CDN の使用方法については、「 [SharePoint Online で office 365 コンテンツ配信ネットワークを使用](use-office-365-cdn-with-spo.md)する」を参照してください。

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>cdns を利用する fqdn の一覧はありますか。

fqdn の一覧と、時間の経過と共に cdns の変更をどのように活用するかについては、「公開された[Office 365 の url と IP アドレスの範囲](https://go.microsoft.com/fwlink/p/?LinkID=293744)」ページを参照して、cdns を活用する最新の fqdn を最新の状態にします。

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>自分の CDN を使用して、ローカルネットワーク上でコンテンツをキャッシュすることはできますか。

お客様のニーズに対応するための新しい方法が絶えず模索されており、現在、キャッシュプロキシソリューションやその他のオンプレミスの CDN ソリューションの使用方法について調査しています。

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Office 365 用の Azure ExpressRoute を使用していますが、変更はありますか?

[office 365 用の Azure ExpressRoute](azure-expressroute.md)は、パブリックインターネットから分離された office 365 インフラストラクチャへの専用の接続を提供します。 この場合も、クライアントは、expressroute 以外の接続を介して接続して、expressroute でサポートされているサービスの一覧に明示的に含まれていない他の Microsoft インフラストラクチャに接続する必要があります。 cdns に対する要求など、特定のトラフィックをルーティングする方法の詳細については、「 [Office 365 ネットワークトラフィック管理](routing-with-expressroute.md)」を参照してください。
  
ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>関連項目

[Office 365 エンドポイントの管理](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[Office 365 の URL と IP アドレスの範囲](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[SharePoint Online での Office 365 コンテンツ配信ネットワークの使用](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Microsoft Trust Center](https://www.microsoft.com/trustcenter)