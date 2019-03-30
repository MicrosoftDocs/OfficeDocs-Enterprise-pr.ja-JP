---
title: Office 365 のディレクトリ同期の状態を表示する
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
ms.openlocfilehash: a38b723db6f5bafe246e774972ca89c65bc9c846
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001570"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Office 365 のディレクトリ同期の状態を表示する

オンプレミス環境と Office 365 を同期することによって、オンプレミスの Active Directory を Azure AD に統合している場合は、同期の状態を確認することもできます。
  
## <a name="view-directory-synchronization-status"></a>ディレクトリ同期の状態を表示する

- [Microsoft 365 管理センター](https://admin.microsoft.com)にサインインし、ホームページの [ **DirSync Status** ] を選択します。
- または、[**アクティブ**な**** \>ユーザー] ページに移動し、 **[アクティブなユーザー** ] ページで、[**ディレクトリ同期**の**追加** \> ] を選択します。 [**ディレクトリ同期**] ウィンドウで、[ **DirSync management に移動] を**選択します。

## <a name="information-on-the-manage-directory-synchronization-page"></a>[ディレクトリ同期の管理] ページの情報

次の表に、ページの情報を取得できる機能を示します。
  
ディレクトリ同期に問題がある場合は、このページにもエラーが表示されます。 発生する可能性のあるさまざまなエラーの詳細については、「 [Office 365 でのディレクトリ同期エラーの識別](identify-directory-synchronization-errors.md)」を参照してください。
  
|**アイテム**|**目的**|
|:-----|:-----|
|**確認されたドメイン** | 自分が所有していることが確認された Office 365 テナント内のドメインの数。 |
|**確認されていないドメイン** | 追加されたが確認されていないドメイン。 |
|**ディレクトリ同期の有効化** |True または False。 ディレクトリ同期を有効にしたかどうかを指定します。 |
|**最新のディレクトリ同期** | ディレクトリ同期が最後に実行した時刻。 前回の同期が3日以上前の場合は、警告とトラブルシューティングツールへのリンクが表示されます。 |
|**パスワード同期の有効化** | True または False。 オンプレミスと Office 365 テナント間でパスワードハッシュを同期するかどうかを指定します。 |
|**前回のパスワード同期** | 前回のパスワードハッシュ同期を実行した時刻。 前回の同期が3日以上前の場合は、警告とトラブルシューティングツールへのリンクが表示されます。 |
|**ディレクトリ同期クライアントバージョン** | Azure AD Connect の新しいバージョンがリリースされた場合のダウンロードリンクが含まれています。 |
|**idfix ツール** | ローカルの Active Directory を確認するためのツールである[idfix](install-and-run-idfix.md)へのリンクをダウンロードします。 |
|**ディレクトリ同期サービスアカウント** | Office 365 ディレクトリ同期サービスアカウントの名前が表示されます。 |