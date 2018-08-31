---
title: Office 365 のネットワークと移行の計画
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: ネットワークの計画とテストに関する情報へのリンクと Office 365 への移行が含まれています。
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223059"
---
# <a name="network-and-migration-planning-for-office-365"></a>Office 365 のネットワークと移行の計画

この資料には、ネットワークの計画とテストに関する情報へのリンクと Office 365 への移行が含まれています。
  
初めて展開したり、Office 365 に移行したりする前に、これらのトピックの情報を使って必要な帯域幅を見積もってから、Office 365 に展開または移行するだけの十分な帯域幅があることをテストし、確認します。

||
|:-----|
| この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)の一部です。|

|||
|:-----|:-----|
|![エンタープライズ設計者のポスターのクラウドのネットワークを参照してください。](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|、Office 365 とその他のマイクロソフトのクラウド プラットフォームおよびサービスのネットワークを最適化するための手順は、[エンタープライズ設計者向けのマイクロソフト クラウド ネットワーク](https://aka.ms/cloudarchnetworking)のポスターを参照してください。 |
   
## <a name="estimate-network-bandwidth-requirements"></a>ネットワーク帯域幅の要件を見積もる
<a name="EstimateBandwidthRequirements"> </a>

Office 365 を使用すると、組織のインターネット回線の使用率が向上します。現在利用可能な帯域幅は、Office 365 が少なくとも 20% のまま、完全に展開した後に予想される増加を処理するために十分なかどうかを決定することが重要、最もよく利用される日の処理能力です。
  
帯域幅を見積もるには、次の手順に従います。
  
1. 各インターネット出口を使用するクライアントの数を評価します。マルチ terabit ネットワーク処理の可能な接続を使用できます。 
    
2. Office 365 のサービスや機能を使用するクライアントに対して使用されますを決定します。グループのさまざまなサービスや利用状況プロファイルを持つユーザーが見込まれます。
    
3. クライアントのパイロット グループのネットワークの使用を測定します。パイロットのクライアントは、別の地理的な場所と同様に、組織内のユーザーのさまざまなプロファイルの担当者を確認します。ことができますクロス チェック結果、古い計算機に対して[交換](https://go.microsoft.com/fwlink/p/?LinkId=321550)と[ビジネス用の Skype](https://go.microsoft.com/fwlink/p/?LinkId=321551)または当社独自のネットワークで実行して、[ケース ・ スタディ](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)用です。 
    
4. パイロット グループからの測定値を使用して、組織全体のニーズを推定して、ネットワークに変更を加える前に、見積もりを検証するテストを再度実行します。
    
## <a name="test-your-existing-network"></a>既存ネットワークをテストします。
<a name="calculators"> </a>

 **ネットワーク ツールです**。テストし、ダウンロード、アップロード、および待機時間の制約を確認するのには、インターネットの帯域幅を検証します。これらのツールを使用すると、移行のためには」と「完全に展開している後に、ネットワークの機能を判断しますできます。 
  
- [Microsoft メッセージ アナライザー](https://technet.microsoft.com/library/jj649776.aspx): メッセージのアナライザーは、ネットワークの問題のトラブルシューティングのための効果的なツールです。メッセージ アナライザーをキャプチャが表示され、プロトコル ベースのメッセージング トラフィックとシステム メッセージを分析します。メッセージ アナライザーを使用して、インポート、集計、およびログ ファイルとトレース ファイルからデータを分析することもできます。
    
- [Microsoft リモート接続アナライザー](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange のオンライン環境での接続をテストします。
    
- Outlook と Office 365 の問題を解決するの[Microsoft のサポート、および Office 365 の回復時のアシスタント](https://diagnostics.office.com/#/Download?env=SOC)を使用します。 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Best practices for network planning and improving migration performance for Office 365
<a name="BestPractices"> </a>

パフォーマンスについて少し掘り下げて、Office 365 の満足度の向上の詳細については、これらのベスト プラクティスにします。
  
1. ユーザーをすぐに支援を開始するか。含む SharePoint Online Exchange Online では、Lync オンラインでは、ネットワークだけで協力されていない場合、Office 365 の使用に関するヒントについては、[低速のネットワーク上の Office 365 を使用するためのベスト プラクティス](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)を参照してください。この資料では、リンク先を TechNet および Support.office.com 上のコンテンツの読み込みを Office 365 のエクスペリエンスを最適化し、簡単に、web ページおよび Internet Explorer の設定を Office 365 で利用する最適な方法をカスタマイズする方法に関する情報が含まれています。 
    
2. 安全に Office 365 のトラフィックを管理し、最高のパフォーマンスを取得するための接続の原理を理解するのには[Office 365 のネットワーク接続性の原則](https://aka.ms/o365networkingprinciples)を参照してください。この資料では Office 365 のネットワーク接続を安全に最適化するため、最新のガイダンスを理解できます。 
    
3. メールの移行のパフォーマンスを向上するには、Windows の更新プログラムのスケジュールを慎重に管理します。バッチ処理でクライアント コンピューターを更新し、すべてのクライアント コンピューターがネットワークの帯域幅の使用を規定するのには Office 365 に移行する前に更新されていることを確認できます。詳細については、[手動で更新し最新の更新プログラムの Office 365 のデスクトップの構成](https://support.microsoft.com/gp/office-2013-365-update)を参照してください。
    
4. ネットワークのトラフィックを office 365 は、信頼できるインターネット サービスとして扱われ、多くの従来のフィルタ リングや信頼されていないインターネット サービスへのネットワーク トラフィックの一部の組織に配置するスキャンをバイパスすることが、ときに発揮します。送信プロキシ ユーザーの認証とパケットの検査などの処理し同様に適切なネットワーク アドレス変換 (NAT) と十分な帯域幅の容量増加を処理するためにインターネットへのローカル出口の確保を削除することがあります。ネットワークに要求します。ネットワーク上の信頼できるインターネット サービスとして Office 365 を処理するためにネットワークの構成に関する追加のガイダンスについては、 [Office 365 の管理のエンドポイント](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)に参照してください。
    
1. [Office 365 の管理の端点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)を確認します。Office 365 に追加のトラフィックは、TLS または SSL 経由で、アウト バウンド プロキシ接続の増加とセキュリティで保護されたトラフィックが増加になります。
    
2. アウト バウンド プロキシがユーザー認証を必要とする場合、接続が低速または機能の損失が発生することがあります。Office 365 のドメインの認証の要件をバイパスすると、このオーバーヘッドを軽減できます。
    
3. 大量の予定表とメールボックスを共有している場合は、Outlook から Exchange への接続数が増加する可能性があります。たとえば、Outlook クライアントは、使用中の共有の予定表ごとに 2 つまでの追加の接続を開くことができます。この場合は、出口プロキシが接続を処理できることを保証するか、Outlook の Office 365 への接続用のプロキシをバイパスします。
    
4. パブリック IP アドレスのサポートされているデバイスの最大数と複数の IP アドレスの間で負荷を分散する方法を決定します。詳細については、 [NAT は、Office 365 のサポート](nat-support-with-office-365.md)を参照してください。
    
5. 接続性とパフォーマンスが場合は、ネットワーク上のコンピューターからの送信接続を調べているが向上、Office 365 のドメインにこのフィルターをバイパスします。さらに、送信頻度を検査をバイパスしてインターネット出口を 1 つの必要性を削除し、Office 365 の宛先のネットワーク要求をローカルのインターネット出力を有効にします。
    
6. 一部のお客様は、パフォーマンスに影響を与える可能性があります内部ネットワークの設定を検索します。オート ・ ネゴシエーションまたは自動検出、ネットワークの最大転送ユニット (MTU) のサイズなどの設定、インターネットへの最適のルートは一般的な場所です。
    
## <a name="network-planning-reference-for-office-365"></a>Office 365 のネットワーク計画の参照
<a name="NetReference"> </a>

これらのトピックには、Office 365 ネットワークの詳細なリファレンス情報が含まれます。
  
- [Office 365 エンドポイントを管理します。](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [クライアント接続](client-connectivity.md)
    
- [コンテンツ配信ネットワーク](content-delivery-networks.md)
    
- [Office 365 の外部のドメイン ネーム システムのレコード](external-domain-name-system-records.md)
    
- [Office 365 サービスでの IPv6 サポート](ipv6-support.md)
    
- [Office 365 ネットワーク接続の原則](https://aka.ms/o365networkingprinciples)
    
- [Microsoft 仮想アカデミー: Office 365 のパフォーマンス管理](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [Office 365 ビデオ ネットワークのよく寄せられる質問 (FAQ)](office-365-video-networking-faq.md)
    
- [Office 365 サービスに接続するネットワーク デバイスの計画](plan-for-network-devices.md)
    
- [Office 365 サービスの展開アドバイザー](deployment-advisors-for-office-365.md)
    

