---
title: データ移行についての一般的な FAQ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
f1.keywords:
- NOCSH
description: ここでは、コア データを新しいデータセンター geo に移行することについての一般的な質問に対する回答を示します。
ms.openlocfilehash: 2954d85b0094a8d0f74980fa4e0ee9cac504abbe
ms.sourcegitcommit: e0603d9259e9be1aeb110fc3dd8b9abc6138c55d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44781042"
---
# <a name="data-move-general-faq"></a>データ移行についての一般的な FAQ

ここでは、コア データを新しいデータセンター geo に移行することについての一般的な質問に対する回答を示します。
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>移行をリクエストする対象となるのは、どんなお客様ですか?
  
新しいデータセンター geo の対象となる国を選択した既存の Microsoft 365 コマーシャルお客様は、移行を要求できます。  このプログラムは、Microsoft 365 テナントに割り当てられた有効な国コードを使用しているテナントにのみ存在し、これに該当する Microsoft 365 データセンター geo に適用可能なワークロードのために、主要な顧客データを移行します。  「[データの移動を要求する](request-your-data-move.md)」ページを参照して、国の適格性を確認してください。   

## <a name="how-do-we-define-core-customer-data"></a>重要な顧客データをどのように定義するか。
 
コア顧客データは、 [Microsoft Online Services の用語](https://aka.ms/ost)で定義されている顧客データのサブセットを参照する用語です。 
- ExchangeOnline メールボックスのコンテンツ (メール本文、予定表のエントリ、メール添付ファイルのコンテンツ)
- SharePoint Online サイトのコンテンツと、そのサイト内に格納されているファイル
- OneDrive for Business にアップロードしたファイル 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>移行が完了した時点で、テナントのコア顧客データが新しい geo に保存されます。

Exchange Online と SharePoint Online/OneDrive for Business の間で共有される依存関係により、両方のサービスが移行されるまで、移行を完了しないことを考慮することはできません。  Exchange Online と SharePoint Online または OneDrive for Business は、多くの場合、別々の時間に個別に移行されます。  テナント管理者は、各サービスの移行が完了すると、メッセージセンターで確認を受け取り、管理センターでデータの場所カードを表示することができます。

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>どのように確実に移行中の顧客データを保護し、ダウンタイムが発生しないようにするのですか?
  
データの移動は、エンドユーザーへの影響を最小限に抑えたバックエンドのサービス操作です。 影響を受ける可能性がある機能は、[データの移行中および移行後](during-and-after-your-data-move.md)に一覧に表示されます。 Microsoft は、 [Microsoft Online Services のサービスレベル契約 (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897)を利用できるようにしています。そのため、移行中にお客様が準備や監視を行う必要はありません。 
  
すべての Microsoft 365 サービスは、データセンターで同じバージョンを実行するので、一貫性のある機能が保証されます。 このプロセス中、サービスは完全にサポートされます。

## <a name="what-is-in-scope-for-teams-migration"></a>Teams の移行の範囲について

Exchange Online、SharePoint Online、OneDrive for Business に加えてMicrosoft は、Teams データをローカルデータセンターに移行します。  
- Teams のチャットメッセージ (プライベートメッセージやチャネルメッセージを含む)。 
- チャットで使用される Teams 画像。 

Teams ファイルは SharePoint Online に格納され、Teams チャットファイルは OneDrive for Business に保存されます。  ボイスメール、予定表、チャット履歴、および連絡先は、Exchange Online に格納されます。  多くの場合、Exchange Online、SharePoint Online、OneDrive for Business は、ローカルのデータセンター geo のお客様によって既に使用されており、資格のあるお客様の国の Microsoft 365 移行プログラムの一部でもあります。
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>異なる geo に異なるサービスがあることには、どんな影響がありますか?

一部の Microsoft 365 サービスは、既存のお客様や、移行プロセスの途中にあるお客様の geo によって異なる場合があります。 これらのサービスは互いに独立して実行されるため、そのような場合にユーザーの利便性に影響を与えることはありません。ただし、データ常駐を目的として、Exchange Online と SharePoint Online/OneDrive for business の両方が同じデータセンター geo に移行されるまで、テナントの移行を完了することはできません。
  
## <a name="will-new-microsoft-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a>新しい Microsoft 365 顧客は新しいデータセンター geo で自動的にプロビジョニングされますか。
  
はい。 新しいデータセンター geo を使用できるようになると、新規の地域の地域を選択した新しい Microsoft 365 のお客様は、新しい地域の geo に保存されている重要な顧客データを新しいデータセンター geo に格納することになります。
  
 ## <a name="where-is-my-core-customer-data-located"></a>重要な顧客データはどこにありますか?

テナント管理者は、管理センターのデータの場所カードを表示して、いつでも各サービスの保存場所にある主要な顧客データを確認することができます (特にそのテナントの場合)。また、データセンターの geo、データセンター、および Office 365 の顧客 [365](https://office.com/datamaps)データの場所を、新しいテナントの保存場所にある現在の既定のコア顧客データの参照として公開しています。  Microsoft 365 管理センターの組織プロファイルの下にある [データの場所] セクションを使用して、お客様のデータの場所を確認できます。  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>いつから移行をリクエストできますか?
  
データセンター geo のサポート対象期間については、「[データの移動を要求する](request-your-data-move.md)」ページを参照してください。
  
## <a name="how-can-i-request-to-be-moved"></a>どのように移行をリクエストしますか?
  
対象となるお客様には、 [Microsoft 365 管理センター](https://admin.microsoft.com/)にページが表示されます。 移行をリクエストする手順については「[データ移行をリクエストする方法](request-your-data-move.md)」をご覧ください。 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>移行をリクエストした後で自分の決定を変更できますか?
  
リクエストを送信した後に、Microsoft 側で移行プロセスからお客様を削除することはできません。
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>期限までに移行をリクエストしないと、どうなりますか?
  
例外ベースで要求を受け入れ、移行を完了するためにテナントにコミット期限を付与することができます。   [Microsoft 365 サポート](https://go.microsoft.com/fwlink/p/?LinkID=522459)に連絡して、要求を行ってください。

## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>ネットワークのパフォーマンスを向上するために、データを移動したらどうなりますか?
  
Microsoft 365 データセンターへの物理的な類似性は、ネットワークのパフォーマンスが向上することを保証するものではありません。 エンドユーザーと Microsoft 365 サービスとの間のネットワークパフォーマンスに影響を与えるさまざまな要素とコンポーネントがあります。 このおよびパフォーマンスチューニングの詳細については、「 [Microsoft 365 のネットワーク計画とパフォーマンスチューニング](network-planning-and-performance.md)」を参照してください。
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a>すべてのサービスは同じ日にデータを移行しますか?
 
各サービスは独立して移動するため、データは異なる時間に移行される可能性があります。
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>データを移行する時期を自分で選ぶことはできますか?
 
Microsoft が移行の具体的な日付や期間を共有することもできません。
  
 ## <a name="can-you-share-when-my-data-will-be-be-moved"></a>データの移動時に共有することは可能ですか?
  
データの移行は、エンドユーザーへの影響を最小限に抑えたバックエンドの操作です。 グローバルに操作され自動化された環境内でデータ移動を実行する際に必要になる複雑さ、精度およびスケールは、テナントまたはその他の任意の単一テナントがデータ移動の完了を期待しているときに、共有の妨げになります。 お客様のデータ移動が完了すると、お客様はメッセージ センターで、参加しているサービスごとに 1 つの確認メッセージを受信します。 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>データの移行中に、ユーザーがサービスにアクセスすると、どうなりますか?

各サービスのデータの移行中に制限される機能の詳細な一覧については「[データの移行中および移行後](during-and-after-your-data-move.md)」を参照してください。 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a>移行が完了したことはどのようにわかりますか?
  
各サービスのデータの移行が完了したことを確認するために、Microsoft 365 メッセージセンターをご覧ください。 各サービスのデータが移動されると、完了通知が送信されます。1つは、Exchange Online、SharePoint Online、Skype for Business Online の3つの完了通知です。  また、Microsoft 365 管理センターの組織プロファイルの下の [データの場所] セクションを使用して、お客様のデータの場所を確認することもできます。  
  
## <a name="i-am-a-microsoft-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>新しいデータセンター geo の1つでマイクロソフトの365ユーザーとして登録されていますが、サインアップするときに別の国を選択しました。 新しいデータセンター geo に移行するにはどうすればよいですか?

テナントに関連付けられているサインアップ国を変更することはできません。 代わりに、新しいサブスクリプションで新しい Microsoft 365 テナントを作成し、ユーザーとデータを新しいテナントに手動で移動する必要があります。
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-microsoft-365-during-the-exchange-online-move"></a>Exchange Online の移動中に Microsoft 365 への電子メールデータの移行を行っている場合はどうなりますか。

これは非常に一般的なシナリオであり、完全にサポートされています。  データセンター geo 間のクラウドの移行では、オンプレミスとの間ではクラウドメールボックスの移行が妨げられることはありません。
  
 ## <a name="can-i-pilot-some-users"></a>一部のユーザーを先に移行できますか?
  
接続をテストするために別の試用版テナントを作成することはできますが、試用版テナントと既存のテナントを統合することはできません。

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Microsoft がデータを移動するのを待つ必要はありません。 新しいテナントを作成して自分で移行することはできますか?
  
だたし、プロセスは Microsoft がデータ移行を実行するときと同じようにシームレスではありません。
  
If you create a new tenant after the new datacenter geo is available, the new tenant will be hosted in the new geo. This new tenant is completely separate from your previous tenant and you would be responsible for moving all user mailboxes, site content, domain names, and any other data. Note that you can't move the tenant name from one tenant to another. We recommend that you wait for the move program provided by Microsoft as we'll take care of moving all settings, data, and subscriptions for your users.
  
## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>私の顧客データは新しいデータセンター geo に既に移行しました。 戻すことはできますか?
 
いいえ、できません。 新しい geo のデータセンターに移行したお客様は、元の geo に戻ることはできません。 任意の geo の顧客として、サービスの品質、パフォーマンス、およびセキュリティ コントロールに関して、これまでと同様のエクスペリエンスを得ることができます。  [Microsoft 365 の複数地域](https://aka.ms/multi-geo)は、一部のお客様がアドオンとして利用でき、1つのテナントで複数のサテライト geo を作成し、データ常駐のコミットメントを使用してそれらの geo にユーザーデータを移動させることができます。
  
## <a name="will-microsoft-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>新しいデータセンターでホストされている Microsoft 365 テナントは、国外のユーザーが使用できるようになりますか。
  
はい。 Microsoft は、世界中の35国に130以上の場所でパブリックインターネット接続を使用する大規模なグローバルネットワークを維持しています。これには、2700を超えるインターネットサービスプロバイダー (Isp) とのピアリング契約があります。 インターネット上のどの場所にいるユーザーでも、データセンターにアクセスできます。

## <a name="my-tenant-has-configured-the-multi-geo-add-on-can-i-still-enroll-in-my-tenant-in-the-microsoft-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>自分のテナント[で複数地域アドオン](https://aka.ms/multi-geo)が構成されている。 Microsoft 365 の移動プログラムで自分のテナントに登録したままにして既定の geo を変更し、サテライト地域にないユーザーを新しい既定の geo に移動することはできますか。

はい。テナントは登録する資格があります。 現在の既定の地域から新しいローカルデータセンター geo にすべての EXO メールボックスを移動します。  複数地域のサテライト地域で構成されている EXO メールボックスは、意図したとおりに、衛星地域のデータ常駐を引き続き尊重するように移行されません。  

SharePoint Online と OneDrive for business は、移動プログラムの一部として新しいデータセンター geo に移行できませんが、OneDrive for Business 共有を構成して、複数地域プログラムで任意の場所に移動することができます。

## <a name="related-topics"></a>関連項目

[新しい Microsoft 365 datacenter geo へのコアデータの移動](moving-data-to-new-datacenter-geos.md)

[データ移行をリクエストする方法](request-your-data-move.md)

[Microsoft 365 複数地域](https://aka.ms/multi-geo)

[Microsoft 365 interactive datacenter map](https://office.com/datamaps)

[Microsoft 365 サポート](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[Microsoft Dynamics CRM Online の新しいデータ センター geo](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure のリージョン](https://azure.microsoft.com/regions/)
