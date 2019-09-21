---
title: Office 365 データ破損を処理する
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
description: Office 365 でのデータ破損の説明と、Microsoft による防止と復旧の取り組み。
ms.openlocfilehash: 9a1c0b2e1ebd0c9f1faa698fa12756d32783914c
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067619"
---
# <a name="dealing-with-data-corruption-in-office-365"></a>Office 365 でのデータ破損の処理

大規模なクラウドサービスを実行するための困難な側面の1つは、大量のデータと独立したシステムがある場合に、データの破損を処理する方法です。 データの破損は、次のような場合に発生することがあります。

- アプリケーションまたはインフラストラクチャのバグ。アプリケーション状態の一部またはすべてが破損している
- データ損失またはデータの読み取りができない原因となるハードウェアの問題
- 人的運用エラー
- 悪意のあるハッカーおよび不満を持つ従業員
- データの損失が発生する外部サービスのインシデント

データ整合性の復元性が高いと、データ破損インシデントが減少するため、Microsoft は Office 365 保護メカニズムを組み込み、破損が発生しないようにします。また、そのような場合にデータを回復できるようにするシステムとプロセスも組み込まれています。 エンジニアリングリリースプロセスのさまざまな段階内に存在するチェックとプロセスは、データ破損に対する復元性を向上させるために、次のようなものがあります。

- システムデザイン
- コードの編成と構造
- コードレビュー
- 単体テスト、統合テスト、およびシステムテスト
- トリップワイヤテスト/ゲート

Office 365 の運用環境では、データセンター間のピアレプリケーションによって、データのライブコピーが常に複数存在することが保証されます。 失われたサーバーを回復するために標準的な画像とスクリプトを使用し、レプリケーションされたデータを使用して顧客データを復元します。 組み込みのデータ復元チェックとプロセスにより、Microsoft は Office 365 情報システムのドキュメント (セキュリティ関連のドキュメントを含む) のみをバックアップし、SharePoint Online に組み込みのレプリケーションを使用し、内部コードを保持しています。リポジトリツール、ソースの修理工場。 システムドキュメントは SharePoint Online に格納されており、ソースの引き取りにはシステムとアプリケーションのイメージが含まれています。 SharePoint Online とソース引き取りの両方がバージョン管理を使用し、ほぼリアルタイムでレプリケートされます。
