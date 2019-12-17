---
title: Office 365 IdFix トランザクションログ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: 例を示し、Office 365 IdFix トランザクションログの名前付け規則と既定のログレベルについて説明します。
ms.openlocfilehash: af1ce72760d9a94438eeead50474094ca0e3a2bd
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072169"
---
# <a name="office-365-idfix-transaction-log"></a><span data-ttu-id="6411e-103">Office 365 IdFix トランザクションログ</span><span class="sxs-lookup"><span data-stu-id="6411e-103">Office 365 IdFix transaction log</span></span>

<span data-ttu-id="6411e-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="6411e-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="6411e-105">例を示し、Office 365 IdFix トランザクションログの名前付け規則と既定のログレベルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6411e-105">Provides an example and describes the naming convention and default log level of the Office 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="6411e-106">IdFix トランザクションログの場所</span><span class="sxs-lookup"><span data-stu-id="6411e-106">IdFix transaction log location</span></span>

<span data-ttu-id="6411e-107">Office 365 IdFix ツールは、[IdFix で**適用**] をクリックし、変更を Active Directory フォレストに適用するたびに、新しいトランザクションログを作成します。</span><span class="sxs-lookup"><span data-stu-id="6411e-107">The Office 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="6411e-108">トランザクションログは、IdFix をインストールしたのと同じフォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="6411e-108">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="6411e-109">既定では、このフォルダーは C:\windows 展開ツール \ [fix] になります。</span><span class="sxs-lookup"><span data-stu-id="6411e-109">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="6411e-110">トランザクションログファイル名には、日付と時刻の形式が使用されます。たとえば、Verbose 6-1-2018 6-17-22 PM は、2018年6月1日 (6:17:22 PM) に生成されたファイルを示します。</span><span class="sxs-lookup"><span data-stu-id="6411e-110">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="6411e-111">Verbose ログレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="6411e-111">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="6411e-112">IdFix トランザクションログのログ出力レベル</span><span class="sxs-lookup"><span data-stu-id="6411e-112">IdFix transaction log logging level</span></span>

<span data-ttu-id="6411e-113">トランザクションログファイル名に verbose という語を指定すると、ファイル内のログ記録のレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="6411e-113">The word verbose in the transaction log file name indicates the level of logging in the file.</span></span> <span data-ttu-id="6411e-114">Verbose は、ログに最大量の情報をキャプチャすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6411e-114">Verbose means that the maximum amount of information is captured in the log.</span></span> <span data-ttu-id="6411e-115">これは、既定のログ出力レベルです。</span><span class="sxs-lookup"><span data-stu-id="6411e-115">This is the default logging level.</span></span> <span data-ttu-id="6411e-116">現時点では、ログ出力レベルを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="6411e-116">At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="6411e-117">IdFix トランザクションログの形式</span><span class="sxs-lookup"><span data-stu-id="6411e-117">IdFix transaction log format</span></span>

<span data-ttu-id="6411e-118">IdFix は、次の例に示すように、各**UPDATE**アクションの結果をトランザクションログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6411e-118">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
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