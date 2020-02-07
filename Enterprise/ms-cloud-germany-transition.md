---
title: Microsoft Cloud Germany (Microsoft Cloud Deutschland) から新しいドイツのデータセンター リージョンの Office 365 サービスへの移行
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: '概要: 新しいドイツのデータセンター リージョンで、Microsoft Cloud Germany (Microsoft Cloud Deutschland) から Office 365 サービスへの移行について理解します。'
ms.openlocfilehash: d8b02d149083095793ef2038c8df3d9b62e7cba8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844878"
---
# <a name="migration-from-microsoft-cloud-germany-microsoft-cloud-deutschland-to-office-365-services-in-the-new-german-datacenter-regions"></a>Microsoft Cloud Germany (Microsoft Cloud Deutschland) から新しいドイツのデータセンター リージョンの Office 365 サービスへの移行


>[!Note]
>この記事は、該当する Microsoft Cloud Germany/Deutschland のお客様にのみ適用されます。
>

## <a name="cloud-service-offerings-in-germany"></a>ドイツでのクラウド サービスの提供

2018 年 8 月に、Microsoft はドイツの新しいクラウド リージョンから完全な Microsoft クラウド (Azure、Office 365、Dynamics 365、および Power Platform) を提供し、お客様のデジタル トランスフォーメーションを促進する意向を発表しました。 2019 年 8 月に、ドイツで新しいクラウド リージョンを開設する準備を進めていることを発表しました。 8 月に Azure が利用可能となったことについて発表し、12 月に Office 365 が利用可能になりました。  Dynamics 365 および Power Platform は、2020 年の第 1 四半期に利用可能となる予定です。  

新しいリージョンは、ドイツの顧客の進化するニーズに柔軟に対応し、最新のインテリジェント クラウド サービス、グローバル クラウド ネットワークへの完全な接続、およびドイツ国内の顧客データ常駐に対応するように設計されています。

## <a name="moving-to-the-new-german-regions"></a>新しいドイツ リージョンへの移動

既存の Microsoft Cloud Germany (Microsoft Cloud Deutschland) のお客様は、Office 365、Dynamics 365 Customer Engagement、および Power Platform BI のユーザーの移行を開始できるようになりました。  最初のステップは、新しいドイツのデータセンター リージョンへの [Microsoft 主導の移行にオプトインする](https://aka.ms/office365germanymoveoptin)ことです。

Microsoft 主導のアプローチにオプトインした組織の場合、2020 年に移行が行われる予定です。 移行の結果、主要な顧客データおよびサブスクリプションは新しいドイツ リージョンへと移動します。 

以下のサービスは、Microsoft 主導のアプローチの一部として移行されます。

- Azure Active Directory
- Exchange Online
- Exchange Online Protection
- SharePoint Online
- OneDrive for Business
- Skype for Business Online

Microsoft Cloud Germanyからドイツのデータセンター リージョンへの移行中に、既存の Skype for Business Online の顧客は Microsoft Teams へと移行されます。 詳細情報については、「[Microsoft Teams へのアップグレードを開始する](https://aka.ms/SkypeToTeams-Home)」を参照してください。

- Office 365 グループ
- Dynamics 365 / Power Platform

これらのサービスの移行に関する前提条件および影響については、「[Dynamics 365 Customer engagement](https://aka.ms/D365ceOptIn)」の記事で説明しています。

## <a name="how-to-prepare-for-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>新しいドイツのデータセンター リージョンでの Office 365 サービスへの移行を準備する方法

最初のステップは Microsoft へと届け出ることです。それによって、Microsoft はサブスクリプションおよびデータを Microsoft Cloud Germany/Deutschland から新しいドイツのデータセンター リージョンの Office 365 サービスに移行するための許可を得ることになります。  手順については、「[オプトイン プロセス](ms-cloud-germany-migration-opt-in.md)」を参照してください。

- 移行するすべてのお客様は、新しいドイツのデータセンター リージョンを含む世界中の [Office 365 URL および IP アドレス](urls-and-ip-address-ranges.md)への接続を確認する必要があります。
- Office 365 プラットフォームのサービス説明を確認して、ドイツ リージョンへの移行完了後に組織で利用できる機能とサービスを理解してください。 
- 移行により、有料サブスクリプションが移行されます。  試用版サブスクリプションを移行することはできません。

テナントの移行は、最小限の顧客の操作でバックエンド サービスの操作として実行されます。  追加の顧客主導タスクおよび全体的な移行状況は、移行プロセス中にメッセージ センター経由で通知されます。  タスクの例には、顧客管理の DNS 更新や、Exchange ハイブリッドの顧客向けハイブリッド セットアップの再構成が含まれる場合があります。

## <a name="customer-experience-during-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>新しいドイツのデータセンター リージョンの Office 365 サービスへの移行中のカスタマー エクスペリエンス

テナントの移行は、エンド カスタマーおよび管理者への影響を最小限に抑えるように設計されています。  ただし、各ワークロードごとに考慮事項があります。  

### <a name="azure-active-directory"></a>Azure Active Directory

Microsoft Cloud Germany の Office/Dynamics サブスクリプションは、Azure Active Directory (Azure AD) の再配置によりドイツ リージョンに移行されます。 その後組織は更新され、新しい世界的なサービス サブスクリプションが反映されます。 短いサブスクリプション移行プロセスの間は、サブスクリプションへの変更はブロックされます。

### <a name="exchange-online"></a>Exchange Online

Exchange Online ハイブリッドのお客様は、移行前にハイブリッド構成ウィザードを再実行して Microsoft Cloud Germany に対するオンプレミス構成を更新し、ワールドワイド サービスに対するクリーンアップに際し HCW を再実行する必要があります。 カスタム ドメインを持つお客様は、追加の DNS 更新が必要になる場合があります。

メールボックスはバックエンド プロセスとして移行され、組織内のユーザーは移行中に Microsoft Cloud Germany またはドイツ リージョンのいずれかに属し、同じ Exchange 組織 (GAL) の一部となる場合があります

### <a name="exchange-online-protection"></a>Exchange Online Protection

バックエンドの Exchange Online Protection の機能は新しいドイツ リージョンにコピーされます

### <a name="sharepoint-online"></a>SharePoint Online

ドイツ リージョンへの SharePoint Online の移行が完了すると、データ インデックスが再構築されます。 インデックスの再構築が完了すると、検索インデックスに依存する機能が影響を受ける場合があります。

既存の sharepoint.de URL は、移行完了後の組織のために保持されます。

### <a name="onedrive-for-business"></a>OneDrive for Business

ドイツ リージョンへの OneDrive for Business の移行が完了すると、データ インデックスが再構築されます。 インデックスの再構築が完了すると、検索インデックスに依存する機能が影響を受ける場合があります。

### <a name="skype-for-business-online"></a>Skype for Business Online

既存の Skype for Business Online の顧客は Microsoft Teams へと移行されます。 詳細については、「[https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home)」を参照してください。


## <a name="key-differences-between-microsoft-cloud-germany-microsoft-cloud-deutschland-and-office-365-services-in-the-new-german-datacenter-regions"></a>新しいドイツのデータセンター リージョンでの Microsoft Cloud Germany (Microsoft Cloud Deutschland) と Office 365 サービスの主な相違点


|| Microsoft Cloud Germany (Microsoft Cloud Deutschland) | 新しいドイツのデータセンター リージョンでの Office 365 サービス |
|:-------|:-----|:-----|
| 1 つの Office 365 テナントのみでサブスクリプションに利用可能な Microsoft 365 サービス | 15 のサービス (REF を参照) | 29 のサービス (REF を参照) |
| 新機能 | 利用可能な新機能はありません。 | 新しい機能は、グローバルな Office 365 サービスと一貫性を持つ形で利用可能になります。 |
| データ トラスティ | はい | いいえ |
| グローバルな Office 365 テナントでのテナント間コラボレーション | いいえ | はい |
| 顧客データの常駐 | 顧客データは、ドイツのデータ センター内にのみ保存されます。 | Microsoft は、以下の顧客データをドイツ国内のみに保存します: Exchange Online メールボックス コンテンツ (メール本文、カレンダー エントリ、およびメールの添付ファイル コンテンツ)、SharePoint Online サイト コンテンツおよびそのサイト内に保存されているファイル、そして OneDrive for Business にアップロードされたファイル。 |
| 該当する条件 | [オンライン サービスの使用条件](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) ([補足](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64)あり) | [オンライン サービスの使用条件](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="frequently-asked-questions"></a>よく寄せられる質問

### <a name="is-migration-required"></a>移行は必要ですか ?

Microsoft は、Microsoft Cloud Germany から新しいドイツのデータセンター リージョンの Office 365 サービスへの Office 365 テナントの移行を追加料金なしで提供します。  新しいドイツのデータセンター リージョンへの移行へのオプトインを強くお勧めしますが、Microsoft は Microsoft Cloud Germany リージョンへの必要なセキュリティ更新プログラムの提供を続けます。  

新しいドイツのデータセンター リージョンでの Office 365 サービスには、追加のメリットがあります。

- [Azure](https://azure.microsoft.com/pricing/calculator/)、[Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans)、[Dynamics 365 Customer Engagement](https://dynamics.microsoft.com/pricing/)、および [Power BI](https://powerbi.microsoft.com/pricing/) について、市場競争力のある価格を提供します。 
- Microsoft のグローバル ネットワークに接続されており、数百のネットワーク エッジ サイト、ピアリング ロケーション、およびエグレス ポイントを提供し、世界中のどこでも堅牢なユーザー エクスペリエンスを提供します。 
- ドイツ国内での顧客データの常駐要件を満たすのに役立ちます。 
- 最新バージョンのサービスおよび Microsoft Teams や Office 365 の Multi-Geo などの新機能を含む、フル機能のグローバル クラウド サービスを提供します。 [Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central)、[Office 365](https://products.office.com/ja-JP/where-is-your-data-located)、[Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability) について、地域ごとに製品を比較します。
- 完全な機能、エンタープライズグレードのセキュリティ、および包括的な機能を提供し、顧客がコンプライアンスおよび規制要件を満たすのを支援します。 
- 既存のオンライン サービス契約を通じてアクセスできます。

#### <a name="what-is-the-service-availability-between-the-different-office-365-cloud-service-offerings"></a>さまざまな Office 365 クラウド サービス間のサービス可用性はどのくらいですか?

次の 15 のサービスは、Microsoft Cloud Germany (Microsoft Cloud Deutschland) クラウド サービスで利用できます。  Microsoft Cloud Germany には、新しいサービスを追加していません。

1. Exchange Online
2. カスタマー ロックボックス (Exchange Online)
3. グループ (モダン グループ)
4. Delve プロファイル
5. Exchange Online Protection
6. Advanced Threat Protection (ATP)
7. Advanced eDiscovery
8. 高度なデータ ガバナンス
9. SharePoint Online
10. カスタマー ロックボックス (SharePoint Online)
11. OneDrive for Business
12. Skype for Business
13. Word Online、Excel Online、PowerPoint、OneNote、Visio Online
14. Office 365 Pro Plus
15. Outlook モバイル

現在、新しいドイツのデータセンター リージョンでの Office 365 サービスの一部として 29 のサービスを利用できます。  新しい機能とサービスは、グローバルな Office 365 サービスと一貫性を持つ形で継続的に利用可能になります。

1. Exchange Online
2. カスタマー ロックボックス (Exchange Online)
3. グループ (モダン グループ)
4. Delve プロファイル
5. MyAnalytics
6. Workplace Analytics
7. Exchange Online Protection
8. Advanced Threat Protection (ATP)
9. Advanced eDiscovery
10. Advanced Security Management
11. Information Rights Management
12. 高度なデータ ガバナンス
13. SharePoint Online
14. カスタマー ロックボックス (SharePoint Online)
15. OneDrive for Business
16. Microsoft Stream
17. Skype for Business (移行中に Microsoft Teams へと移行します)
18. クラウド PBX
19. PSTN 会議
20. PSTN 通話
21. Microsoft Teams
22. 管理者レポート/利用状況レポート
23. Word Online、Excel Online、PowerPoint、OneNote、およびVisio Online
24. Planner
25. Sway
26. Office 365 Pro Plus
27. Outlook モバイル
28. EMS E3 (Azure Active Directory Premium P1 + Intune + Rights Management Service)
29. Yammer Online

### <a name="when-will-migration-happen"></a>移行はいつ行われますか ?

#### <a name="azure"></a>Azure 

Azure リソースの別リージョンへの[移行](https://docs.microsoft.com/azure/germany/germany-migration-main)は、今すぐ開始できます。 Azure 上に Office 365、Dynamics 365、または Power BI がインストールされている場合は、以下の手順に従ってください。

#### <a name="office-365"></a>Office 365

今すぐ、Microsoft 主導の移行に[オプトイン](https://aka.ms/office365germanymoveoptin)してください。 移行を開始する準備ができたら、Microsoft 365 管理センターの[メッセージ センター](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide)からお知らせします。

#### <a name="dynamics-365-and-power-bi"></a>Dynamics 365 および Power BI

[Dynamics 365 Customer Engagement](https://aka.ms/D365ceOptIn) および [Power BI](https://aka.ms/pbioptin) 向けの Microsoft 主導の移行に今すぐオプトインしてください。 移行を開始する準備ができたら、Microsoft 365 管理センターの[メッセージ センター](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide)からお知らせします。

### <a name="will-the-price-change-for-the-office-services-that-i-use"></a>使用する Office サービスの価格は変わりますか ?

はい、Microsoft のグローバル クラウド リージョン (新しいデータセンター リージョンを含む) の価格は一般的に低くなっています。

### <a name="how-do-i-get-help-from-microsoft-to-migrate-to-a-new-region-or-answer-support-questions"></a>新しいリージョンに移行したりサポートの質問に答えたりするために、Microsoft からヘルプを得るにはどうすればよいですか ?

ご質問がある場合には、以下の方法またはパートナーを通じてお問い合わせください。

- Azure の場合、Azure ポータルで[新しいサポート リクエスト](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest)を送信できます。
- Office 365 の場合、“サポートが必要ですか ?” を使用して質問を送信できます。 [Microsoft 365 管理センター](https://portal.office.de/)のリンクです。
- Office 365 も持っている Dynamics 365 Customer Engagement および Power BI のお客様の場合、“サポートが必要ですか ?” を使用して質問を送信できます。 [Microsoft 365 管理センター](https://portal.office.de/)のリンクです。 Dynamics 365 Customer Engagement のサポート オプションは[こちら](https://docs.microsoft.com/dynamics365/get-started/support/)にあります。 Power BI のサポート オプションは[こちら](https://powerbi.microsoft.com/support/)にあります。

## <a name="more-information"></a>詳細情報

- [Microsoft Cloud Deutschland 移行アシスタント](https://aka.ms/germanymigrateassist)
- [移行のオプトイン方法](https://aka.ms/office365germanymoveoptin)
- [Dynamics 365 移行プログラム情報](https://aka.ms/D365ceOptIn)
- [Power BI 移行プログラム情報](https://aka.ms/pbioptin)
- [Office 365 の URL と IP アドレスの範囲](https://aka.ms/o365endpoints)
- [Office 365 ハイブリッド構成ウィザード](https://aka.ms/HybridWizard)
- [Microsoft Teams へのアップグレードを開始する](https://aka.ms/SkypeToTeams-Home)
