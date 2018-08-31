---
title: 無駄のない popouts を使用して、メール メッセージを読むときに使用するメモリを削減するには
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
description: この資料には、web 上の Outlook でメッセージのダウンロードのパフォーマンスを向上させるための情報が含まれています。
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541589"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>無駄のない popouts を使用して、メール メッセージを読むときに使用するメモリを削減するには

この資料には、web 上の Outlook でメッセージのダウンロードのパフォーマンスを向上させるための情報が含まれています。この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)のプロジェクトの一部です。
   
Office 365 グローバル管理者は、*無駄のない popouts*より小さなメモリを消費するバージョンは、マイクロソフトのエッジまたは Internet Explorer で特定の電子メール メッセージの削減を実現するのには、web 上で Outlook を構成できます。無駄のない popouts は、構成すると、web 上の Outlook のパフォーマンスを最適化するサーバー側のコンポーネントの表示が読み込まれます。 
  
> [!NOTE]
> 2018 年 3 月の時点で無駄のない popouts 現在ご利用いただけませんの使用権の制限、情報権利管理 (IRM) などを指定するメッセージ。 
  
これらの機能は、メイン ウィンドウでの作業は続行されますが、無駄のない popouts では使用できません。
  
- Outlook アドイン
    
- Skype ビジネスの存在を
    
 **Office 365 組織内のすべてのユーザーに対して無駄のない popouts を構成するのには**
  
1. [オンライン リモート PowerShell を使用して Exchange に接続](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )します。
    
2. 次のように LeanPopoutEnabled パラメーターを使用して[セット OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx)コマンドレットを実行します。 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    たとえば、組織内のすべてのユーザーに対して無駄のない popouts を有効にします。
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    組織内のすべてのユーザーに対して無駄のない popouts を無効にするには。
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


