---
title: Office 365 のディレクトリ同期の状態を表示する
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: ディレクトリ同期を無効にする方法を説明します。ステータスを表示することもできます。
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541821"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Office 365 のディレクトリ同期の状態を表示する
Azure AD を Office 365 で、オンプレミス環境を同期することにより、オンプレミスの Active Directory を統合した場合は、同期のステータスを確認することも。
  
## <a name="view-directory-synchronization-status"></a>ディレクトリ同期の状態の表示
- Office 365 の管理センターにサインインし、[ホーム] ページで、**ディレクトリ同期のステータス**を選択します。 
- 代わりに、**ユーザー**に情報を移動することができます\>**アクティブなユーザー**の**詳細**を選択して [**アクティブ ユーザ**] ページで、 \> **ディレクトリ同期**します。**ディレクトリ同期**] ウィンドウで、[**ディレクトリ同期の管理に移動します**を選択します。
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>ディレクトリ同期の管理] ページの情報

次の表は、ページ上の情報を確認する機能を一覧します。
  
ディレクトリ同期によって、問題がある、このページにも同様のエラーの一覧が表示されます。さまざまなエラーが発生する可能性の詳細については、 [Office 365 のディレクトリ同期エラーを識別する](identify-directory-synchronization-errors.md)を参照してください。
  
|**アイテム**|**何**|
|:-----|:-----|
|**ドメインの確認** | 所有することを確認した場合、Office 365 テナント内のドメインの数。 |
|**ドメインが確認されていません** | ドメインを追加するが確認されていません。 |
|**ディレクトリ同期が有効になっています。** |True または false を指定します。ディレクトリ同期を有効にするかどうかを指定します。 |
|**最新のディレクトリ同期** | 前回のディレクトリ同期を実行します。表示されます警告リンク トラブルシューティング ツールを前回の同期が 3 日以上前である場合。 |
|**パスワード同期が有効になっています。** | True または false を指定します。設置と、Office 365 テナント間でのパスワード ハッシュの同期があるかどうかを指定します。 |
|**最後のパスワード同期** | 前回のパスワード ハッシュの同期を実行します。表示されます警告リンク トラブルシューティング ツールを前回の同期が 3 日以上前である場合。 |
|**ディレクトリ同期クライアントのバージョン** | Azure AD 接続の新しいバージョンがリリースされている場合は、ダウンロードのリンクに含まれています。 |
|**IDFix ツール** | [IDFix](install-and-run-idfix.md)、ローカルの Active Directory をチェックすることができますを使用するツールへのリンクをダウンロードします。 |
|**ディレクトリ同期サービス アカウント** | Office 365 のディレクトリ同期サービス アカウントの名前を表示します。 |