---
title: リーンポップアウトを使用してメールメッセージの読み取り時に使用されるメモリを削減する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/8/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: この記事では、Outlook on the web でのメッセージダウンロードのパフォーマンスを向上させる方法について説明します。
ms.openlocfilehash: bb9a11a27af0b66f1dd557c459d1904c2e57ae92
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030872"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="7eddf-103">リーンポップアウトを使用してメールメッセージの読み取り時に使用されるメモリを削減する</span><span class="sxs-lookup"><span data-stu-id="7eddf-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="7eddf-104">この記事では、Outlook on the web でのメッセージダウンロードのパフォーマンスを向上させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7eddf-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="7eddf-105">この記事は、 [Office 365 プロジェクトのネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="7eddf-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="7eddf-106">Office 365 のグローバル管理者として、Outlook on the web を構成して、Microsoft Edge または Internet Explorer で特定の電子メール*メッセージをより*小さく、より小さなメモリを消費するバージョンにすることができます。</span><span class="sxs-lookup"><span data-stu-id="7eddf-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="7eddf-107">Web 上の Outlook に対してリーンポップアウトが構成されている場合、サーバー側でレンダリングされるコンポーネントはパフォーマンスを最適化するために読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="7eddf-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="7eddf-108">2018年3月現在、使用権限の制限を指定するメッセージ (Information rights Management (IRM) など) に対して、リーンポップアウトは現在使用できません。</span><span class="sxs-lookup"><span data-stu-id="7eddf-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="7eddf-109">これらの機能は、メインウィンドウでは引き続き動作しますが、リーン popouts では使用できません。</span><span class="sxs-lookup"><span data-stu-id="7eddf-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="7eddf-110">Outlook アドイン</span><span class="sxs-lookup"><span data-stu-id="7eddf-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="7eddf-111">Skype for Business のプレゼンス</span><span class="sxs-lookup"><span data-stu-id="7eddf-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="7eddf-112">**Office 365 組織内のすべてのユーザーのリーンポップアウトを構成するには**</span><span class="sxs-lookup"><span data-stu-id="7eddf-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="7eddf-113">[リモート PowerShell を使用して Exchange Online に接続](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )します。</span><span class="sxs-lookup"><span data-stu-id="7eddf-113">[Connect to Exchange Online Using Remote PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="7eddf-114">LeanPopoutEnabled パラメーターを使用して、次のように[コマンドレットを実行します](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7eddf-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="7eddf-115">たとえば、組織内のすべてのユーザーのリーンポップアウトを有効にするには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="7eddf-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="7eddf-116">組織内のすべてのユーザーのリーンポップアウトを無効にするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="7eddf-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


