---
title: Office 365 データの不変性
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
f1.keywords:
- NOCSH
description: Office 365 のデータの不変性を定義して説明します。
ms.openlocfilehash: fe6b2cf3d3ba2e0bb69f4275c77de0a452b3140f
ms.sourcegitcommit: 1c646afb10db9d3d1e6a346089b7845268b0c9d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "42605632"
---
# <a name="immutability-in-office-365"></a>Office 365 の不変性

コンプライアンス、内部ガバナンスの要件、訴訟リスクによって、組織はメールと関連データを検出可能な形式で保持する必要があります。 システム内のすべてのデータは検出可能である必要があり、破棄または変更することはできません。 業界標準の用語は、"不変" です。

従来の不変処理方法では、電子メールメッセージを別の読み取り専用の保存場所に移動することによって動作します。 このようなシステムは、証拠開示のためにメールボックスアイテムを保持することを目的としていますが、通常は日常のワークフローから保持されているアイテムを削除することによって、ユーザーの作業感に影響 IT 担当者にとって、この不変手法を使用するには、個別のサーバーとストレージインフラストラクチャを展開し、継続的に保守する必要があります。 検出は、メールシステムの外部にあるツールを使用して実行され、関連する展開とメンテナンスのコストを含みます。

Office 365 およびそのサービスのアーカイブのインプレース保持および保持ポリシー機能により、さまざまな種類の受信、内部、送信データを保持して保持することができます。 これには、次の内容が含まれます。

- 受信および送信電子メール通信
- メールフォームまたは共有オンラインドキュメントに含まれるブックとレコード
- 会議出席依頼
- Fax
- インスタントメッセージ
- オンライン会議中に共有するドキュメント
- Voicemails

さらに、Microsoft は、サードパーティのデータキャプチャおよび管理ソリューションとの統合により、他のソースからの[データのアーカイブ](https://support.office.com/article/Archiving-third-party-data-in-Office-365-0ce338d5-3666-4a18-86ab-c6910ff408cc)を可能にするアドオン機能を開発しました。 サードパーティのデータがインポートされたら、次のような Office 365 コンプライアンス機能をデータに適用できます。

- [訴訟ホールド](https://docs.microsoft.com/microsoft-365/compliance/create-a-litigation-hold)
- [インプレース電子情報開示とホールド](https://docs.microsoft.com/microsoft-365/compliance/manage-legal-investigations)
- [コンプライアンス検索](https://docs.microsoft.com/microsoft-365/compliance/search-for-content)
- [インプレース アーカイブ](https://docs.microsoft.com/microsoft-365/compliance/enable-archive-mailboxes)
- [メールボックスの監査](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing)
- [アイテム保持ポリシー](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)

たとえば、メールボックスが訴訟ホールドの対象となっている場合、サードパーティのデータは保持されます。 インプレース電子情報開示またはコンプライアンス検索を使用して、サードパーティのデータを検索できます。 また、Microsoft データの場合と同じように、アーカイブポリシーとアイテム保持ポリシーをサードパーティデータに適用することができます。 Office 365 でサードパーティのデータをアーカイブすることにより、組織は政府および規制ポリシーに準拠し続けることができます。

Office 365 のアーカイブでは、有価証券取引委員会 (SEC) ルール 17a-4 (SEC) に準拠したストレージが提供されています。 Office 365 は、保持ロックを含む、インプレース保持ポリシーと保持ポリシーを使用して、書き換え不可で消去不可能な形式で収集されたすべてのデータの永続的なファイルを保持します。

具体的には次のとおりです。

- 前述のアイテム保持ポリシーを使用して保存されたすべてのレコードは、通常のユーザーの purview から専用のストレージ領域に保持されます。 許可されたユーザーのみが、これらのレコードにアクセスして検索できますが、変更または削除することはできません。
- 各アイテムのメタデータには、保持期間の計算に使用されるタイムスタンプが含まれています。 新しいアイテムを受信または作成したときに、タイムスタンプが適用され、メタデータから変更または削除することはできません。
- Office 365 のアーカイブを使用すると、ユーザーはさまざまなアイテム保持ポリシーを組み合わせ、アクションを保持して詳細なアイテム保持ポリシーを作成できます。 これらのポリシーは、保持されるアイテムの種類または場所、および保持期間を定義します。
- 保持ロック機能を使用すると、ポリシーを制限されたポリシーにするかどうかをユーザーが選択できるようになります。 制限付きポリシーを使用すると、すべてのユーザーがアイテム保持ポリシーを削除、無効化、または変更することができなくなります。 これは、保持ロックが有効になっている場合、無効にすることはできず、アイテム保持ポリシーによって収集された既存の保管担当者からのデータは、その中で上書き、変更、消去、削除される可能性があることを意味します。保持期間。 さらに、保持ロックで設定された保持期間を短縮または縮小することはできません。 しかし、前述したように、保存されたデータの保存期間を維持するために法的な要件がある場合は、延長される可能性があります。 保持ロックによって、管理者や特定のコントロールアクセス権を持つユーザー以外は、設定を変更したり、2003 365 保存されているデータを上書きまたは消去したりすることができます。ルール 17a-4-4。

Office 365 が規制上の義務を満たすのにどのように役立つかについて理解するために、特にルール17a-4 の要件については、「Exchange Online のアーカイブ、SharePoint Online、OneDrive for Business、Skype for Business に関する[ホワイトペーパー](https://www.microsoft.com/microsoft-365/blog/wp-content/uploads/2015/11/Microsoft-EOA-White-Paper.pdf) 」を参照してください。 ホワイトペーパーでは、SEC Rule 17a-4 の各要件に対して Office 365 アーカイブの機能と機能の詳細な分析を行い、Office 365 のアーカイブによってこれらの機能を満たすことができるようにすることについても説明します。要件.
