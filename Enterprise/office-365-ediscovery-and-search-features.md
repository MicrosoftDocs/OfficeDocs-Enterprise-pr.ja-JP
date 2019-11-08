---
title: Office 365 の電子情報開示と検索機能の概要
ms.author: robmazz
author: robmazz
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
description: 監査機能の概要、および Office 365 の他の検索機能を使用して監査の使用と透明性を実現します。
ms.openlocfilehash: e94c8e27c2ddf7bd50dca15eb849337de6f89c1a
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032032"
---
# <a name="ediscovery-and-search-features"></a>電子情報開示と検索機能 

## <a name="ediscovery"></a>電子情報開示

電子情報開示機能は、管理者、コンプライアンス責任者、およびその他の承認されたユーザーが Office 365 ユーザーアクティビティの包括的な調査を実施するための単一の場所を提供します。 適切なアクセス許可を持つセキュリティ担当者が検索を実行し、コンテンツを保持します。 検索結果は、適用されている保留リストに対して電子情報開示ケースが作成されている場合を除き、コンテンツ検索から得られる結果と同じです。 電子情報開示検索の結果は、セキュリティを強化するために暗号化され、[高度な電子情報開示](https://support.office.com/article/office-365-advanced-ediscovery-fd53438a-a760-45f6-9df4-861b50161ae4)でエクスポートされたデータを分析することができます。

## <a name="content-search"></a>コンテンツ検索

[コンテンツ検索](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a)は、以前の電子情報開示検索ツールよりも向上したスケーリングとパフォーマンスの機能を提供する電子情報開示検索ツールです。 コンテンツ検索を使用して、メールボックス、パブリックフォルダー、SharePoint Online サイト、および OneDrive for Business の場所を検索します。 コンテンツ検索では大規模な検索がサポートされます。 検索できるメールボックスとサイトの数に制限はありません。 同時に実行される検索の数についても制限はありません。 検索を実行すると、検索ページの [詳細] ウィンドウに、コンテンツソースの数と予想される検索結果の数が表示されます。 結果をプレビューしたり、ローカルコンピューターにエクスポートしたりすることができます。 Office 365 Enterprise E5 サブスクリプションがある組織では、 [office 365 Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?LinkID=620116)の強力な分析機能を使用して分析の[結果を準備](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a#prepare)することができます。

## <a name="audit-log-search"></a>監査ログの検索

Office 365 組織の変更を追跡するだけでなく、監査レポートを表示したり、監査ログをエクスポートしたりすることができます。 Office 365 テナントの監査を有効にすると、ユーザーおよび管理アクティビティはイベントログに記録され、検索可能になります。 たとえば、メールボックス監査ログを使用して、メールボックスの所有者以外のユーザーによってメールボックスに対して実行された操作を追跡できます。 コンプライアンス責任者は、特定のユーザーアクティビティに対して検索機能とフィルター機能を使用できます。 たとえば、特定のドキュメントを表示またはダウンロードしたユーザーを特定する場合、管理者がユーザー管理アクティビティを実行した場合、または過去90日間のテナント構成の変更を表示する場合などです。 検索結果には、ユーザーまたは管理者によって実行された特定のアクティビティに関する貴重な法的情報が含まれます。 Office 365 に記録されるユーザーおよび管理アクティビティの説明については、「 [office 365 の監査アクティビティ](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c#auditlogevents)」を参照してください。

SharePoint Online と OneDrive for business からのイベントは、発生する30分以内にログに表示されます。 Exchange Online からのイベントは、発生した場合は24時間以内に監査ログに記録されます。 Azure AD からのログインイベントは、発生から数分以内に利用可能になり、Azure AD からのその他のディレクトリイベントは、24時間以内に利用可能になります。 監査ログの検索結果では、通風孔をエクスポートしてさらに分析することができます。 単一の監査ログ検索からの最大5万エントリがエクスポートされます。 この制限を超えるエントリをエクスポートするには、日付の範囲を減らすか、複数の監査ログの検索を実行します。

次の表に、アクティビティレポートに表示される情報の詳細を示します。 Office 365 ワークロードごとに収集されるプロパティの詳細については、「 [office 365 監査ログの詳細なプロパティ](https://support.office.com/article/detailed-properties-in-the-office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)」を参照してください。

| プロパティ | 説明 |
|----------------|----------------------------------------------------------------------------------------------------------------------|
| 日付 | イベントの日付と時刻 |
| ユーザー | アクションを実行したユーザー |
| ClientIP | アクティビティがログに記録されたときに使用されたデバイスの IPv4 または IPv6 アドレス。 |
| CreationTime | ユーザーがアクティビティを実行したときの協定世界時 (UTC) の日付と時刻。 |
| EventSource | イベントが発生したことを示します。 可能な値は、SharePoint と ObjectModel です。 |
| ID | レポートエントリの ID。 ID はレポートエントリを一意に識別します。 |
| 操作 | [このユーザーアクティビティの結果を表示] で選択された値に対応するユーザーまたはアクティビティの名前。 |
| OrganizationId | イベントが発生した組織の Office 365 サービスの GUID。 |
| UserAgent | ブラウザーによって提供される、ユーザーのブラウザーに関する情報。 |
| UserId | レコードが記録されるようになった (Operation プロパティで指定された) アクションを実行したユーザー。 |
| UserType | 操作を実行したユーザーの種類。 次の値は、ユーザーの種類を示します。 |
|  | 0は、通常のユーザーを示します。 |
|  | 2は、Office 365 組織の管理者を示します。 |
|  | 3 Microsoft データセンターの管理者またはデータセンターのシステムアカウントを示します。 |
| Workload | アクティビティが発生した Office 365 サービス。 このプロパティに指定できる値は次のとおりです。 |
|  | Exchange Online |
|  | SharePoint Online |
|  | OneDrive for Business |
|  | Azure Active Directory レポート |

Office 365 監査ログを検索する詳細な手順については、「 [office 365 での監査ログの検索](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)」を参照してください。

## <a name="search-unified-audit-log"></a>検索統合監査ログ

監査ログ検索機能を使用して、統合監査ログを検索します。 Office 365 では、リモート PowerShell を使用してこのログを検索することもできます。 Exchange Online PowerShell の[search-unifiedauditlog コマンドレット](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/Search-UnifiedAuditLog?view=exchange-ps)は、exchange Online、SharePoint Online、OneDrive for business、および Azure AD からのユーザー操作に関連するイベントの統合監査ログを検索するために使用されます。 

指定した日付範囲内のすべてのイベントを検索することも、特定のアクション、アクションを実行したユーザー、またはターゲットオブジェクトなどの特定の条件に基づいて結果をフィルター処理することもできます。 管理者は、Exchange Online の PowerShell セッションを最大3つまで同時に使用して、長い期間の検索を分割できます。