---
title: Microsoft 365 データの不変性
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
f1.keywords:
- NOCSH
description: Microsoft 365 のデータ不変性を定義して説明します。
ms.openlocfilehash: 8648060f3036d2f3c81704cf53a817910607263a
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998461"
---
# <a name="immutability-in-microsoft-365"></a>Microsoft 365 での不変性

コンプライアンス、内部ガバナンスの要件、訴訟リスクによって、組織はメールと関連データを検出可能な形式で保持する必要があります。 システム内のすべてのデータは検出可能である必要があり、破棄または変更することはできません。 業界標準の用語は、"不変" です。

従来の不変処理方法では、電子メールメッセージを別の読み取り専用の保存場所に移動することによって動作します。 このようなシステムは、証拠開示のためにメールボックスアイテムを保持することを目的としていますが、通常は日常のワークフローから保持されているアイテムを削除することによって、ユーザーの作業感に影響 IT 担当者にとって、この不変手法を使用するには、個別のサーバーとストレージインフラストラクチャを展開し、継続的に保守する必要があります。 検出は、メールシステムの外部にあるツールを使用して実行され、関連する展開とメンテナンスのコストを含みます。

Microsoft 365 とそのサービスのアーカイブのインプレース保持ポリシー機能と保持ポリシー機能により、受信、内部、送信データの多くのクラスを保持して保持することができます。 次のようなシナリオが考えられます。

- 受信および送信電子メール通信
- メールフォームまたは共有オンラインドキュメントに含まれるブックとレコード
- 会議出席依頼
- Fax
- インスタントメッセージ
- オンライン会議中に共有するドキュメント
- Voicemails

さらに、Microsoft は、サードパーティのデータキャプチャおよび管理ソリューションとの統合により、他のソースからの[データのアーカイブ](https://support.office.com/article/Archiving-third-party-data-in-Office-365-0ce338d5-3666-4a18-86ab-c6910ff408cc)を可能にするアドオン機能を開発しました。 サードパーティのデータがインポートされた後、Microsoft 365 のコンプライアンス機能をデータに適用することができます。次のようなものがあります。

- [訴訟ホールド](https://docs.microsoft.com/microsoft-365/compliance/create-a-litigation-hold)
- [インプレース電子情報開示とホールド](https://docs.microsoft.com/microsoft-365/compliance/manage-legal-investigations)
- [コンプライアンス検索](https://docs.microsoft.com/microsoft-365/compliance/search-for-content)
- [インプレース アーカイブ](https://docs.microsoft.com/microsoft-365/compliance/enable-archive-mailboxes)
- [メールボックスの監査](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing)
- [アイテム保持ポリシー](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)

たとえば、メールボックスが訴訟ホールドの対象となっている場合、サードパーティのデータは保持されます。 インプレース電子情報開示またはコンプライアンス検索を使用して、サードパーティのデータを検索できます。 また、Microsoft データの場合と同じように、アーカイブポリシーとアイテム保持ポリシーをサードパーティデータに適用することができます。 Microsoft 365 でサードパーティのデータをアーカイブすることにより、組織は政府および規制ポリシーに準拠し続けることができます。

Microsoft 365 のアーカイブでは、有価証券取引委員会 (SEC) ルール 17a-4 (SEC) に準拠したストレージが提供されています。 Microsoft 365 は、保持ロックを含む、インプレース保持ポリシーと保持ポリシーを使用して、書き換え不可で消去不可能な形式で収集されたすべてのデータの永続的なファイルを保持します。

具体的には次のとおりです。

- 前述のアイテム保持ポリシーを使用して保存されたすべてのレコードは、通常のユーザーの purview から専用のストレージ領域に保持されます。 許可されたユーザーのみが、これらのレコードにアクセスして検索できますが、変更または削除することはできません。
- 各アイテムのメタデータには、保持期間の計算に使用されるタイムスタンプが含まれています。 新しいアイテムを受信または作成したときに、タイムスタンプが適用され、メタデータから変更または削除することはできません。
- Microsoft 365 のアーカイブを使用すると、ユーザーはさまざまなアイテム保持ポリシーを組み合わせ、アクションを保持して詳細なアイテム保持ポリシーを作成できます。 これらのポリシーは、保持されるアイテムの種類または場所、および保持期間を定義します。
- 保持ロック機能を使用すると、ポリシーを制限されたポリシーにするかどうかをユーザーが選択できるようになります。 制限付きポリシーを使用すると、すべてのユーザーがアイテム保持ポリシーを削除、無効化、または変更することができなくなります。 これは、保持ロックが有効になっている場合、無効にすることはできず、保持ポリシーによって収集された既存の保管担当者からのデータが保存期間中に上書き、変更、消去、または削除されるメカニズムは存在しないことを意味します。 さらに、保持ロックで設定された保持期間を短縮または縮小することはできません。 しかし、前述したように、保存されたデータの保存期間を維持するために法的な要件がある場合は、延長される可能性があります。 保持ロックを使用すると、管理者または特定のコントロールアクセス権を持つユーザー以外は、その設定を変更したり、2003 365 保存されているデータを上書きまたは消去したりすることができなくなります。

Microsoft 365 によって規制上の義務にどのように役立つかを理解するために、特にルール17a-4 の要件については、「Exchange Online のアーカイブ、SharePoint Online、OneDrive for Business、Skype for Business に関する[ホワイトペーパー](https://www.microsoft.com/microsoft-365/blog/wp-content/uploads/2015/11/Microsoft-EOA-White-Paper.pdf) 」を参照してください。 ホワイトペーパーでは、SEC Rule 17a-4 の各要件に対して Microsoft 365 アーカイブの機能と機能の詳細な分析を行い、Microsoft 365 のアーカイブによってこれらの要件を満たすことができるようにすることについても説明します。
