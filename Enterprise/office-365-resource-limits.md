---
title: Office 365 リソースの制限
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
f1.keywords:
- NOCSH
description: '概要: Office 365 内のさまざまなアプリケーションのリソース制限についての情報。'
ms.openlocfilehash: 55fa8d90c6f83c84a1e43f32cf7cd0eeafbf1274
ms.sourcegitcommit: ed4482ad35274b79d44d0f9a17be3e52d5ad0492
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "43666328"
---
# <a name="resource-limits"></a><span data-ttu-id="943e7-103">リソースの制限</span><span class="sxs-lookup"><span data-stu-id="943e7-103">Resource Limits</span></span>

<span data-ttu-id="943e7-104">リソースの制限は、クォータ (制限) と調整を使用して適用されます。</span><span class="sxs-lookup"><span data-stu-id="943e7-104">Resource limits are enforced using quotas (limits) and throttling.</span></span> <span data-ttu-id="943e7-105">Azure Active Directory と個別の Office 365 サービスは両方を使用します。</span><span class="sxs-lookup"><span data-stu-id="943e7-105">Azure Active Directory and the individual Office 365 services use both.</span></span> <span data-ttu-id="943e7-106">新しい機能が追加されると、制限はサービスに依存し、時間の経過と共に変化します。</span><span class="sxs-lookup"><span data-stu-id="943e7-106">Limits are service-specific and change over time as new capabilities are added.</span></span> <span data-ttu-id="943e7-107">さまざまなサービスの現在の制限の詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="943e7-107">For details on the current limits for the various services, see the following topics:</span></span>

- [<span data-ttu-id="943e7-108">Azure Active Directory サービスの制限と制限事項</span><span class="sxs-lookup"><span data-stu-id="943e7-108">Azure Active Directory service limits and restrictions</span></span>](https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits)
- [<span data-ttu-id="943e7-109">Exchange Online の制限</span><span class="sxs-lookup"><span data-stu-id="943e7-109">Exchange Online Limits</span></span>](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [<span data-ttu-id="943e7-110">Exchange Online Protection の制限</span><span class="sxs-lookup"><span data-stu-id="943e7-110">Exchange Online Protection Limits</span></span>](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [<span data-ttu-id="943e7-111">SharePoint Online ソフトウェアの境界と制限</span><span class="sxs-lookup"><span data-stu-id="943e7-111">SharePoint Online software boundaries and limits</span></span>](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [<span data-ttu-id="943e7-112">Skype for Business の制限</span><span class="sxs-lookup"><span data-stu-id="943e7-112">Skype for Business Limits</span></span>](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [<span data-ttu-id="943e7-113">Yammer REST API とレート制限</span><span class="sxs-lookup"><span data-stu-id="943e7-113">Yammer REST API and Rate Limits</span></span>](https://developer.yammer.com/docs/rest-api-rate-limits)
- [<span data-ttu-id="943e7-114">Sway でのファイルサイズの制限</span><span class="sxs-lookup"><span data-stu-id="943e7-114">File Size Limits in Sway</span></span>](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

<span data-ttu-id="943e7-115">これらの制限に加えて、Azure Active Directory と Office 365 の間では、いくつかの調整メカニズムが使用されています。</span><span class="sxs-lookup"><span data-stu-id="943e7-115">In addition to these limits, several throttling mechanisms are used throughout Azure Active Directory and Office 365.</span></span> <span data-ttu-id="943e7-116">Microsoft のデータセンター内のネットワークリソースが、サービスを使用する幅広い顧客向けに最適化されているため、サービス内の調整は特に重要です。</span><span class="sxs-lookup"><span data-stu-id="943e7-116">Throttling within the service is especially important, given that network resources in Microsoft's datacenters are optimized for the broad set of customers that use the services.</span></span> <span data-ttu-id="943e7-117">調整メカニズムは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="943e7-117">Throttling mechanisms include:</span></span>

- <span data-ttu-id="943e7-118">Azure Active Directory と Office 365 のユーザーレベルの調整。単一のユーザーが実行できるトランザクションまたは同時呼び出し (スクリプトまたはコード) の数を制限します。</span><span class="sxs-lookup"><span data-stu-id="943e7-118">Azure Active Directory and Office 365 feature user-level throttling, which limit the number of transactions or concurrent calls (by script or code) that can be performed by a single user.</span></span>
- <span data-ttu-id="943e7-119">テナントの作成時に、各テナントに既定の PowerShell 調整ポリシーが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="943e7-119">A default PowerShell throttling policy is assigned to each tenant at tenant creation.</span></span> <span data-ttu-id="943e7-120">これらの設定は、1人の管理者が開くことのできる同時 PowerShell セッションの最大数など、他のアイテムに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="943e7-120">These settings affect other items, such as the maximum number of simultaneous PowerShell sessions that can be opened by a single administrator.</span></span>
- <span data-ttu-id="943e7-121">各 Exchange Online の顧客には、EWS クライアントの操作用に調整された既定の Exchange Web サービス (EWS) ポリシーと、すべての Outlook クライアントに適用される調整があります。</span><span class="sxs-lookup"><span data-stu-id="943e7-121">Each Exchange Online customer has a default Exchange Web Services (EWS) policy that is tuned for EWS client operations, and throttling that applies to all Outlook clients.</span></span>
