---
title: Microsoft 365 でのディレクトリ同期状態の表示
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: ディレクトリ同期を非アクティブ化する方法について説明します。 その状態を表示することもできます。
ms.openlocfilehash: d6f3a9f1f4e069716501f58e188daedacbf7e597
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906200"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Microsoft 365 でのディレクトリ同期状態の表示

オンプレミス環境を Microsoft 365 と同期させることによって、オンプレミスの Active Directory を Azure AD と統合した場合は、同期の状態を確認することもできます。
  
## <a name="view-directory-synchronization-status"></a>ディレクトリ同期の状態を表示する

- [Microsoft 365 管理センター](https://admin.microsoft.com)にサインインし、ホームページの [ **DirSync Status** ] を選択します。
- または、[アクティブなユーザー] ページ**に移動**し、[ \> **Active users****アクティブなユーザー** ] ページで、[ディレクトリ同期の**追加**] を選択し \> **Directory synchronization**ます。 [**ディレクトリ同期**] ウィンドウで、[ **DirSync management に移動] を**選択します。

## <a name="information-on-the-manage-directory-synchronization-page"></a>[ディレクトリ同期の管理] ページの情報

次の表に、ページの情報を取得できる機能を示します。
  
ディレクトリ同期に問題がある場合は、このページにもエラーが表示されます。 発生する可能性のあるさまざまなエラーの詳細については、「 [Microsoft 365 でのディレクトリ同期エラーの識別](identify-directory-synchronization-errors.md)」を参照してください。
  
|**アイテム**|**目的**|
|:-----|:-----|
|**確認されたドメイン** | 自分が所有していることを確認した Microsoft 365 テナント内のドメインの数。 |
|**確認されていないドメイン** | 追加されたが確認されていないドメイン。 |
|**ディレクトリ同期の有効化** |True または False。 ディレクトリ同期を有効にしたかどうかを指定します。 |
|**最新のディレクトリ同期** | ディレクトリ同期が最後に実行した時刻。 前回の同期が3日以上前の場合は、警告とトラブルシューティングツールへのリンクが表示されます。 |
|**パスワード同期の有効化** | True または False。 オンプレミスと Microsoft 365 テナント間でパスワードハッシュを同期するかどうかを指定します。 |
|**前回のパスワード同期** | 前回のパスワードハッシュ同期を実行した時刻。 前回の同期が3日以上前の場合は、警告とトラブルシューティングツールへのリンクが表示されます。 |
|**ディレクトリ同期クライアントバージョン** | Azure AD Connect の新しいバージョンがリリースされた場合のダウンロードリンクが含まれています。 |
|**IDFix ツール** | ローカルの Active Directory を確認するためのツールである[Idfix](install-and-run-idfix.md)へのリンクをダウンロードします。 |
|**ディレクトリ同期サービスアカウント** | Microsoft 365 ディレクトリ同期サービスアカウントの名前を表示します。 |