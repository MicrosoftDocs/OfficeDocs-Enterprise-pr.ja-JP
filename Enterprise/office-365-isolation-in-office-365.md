---
title: Office 365 の分離とアクセス制御 (Office 365)
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
- SPO_Content
f1.keywords:
- NOCSH
description: '概要: Office 365 のさまざまなアプリケーションでの分離とアクセス制御について説明します。'
ms.openlocfilehash: 2cf98480a2a3f5d202198c9056ecb46d281e1a3e
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844408"
---
# <a name="isolation-and-access-control-in-office-365"></a>Office 365 での分離とアクセス制御

Azure Active Directory と Office 365 では、非常に複雑なデータモデルが使用されています。これには、数百のエンティティ、数千件の関係、および数万の属性が含まれています。 高レベルでは、Azure Active Directory とサービスディレクトリは、状態ベースのレプリケーションプロトコルを使用して同期されたテナントと受信者のコンテナーです。 Azure Active Directory 内に保持されているディレクトリ情報に加えて、各サービスワークロードには独自のディレクトリサービスインフラストラクチャがあります。
 
![Office 365 テナントデータ同期](media/office-365-isolation-tenant-data-sync.png)

このモデルでは、ディレクトリデータの単一のソースはありません。 特定のシステムは個別のデータを所有していますが、すべてのデータを保持する単一のシステムはありません。 Office 365 サービスは、このデータモデルの Azure Active Directory と連携します。 Azure Active Directory は共有データの "真実のシステム" です。これは、通常、すべてのサービスで使用される小さなデータおよび静的データです。 Office 365 および Azure Active Directory 内で使用されているフェデレーションモデルは、データの共有ビューを提供します。

Office 365 は、物理ストレージと Azure クラウドストレージの両方を使用します。 Exchange Online (Exchange Online Protection を含む) および Skype for Business は、お客様のデータに独自のストレージを使用します。 SharePoint Online は、SQL Server ストレージと Azure ストレージの両方を使用するため、ストレージレベルで顧客データをさらに分離する必要があります。

## <a name="exchange-online"></a>Exchange Online

Exchange Online は、メールボックス内に顧客データを格納します。 メールボックスは、メールボックスデータベースと呼ばれる拡張記憶域エンジン (ESE) データベース内でホストされます。 これには、ユーザーメールボックス、リンクされたメールボックス、共有メールボックス、およびパブリックフォルダーメールボックスが含まれます。 ユーザーメールボックスには、会話の履歴など、保存された Skype for Business コンテンツが含まれています。

ユーザーメールボックスのコンテンツには次のものが含まれます。

- メールと電子メールの添付ファイル
- 予定表と空き時間情報
- 連絡先
- タスク
- メモ
- グループ
- 推論データ

Exchange Online 内の各メールボックスデータベースには、複数のテナントからのメールボックスが含まれています。 認証コードは、テナント内などの各メールボックスをセキュリティで保護します。 既定では、割り当てられたユーザーのみがメールボックスにアクセスできます。 メールボックスをセキュリティで保護するアクセス制御リスト (ACL) には、テナントレベルで Azure Active Directory によって認証された id が含まれています。 各テナントのメールボックスは、テナントの認証プロバイダーに対して認証された id に制限されます。これには、そのテナントのユーザーのみが含まれます。 テナント a で明示的に承認されていない限り、テナント内のコンテンツは、テナント B のユーザーによって取得されることはできません。

## <a name="skype-for-business"></a>Skype for Business

Skype for Business は、さまざまな場所にデータを格納します。

- 接続エンドポイント、テナント Id、ダイヤルプラン、ローミング設定、プレゼンス状態、連絡先リストなどを含むユーザーおよびアカウント情報は、Skype for Business Active Directory サーバー、およびさまざまな Skype for Business データベースサーバーに格納されます。 ユーザーが両方の製品に対して有効になっている場合、またはユーザーがいない場合、Skype for Business サーバーでユーザーの Exchange Online メールボックスに連絡先リストが格納されます。 Skype for Business データベースサーバーはテナントごとにパーティション分割されませんが、データのマルチテナント分離は、役割ベースのアクセス制御 (RBAC) によって適用されます。
- 会議コンテンツとアップロードデータは、分散ファイルシステム (DFS) 共有に保存されます。 このコンテンツは、有効になっている場合に Exchange Online にアーカイブすることもできます。 DFS 共有は、テナントごとにパーティション分割されません。 コンテンツは Acl を使用してセキュリティ保護され、マルチテナントは RBAC によって適用されます。
- 通話履歴、IM セッション、アプリケーション共有、IM 履歴などのアクティビティ履歴である通話詳細レコードは、Exchange Online にも保存できますが、ほとんどの通話詳細レコードは、通話詳細記録 (CDR) サーバーに一時的に格納されます。 コンテンツはテナントごとにパーティション分割されませんが、マルチテナントは RBAC を介して適用されます。

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online には、データの分離を提供する独立したメカニズムがいくつかあります。 オブジェクトをアプリケーションデータベース内の抽象化されたコードとして格納します。 たとえば、ユーザーがファイルを SharePoint Online にアップロードすると、ファイルは分解され、アプリケーションコードに変換され、複数のデータベースにわたって複数のテーブルに格納されます。

ユーザーがデータが格納されているストレージに直接アクセスできた場合、そのコンテンツは、手動または SharePoint Online 以外のシステムによって解釈されることはありません。 これらのメカニズムには、セキュリティアクセス制御およびプロパティが含まれます。 すべての SharePoint Online リソースは、認証コードと、テナントの内部を含む RBAC ポリシーによって保護されます。 リソースを保護するアクセス制御リスト (ACL) には、テナントレベルで認証された id が含まれています。 テナントの SharePoint Online データは、テナントの認証プロバイダによって認証された id に限定されます。

Acl に加えて、認証プロバイダ (テナント固有の Azure Active Directory) を指定するテナントレベルのプロパティは一度書き込まれます。一度設定すると、設定後に変更することはできません。 テナントに対して認証プロバイダのテナントプロパティを設定すると、テナントに公開されている Api を使用して変更することはできません。

一意の*SubscriptionId*が各テナントに使用されます。 すべての顧客サイトはテナントによって所有され、テナントに固有の*SubscriptionId*が割り当てられます。 サイトの*SubscriptionId*プロパティは、一度だけ書き込まれ、永続的なものになります。 テナントに割り当てられた後は、サイトを別のテナントに移動することはできません。 *SubscriptionId*は、認証プロバイダーのセキュリティスコープを作成するために使用されるキーで、テナントに関連付けられています。

SharePoint Online は、SQL Server と、コンテンツメタデータストレージ用の Azure ストレージを使用します。 コンテンツストアのパーティションキーは SQL での*SiteId*です。 SQL クエリを実行している場合、SharePoint Online はテナントレベルの*SubscriptionId*チェックの一部として確認された*SiteId*を使用します。

SharePoint Online は、暗号化されたファイルコンテンツを Microsoft Azure blob に格納します。 各 SharePoint Online ファームには独自の Microsoft Azure アカウントがあり、Azure に保存されているすべての blob は、SQL コンテンツストアに格納されているキーを使用して個別に暗号化されます。 認証層によってコードで保護されており、エンドユーザーに直接公開されていない暗号化キー。 SharePoint Online はリアルタイム監視を使用して、HTTP 要求が複数のテナントに対してデータを読み書きするタイミングを検出します。 要求 id *subscriptionid*は、アクセスされるリソースの*subscriptionid*に対して追跡されます。 複数のテナントのリソースにアクセスする要求は、エンドユーザーによって発生することはありません。 マルチテナント環境のサービス要求だけが例外です。 たとえば、検索クローラーは、データベース全体に対するコンテンツの変更を一度に1つずつ取得します。 通常、1つのサービス要求で複数のテナントのサイトに対してクエリを実行する必要があります。これは、効率性上の理由によります。
