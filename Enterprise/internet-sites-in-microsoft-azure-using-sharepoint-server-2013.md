---
title: "SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト"
ms.author: bcarter
author: bcarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: "概要: Azure インフラストラクチャ サービス でホストされるインターネット サイトを SharePoint Server 2013 でホストすることにはメリットがあります。この記事では、このソリューションを設計し、実装するためのリソースを提供します。"
ms.openlocfilehash: d302410580a03265d7ba20b9b372896c87d397bf
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="20750-104">SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="20750-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="20750-p102">**概要:** Azure インフラストラクチャ サービス でホストされるインターネット サイトを SharePoint Server 2013 でホストすることにはメリットがあります。この記事では、このソリューションを設計し、実装するためのリソースを提供します。</span><span class="sxs-lookup"><span data-stu-id="20750-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="20750-107">インターネット サイト向けの Azure インフラストラクチャ サービスの使用</span><span class="sxs-lookup"><span data-stu-id="20750-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="20750-p103">Microsoft Azure は SharePoint Server 2013 に基づくインターネット サイトをホストするための強力なオプションを提供します。その利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="20750-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="20750-110">インフラストラクチャの構築ではなく、魅力的なサイトの開発に重点を置きます。</span><span class="sxs-lookup"><span data-stu-id="20750-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="20750-111">スケール アウトとスケール インにより、需要に基づきソリューション規模を柔軟に決めることができます。</span><span class="sxs-lookup"><span data-stu-id="20750-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="20750-112">必要で実際に使用するリソースだけに課金されます。</span><span class="sxs-lookup"><span data-stu-id="20750-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="20750-113">顧客アカウントに Azure Active Directory を利用できます。</span><span class="sxs-lookup"><span data-stu-id="20750-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="20750-114">詳細なレポートや分析など、Office 365 では現在利用できない機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="20750-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="20750-115">リソース</span><span class="sxs-lookup"><span data-stu-id="20750-115">Resources</span></span>

<span data-ttu-id="20750-116">次の技術説明図および記事は、SharePoint Server 2013 を使用して Azure でインターネット サイトを設計し、実装する方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="20750-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="20750-117">**リソース**</span><span class="sxs-lookup"><span data-stu-id="20750-117">**Resource**</span></span>|<span data-ttu-id="20750-118">**詳細情報**</span><span class="sxs-lookup"><span data-stu-id="20750-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="20750-119">**Azure での SharePoint Server 2013 のインターネット サイト**</span><span class="sxs-lookup"><span data-stu-id="20750-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="20750-120">[![SharePoint を使用した Azure のインターネット サイトのイメージ](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="20750-120">[![Image of Internet sites in Azure using SharePoint](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="20750-121">![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="20750-121">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> |<span data-ttu-id="20750-122">[![Visio ファイル](images/ITPro_Other_VisioIcon.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span><span class="sxs-lookup"><span data-stu-id="20750-122">[![Visio file](images/ITPro_Other_VisioIcon.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="20750-123">このアーキテクチャ モデルは、Azure のインターネット サイトの主要な設計活動および推奨されるアーキテクチャの選択肢の概要を説明しています。</span><span class="sxs-lookup"><span data-stu-id="20750-123">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="20750-124">**設計サンプル: SharePoint Server 2013 用の Azure のインターネット サイト**</span><span class="sxs-lookup"><span data-stu-id="20750-124">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="20750-125">[![設計サンプルのイメージ: Microsoft Azure for SharePoint 2013 のインターネット サイト](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="20750-125">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="20750-126">![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="20750-126">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> |<span data-ttu-id="20750-127">![Visio ファイル](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="20750-127">![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="20750-128">独自のアーキテクチャの開始点としてこの設計サンプルをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="20750-128">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="20750-129">**[SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="20750-129">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="20750-130">この記事は、SharePoint ソリューションをホストするための Azure アーキテクチャの設計方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="20750-130">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |
|<span data-ttu-id="20750-131">**[SharePoint 2013 認証に Microsoft Azure Active Directory を使用する](using-microsoft-azure-active-directory-for-sharepoint-2013-authentication.md)**</span><span class="sxs-lookup"><span data-stu-id="20750-131">**[Using Microsoft Azure Active Directory for SharePoint 2013 authentication](using-microsoft-azure-active-directory-for-sharepoint-2013-authentication.md)**</span></span> <br/> |<span data-ttu-id="20750-132">SharePoint 2013 ファームで Azure AD を構成するための詳細な手順を説明しています。</span><span class="sxs-lookup"><span data-stu-id="20750-132">Step-by-step instructions for configuring Azure AD with a SharePoint 2013 farm.</span></span>  <br/> |
   
<span data-ttu-id="20750-133">**ディスカッションへの参加**</span><span class="sxs-lookup"><span data-stu-id="20750-133">**Join the discussion**</span></span>

|<span data-ttu-id="20750-134">**お問い合わせ**</span><span class="sxs-lookup"><span data-stu-id="20750-134">**Contact us**</span></span>|<span data-ttu-id="20750-135">**説明**</span><span class="sxs-lookup"><span data-stu-id="20750-135">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="20750-136">**必要なソリューション**</span><span class="sxs-lookup"><span data-stu-id="20750-136">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="20750-p104">複数の Microsoft 製品やサービスにまたがるソリューションに関するコンテンツを作成しています。[MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) に電子メールを送信して、サーバー間のソリューションに関するご意見や、特定のソリューションに関するご質問をお寄せください。</span><span class="sxs-lookup"><span data-stu-id="20750-p104">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="20750-139">**ソリューションのディスカッションへの参加**</span><span class="sxs-lookup"><span data-stu-id="20750-139">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="20750-p105">クラウド ・ ベースのソリューションに熱心である場合、クラウド採用アドバイザリー ボード (CAAB) Microsoft コンテンツ開発者、業界の専門家、および世界中のお客様より大規模で活気のあるコミュニティに接続するために参加を検討してください。参加するには、マイクロソフトのテクニカル コミュニティの[CAAB (クラウド導入の諮問委員会) の空き領域](https://aka.ms/caab)のメンバーとして自分自身を追加し、[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)でのクイック メールを送信します。[CAAB のブログ](https://blogs.technet.com/b/solutions_advisory_board/)上のコミュニティに関連するコンテンツをだれでも読み取ることができます。ただし、CAAB のメンバーは、新しいクラウド導入リソースとソリューションについて説明するプライベートのウェビナーへの招待を取得します。</span><span class="sxs-lookup"><span data-stu-id="20750-p105">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="20750-143">**記載されているアートの取得方法**</span><span class="sxs-lookup"><span data-stu-id="20750-143">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="20750-p106">参照してくださいアートの編集可能なコピーを実行する場合に、私たちに送信するようになります。[Cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)に、アートのタイトルと URL を含む、要求を電子メールで送信します。</span><span class="sxs-lookup"><span data-stu-id="20750-p106">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="20750-146">See Also</span><span class="sxs-lookup"><span data-stu-id="20750-146">See Also</span></span>

[<span data-ttu-id="20750-147">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="20750-147">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



