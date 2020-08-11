---
title: Microsoft クラウドサービスでの監査とレポート
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- M365-analytics
- SPO_Content
f1.keywords:
- NOCSH
description: Office 365、Microsoft 365、およびサービスアシュアランス内の監査とレポート機能の概要について説明します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 40e68954cb0128ad323305bf8347a8e13afda9d5
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606683"
---
# <a name="auditing-and-reporting-in-microsoft-cloud-services"></a>Microsoft クラウドサービスでの監査とレポート

Microsoft クラウドサービスには、テナント内のユーザーおよび管理者のアクティビティを追跡するために使用できるいくつかの監査およびレポート機能が含まれています。例には、Exchange Online および SharePoint Online テナントの構成設定に加えられた変更や、ユーザーによるドキュメントやその他のアイテムの変更があります。 Microsoft クラウドサービスで利用可能な監査情報とレポートを使用して、ユーザーの利便性をさらに向上させることができます。また、リスクを軽減し、法令遵守の義務を満たすことができます。

## <a name="security--compliance-centers"></a>セキュリティ & コンプライアンスセンター

Microsoft [365 セキュリティ & コンプライアンスセンター](https://protection.office.com)、 [Microsoft 365 セキュリティセンター](https://security.microsoft.com)、および[microsoft 365 コンプライアンスセンター](https://compliance.microsoft.com)は、組織内のデータを保護するための1つの停止ポータルで、多くの監査およびレポート機能を備えています。 これらのセンターは、データ保護またはコンプライアンスニーズを支援し、ユーザーと管理者のアクティビティを監査します。 これらのセンターには、サブスクリプション管理者アカウントを使用してアクセスできます。

これらのセンターには、いくつかの機能にアクセスするためのナビゲーションウィンドウが含まれています。

- **通知:**[Cloud App security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)を使用して、アラートの管理、セキュリティ関連の警告の表示、高度な通知の管理を行うことができます。
- **アクセス許可:** コンプライアンス管理者、電子情報開示マネージャーなどの[アクセス許可](https://docs.microsoft.com/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center)を組織内のユーザーに割り当てることができるようにして、これらのセンターでタスクを実行できるようにします。 各センターでは、ほとんどの機能に対するアクセス許可を割り当てることができますが、その他のアクセス許可は Exchange 管理センターおよび SharePoint 管理センターを使用して構成する必要があります。
- **脅威管理:**[Microsoft 365 モバイルデバイス管理](https://support.microsoft.com/office/overview-of-mobile-device-management-mdm-for-microsoft-365-faa7d8e5-645d-4d59-839c-c8d4c1869e4a)を使用してデバイス管理ポリシーを作成および適用し、組織の[データ損失防止](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies)(DLP) ポリシーを設定したり、電子メールフィルター、マルウェア対策、domainkeys 識別メール (dkim)、安全な添付ファイル、安全なリンク、および OAuth アプリを構成したりすることができます。
- **データガバナンス:**[他のシステムからの電子メールまたは SharePoint データを Microsoft 365 にインポート](https://support.office.com/article/Import-PST-files-or-SharePoint-data-to-Office-365-ba688e0a-0fcb-4bd7-8e57-2b669564ea84)して、[アーカイブメールボックスを構成](https://support.office.com/article/Enable-archive-mailboxes-in-the-Office-365-Security-Compliance-Center-268a109e-7843-405b-bb3d-b9393b2342ce)し、組織内の電子メールおよびその他のコンテンツの[保持ポリシー](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)を設定できます。
- **検索 & 調査:** Exchange Online のメールボックス、グループ、パブリックフォルダー、SharePoint Online、OneDrive for business のアクティビティにすばやくドリルインするための[コンテンツ検索](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a)、[監査ログ](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)、検疫、[電子情報開示ケース管理](https://support.office.com/article/Manage-eDiscovery-cases-in-the-Office-365-Security-Compliance-Center-edea80d6-20a7-40fb-b8c4-5e8c8395f6da)ツールを提供します。
- **レポート:** SharePoint Online、OneDrive for Business、Exchange Online、および Azure AD の[レポート](https://support.office.com/article/Reports-in-the-Office-365-Security-Compliance-Center-7acd33ce-1ec8-49fb-b625-43bac7b58c5a)にすばやくアクセスできます。
- **サービスアシュアランス:** Microsoft 365、Azure、Microsoft Dynamics CRM Online、Microsoft Intune、およびその他のクラウドサービスのグローバル標準に関するセキュリティ、プライバシー、コンプライアンスを維持する方法について説明します。 また、サードパーティの ISO、SOC、その他の監査レポート、および監査対象のコントロールにアクセスすることもできます。これにより、Microsoft 365 のサードパーティの監査者がテストおよび検証したさまざまなコントロールに関する詳細が提供されます。

## <a name="service-assurance"></a>サービス保証

規制された業界の多くの組織は、幅広いコンプライアンス要件の対象となります。 独自のリスク評価を実施するために、多くの場合、Microsoft 365 がデータのセキュリティとプライバシーをどのように維持するかについて詳細な情報をお客様に提供する必要があります。 Microsoft は、クラウドサービスの顧客データのセキュリティとプライバシーに関する情報を提供し、その操作を透過的に表示することにより、お客様の信頼を得ることができます。また、コンプライアンスに関する個別のレポートや評価へのアクセスが容易になります。

サービス保証は、microsoft 365 で Microsoft がお客様のデータのセキュリティ、プライバシー、コンプライアンスをどのように維持しているかに関する操作の透明性と情報を提供します。 データの暗号化、データの復元、セキュリティインシデントの管理など、Microsoft 365 に関するホワイトペーパー、Faq、およびその他の資料のライブラリと共に、サードパーティの監査レポートも含まれています。 お客様は、この情報を使用して、独自の規制リスク評価を実行できます。 コンプライアンス責任者は、サービスアシュアランスへのアクセス権をユーザーに付与するために、"サービス保証ユーザー" 役割を割り当てることができます。 また、テナント管理者は、 [Microsoft Cloud Service Trust Portal](https://aka.ms/STP) (STP) を使用してサービス保証ダッシュボードの情報にアクセスすることによって、独立した監査者などの外部ユーザーを提供することもできます。

## <a name="onedrive-for-business-admin-center"></a>OneDrive for Business 管理センター

Microsoft OneDrive 管理センターを使用すると、組織の OneDrive for Business の設定を1か所ですばやく簡単に管理できます。 OneDrive 管理センターを使用するには、onedrive.com へのアクセスが必要です。 また、組織のグローバル管理者、または SharePoint 管理者の役割を持つカスタムの管理者である必要があります。 OneDrive for Business 管理センターにアクセスし [https://admin.onedrive.com](https://admin.onedrive.com/) ます。

主な機能には、監査ログの検索、DLP、保持、電子情報開示、警告の処理などの主要なシナリオについて、管理者に適切な管理センターへのリンクを提供するコンプライアンス領域が含まれています。

## <a name="related-links"></a>関連リンク

- [電子情報開示と検索機能](office-365-ediscovery-and-search-features.md)
- [Microsoft 365 のレポート作成機能](office-365-reporting-features.md)
- [Microsoft 365 マネージメント アクティビティ API](office-365-management-activity-api.md)
- [Microsoft 365 のメールボックスの移行](office-365-mailbox-migrations.md)
- [Microsoft 365 のエンジニアリングのための内部ログ記録](office-365-internal-logging.md)