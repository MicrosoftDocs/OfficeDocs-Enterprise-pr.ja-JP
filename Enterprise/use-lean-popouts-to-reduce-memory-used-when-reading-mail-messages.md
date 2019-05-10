---
title: リーンポップアウトを使用してメールメッセージの読み取り時に使用されるメモリを削減する
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: この記事では、Outlook on the web でのメッセージダウンロードのパフォーマンスを向上させる方法について説明します。
ms.openlocfilehash: 55cbdec3dc994f3301afaf1bf0a261de446d522a
ms.sourcegitcommit: a35d23929bfbfd956ee853b5e828b36e2978bf36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "33655781"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>リーンポップアウトを使用してメールメッセージの読み取り時に使用されるメモリを削減する

この記事では、Outlook on the web でのメッセージダウンロードのパフォーマンスを向上させる方法について説明します。 この記事は、 [Office 365 プロジェクトのネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。
   
Office 365 のグローバル管理者として、Outlook on the web を構成** して、Microsoft Edge または Internet Explorer で特定の電子メールメッセージをより小さく、より小さなメモリを消費するバージョンにすることができます。 Web 上の Outlook に対してリーンポップアウトが構成されている場合、サーバー側でレンダリングされるコンポーネントはパフォーマンスを最適化するために読み込まれます。 
  
> [!NOTE]
> 2018年3月現在、使用権限の制限を指定するメッセージ (Information rights Management (IRM) など) に対して、リーンポップアウトは現在使用できません。 
  
これらの機能は、メインウィンドウでは引き続き動作しますが、リーン popouts では使用できません。
  
- Outlook アドイン
    
- Skype for Business のプレゼンス
    
 **Office 365 組織内のすべてのユーザーのリーンポップアウトを構成するには**
  
1. [リモート PowerShell を使用して Exchange Online に接続](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )します。
    
2. LeanPopoutEnabled パラメーター [](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx)を使用して、次のようにコマンドレットを実行します。 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  たとえば、組織内のすべてのユーザーのリーンポップアウトを有効にするには、次のように入力します。
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  組織内のすべてのユーザーのリーンポップアウトを無効にするには、次のようにします。
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


