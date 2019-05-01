---
title: Office 365 idfix トランザクションログ
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: 例を示し、Office 365 idfix トランザクションログの名前付け規則と既定のログレベルについて説明します。
ms.openlocfilehash: c652f8dcbc23a6f0165d894ce6317443db72ceee
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490943"
---
# <a name="office-365-idfix-transaction-log"></a>Office 365 idfix トランザクションログ

例を示し、Office 365 idfix トランザクションログの名前付け規則と既定のログレベルについて説明します。
  
## <a name="idfix-transaction-log-location"></a>idfix トランザクションログの場所

Office 365 idfix ツールは、[idfix で**適用**] をクリックし、変更を Active Directory フォレストに適用するたびに、新しいトランザクションログを作成します。 トランザクションログは、idfix をインストールしたのと同じフォルダーに保存されます。 既定では、このフォルダーは c:\windows 展開ツール \ [fix] になります。 トランザクションログファイル名には、日付と時刻の形式が使用されます。たとえば、Verbose 6-1-2018 6-17-22 pm は、2018年6月1日 (6:17:22 pm) に生成されたファイルを示します。 Verbose ログレベルを示します。 
  
## <a name="idfix-transaction-log-logging-level"></a>idfix トランザクションログのログ出力レベル

トランザクションログファイル名に verbose という語を指定すると、ファイル内のログ記録のレベルを示します。 Verbose は、ログに最大量の情報をキャプチャすることを意味します。 これは、既定のログ出力レベルです。 現時点では、ログ出力レベルを変更することはできません。
  
## <a name="idfix-transaction-log-format"></a>idfix トランザクションログの形式

idfix は、次の例に示すように、各**UPDATE**アクションの結果をトランザクションログに書き込みます。
  
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