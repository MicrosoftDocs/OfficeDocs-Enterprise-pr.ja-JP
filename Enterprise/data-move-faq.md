---
title: データ移行についての一般的な FAQ
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: ここでは、コア データを新しいデータセンター geo に移行することについての一般的な質問に対する回答を示します。
ms.openlocfilehash: 29706f49ee0faf8c535b50843f224b7b1b2a372e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067902"
---
# <a name="data-move-general-faq"></a>データ移行についての一般的な FAQ

ここでは、コア データを新しいデータセンター geo に移行することについての一般的な質問に対する回答を示します。
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>移行をリクエストする対象となるのは、どんなお客様ですか?
  
新しいデータセンター geo の対象となる国を選択した既存の Office 365 の商用ユーザーは、移行をリクエストできます。  このプログラムは、Office 365 テナントに割り当てられている資格のある国コードを持つテナントにのみ存在し、対応する Office 365 データセンター geo への適用可能なワークロードに対して、コア顧客データを移行します。  「[データの移動を要求する](request-your-data-move.md)」ページを参照して、国の適格性を確認してください。   

## <a name="how-do-we-define-core-customer-data"></a>重要な顧客データをどのように定義するか。
 
コア顧客データは、 [Microsoft Online Services の用語](https://go.microsoft.com/fwlink/p/?LinkID=249048)で定義されている顧客データのサブセットを参照する用語です。 
- Exchange Online メールボックスのコンテンツ (電子メール本文、予定表のエントリ、電子メールの添付ファイルの内容)
- SharePoint Online サイトのコンテンツと、そのサイト内に格納されているファイル
- OneDrive for business にアップロードされたファイル 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>移行が完了した時点で、テナントのコア顧客データが新しい geo に保存されます。

Exchange Online と SharePoint Online/OneDrive for Business の間で共有される依存関係により、両方のサービスが移行されるまで、移行を完了しないことを考慮することはできません。  Exchange Online と SharePoint Online または OneDrive for Business は、多くの場合、別々の時間に個別に移行されます。  テナント管理者は、各サービスの移行が完了すると、メッセージセンターで確認を受け取り、管理センターでデータの場所カードを表示することができます。

## <a name="will-my-tenant-automatically-be-moved-to-the-new-datacenter-geo"></a>自分のテナントは新しいデータセンター geo に自動的に移動しますか?
 
テナント管理者として実行できるアクションは2つあります。

- オプトイン。Office 365 引っ越しプログラムに登録し、お客様のサービスが主要な顧客データを新しいデータセンター geo に移行するための、コミットされた期限を受け取ります。プログラムにオプトインする方法については、「[データの移動を要求する方法](request-your-data-move.md)」ページを参照してください。
- 何もしません。何もしないでください。 Microsoft は、サービスの管理と最適化の一環として、お客様の主要な顧客データを時間の経過と共に新しいデータセンター geo に移行できます。データは、他の geo ではなく、新しいデータセンター geo にのみ移行する可能性があります。このようなサービス管理移動が完了すると、メッセージセンター経由で通知を行います。

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>どのように確実に移行中の顧客データを保護し、ダウンタイムが発生しないようにするのですか?
  
データの移動は、エンドユーザーへの影響を最小限に抑えたバックエンドのサービス操作です。 影響を受ける可能性がある機能は、[データの移行中および移行後](during-and-after-your-data-move.md)に一覧に表示されます。 Microsoft は、 [Microsoft Online Services のサービスレベル契約 (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897)を利用できるようにしています。そのため、移行中にお客様が準備や監視を行う必要はありません。 
  
Office 365 サービスは、どのデータセンターでもすべて同じバージョンが実行されるため、機能の一貫性が確保されます。このプロセス中、サービスは完全にサポートされます。
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>異なる geo に異なるサービスがあることには、どんな影響がありますか?

一部の Office 365 サービスは、既存のお客様や、移動プロセスの途中にあるお客様の geo によって異なる場合があります。  これらのサービスは互いに独立して実行されます。この場合、ユーザーの利便性に影響を与えることはありません。ただし、データ常駐を目的として、Exchange Online と SharePoint Online/OneDrive for business の両方が同じデータセンター geo に移行されるまで、テナントの移行を完了することはできません。
  
## <a name="will-new-office-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a>新しい Office 365 のユーザーは自動的に新しいデータセンター geo でプロビジョニングされますか?
  
はい。 新しいデータセンター geo を利用できるようになると、新しい365支社では、新規の geo の資格がある国を登録時に国として選択すると、新しいデータセンター geo に保存されている重要な顧客データが含まれます。
  
 ## <a name="where-is-my-core-customer-data-is-located"></a>コア顧客データはどこにありますか?

テナント管理者は、管理センターのデータの場所カードを表示して、いつでも各サービスの保存場所にある主要な顧客データを確認することができます (特にそのテナントの場合)。また、データセンターの geo、データセンター、および office 365 の顧客365データの場所を、新しいテナントの保存場所にある現在の既定のコア顧客データの参照として公開しています。  Office 365 管理センターの組織プロファイルの下にある [データの場所] セクションを使用して、お客様のデータの場所を確認できます。  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>いつから移行をリクエストできますか?
  
データセンター geo のサポート対象期間については、「[データの移動を要求する](request-your-data-move.md)」ページを参照してください。
  
## <a name="how-can-i-request-to-be-moved"></a>どのように移行をリクエストしますか?
  
対象となるお客様には、[Office 365 管理ポータル](https://portal.office.com/)のページが表示されます。 移行をリクエストする手順については「[データ移行をリクエストする方法](request-your-data-move.md)」をご覧ください。 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>移行をリクエストした後で自分の決定を変更できますか?
  
リクエストを送信した後に、Microsoft 側で移行プロセスからお客様を削除することはできません。
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>期限までに移行をリクエストしないと、どうなりますか?
  
 移行を完了するために、テナントにコミット期限を付与するために、例外ベースで要求を受け入れることができる場合があります。  [Office 365 サポート](https://go.microsoft.com/fwlink/p/?LinkID=522459)に連絡して、要求を行ってください。  Microsoft では、サービスの管理と最適化の一環として、お客様の主要な顧客データを時間の経過と共に新しいデータセンター geo に移行することはできませんが、一部のワークロードは新しい geo に移行する可能性があることを思い出してください。データは、他の geo ではなく、新しいデータセンター geo にのみ移行する可能性があります。  このようなサービス管理移動が完了すると、メッセージセンター経由で通知を行います。
  
 ## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>ネットワークのパフォーマンスを向上するために、データを移動したらどうなりますか?
  
Office 365 データセンターに近づいても、ネットワークのパフォーマンスが向上するわけではありません。 エンド ユーザーと Office 365 サービス間のネットワークのパフォーマンスに影響を及ぼす要因とコンポーネントは数多くあります。 このおよびパフォーマンスのチューニングの詳細については、「 [Office 365 のネットワーク計画とパフォーマンスチューニング](network-planning-and-performance.md)」を参照してください。
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a>すべてのサービスは同じ日にデータを移行しますか?
 
各サービスは独立して移動するため、データは異なる時間に移行される可能性があります。
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>データを移行する時期を自分で選ぶことはできますか?
 
 Microsoft が移行の具体的な日付や期間を共有することもできません。
  
 ## <a name="can-you-share-when-my-data-will-be-be-moved"></a>データの移動時に共有することは可能ですか?
  
データの移行は、エンドユーザーへの影響を最小限に抑えたバックエンドの操作です。 グローバルに操作され自動化された環境内でデータ移動を実行する際に必要になる複雑さ、精度およびスケールは、テナントまたはその他の任意の単一テナントがデータ移動の完了を期待しているときに、共有の妨げになります。 お客様のデータ移動が完了すると、お客様はメッセージ センターで、参加しているサービスごとに 1 つの確認メッセージを受信します。 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>データの移行中に、ユーザーがサービスにアクセスすると、どうなりますか?

各サービスのデータの移行中に制限される機能の詳細な一覧については「[データの移行中および移行後](during-and-after-your-data-move.md)」を参照してください。 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a>移行が完了したことはどのようにわかりますか?
  
各サービスのデータの移行が完了したことを確認するために、Office 365 メッセージセンターを見てください。 各サービスのデータが移動されると、完了通知が送信されます。1つは、Exchange Online、SharePoint Online、Skype for Business Online の3つの完了通知です。  また、Office 365 管理センターの組織プロファイルの下にある [データの場所] セクションを使用して、お客様のデータの場所を確認することもできます。  
  
## <a name="i-am-an-office-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>私は新しいデータセンター geo にいる Office 365 のユーザーですが、サインアップ時には別の国を選択しました。 新しいデータセンター geo に移行するにはどうすればよいですか?

テナントに関連付けられているサインアップ国を変更することはできません。 代わりに、新しいサブスクリプションで新しい Office 365 テナントを作成し、ユーザーとデータを手動で新しいテナントに移行する必要があります。
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-office-365-during-the-exchange-online-move"></a>Exchange Online の移行中にメール データの Office 365 への移行が進行中の場合、どんなことが生じますか?

これは非常に一般的なシナリオであり、完全にサポートされています。  データセンター geo 間のクラウドの移行では、オンプレミスとの間ではクラウドメールボックスの移行が妨げられることはありません。
  
 ## <a name="can-i-pilot-some-users"></a>一部のユーザーを先に移行できますか?
  
接続をテストするために別の試用版テナントを作成することはできますが、試用版テナントと既存のテナントを統合することはできません。

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Microsoft がデータを移動するのを待つ必要はありません。 新しいテナントを作成して自分で移行することはできますか?
  
だたし、プロセスは Microsoft がデータ移行を実行するときと同じようにシームレスではありません。
  
新しいデータセンター geo が利用可能になった後に新しいテナントを作成すると、新しいテナントは新しい geo でホストされます。この新しいテナントは以前のテナントとは完全に別個のものであり、すべてのユーザー メールボックス、サイトのコンテンツ、ドメイン名、その他のデータの移行をお客様自身の責任で実行していただくことになります。なお、テナント名は 1 つのテナントから別のテナントへ移行できないことに注意してください。Microsoft によって提供される移行プログラムをお待ちいただくことをお勧めします。すべての設定、データ、ユーザーのサブスクリプションの移行は、弊社にお任せください。
  
 ## <a name="im-not-ready-to-be-moved-can-i-pick-a-specific-move-date"></a>移動の準備ができていませんが、特定の移動日を選択することはできますか?
  
いいえ、各サービスの主要な顧客データが移動されるときに変更することはできません。
  
 ## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>私の顧客データは新しいデータセンター geo に既に移行しました。 戻すことはできますか?
 
いいえ、これはできません。 新しい geo のデータセンターに移行したお客様は、元の geo に戻ることはできません。 任意の geo の顧客として、サービスの品質、パフォーマンス、およびセキュリティ コントロールに関して、これまでと同様のエクスペリエンスを得ることができます。  [Office 365 の複数地域](https://aka.ms/multi-geo)は、一部のお客様がアドオンとして利用でき、1つのテナントで複数のサテライト geo を作成し、データ常駐責任を持つ geo にユーザーデータを移動することができます。
  
 ## <a name="do-the-new-datacenter-geos-use-the-same-versions-of-office-365-services-as-the-current-datacenter-geos"></a>新しいデータセンター geo では、現在のデータセンター geo と同じバージョンの Office 365 サービスを使いますか?

はい。
  
## <a name="will-office-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>新しいデータセンターでホストされる Office 365 テナントは、国外のユーザーも利用できますか?
  
A. はい。 Microsoft は、世界中の35国に130以上の場所でパブリックインターネット接続を使用する大規模なグローバルネットワークを維持しています。これには、2700を超えるインターネットサービスプロバイダー (Isp) とのピアリング契約があります。 インターネット上のどの場所にいるユーザーでも、データセンターにアクセスできます。

## <a name="my-tenant-is-configured-for-office-365-multi-geohttpsakamsmulti-geo--can-i-still-enroll-in-my-tenant-in-the-office-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>My テナントは、 [Office 365 の複数 Geo](https://aka.ms/multi-geo)に対して構成されています。  Office 365 の移動プログラムで自分のテナントに登録したままにして既定の geo を変更し、サテライト地域にないユーザーを新しい既定の geo に移動することはできますか。

はい。テナントは登録する資格があります。  現在の既定の地域から新しいローカルデータセンター geo にすべての EXO メールボックスを移動します。  複数地域のサテライト地域で構成されている EXO メールボックスは、意図したとおりに、衛星地域のデータ常駐を引き続き尊重するように移行されません。  SharePoint Online と OneDrive for business は、移動プログラムの一部として新しいデータセンター geo に移行できませんが、OneDrive for Business 共有を構成して、複数地域プログラムで任意の場所に移動することができます。
  
## <a name="related-topics"></a>関連項目

[コアデータを新しい Office 365 データセンター geo に移行する](moving-data-to-new-datacenter-geos.md)

[データ移行をリクエストする方法](request-your-data-move.md)

[Office 365 複数地域](https://aka.ms/multi-geo)

[Office 365 interactive datacenter map](https://office.com/datamaps)

[Office 365 サポート](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[Microsoft Dynamics CRM Online の新しいデータ センター geo](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure のリージョン](https://azure.microsoft.com/en-us/regions/)
