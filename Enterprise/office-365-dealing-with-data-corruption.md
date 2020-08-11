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
ms.custom: seo-marvel-apr2020
description: この記事では、Microsoft 365 のデータ破損と、データの防止と回復のために Microsoft によって行われた作業について説明します。
ms.openlocfilehash: dc8e865a69e110fa0a68e6cd9d9f4d6b45d43d71
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606633"
---
# <a name="dealing-with-data-corruption-in-microsoft-365"></a>Microsoft 365 でのデータの破損への対処

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
