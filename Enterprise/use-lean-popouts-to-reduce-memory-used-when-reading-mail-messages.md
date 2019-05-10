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
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="94b64-103">リーンポップアウトを使用してメールメッセージの読み取り時に使用されるメモリを削減する</span><span class="sxs-lookup"><span data-stu-id="94b64-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="94b64-104">この記事では、Outlook on the web でのメッセージダウンロードのパフォーマンスを向上させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="94b64-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="94b64-105">この記事は、 [Office 365 プロジェクトのネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="94b64-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="94b64-106">Office 365 のグローバル管理者として、Outlook on the web を構成\*\* して、Microsoft Edge または Internet Explorer で特定の電子メールメッセージをより小さく、より小さなメモリを消費するバージョンにすることができます。</span><span class="sxs-lookup"><span data-stu-id="94b64-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="94b64-107">Web 上の Outlook に対してリーンポップアウトが構成されている場合、サーバー側でレンダリングされるコンポーネントはパフォーマンスを最適化するために読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="94b64-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="94b64-108">2018年3月現在、使用権限の制限を指定するメッセージ (Information rights Management (IRM) など) に対して、リーンポップアウトは現在使用できません。</span><span class="sxs-lookup"><span data-stu-id="94b64-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="94b64-109">これらの機能は、メインウィンドウでは引き続き動作しますが、リーン popouts では使用できません。</span><span class="sxs-lookup"><span data-stu-id="94b64-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="94b64-110">Outlook アドイン</span><span class="sxs-lookup"><span data-stu-id="94b64-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="94b64-111">Skype for Business のプレゼンス</span><span class="sxs-lookup"><span data-stu-id="94b64-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="94b64-112">**Office 365 組織内のすべてのユーザーのリーンポップアウトを構成するには**</span><span class="sxs-lookup"><span data-stu-id="94b64-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="94b64-113">[リモート PowerShell を使用して Exchange Online に接続](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )します。</span><span class="sxs-lookup"><span data-stu-id="94b64-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="94b64-114">LeanPopoutEnabled パラメーター [](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx)を使用して、次のようにコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="94b64-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="94b64-115">たとえば、組織内のすべてのユーザーのリーンポップアウトを有効にするには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="94b64-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="94b64-116">組織内のすべてのユーザーのリーンポップアウトを無効にするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="94b64-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


