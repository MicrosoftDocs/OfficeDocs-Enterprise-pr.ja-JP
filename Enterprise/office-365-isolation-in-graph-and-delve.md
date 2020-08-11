---
title: Microsoft Graph および Delve での microsoft 365 テナントの分離
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
description: この記事では、Office Graph と Delve で Microsoft 365 テナントの分離がどのように機能するかについて説明します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 285f910362628f52c379fcf535da7d0b1365383a
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605599"
---
# <a name="microsoft-365-tenant-isolation-in-the-microsoft-graph-and-delve"></a>Microsoft Graph および Delve での microsoft 365 テナントの分離

## <a name="tenant-isolation-in-the-microsoft-graph"></a>Microsoft Graph でのテナントの分離

Microsoft [Graph](https://developer.microsoft.com/graph)では、microsoft 365 Services (Exchange Online、SharePoint Online、Yammer、Skype for Business、Azure Active Directory など)、および外部サービス (他の microsoft サービスやサードパーティのサービスなど) でのアクティビティについて解説しています。 Microsoft Graph のコンポーネントは、Microsoft 365 全体で使用されます。 Microsoft Graph は、コンテンツとアクティビティのコレクション、およびそれらの間の関係を表しています。これらは、Office スイート全体で行われます。 洗練されたマシン学習技術を使用して、ユーザーを関連するコンテンツ、会話、ユーザーに接続します。 たとえば、SharePoint Online のテナントインデックスには、Delve クエリを処理するために使用される Microsoft Graph インデックスがあり、SharePoint Online の分析処理エンジンを使用してシグナルを格納し、insights を計算します。 Exchange Online は、各ユーザーの受信者キャッシュをテナント分析への入力として計算します。

Microsoft Graph には、ユーザーやドキュメントなどのエンタープライズオブジェクト、およびこれらのオブジェクト間の関係と相互作用に関する情報が含まれています。 関係とやり取りは、*エッジ*で表現されます。 Microsoft Graph は、同じテナント内の*ノード*間でのみエッジが存在できるように、テナントでセグメント化されます。 *ノード*は、URI (Uniform resource Identifier)、ノードの種類、アクセス制御リスト、および*メタデータ*とエッジを含む一連のファセットを持つエンティティです。 各ノードにはメタデータとエッジが関連付けられており、共通のナレッジモデルと同じように*ファセット*に配置されています。 *メタデータ*には、Microsoft Graph での検索、フィルター処理、分析に使用できるノードに格納されているプロパティという名前が付けられています。 *ファセット*は、ノード上のメタデータとエッジの論理的なコレクションです。 各ファセットは、ノードの1つの側面について記述します。 

Microsoft Graph では、すべてのデータが単一のリポジトリに格納されるわけではありません。代わりに、他の場所に存在するデータに関するメタデータと関係が保存されます。 Microsoft Graph は、いくつかのデータストアと処理コンポーネントで構成されています。

- テナントグラフストアは、効率的な分析のために最適化されたバルクストレージを提供します。
- アクティブなコンテンツキャッシュを使用すると、ユーザーエクスペリエンスを促進するためにアクティブなノードとエッジにすばやくランダムにアクセスできます。
- 入力ルーターは、テナントグラフへの変更の内部および外部にあるコンポーネントに通知します。

テナント全体の計算に関連する各ワークロードの分析を推定し、テナントのグラフにプッシュします。 テナント内のすべてのアクティビティについてのテナント分析の理由。動作のパターンに関する洞察を生み出すことができます。 たとえば、Exchange Online は、分析を使用している各ユーザーの受信者キャッシュを、各ユーザーのメールボックスに対して効率的に計算します。 これらのユーザーごとの分析によって、各ユーザーに一連の*受信者キャッシュエッジ*が生成されます。これは、テナントのグラフにプッシュされます。 これにより、分析処理の多くがソースデータにできるだけ近い状態に保たれます。

## <a name="tenant-isolation-in-delve"></a>Delve でのテナントの分離

前述したように、Microsoft Graph では、ユーザーが企業内の現在のアクティビティを見つけて共同作業する際に役立つエクスペリエンスを向上させることができます。また、ワークロードと Microsoft 365 を越えたコンテンツとアクティビティに関する分析のための、エンティティ中心のプラットフォームを提供します。 Delve は、Microsoft Graph が提供する最初の作業です。
Delve は microsoft 365 の web experience で、microsoft Graph を介して microsoft の365および Yammer Enterprise から Microsoft 365 ユーザーにコンテンツを表示します。 Web *experience は、* データをさまざまなボードとして表示し、*それぞれに特定*のトピックを表示します。 各ボードは、ドキュメントの概要テキストと画像を表示する複数のドキュメントカードで構成されます。 カードを使用すると、ドキュメントまたは Yammer ページを開くなど、ユーザーがドキュメントを開くことができます。 Microsoft 365 テナントの各ユーザーには、このユーザーに最も関連のあるドキュメントを表示するページと、その人物と対話するために Exchange Online または Skype for Business を起動できるアイコンがあります。 Delve は Microsoft Graph API に基づいているため、その API のテナントベースの分離によってバインドされます。