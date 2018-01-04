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
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト

 **概要:** Azure インフラストラクチャ サービス でホストされるインターネット サイトを SharePoint Server 2013 でホストすることにはメリットがあります。この記事では、このソリューションを設計し、実装するためのリソースを提供します。
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a>インターネット サイト向けの Azure インフラストラクチャ サービスの使用

Microsoft Azure は SharePoint Server 2013 に基づくインターネット サイトをホストするための強力なオプションを提供します。その利点は次のとおりです。
  
- インフラストラクチャの構築ではなく、魅力的なサイトの開発に重点を置きます。
    
- スケール アウトとスケール インにより、需要に基づきソリューション規模を柔軟に決めることができます。
    
- 必要で実際に使用するリソースだけに課金されます。
    
- 顧客アカウントに Azure Active Directory を利用できます。
    
- 詳細なレポートや分析など、Office 365 では現在利用できない機能を追加できます。
    
## <a name="resources"></a>リソース

次の技術説明図および記事は、SharePoint Server 2013 を使用して Azure でインターネット サイトを設計し、実装する方法に関する情報を提供します。
  
|**Resource**|**詳細情報**|
|:-----|:-----|
|**Azure での SharePoint Server 2013 のインターネット サイト** <br/> [![SharePoint を使用した Azure のインターネット サイトのイメージ](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [![Visio ファイル](images/ITPro_Other_VisioIcon.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551) <br/> |このアーキテクチャ モデルは、Azure のインターネット サイトの主要な設計活動および推奨されるアーキテクチャの選択肢の概要を説明しています。  <br/> |
|**設計サンプル: SharePoint Server 2013 用の Azure のインターネット サイト** <br/> [![設計サンプルのイメージ: Microsoft Azure for SharePoint 2013 のインターネット サイト](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| ![Visio ファイル](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548) <br/> |独自のアーキテクチャの開始点としてこの設計サンプルをご利用ください。  <br/> |
|**[SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md)** <br/> |この記事は、SharePoint ソリューションをホストするための Azure アーキテクチャの設計方法について説明しています。  <br/> |
|**[SharePoint 2013 認証に Microsoft Azure Active Directory を使用する](using-microsoft-azure-active-directory-for-sharepoint-2013-authentication.md)** <br/> |SharePoint 2013 ファームで Azure AD を構成するための詳細な手順を説明しています。  <br/> |
   
**ディスカッションへの参加**

|**お問い合わせ**|**説明**|
|:-----|:-----|
|**必要なソリューション** <br/> |複数の Microsoft 製品やサービスにまたがるソリューションに関するコンテンツを作成しています。[MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) に電子メールを送信して、サーバー間のソリューションに関するご意見や、特定のソリューションに関するご質問をお寄せください。<br/> |
|**ソリューションのディスカッションへの参加** <br/> |クラウドベースのソリューションに関して強い関心がある場合は、Cloud Adoption Advisory Board (CAAB) に参加して、大規模で活発な Microsoft コンテンツ開発者、業界プロフェッショナル、および世界中のお客様の大規模で活発なコミュニティとつながることを検討してください。参加するには、Microsoft Tech Community の [CAAB (Cloud Adoption Advisory Board) スペース]((https://aka.ms/caab))のメンバーとしてご自分を追加し、[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!) 宛に電子メールを送信してください。[CAAB ブログ]((https://blogs.technet.com/b/solutions_advisory_board/))でコミュニティ関連のコンテンツをだれでも読むことができます。ただし、CAAB のメンバーになると、新しいクラウド導入のリソースやソリューションについての非公開 Web セミナーへの招待が送られます。<br/> |
|**記載されているアートの取得方法** <br/> |この記事にあるアートの編集可能なコピーが必要な方には、喜んでお送りします。アートの URL とタイトルを記述した電子メールを [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20) に送信してください。<br/> |
   
## <a name="see-also"></a>関連項目

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)



