---
title: Microsoft 365 Yammer エンタープライズアクセスコントロール
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: '概要: 運用環境での Yammer エンタープライズアクセス制御についての簡単な概要。'
ms.openlocfilehash: 0da479eb36359ec6b795a8e4323441edc4678f1a
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44775116"
---
# <a name="yammer-enterprise-access-controls"></a><span data-ttu-id="95b5a-103">Yammer エンタープライズアクセスコントロール</span><span class="sxs-lookup"><span data-stu-id="95b5a-103">Yammer enterprise access controls</span></span> 

<span data-ttu-id="95b5a-104">Yammer の運用環境への物理的および論理的なアクセスは、少数のユーザー (インフラストラクチャおよび運用) に制限されます。</span><span class="sxs-lookup"><span data-stu-id="95b5a-104">Physical and logical access to the Yammer production environment is restricted to a small set of people (infrastructure and operations).</span></span> <span data-ttu-id="95b5a-105">他の Microsoft 365 エンジニアと同様に、Yammer のエンジニアは顧客データへのアクセスをゼロにします。</span><span class="sxs-lookup"><span data-stu-id="95b5a-105">As with other Microsoft 365 engineers, Yammer engineers have zero standing access to customer data.</span></span> <span data-ttu-id="95b5a-106">承認者の数が限られているロックボックスに似た、承認ベースのジャストインタイムのアクセス制御システムを使用して、アクセスを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95b5a-106">Access must be requested using an approval-based just-in-time access control system similar to Lockbox with a limited number of approvers.</span></span> <span data-ttu-id="95b5a-107">承認者は、要求を確認します (たとえば、要求が正当であるかどうか、ビジネスケース、時間などに基づいて確認し、要求を承認または拒否するなど)。</span><span class="sxs-lookup"><span data-stu-id="95b5a-107">Approvers verify the request (for example, they verify whether the request is legitimate based on need, business case, time, etc.), and then approve or deny the request.</span></span> <span data-ttu-id="95b5a-108">要求が承認された場合、JIT アクセスは定義済みの時間に限定されて付与されます。</span><span class="sxs-lookup"><span data-stu-id="95b5a-108">If the request is approved, JIT access is granted for a defined and limited time.</span></span> <span data-ttu-id="95b5a-109">アクセス時間が超過すると、アクセスは自動的に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="95b5a-109">After access time is exceeded, the access automatically expires.</span></span>

<span data-ttu-id="95b5a-110">他の Microsoft 365 サービスと同様に、Yammer 運用環境へのすべてのアクセスでは多要素認証が使用されます。</span><span class="sxs-lookup"><span data-stu-id="95b5a-110">As with other Microsoft 365 services, all access to the Yammer production environment uses multi-factor authentication.</span></span> <span data-ttu-id="95b5a-111">すべてのアクセスおよびコマンド履歴はユーザーに帰属し、Yammer セキュリティチームによって定期的にログおよび確認されます。</span><span class="sxs-lookup"><span data-stu-id="95b5a-111">All access and command history is attributed to a user, and logged and reviewed regularly by the Yammer security team.</span></span>

<span data-ttu-id="95b5a-112">Yammer の管理と管理の詳細については、「 [yammer 管理者のヘルプ](https://docs.microsoft.com/yammer/yammer-landing-page)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95b5a-112">For more information about Yammer administration and management, see [Yammer admin help](https://docs.microsoft.com/yammer/yammer-landing-page).</span></span>