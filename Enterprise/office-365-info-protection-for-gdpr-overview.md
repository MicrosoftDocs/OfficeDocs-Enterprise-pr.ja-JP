---
title: GDPR のための Office 365 の情報保護の概要
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: ''
description: GDPR のための Office 365 の情報保護の概要を確認します。個人データを検出、分類、保護、監視する方法について説明します。
ms.openlocfilehash: 472fa9592c87b2ccd0f684aa06b5a996e33f34c2
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914882"
---
# <a name="overview-of-office-365-information-protection-for-gdpr"></a>GDPR のための Office 365 の情報保護の概要

このソリューションでは、Office 365 サービスに保存されている機密データを保護する方法を示します。これには個人データの検出、分類、保護、監視に規定された推奨事項が含まれています。このソリューションでは、例として一般データ保護規制 (GDPR) を使用しますが、その他の多くの規制遵守のためにも同じ手順を適用することができます。

GDPR は個人データの収集、保存、処理、共有を規制します。個人データは GDPR のもとで、欧州連合 (EU) 内で特定される個人、または特定可能な個人に関連するあらゆるデータとして、非常に広範に定義されています。

記事 4: 定義

> ‘個人データ’ とは特定される個人、または特定可能な個人 (‘データ主体’) に関連するあらゆる情報であり、特定可能な個人とは、その個人の名前、ID 番号、位置データ、オンライン ID、または物理的、生理学的、遺伝子上、心理的、経済的、文化的、社会的な識別情報に固有の 1 つ以上の因子を参照することによって直接または間接的に特定される人物です。

このソリューションは組織が GDPR の対象となる Office 365 での個人データを検出し、保護するためのものです。これは GDPR のコンプライアンス構成証明としては提供されません。組織は独自に GDPR コンプライアンスを確認する責任を負うため、法務チームまたはコンプライアンス チームに問い合わせるか、コンプライアンスに特化したサード パーティに指導とアドバイスを求めることを推奨します。

[GDPR 評価](https://assessment.microsoft.com/gdpr-compliance)は迅速なオンライン自己評価ツールであり、組織はコストをかけずに、それ自体の GDPR への遵守状況の全体的なレベルを確認することができます (<http://aka.ms/gdprassessment>)。

## <a name="assess-and-manage-your-compliance-risk"></a>コンプライアンスのリスクを評価および管理する

GDPR 遵守に向けた最初の手順は、GDPR が組織に適用されるかどうか、また適用される場合はその範囲を評価することです。この分析には、組織で保持するデータとその場所を理解することが含まれます。

### <a name="step-1--use-compliance-manager-to-view-the-regulation-requirements-and-track-your-progress"></a>手順 1: コンプライアンス マネージャーを使用して規制要件を確認し、進捗状況を追跡します。

コンプライアンス マネージャーには監査制御を追跡、実装、管理するためのツールが用意されており、組織は GDPR をはじめとするさまざまな基準に対してコンプライアンスを達成することができます。

![コンプライアンス マネージャーを使用して要件を表示して進捗状況を追跡する](Media/Overview-image1.png)

詳細については、「[Service Trust Portal でコンプライアンス マネージャーを使用する](https://support.office.com/ja-JP/article/Use-Compliance-Manager-in-the-Service-Trust-Portal-Preview-5756d342-5af9-4496-82e8-4dd50fa39942)」を参照してください。 

### <a name="step-2--use-content-search-and-sensitive-information-types-to-find-personal-data"></a>手順 2: コンテンツ検索と機密情報の種類を使用して個人データを検索する 

環境内で GDPR の対象となる個人データを検出します。コンテンツ検索と機密情報の種類を組み合わせて次のようにします。

-   個人データの保存場所について、検索とレポートを実行します。

-   機密データの種類とその他のクエリを最適化して、環境内のすべての個人データを検索します。

![コンテンツ検索と機密情報の種類を使用して個人データを検索する](Media/Overview-image2.png)

機密情報の種類は、自動化されたプロセスで、健康保険番号やクレジット カード番号など、特定の情報の種類をどのように認識するかを定義するものです。この記事では、開始点として使用できるセットが含まれています。EU 加盟国の個人データについては、他にも機密情報の種類が追加される予定です。

詳細については、「[個人データの検索および検出](search-for-and-find-personal-data.md)」を参照してください。 

## <a name="classify-protect-and-monitor-personal-data-in-office-365-and-other-saas-apps"></a>Office 365 およびその他の SaaS アプリの個人データを分類、保護、監視します。

Office 365 での情報保護に使用される一部の機能は、その他の SaaS アプリケーションの機密データ保護にも使用されます。

![個人データを分類、保護、監視する](Media/Overview-image3.png)

この図はこのセクションの後半 (手順 3-5) で説明します。

### <a name="step-3--decide-if-you-want-to-use-labels-in-addition-to-sensitive-information-types"></a>手順 3: 機密データの種類の他にラベルを使用するかどうかを決定する

機密データの種類とは、分類の 1 形式です。「[個人データの分類スキーマを設計する](architect-a-classification-schema-for-personal-data.md)」を参照して、ラベルの導入を許可するかどうかを決定します。ラベルを適用するには、「[Office 365 の個人データにラベルを適用する](apply-labels-to-personal-data-in-office-365.md)」を参照してください。

この図では、機密情報の種類とラベルは Office 365 全体で機能します。今後はこれらを Cloud App Security で使用して、Box や Salesforce など他の SaaS アプリにある機密データを検索できるようになります。

### <a name="step-4--protect-personal-data-in-office-365"></a>手順 4: Office 365 の個人データを保護する 

個人データの保護は Office 365 のデータ損失防止から始まります。個人データへのアクセスを保護するには、電子メールのための Office 365 Message Encryption など、他にもいくつかの推奨機能があります。

これらの保護のターゲットは、特定のデータ セットに設定できます。

-   サイトおよびライブラリ レベルのアクセス許可

-   サイト レベルの外部共有ポリシー

-   サイトレベルのデバイス アクセス ポリシー

Office 365 およびその他のクラウド サービスへのアクセス保護には、次のものがあります。

-   Enterprise Mobility + Security (EMS) の ID およびデバイスのアクセス保護

-   特権アクセスの管理

-   Windows 10 のセキュリティ機能

保護を適用する方法の詳細については、「[Office 365 の個人データに保護を適用する](apply-protection-to-personal-data-in-office-365.md)」を参照してください。

### <a name="step-5--monitor-for-leaks-of-personal-data"></a>手順 5: 個人情報の漏えいを監視する

Office 365 データ損失防止レポートでは、機密データ監視について最高レベルの詳細を提供します。自動アラートを設定し、Office 365 監査ログを使用して侵害を調査することができます。Cloud App Security は機密データの検索と監視の機能を他の SaaS プロバイダーまで拡張します。これらのツールの詳細は、「[個人データ侵害を監視する](monitor-for-leaks-of-personal-data.md)」を参照してください。
