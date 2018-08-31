---
title: Office 365 IdFix トランザクション ・ ログ
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: 例を提供し、Office 365 の IdFix トランザクション ・ ログの既定のログ レベル、名前付け規則について説明します。
ms.openlocfilehash: 016318c7e771ec6c5f90336e11c5dd011144d12e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541664"
---
# <a name="office-365-idfix-transaction-log"></a>Office 365 IdFix トランザクション ・ ログ

例を提供し、Office 365 の IdFix トランザクション ・ ログの既定のログ レベル、名前付け規則について説明します。
  
## <a name="idfix-transaction-log-location"></a>IdFix トランザクション ログの場所

Office 365 の IdFix ツールは、IdFix で、 **[適用**] をクリックし、Active Directory フォレストに変更を適用するたびに新しいトランザクション ・ ログを作成します。トランザクション ・ ログは、IdFix がインストールされている同じフォルダーに保存されます。既定では、このフォルダーは C:\Deployment の Tools\IDFix です。トランザクション ログ ファイル名の例では、Verbose 2018 1-6-6-17-22 PM 6 17:22 午後に、2018 年 6 月 1 日に生成されたファイルを指定する日付と時刻のスタンプ形式を使用して詳細をログ出力のレベルを示します。 
  
## <a name="idfix-transaction-log-logging-level"></a>IdFix トランザクション ログのログ出力レベル

トランザクション ログ ファイル名に含まれる verbose という単語は、ファイルのログ出力のレベルを示します。Verbose は、ログ内に最大量の情報が収集されることを表しています。既定では、このログ出力レベルになっています。現状では、ログ出力レベルを変更することはできません。
  
## <a name="idfix-transaction-log-format"></a>IdFix トランザクション ログの形式

IdFix では、各**更新**操作の結果を次の例のように、トランザクション ・ ログに書き込まれます。
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE

```