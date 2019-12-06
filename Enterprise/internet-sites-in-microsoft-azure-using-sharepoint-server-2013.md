---
title: SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: '概要: SharePoint Server 2013 を使用したインターネット サイトを Azure インフラストラクチャ サービスでホストすることにはメリットがあります。この記事では、このソリューションを設計し、実装するためのリソースを提供します。'
ms.openlocfilehash: 762b09d9d4812056b445160d9519802ae56396f4
ms.sourcegitcommit: d4c1ed4e4970683851d63ca980dcc5d1dd73fa78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "39858000"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="5ffe8-104">SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="5ffe8-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="5ffe8-p102">**概要:** SharePoint Server 2013 を使用したインターネット サイトを Azure インフラストラクチャ サービスでホストすることにはメリットがあります。この記事では、このソリューションを設計し、実装するためのリソースを提供します。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="5ffe8-107">インターネット サイト向けの Azure インフラストラクチャ サービスの使用</span><span class="sxs-lookup"><span data-stu-id="5ffe8-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="5ffe8-p103">Microsoft Azure は SharePoint Server 2013 に基づくインターネット サイトをホストするための強力なオプションを提供します。その利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="5ffe8-110">インフラストラクチャの構築ではなく、魅力的なサイトの開発に重点を置きます。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="5ffe8-111">スケール アウトとスケール インにより、需要に基づきソリューション規模を柔軟に決めることができます。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="5ffe8-112">必要で実際に使用するリソースだけに課金されます。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="5ffe8-113">顧客アカウントに Azure Active Directory を利用できます。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="5ffe8-114">詳細なレポートや分析など、Office 365 では現在利用できない機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="5ffe8-115">リソース</span><span class="sxs-lookup"><span data-stu-id="5ffe8-115">Resources</span></span>

<span data-ttu-id="5ffe8-116">次の技術説明図および記事は、SharePoint Server 2013 を使用して Azure でインターネット サイトを設計し、実装する方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="5ffe8-117">**Resource**</span><span class="sxs-lookup"><span data-stu-id="5ffe8-117">**Resource**</span></span>|<span data-ttu-id="5ffe8-118">**詳細情報**</span><span class="sxs-lookup"><span data-stu-id="5ffe8-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5ffe8-119">**Azure での SharePoint Server 2013 のインターネット サイト**</span><span class="sxs-lookup"><span data-stu-id="5ffe8-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="5ffe8-120">[![SharePoint を使用した Azure のインターネット サイトのイメージ](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="5ffe8-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="5ffe8-121">[](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| PDF [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="5ffe8-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="5ffe8-122">このアーキテクチャ モデルは、Azure のインターネット サイトの主要な設計活動および推奨されるアーキテクチャの選択肢の概要を説明しています。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="5ffe8-123">\*\*設計サンプル: SharePoint Server 2013 用の Azure のインターネット サイト \*\*</span><span class="sxs-lookup"><span data-stu-id="5ffe8-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="5ffe8-124">[![デザイン サンプルの図:SharePoint 2013 用の Microsoft Azure のインターネット サイト](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="5ffe8-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="5ffe8-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="5ffe8-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="5ffe8-126">独自のアーキテクチャの開始点としてこの設計サンプルをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="5ffe8-127">**[SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="5ffe8-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="5ffe8-128">この記事は、SharePoint ソリューションをホストするための Azure アーキテクチャの設計方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="5ffe8-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

## <a name="see-also"></a><span data-ttu-id="5ffe8-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ffe8-129">See Also</span></span>

[<span data-ttu-id="5ffe8-130">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="5ffe8-130">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



