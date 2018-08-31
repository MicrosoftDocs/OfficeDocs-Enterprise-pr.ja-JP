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
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="2ee65-103">無駄のない popouts を使用して、メール メッセージを読むときに使用するメモリを削減するには</span><span class="sxs-lookup"><span data-stu-id="2ee65-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="2ee65-p101">この資料には、web 上の Outlook でメッセージのダウンロードのパフォーマンスを向上させるための情報が含まれています。この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)のプロジェクトの一部です。</span><span class="sxs-lookup"><span data-stu-id="2ee65-p101">This article contains information for improving message download performance in Outlook on the web. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="2ee65-p102">Office 365 グローバル管理者は、*無駄のない popouts*より小さなメモリを消費するバージョンは、マイクロソフトのエッジまたは Internet Explorer で特定の電子メール メッセージの削減を実現するのには、web 上で Outlook を構成できます。無駄のない popouts は、構成すると、web 上の Outlook のパフォーマンスを最適化するサーバー側のコンポーネントの表示が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="2ee65-p102">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer. When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="2ee65-108">2018 年 3 月の時点で無駄のない popouts 現在ご利用いただけませんの使用権の制限、情報権利管理 (IRM) などを指定するメッセージ。</span><span class="sxs-lookup"><span data-stu-id="2ee65-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="2ee65-109">これらの機能は、メイン ウィンドウでの作業は続行されますが、無駄のない popouts では使用できません。</span><span class="sxs-lookup"><span data-stu-id="2ee65-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="2ee65-110">Outlook アドイン</span><span class="sxs-lookup"><span data-stu-id="2ee65-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="2ee65-111">Skype ビジネスの存在を</span><span class="sxs-lookup"><span data-stu-id="2ee65-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="2ee65-112">**Office 365 組織内のすべてのユーザーに対して無駄のない popouts を構成するのには**</span><span class="sxs-lookup"><span data-stu-id="2ee65-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="2ee65-113">[オンライン リモート PowerShell を使用して Exchange に接続](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )します。</span><span class="sxs-lookup"><span data-stu-id="2ee65-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="2ee65-114">次のように LeanPopoutEnabled パラメーターを使用して[セット OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx)コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="2ee65-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    <span data-ttu-id="2ee65-115">たとえば、組織内のすべてのユーザーに対して無駄のない popouts を有効にします。</span><span class="sxs-lookup"><span data-stu-id="2ee65-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    <span data-ttu-id="2ee65-116">組織内のすべてのユーザーに対して無駄のない popouts を無効にするには。</span><span class="sxs-lookup"><span data-stu-id="2ee65-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


