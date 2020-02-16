---
title: 複数地域環境の管理
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: 複数地域環境での SharePoint サービスおよび OneDrive サービスの管理について説明します。
ms.openlocfilehash: 483250f8956ba1220c29bb769abef187ac9ec53d
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974029"
---
# <a name="administering-a-multi-geo-environment"></a>複数地域環境の管理

ここでは、複数地域環境で Office 365 のサービスが動作するしくみについて説明します。

## <a name="audit-log-search"></a>監査ログ検索

すべてのサテライト地域に対して統合された[監査ログ](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)は、Office 365 監査ログの検索ページから利用できます。 すべての地域からの監査ログのエントリを参照できます。たとえば、NAM ユーザーと EUR ユーザーのアクティビティが、1 つの組織ビューに表示され、既存のフィルターを適用することで特定のユーザーのアクティビティを確認できます。

## <a name="bcs-secure-store-apps"></a>BCS、Secure Store、Apps

BCS、Secure Store、およびすべての App は、各サテライトの場所に個別のインスタンスがあります。そのため、SharePoint Online 管理者は、これらのサービスを各サテライトの場所とは別に管理および構成する必要があります。

## <a name="ediscovery"></a>電子情報開示 

デフォルトでは、複数地域のテナントの eDiscovery Manager またはeDiscovery Administrator が、そのテナントの中心地でのみ電子情報の開示ができるようになります。 Office 365 全体管理者は、別のユーザーが電子情報開示を実行できるように電子情報開示マネージャーのアクセス許可を割り当てる必要があります。また、サテライトの場所として電子情報開示を実施する地域を指定するために該当するコンプライアンス セキュリティ フィルターで "Region" パラメーターを割り当てる必要があります。それ以外の場合は、サテライトの場所で電子情報開示は実施されません。 地域のコンプライアンス セキュリティ フィルター を構成するには、[Office 365 Multi-Geo eDiscovery の構成](multi-geo-ediscovery-configuration.md)を参照してください。

## <a name="exchange-mailboxes"></a>Exchange メールボックス

ユーザーの PDL が変更された場合、Exchange メールボックスが自動的に移動します。 新しいメールボックスが作成されたとき、ユーザーの PDL の値が設定されていない場合は、ユーザーの PDL または中心地にメールボックスがプロビジョニングされます。

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Information Protection (IP) データ損失防止 (DLP) ポリシー

必要に応じて、テナント全体または該当するユーザーにポリシーの範囲を指定するセキュリティ & コンプライアンス センターで、OneDrive for Business、SharePoint、Exchange の IP DLP ポリシーを設定できます。 例: サテライト地域にいるユーザーのポリシーを選択する場合は、そのポリシーを特定の OneDrive に適用し、ユーザーの OneDrive URL を入力するように選択します。 DLP ポリシーを作成する際の一般的なガイダンスについては、[データ損失防止ポリシーの概要](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)を参照してください。

DLP ポリシーは、そのポリシーの適用性に基づいて各地域の場所に自動的に同期されます。

地域の場所のすべてのユーザーに対する Information Protection ポリシーとデータ損失防止ポリシーの実装は、UI で使用可能なオプションではありません。その代わりに、ポリシーの適用が可能なアカウントを選択するか、すべてのアカウントにグローバルにポリシーを適用する必要があります。

## <a name="microsoft-flow"></a>Microsoft Flow

サテライト地域に作成された Flow は、テナントのデフォルトの地域にあるエンドポイントを使用します。  Microsoft Flow は、Multi-Geo サービスではありません。 

## <a name="microsoft-powerapps"></a>Microsoft PowerApps

サテライト地域に作成された PowerApps は、テナントの中心地にあるエンドポイントを使用します。 Microsoft PowerApps は、Multi-Geo サービスではありません。 

## <a name="onedrive-administrator-experience"></a>OneDrive 管理者のエクスペリエンス

[OneDrive 管理センター](https://admin.onedrive.com)の左側のナビゲーションには、**[地域の場所]** タブがあります。このタブには、地域の場所の地図があり、地域の場所を確認および管理できます。

## <a name="security-and-compliance-admin-center"></a>セキュリティ/コンプライアンス管理センター

複数地域テナントには、[Office 365 セキュリティ/コンプライアンス センター](https://protection.office.com/?rfr=AdminCenter\#/homepage)という 1 つの中心的なコンプライアンス センターがあります。

## <a name="sharepoint-storage-quota"></a>SharePoint のストレージ クォータ

デフォルトでは、複数地域環境のすべての地域では、使用できるテナントの ストレージ クォータを共有します。  特定の地域に固有のクォータを割り当てることで、ストレージ クォータを管理することもできます。 詳細については、[複数地域環境における SharePoint ストレージ クォータ](sharepoint-multi-geo-storage-quota.md)を参照してください。

## <a name="sharing"></a>共有

管理者は、各地域のポリシーの共有を設定し管理できます。 各地域の OneDrive と SharePoint サイトは、対応する地域固有の共有設定のみを優先します。 (たとえば、中心地への[外部共有](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)は許可できますが、サテライト地域またはその逆にはできません) 共有設定は地域間の共有制限を構成できませんので注意してください。

## <a name="taxonomy"></a>分類

マスターは会社の中心地にホストされているため、地域全体で会社の管理されたメタデータに統一された[分類](https://docs.microsoft.com/sharepoint/managed-metadata)をサポートしています。 中心地からグローバル分類を管理し、サテライト地域の分類に地域固有の用語を追加することをお勧めします。 グローバル分類の用語は、サテライト地域に同期されます。

詳細と開発者向けガイダンスについては、[複数地域テナントにおけるメタデータの管理](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-managedmetadata)を参照してください。

## <a name="user-profile-application"></a>ユーザー プロファイル アプリケーション

各地域に[ユーザー プロフィール アプリケーション](https://docs.microsoft.com/sharepoint/manage-user-profiles)があります。 各ユーザーのプロフィール情報は、ユーザーの地域でホストされており、その地域の管理者が利用できます。

カスタムのプロフィール プロパティがある場合は、すべての地域で同じプロフィール スキーマを使用して、すべての地域の場所または必要な場所のどちらかにカスタムのプロフィール プロパティを設定します。 プログラムを使用したユーザー プロフィール データの設定方法に関するガイダンスは、[ユーザー プロフィールの一括更新 API](https://docs.microsoft.com/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)を参照してください。

詳細と開発者向けガイダンスについては、[複数地域テナントのユーザー プロフィールの操作](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-userprofileexperience)を参照してください。

## <a name="video-portal"></a>ビデオ ポータル

複数地域テナントでは、O365 ビデオ ポータルはデフォルト地域からのみ提供され、すべてのユーザーはその中央ポータル URL にリダイレクトされます。 そのため、その地域の Remote Media Service (RMS) が、中心地に基づいて次のように使用されます。

現在、Stream は以下の地域で利用できます。

- 北米 (米国でホストされている) 
- ヨーロッパ
- アジア太平洋

ただし Stream は、現在 Office 365 ビデオ向けにサポートされている次の地域ではまだ使用できません。そのため、これらのローカル インスタンスには、サポートされている最も近い地域にある RMS を使用します。

- オーストラリア
- カナダ
- インド
- 英国
