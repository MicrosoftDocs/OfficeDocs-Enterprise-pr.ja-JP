---
title: Office 365 Yammer エンタープライズアクセスコントロール
ms.author: robmazz
author: robmazz
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
description: '概要: 運用環境での Yammer エンタープライズアクセス制御についての簡単な概要。'
ms.openlocfilehash: 19910ec0771b3034e7a290190ae7045ffc8651cf
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067602"
---
# <a name="yammer-enterprise-access-controls"></a><span data-ttu-id="42b5d-103">Yammer Enterprise でのアクセス制御</span><span class="sxs-lookup"><span data-stu-id="42b5d-103">Yammer Enterprise Access Controls</span></span> 

<span data-ttu-id="42b5d-104">Yammer の運用環境への物理的および論理的なアクセスは、少数のユーザー (インフラストラクチャおよび運用) に制限されます。</span><span class="sxs-lookup"><span data-stu-id="42b5d-104">Physical and logical access to the Yammer production environment is restricted to a small set of people (infrastructure and operations).</span></span> <span data-ttu-id="42b5d-105">他の Office 365 エンジニアと同様に、Yammer のエンジニアは顧客データへのアクセスをゼロにします。</span><span class="sxs-lookup"><span data-stu-id="42b5d-105">As with other Office 365 engineers, Yammer engineers have zero standing access to Customer Data.</span></span> <span data-ttu-id="42b5d-106">承認者の数が限られているロックボックスに似た、承認ベースのジャストインタイムのアクセス制御システムを使用して、アクセスを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42b5d-106">Access must be requested using an approval-based just-in-time access control system similar to Lockbox with a limited number of approvers.</span></span> <span data-ttu-id="42b5d-107">承認者は、要求を確認します (たとえば、要求が正当であるかどうか、ビジネスケース、時間などに基づいて確認し、要求を承認または拒否するなど)。</span><span class="sxs-lookup"><span data-stu-id="42b5d-107">Approvers verify the request (for example, they verify whether the request is legitimate based on need, business case, time, etc.), and then approve or deny the request.</span></span> <span data-ttu-id="42b5d-108">要求が承認された場合、JIT アクセスは定義済みの時間に限定されて付与されます。</span><span class="sxs-lookup"><span data-stu-id="42b5d-108">If the request is approved, JIT access is granted for a defined and limited time.</span></span> <span data-ttu-id="42b5d-109">アクセス時間が超過すると、アクセスは自動的に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="42b5d-109">After access time is exceeded, the access automatically expires.</span></span>

<span data-ttu-id="42b5d-110">他の Office 365 サービスと同様に、Yammer 運用環境へのすべてのアクセスでは多要素認証が使用されます。</span><span class="sxs-lookup"><span data-stu-id="42b5d-110">As with other Office 365 services, all access to the Yammer production environment uses multi-factor authentication.</span></span> <span data-ttu-id="42b5d-111">すべてのアクセスおよびコマンド履歴はユーザーに帰属し、Yammer セキュリティチームによって定期的にログおよび確認されます。</span><span class="sxs-lookup"><span data-stu-id="42b5d-111">All access and command history is attributed to a user, and logged and reviewed regularly by the Yammer security team.</span></span>

<span data-ttu-id="42b5d-112">Yammer の管理と管理の詳細については、「 [yammer 管理者のヘルプ](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42b5d-112">For more information about Yammer administration and management, see [Yammer Admin Help](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US).</span></span>