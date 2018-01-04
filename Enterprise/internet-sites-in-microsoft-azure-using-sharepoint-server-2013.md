---
title: "SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト"
ms.author: bcarter
author: brendacarter
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
ms.openlocfilehash: beea61b037a55f0de49869c5d6f206979a9a578f
ms.sourcegitcommit: 4a347cfb16405d5213b28f332d80e244fca0fb8f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2017
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="70cca-104">SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="70cca-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="70cca-p102">**概要:** Azure インフラストラクチャ サービス でホストされるインターネット サイトを SharePoint Server 2013 でホストすることにはメリットがあります。この記事では、このソリューションを設計し、実装するためのリソースを提供します。</span><span class="sxs-lookup"><span data-stu-id="70cca-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="70cca-107">インターネット サイト向けの Azure インフラストラクチャ サービスの使用</span><span class="sxs-lookup"><span data-stu-id="70cca-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="70cca-p103">Microsoft Azure は SharePoint Server 2013 に基づくインターネット サイトをホストするための強力なオプションを提供します。その利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="70cca-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="70cca-110">インフラストラクチャの構築ではなく、魅力的なサイトの開発に重点を置きます。</span><span class="sxs-lookup"><span data-stu-id="70cca-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="70cca-111">スケール アウトとスケール インにより、需要に基づきソリューション規模を柔軟に決めることができます。</span><span class="sxs-lookup"><span data-stu-id="70cca-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="70cca-112">必要で実際に使用するリソースだけに課金されます。</span><span class="sxs-lookup"><span data-stu-id="70cca-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="70cca-113">顧客アカウントに Azure Active Directory を利用できます。</span><span class="sxs-lookup"><span data-stu-id="70cca-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="70cca-114">詳細なレポートや分析など、Office 365 では現在利用できない機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="70cca-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="70cca-115">リソース</span><span class="sxs-lookup"><span data-stu-id="70cca-115">Resources</span></span>

<span data-ttu-id="70cca-116">次の技術説明図および記事は、SharePoint Server 2013 を使用して Azure でインターネット サイトを設計し、実装する方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="70cca-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="70cca-117">**Resource**</span><span class="sxs-lookup"><span data-stu-id="70cca-117">**Resource**</span></span>|<span data-ttu-id="70cca-118">**詳細情報**</span><span class="sxs-lookup"><span data-stu-id="70cca-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="70cca-119">**Azure での SharePoint Server 2013 のインターネット サイト**</span><span class="sxs-lookup"><span data-stu-id="70cca-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="70cca-120">[![SharePoint を使用した Azure のインターネット サイトのイメージ](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="70cca-120">[![Image of Internet sites in Azure using SharePoint](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="70cca-121">![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \\</span><span class="sxs-lookup"><span data-stu-id="70cca-121">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span>| <span data-ttu-id="70cca-122">[![Visio ファイル](images/ITPro_Other_VisioIcon.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span><span class="sxs-lookup"><span data-stu-id="70cca-122">[![Visio file](images/ITPro_Other_VisioIcon.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="70cca-123">このアーキテクチャ モデルは、Azure のインターネット サイトの主要な設計活動および推奨されるアーキテクチャの選択肢の概要を説明しています。</span><span class="sxs-lookup"><span data-stu-id="70cca-123">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="70cca-124">**設計サンプル: SharePoint Server 2013 用の Azure のインターネット サイト**</span><span class="sxs-lookup"><span data-stu-id="70cca-124">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="70cca-125">[![設計サンプルのイメージ: Microsoft Azure for SharePoint 2013 のインターネット サイト](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="70cca-125">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="70cca-126">![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \\</span><span class="sxs-lookup"><span data-stu-id="70cca-126">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span>| <span data-ttu-id="70cca-127">![Visio ファイル](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="70cca-127">![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="70cca-128">独自のアーキテクチャの開始点としてこの設計サンプルをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="70cca-128">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="70cca-129">**[SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="70cca-129">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="70cca-130">この記事は、SharePoint ソリューションをホストするための Azure アーキテクチャの設計方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="70cca-130">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |
|<span data-ttu-id="70cca-131">**[SharePoint 2013 認証に Microsoft Azure Active Directory を使用する](using-microsoft-azure-active-directory-for-sharepoint-2013-authentication.md)**</span><span class="sxs-lookup"><span data-stu-id="70cca-131">**[Using Microsoft Azure Active Directory for SharePoint 2013 authentication](using-microsoft-azure-active-directory-for-sharepoint-2013-authentication.md)**</span></span> <br/> |<span data-ttu-id="70cca-132">SharePoint 2013 ファームで Azure AD を構成するための詳細な手順を説明しています。</span><span class="sxs-lookup"><span data-stu-id="70cca-132">Step-by-step instructions for configuring Azure AD with a SharePoint 2013 farm.</span></span>  <br/> |
   
<span data-ttu-id="70cca-133">**ディスカッションへの参加**</span><span class="sxs-lookup"><span data-stu-id="70cca-133">**Join the discussion**</span></span>

|<span data-ttu-id="70cca-134">**お問い合わせ**</span><span class="sxs-lookup"><span data-stu-id="70cca-134">**Contact us**</span></span>|<span data-ttu-id="70cca-135">**説明**</span><span class="sxs-lookup"><span data-stu-id="70cca-135">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="70cca-136">**必要なソリューション**</span><span class="sxs-lookup"><span data-stu-id="70cca-136">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="70cca-p104">複数の Microsoft 製品やサービスにまたがるソリューションに関するコンテンツを作成しています。[MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) に電子メールを送信して、サーバー間のソリューションに関するご意見や、特定のソリューションに関するご質問をお寄せください。</span><span class="sxs-lookup"><span data-stu-id="70cca-p104">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="70cca-139">**ソリューションのディスカッションへの参加**</span><span class="sxs-lookup"><span data-stu-id="70cca-139">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="70cca-p105">クラウドベースのソリューションに関して強い関心がある場合は、Cloud Adoption Advisory Board (CAAB) に参加して、大規模で活発な Microsoft コンテンツ開発者、業界プロフェッショナル、および世界中のお客様の大規模で活発なコミュニティとつながることを検討してください。参加するには、Microsoft Tech Community の [CAAB (Cloud Adoption Advisory Board) スペース]((https://aka.ms/caab))のメンバーとしてご自分を追加し、[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!) 宛に電子メールを送信してください。[CAAB ブログ]((https://blogs.technet.com/b/solutions_advisory_board/))でコミュニティ関連のコンテンツをだれでも読むことができます。ただし、CAAB のメンバーになると、新しいクラウド導入のリソースやソリューションについての非公開 Web セミナーへの招待が送られます。</span><span class="sxs-lookup"><span data-stu-id="70cca-p105">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space]((https://aka.ms/caab)) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog]((https://blogs.technet.com/b/solutions_advisory_board/)). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="70cca-143">**記載されているアートの取得方法**</span><span class="sxs-lookup"><span data-stu-id="70cca-143">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="70cca-p106">この記事にあるアートの編集可能なコピーが必要な方には、喜んでお送りします。アートの URL とタイトルを記述した電子メールを [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20) に送信してください。</span><span class="sxs-lookup"><span data-stu-id="70cca-p106">If you want an editable copy of the art you see in the Solutions using Office Servers and the Cloud content, we’ll be glad to send it to you. Email your request, including the URL and title of the art, to  MODAcontent@microsoft.com mailto:modacontent@microsoft.com?subject=[Art%20Request]:%20 .</span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="70cca-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="70cca-146">See Also</span></span>

[<span data-ttu-id="70cca-147">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="70cca-147">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



