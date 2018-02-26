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
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: "概要: SharePoint Server 2013 を使用したインターネット サイトを Azure インフラストラクチャ サービスでホストすることにはメリットがあります。この記事では、このソリューションを設計し、実装するためのリソースを提供します。"
ms.openlocfilehash: 52af2dfe250007156848d1892fbee6bca89ab708
ms.sourcegitcommit: 38001ca323a60126fcf31667393c31322044cedc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト

 **概要:** SharePoint Server 2013 を使用したインターネット サイトを Azure インフラストラクチャ サービスでホストすることにはメリットがあります。この記事では、このソリューションを設計し、実装するためのリソースを提供します。
  
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
|**設計サンプル: SharePoint Server 2013 用の Azure のインターネット サイト ** <br/> [![デザイン サンプルの図:SharePoint 2013 用の Microsoft Azure のインターネット サイト](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| ![Visio ファイル](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548) <br/> |独自のアーキテクチャの開始点としてこの設計サンプルをご利用ください。  <br/> |
|**[SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md)** <br/> |この記事は、SharePoint ソリューションをホストするための Azure アーキテクチャの設計方法について説明しています。  <br/> |

   
**ディスカッションへの参加**

|**お問い合わせ**|**説明**|
|:-----|:-----|
|**必要なソリューション** <br/> |複数の Microsoft クラウド プラットフォームおよびサービスにまたがるクラウド導入のコンテンツを作成しています。クラウド導入のコンテンツについてのご意見や特定のコンテンツの依頼を、電子メールで [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 宛にお寄せください。<br/> |
|**クラウド導入のディスカッションへの参加** <br/> |クラウドベースのソリューションに関して強い関心がある場合は、Cloud Adoption Advisory Board (CAAB) に参加して、Microsoft コンテンツ開発者、業界プロフェッショナル、および世界中のお客様の大規模で活発なコミュニティとつながることを検討してください。参加するには、Microsoft Tech Community の [CAAB (Cloud Adoption Advisory Board) スペース](https://aka.ms/caab)スペースのメンバーに加わり、[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!) 宛に電子メールを送信してください。[CAAB ブログ](https://blogs.technet.com/b/solutions_advisory_board/)でコミュニティ関連のコンテンツをだれでも読むことができますが、CAAB のメンバーになると、新しいクラウド導入のリソースやソリューションについての非公開 Web セミナーへの招待が送られます。<br/> |
|**掲載されているアートの取得方法** <br/> |この記事に掲載されているアートの編集可能なコピーが必要な場合は、喜んでお送りします。アートの URL とタイトルを記載したリクエストを電子メールで、[cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20) 宛にお送りください。<br/> |
   
## <a name="see-also"></a>関連項目

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)



