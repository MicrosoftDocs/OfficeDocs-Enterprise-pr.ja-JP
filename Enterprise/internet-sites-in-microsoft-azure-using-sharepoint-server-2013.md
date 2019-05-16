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
ms.openlocfilehash: ae05cc38999c3838b030809673c1c30bc1d44c54
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067283"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="65dd2-104">SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="65dd2-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="65dd2-p102">**概要:** SharePoint Server 2013 を使用したインターネット サイトを Azure インフラストラクチャ サービスでホストすることにはメリットがあります。この記事では、このソリューションを設計し、実装するためのリソースを提供します。</span><span class="sxs-lookup"><span data-stu-id="65dd2-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="65dd2-107">インターネット サイト向けの Azure インフラストラクチャ サービスの使用</span><span class="sxs-lookup"><span data-stu-id="65dd2-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="65dd2-p103">Microsoft Azure は SharePoint Server 2013 に基づくインターネット サイトをホストするための強力なオプションを提供します。その利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="65dd2-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="65dd2-110">インフラストラクチャの構築ではなく、魅力的なサイトの開発に重点を置きます。</span><span class="sxs-lookup"><span data-stu-id="65dd2-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="65dd2-111">スケール アウトとスケール インにより、需要に基づきソリューション規模を柔軟に決めることができます。</span><span class="sxs-lookup"><span data-stu-id="65dd2-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="65dd2-112">必要で実際に使用するリソースだけに課金されます。</span><span class="sxs-lookup"><span data-stu-id="65dd2-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="65dd2-113">顧客アカウントに Azure Active Directory を利用できます。</span><span class="sxs-lookup"><span data-stu-id="65dd2-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="65dd2-114">詳細なレポートや分析など、Office 365 では現在利用できない機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="65dd2-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="65dd2-115">リソース</span><span class="sxs-lookup"><span data-stu-id="65dd2-115">Resources</span></span>

<span data-ttu-id="65dd2-116">次の技術説明図および記事は、SharePoint Server 2013 を使用して Azure でインターネット サイトを設計し、実装する方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="65dd2-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="65dd2-117">**Resource**</span><span class="sxs-lookup"><span data-stu-id="65dd2-117">**Resource**</span></span>|<span data-ttu-id="65dd2-118">**詳細情報**</span><span class="sxs-lookup"><span data-stu-id="65dd2-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="65dd2-119">**Azure での SharePoint Server 2013 のインターネット サイト**</span><span class="sxs-lookup"><span data-stu-id="65dd2-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="65dd2-120">[![SharePoint を使用した Azure のインターネット サイトのイメージ](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="65dd2-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="65dd2-121">[](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| PDF [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="65dd2-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="65dd2-122">このアーキテクチャ モデルは、Azure のインターネット サイトの主要な設計活動および推奨されるアーキテクチャの選択肢の概要を説明しています。</span><span class="sxs-lookup"><span data-stu-id="65dd2-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="65dd2-123">\*\*設計サンプル: SharePoint Server 2013 用の Azure のインターネット サイト \*\*</span><span class="sxs-lookup"><span data-stu-id="65dd2-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="65dd2-124">[![デザイン サンプルの図:SharePoint 2013 用の Microsoft Azure のインターネット サイト](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="65dd2-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="65dd2-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549) \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="65dd2-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="65dd2-126">独自のアーキテクチャの開始点としてこの設計サンプルをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="65dd2-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="65dd2-127">**[SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="65dd2-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="65dd2-128">この記事は、SharePoint ソリューションをホストするための Azure アーキテクチャの設計方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="65dd2-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

   
<span data-ttu-id="65dd2-129">**ディスカッションへの参加**</span><span class="sxs-lookup"><span data-stu-id="65dd2-129">**Join the discussion**</span></span>

|<span data-ttu-id="65dd2-130">**お問い合わせ**</span><span class="sxs-lookup"><span data-stu-id="65dd2-130">**Contact us**</span></span>|<span data-ttu-id="65dd2-131">**説明**</span><span class="sxs-lookup"><span data-stu-id="65dd2-131">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="65dd2-132">**必要なソリューション**</span><span class="sxs-lookup"><span data-stu-id="65dd2-132">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="65dd2-p104">複数の Microsoft クラウド プラットフォームおよびサービスにまたがるクラウド導入のコンテンツを作成しています。クラウド導入のコンテンツについてのご意見や特定のコンテンツの依頼を、電子メールで [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 宛にお寄せください。</span><span class="sxs-lookup"><span data-stu-id="65dd2-p104">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="65dd2-135">**クラウド導入のディスカッションへの参加**</span><span class="sxs-lookup"><span data-stu-id="65dd2-135">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="65dd2-p105">クラウドベースのソリューションに関して強い関心がある場合は、Cloud Adoption Advisory Board (CAAB) に参加して、Microsoft コンテンツ開発者、業界プロフェッショナル、および世界中のお客様の大規模で活発なコミュニティとつながることを検討してください。参加するには、Microsoft Tech Community の [CAAB (Cloud Adoption Advisory Board) スペース](https://aka.ms/caab)スペースのメンバーに加わり、[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!) 宛に電子メールを送信してください。[CAAB ブログ](https://blogs.technet.com/b/solutions_advisory_board/)でコミュニティ関連のコンテンツをだれでも読むことができますが、CAAB のメンバーになると、新しいクラウド導入のリソースやソリューションについての非公開 Web セミナーへの招待が送られます。</span><span class="sxs-lookup"><span data-stu-id="65dd2-p105">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="65dd2-140">**掲載されているアートの取得方法**</span><span class="sxs-lookup"><span data-stu-id="65dd2-140">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="65dd2-p106">この記事に掲載されているアートの編集可能なコピーが必要な場合は、喜んでお送りします。アートの URL とタイトルを記載したリクエストを電子メールで、[cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20) 宛にお送りください。</span><span class="sxs-lookup"><span data-stu-id="65dd2-p106">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="65dd2-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="65dd2-143">See Also</span></span>

[<span data-ttu-id="65dd2-144">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="65dd2-144">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



