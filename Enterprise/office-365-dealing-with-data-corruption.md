---
title: Microsoft 365 データ破損の処理
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
description: Microsoft 365 でのデータ破損の説明と、Microsoft による防止と復旧の取り組み。
ms.openlocfilehash: 674f2a3a026c5706f5c3a23db6e2d968ed815656
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998451"
---
# <a name="dealing-with-data-corruption-in-microsoft-365"></a>Microsoft 365 でのデータ破損の処理

大規模なクラウドサービスを実行するための困難な側面の1つは、大量のデータと独立したシステムがある場合に、データの破損を処理する方法です。 データの破損は、次のような場合に発生することがあります。

- アプリケーションまたはインフラストラクチャのバグ。アプリケーション状態の一部またはすべてが破損している
- データ損失またはデータの読み取りができない原因となるハードウェアの問題
- 人的運用エラー
- 悪意のあるハッカーおよび不満を持つ従業員
- データの損失が発生する外部サービスのインシデント

データ整合性の弾力性が高いと、データ破損インシデントが減少するため、Microsoft は、破損が発生しないように Microsoft 365 保護メカニズムに組み込みました。また、そのような場合にデータを回復できるようにするためのシステムとプロセスも組み込まれています。 エンジニアリングリリースプロセスのさまざまな段階内に存在するチェックとプロセスは、データ破損に対する復元性を向上させるために、次のようなものがあります。

- システムデザイン
- コードの編成と構造
- コードレビュー
- 単体テスト、統合テスト、およびシステムテスト
- トリップワイヤテスト/ゲート

Microsoft 365 の運用環境では、データセンター間のピアレプリケーションによって、データのライブコピーが常に複数存在することが保証されます。 失われたサーバーを回復するために標準的な画像とスクリプトを使用し、レプリケーションされたデータを使用して顧客データを復元します。 組み込まれているデータの復元チェックとプロセスにより、Microsoft は Microsoft 365 information system のドキュメント (セキュリティ関連ドキュメントを含む) のみをバックアップし、SharePoint Online の組み込みレプリケーションおよび内部コードリポジトリツールであるソースの引き取り修理を使用しています。 システムドキュメントは SharePoint Online に格納されており、ソースの引き取りにはシステムとアプリケーションのイメージが含まれています。 SharePoint Online とソース引き取りの両方がバージョン管理を使用し、ほぼリアルタイムでレプリケートされます。
