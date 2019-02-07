---
title: Microsoft クラウド IT アーキテクチャのリソース
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 28986107-e2fb-4116-bfdd-f66d751a7c16
search.appverid:
- MET150
description: '概要: Microsoft ID, セキュリティ、ネットワーク、およびハイブリッドにおけるコア クラウド アーキテクチャの概念について説明します。Microsoft のクラウドを使用する場合は、ファイル、ID、およびデバイスを保護するための推奨事項を確認してください。Windows 10 および Office ProPlus で最新のセキュリティで保護されたデスクトップを展開する方法について説明します。'
ms.openlocfilehash: a32b73facd54da98d7c5df84223237d857883cfe
ms.sourcegitcommit: e56f830ccff8d74d9edbff4a46a9ee1d613291ed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2019
ms.locfileid: "29741240"
---
# <a name="microsoft-cloud-it-architecture-resources"></a>Microsoft クラウド IT アーキテクチャのリソース

 **概要:** Microsoft ID, セキュリティ、ネットワーク、およびハイブリッドにおけるコア クラウド アーキテクチャの概念について説明します。Microsoft のクラウドを使用する場合は、ファイル、ID、およびデバイスを保護するための推奨事項を確認してください。Windows 10 および Office ProPlus で最新のセキュリティで保護されたデスクトップを展開する方法について説明します。
  
これらのアーキテクチャ ツールおよびポスターでは、Office 365、Windows 10、Azure Active Directory, Microsoft Intune、Microsoft Dynamics 365、および プライベート クラウドのデータ センター、オンプレミスとクラウドのハイブリッド ソリューションを含む Microsoft クラウド サービスについての情報を提供します。IT 意思決定者と設計者はこれらのリソースを使用して、ワークロードに最適なソリューションを決定し、ID やセキュリティなどのコア インフラストラクチャ コンポーネントについて決定することができます。 
  
<!---**[Microsoft's Enterprise Cloud Roadmap](microsoft-cloud-it-architecture-resources.md#roadmap)** (Sway) --->
    
- **[エンタープライズ アーキテクト シリーズ向けの Microsoft クラウド](microsoft-cloud-it-architecture-resources.md#cloudarch)** <!--- [Microsoft Cloud Services and Platform Options](microsoft-cloud-it-architecture-resources.md#platformoptions) --->
    - [エンタープライズ アーキテクトのための Microsoft クラウド ID](microsoft-cloud-it-architecture-resources.md#identity)
    - [エンタープライズ アーキテクトのための Microsoft クラウドのセキュリティ](microsoft-cloud-it-architecture-resources.md#security)
    - [エンタープライズ アーキテクトのための Microsoft Cloud ネットワーク](microsoft-cloud-it-architecture-resources.md#networking)
    - [エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド](microsoft-cloud-it-architecture-resources.md#hybrid)
    - [一般的な攻撃と、組織を保護する Microsoft の機能](#common-attacks-and-microsoft-capabilities-that-protect-your-organization)
    
- **[Microsoft 365 Enterprise ソリューション シリーズ](microsoft-cloud-it-architecture-resources.md#BKMK_o365solutions)**:
    - [Office 365 の ID とデバイス保護](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    - [Office 365 のファイル保護ソリューション](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    - [GDPR のための Office 365 の情報保護](#office-365-information-protection-for-gdpr)
    - [選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](#microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations)
    - [Microsoft テレフォニー ソリューション](#microsoft-telephony-solutions) 
    - [Microsoft の最新のセキュリティで保護されたデスクトップの展開](microsoft-cloud-it-architecture-resources.md#msd)
    

  
ご意見を電子メールで [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com) 宛てにお送りください。 

<!---
<a name="roadmap"> </a>
## Microsoft's Enterprise Cloud Roadmap

See the posters, icon sets, community venues, and other resources that describe the industry's most complete cloud solution.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumbnail for Enterprise Cloud Roadmap](media/c8b293b9-5992-4d29-b579-a6bbbd59d8d6.png)          ](https://aka.ms/cloudarchitecture) <br/> [Microsoft's Enterprise Cloud Roadmap](https://aka.ms/cloudarchitecture) (https://aka.ms/cloudarchitecture) <br/> |Swipe through this Sway experience for the resources that describe the industry's most complete cloud solution.  <br/> |
--->
  
<a name="cloudarch"> </a>
##エンタープライズ アーキテクト シリーズ向けの Microsoft クラウド

これらのクラウド アーキテクチャ ポスターでは、Office 365、Azure Active Directory、Microsoft Intune、Microsoft Dynamics CRM Online、およびオンプレミスとクラウドのハイブリッド ソリューションを含む Microsoft クラウド サービスについての情報を提供します。IT 意思決定者と設計者はこれらのリソースを使用して、ワークロードに最適なソリューションを決定し、ID やセキュリティなどのコア インフラストラクチャ コンポーネントについて決定することができます。

<!---  
<a name="platformoptions"> </a>
### Microsoft Cloud Services and Platform Options

Learn key differences between Microsoft cloud services and platform offerings. Find the best fit for your solution.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumb image of cloud architecture model with service options](media/ff5c74e2-afc6-40c1-9292-cc4cb128cdd1.png)          ](https://www.microsoft.com/download/details.aspx?id=54432) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=524731)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=524732)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=54432) <br/> | This model describes: <ul><li>  Software as a Service (SaaS) offerings, including Office 365 </li><li>  Platform as a Service (PaaS) features in Microsoft Azure </li><li>  Infrastructure as a Service (IaaS) features in Microsoft Azure </li><li>  Private cloud datacenter capabilities using Windows Server and System Center </li><li>  Learn how Microsoft's own IT department is migrating to these cloud services and building its hybrid cloud. </li></ul><br/>|
--->

   
<a name="identity"> </a>
###エンタープライズ アーキテクトのための Microsoft クラウド ID

Microsoft クラウド サービスおよびプラットフォームを使用して、組織のためのアイデンティティを設計する上で IT アーキテクトが知る必要のある事柄。
  
|**アイテム**|**説明**|
|:-----|:-----|
|[![Microsoft クラウド ID モデルのサムネイル画像](media/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png)          ](https://www.microsoft.com/download/details.aspx?id=54431) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586)  \| [Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd)           \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=54431) <br/> | このモデルには次のものが含まれています。 <ul><li>Microsoft のクラウド ID の概要 </li> <li>Azure AD IDaaS 機能 </li><li>オンプレミスの Active Directory Domain Services アカウントと Microsoft Azure Active Directory を統合する </li> <li>ディレクトリ コンポーネントを Azure に配置する </li><li>Azure IaaS のワークロードのドメイン サービス オプション </li></ul> <br/>|
   
<a name="security"> </a>
### <a name="microsoft-cloud-security-for-enterprise-architects"></a>エンタープライズ アーキテクトのための Microsoft クラウドのセキュリティ

Microsoft クラウド サービスおよびプラットフォームにおけるセキュリティについて IT アーキテクトが知る必要のある事柄。
  
|**アイテム**|**説明**|
|:-----|:-----|
|[![Microsoft クラウドのセキュリティ モデルのサムネイル画像](media/5dc26f80-8888-4572-8ed9-a120d711e0f0.png)          ](https://www.microsoft.com/download/details.aspx?id=48121) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842070)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=842071)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=48121) <br/> | このモデルには次のものが含まれています。 <ul><li>安全なサービスとプラットフォームを提供することにおける Microsoft の役割</li><li>セキュリティ上のリスクを軽減するというお客様側の責任</li><li>最高位のセキュリティ認定 </li><li>Microsoft コンサルティング サービスが提供するセキュリティ サービス </ul> <br/>|
   
<a name="networking"> </a>
### <a name="microsoft-cloud-networking-for-enterprise-architects"></a>エンタープライズ アーキテクトのための Microsoft Cloud ネットワーク

Microsoft クラウド サービスおよびプラットフォームのネットワーキングに関して IT アーキテクトが知る必要のある事柄。
  
|**アイテム**|**説明**|
|:-----|:-----|
|[![Microsoft クラウドのネットワーク モデルのサムネイル画像](media/95e8ab6a-b4d0-4836-acc1-b0b77ebf46e6.png)          ](https://www.microsoft.com/download/details.aspx?id=54425) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842073)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=842074)           \| [記事](https://technet.microsoft.com/library/mt733214.aspx) <br/>[その他の言語](https://www.microsoft.com/download/details.aspx?id=54425) <br/> | このモデルには以下のページが含まれています。 <ul><li> **クラウド接続用のネットワークの進化**: クラウド移行によって、企業ネットワークの内外でのトラフィック フローの容量と特性が変化します。また、セキュリティ リスクを軽減するためのアプローチにも影響します。</li><li> **Microsoft クラウド接続の一般的な要素**: ネットワーキングと Microsoft クラウドの統合によって、広範なサービスへの最適なアクセスが提供されます。 </li><li> **Microsoft クラウド接続用の ExpressRoute** ExpressRoute は、Microsoft のクラウドへのプライベートで専用の高スループットなネットワーク接続を提供します。 </li><li> **Microsoft SaaS (Office 365、Microsoft Intune、および Dynamics CRM Online) 用ネットワーキングの設計**: Microsoft SaaS サービス用のネットワークを最適化するには、インターネット エッジ、クライアント デバイス、および標準の IT 運用を慎重に分析する必要があります。 </li><li> **Azure PaaS 用のネットワーキングの設計**: Azure PaaS アプリ用のネットワーキングを最適化するには、適切なインターネット帯域幅が必要であり、複数のサイトまたはアプリにまたがるネットワーク トラフィックの分散が必要とされる可能性があります。 </li><li> **Azure IaaS のネットワークの設計** サブネット、アドレス空間、ルーティング、DNS、負荷分散や、オンプレミスのネットワーク、その他の VNet、インターネットなどへの接続など、サーバーベースの IT ワークロードをホストするために最適な Azure 仮想ネットワーク (VNet) を作成するには、設計プロセスを実行します。 </li></ul><br/>  このアーキテクチャ ポスターに基づく新しい Microsoft Virtual Academy コースである「[Microsoft クラウド サービスに合わせてネットワークを最適化する](https://aka.ms/optimizecloudnetworkingmva)」を受講してください。  <br/>|
   
   
<a name="hybrid"> </a>
### <a name="microsoft-hybrid-cloud-for-enterprise-architects"></a>エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド

Microsoft のサービスとプラットフォーム用のハイブリッド クラウドに関して IT アーキテクトが知る必要のある事柄。
  
|**アイテム**|**説明**|
|:-----|:-----|
|[![Microsoft ハイブリッド クラウド モデルのサムネイル画像](media/9989c71e-f6a0-4dbe-906c-43e67b3ce537.png)          ](https://www.microsoft.com/download/details.aspx?id=54424) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842082)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=842083)           \| [記事](https://technet.microsoft.com/library/mt750500.aspx) <br/>[その他の言語](https://www.microsoft.com/download/details.aspx?id=54424) <br/> | このモデルには以下のページが含まれています。 <ul><li> **ハイブリッド クラウドの概要** Microsoft のクラウド サービス (SaaS、Azure PaaS、そして Azure IaaS) とそれらの共通の要素。 </li><li> **Microsoft ハイブリッド クラウド シナリオのアーキテクチャ** Microsoft のクラウド製品のハイブリッド クラウドのアーキテクチャ ダイアグラム。オンプレミス インフラストラクチャ、ネットワーク、および ID の共通レイヤーを示します。 </li><li> **Microsoft SaaS (Office 365) のハイブリッド クラウド シナリオ** SaaS ハイブリッド シナリオ アーキテクチャと、Skype for Business、SharePoint Server、そして Exchange Server の主要なハイブリッド構成の説明。 </li><li> **Azure PaaS のハイブリッド クラウド シナリオ** Azure PaaS ハイブリッド シナリオのアーキテクチャ、および Azure PaaS ハイブリッド アプリケーションの説明とその例、および SQL Server 2016 Stretch Database の説明。 </li><li> **Azure IaaS のハイブリッド クラウド シナリオ** Azure IaaS ハイブリッド シナリオのアーキテクチャ、および Azure IaaS でホストされる基幹業務 (LOB) アプリケーションの説明。 </li></ul><br/>|
   
<a name="attacks"> </a>
### <a name="common-attacks-and-microsoft-capabilities-that-protect-your-organization"></a>一般的な攻撃と、組織を保護する Microsoft の機能
最も一般的なサイバー攻撃と、攻撃の各段階で Microsoft が組織を支援する方法について説明します。 

|**アイテム**|**説明**|
|:-----|:-----|
|[![一般的な攻撃ポスターのサムネイル画像。](media/common%20attacks-thumb3.png) ](http://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.pdf) <br/> [PDF](http://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.pdf) \| [Visio](http://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.vsdx) <br/> | このポスターは、一般的な攻撃の経路を示し、攻撃の各段階で攻撃者を阻止する機能について説明します。 <br/>|


<!---<a name="santa"> </a>
### The Santa cloud

How Santa and his elves use Microsoft's cloud offerings to make their annual deliveries.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumbnail image of The Santa Cloud poster](media/d47e1448-329b-41b7-9e51-cfc4ea5d0069.png)](https://www.microsoft.com/download/details.aspx?id=55039) <br/> [View online](https://onedrive.live.com/?authkey=%21ANT1PMgxEdniCyY&cid=8A8EC4F6612625E0&id=8A8EC4F6612625E0%21440&parId=8A8EC4F6612625E0%21218&o=OneUp) \| [PDF](https://go.microsoft.com/fwlink/p/?linkid=842088) <br/> |To determine who is naughty or nice and the presents to deliver on December 24, Santa Claus and his elfish IT department use Office 365, Azure, Dynamics 365, and Intune.  <br/>| --->
   
<a name="BKMK_o365solutions"> </a>
## Microsoft 365 Enterprise ソリューション シリーズ

Microsoft 365 Enterprise ソリューション シリーズには、Microsoft 365 の機能、特にざまざまなプラットフォームで使える機能を実装するためのガイダンスが用意されています。

<!---  
<a name="BKMK_infoprotect"> </a>
### Information Protection for Office 365

Capabilities for enterprise organizations to protect corporate assets.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Information protection capabilities for Office 365](media/51bf70b4-029c-4189-9425-7ed34038d4dc.png)          ](https://www.microsoft.com/download/details.aspx?id=54429) <br/> [PDF](http://download.microsoft.com/download/2/3/D/23D91386-8349-4F7A-9470-FD5AED861F16/MSFT_cloud_architecture_informationprotection.pdf)  \| [Visio](http://download.microsoft.com/download/2/3/D/23D91386-8349-4F7A-9470-FD5AED861F16/MSFT_cloud_architecture_informationprotection.vsd)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=54429) <br/> |Microsoft provides the most complete set of capabilities to protect your corporate assets. This model helps organizations take a methodical approach when planning which capabilities to implement.  <br/>|
--->
   
<a name="BKMK_O365IDP"> </a>
### Office 365 の ID とデバイス保護

Office 365、他の SaaS サービス、および Azure AD アプリケーション プロキシで公開したオンプレミス アプリケーションにアクセスする ID とデバイスを保護するために推奨される機能。
  
|**アイテム**|**説明**|
|:-----|:-----|
|[![モデル ポスター:Office 365 およびその他の SaaS アプリケーションの ID とデバイス保護](media/c1cfb31b-5150-45ff-b46c-3a237e9f5581.png)          ](https://www.microsoft.com/download/details.aspx?id=55032) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=841656)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=55032) <br/> |データ、ID、デバイス全体で一貫したレベルの保護を使用することが重要です。このドキュメントでは、ID とデバイスを保護する機能に関する詳細情報に、どの機能が相当するのかを説明します。  <br/> |
   
<a name="BKMK_O365fileprotect"> </a>
### <a name="file-protection-solutions-in-office-365"></a>Office 365 のファイル保護ソリューション

Office 365 のファイル保護のために推奨される機能は、3 段階の秘密度レベルに基づいています。
  
|**アイテム**|**説明**|
|:-----|:-----|
|[![Office 365 でのファイル保護ソリューションのミニ ポスター セットのサムネイル](media/24be68b5-d852-4fdb-94ad-94491a19edd8.png)          ](https://www.microsoft.com/download/details.aspx?id=55523) <br/> [PDF](https://go.microsoft.com/fwlink/?linkid=2004320)  \| [Visio](http://download.microsoft.com/download/7/8/9/789645A5-BD10-4541-BC33-F8D1EFF5E911/MSFT_cloud_architecture_O365%20file%20protection.vsdx) <br/> |データ、ID、デバイス全体で一貫したレベルの保護を使用することが重要です。このドキュメントでは、Office 365 のファイルを保護する機能に関する詳細情報に、どの機能が相当するのかを説明します。  <br/> |
   

### <a name="office-365-information-protection-for-gdpr"></a>GDPR のための Office 365 の情報保護

個人データの検出、分類、保護、および監視に規定された推奨事項。このソリューションでは、例として一般データ保護規制 (GDPR) を使用しますが、その他の多くの規制遵守のためにも同じ手順を適用することができます。

|**Item**|**説明**|
|:-----|:-----|
|![GDPR のための Office 365 の情報保護のサムネイル](media/o365infoprotectforgdpr-thumb.png)  <br/> [PDF](http://download.microsoft.com/download/E/C/D/ECD5A339-EF10-4420-B3A9-99098884D716/MSFT_Cloud_architecture_information%20protection%20for%20GDPR.pdf) \| [Visio](http://download.microsoft.com/download/E/C/D/ECD5A339-EF10-4420-B3A9-99098884D716/MSFT_Cloud_architecture_information%20protection%20for%20GDPR.vsdx)    |このコンテンツを記事形式で表示するには、「[GDPR のための Office 365 の情報保護](https://docs.microsoft.com/ja-JP/Office365/SecurityCompliance/office-365-information-protection-for-gdpr)」を参照してください。      |

### <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a>選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス 

このガイドでは、セキュリティで保護されたクラウド環境を実装する方法について説明します。このソリューション ガイダンスは、どのような組織でも使用できます。アジャイルな組織向けの、BYOD によるアクセスおよびゲスト アカウントに関する追加のヘルプが含まれています。このガイダンスは、独自の環境を設計するための開始点としてご利用ください。


|**Item**|**説明**|
|:-----|:-----|
|**選挙運動のための Microsoft Security ガイダンス** <br/> [![ミニ ポスター セット用のサムネイル。](media/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf) <br/> [PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf)  \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.vsdx) <br/> |このガイダンスでは、選挙運動を行う団体を例として使用しています。このガイダンスは、任意の環境を設計するための開始点としてご利用ください。  <br/> |
|**非営利組織のための Microsoft Security ガイダンス** <br/> [![ダウンロード可能なファイル用のサムネイル画像](media/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf) <br/> [PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf)  \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.vsdx) <br/> |このガイドは、非営利組織用に少し改定されています。たとえば、Office 365 Nonprofit のプランについて言及しています。技術的なガイダンスは選挙運動のソリューション ガイドと同じです。  <br/> |

このガイダンスにはテスト ラボ ガイドが含まれます。詳細については、「[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](https://docs.microsoft.com/ja-JP/Office365/SecurityCompliance/microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o)」を参照してください。

### <a name="microsoft-telephony-solutions"></a>Microsoft テレフォニー ソリューション

Microsoft では、Microsoft クラウド内の Teams の使用を開始する際に使用できるいくつかのオプションをサポートしています。このポスターは、どの Microsoft テレフォニー ソリューション (クラウド内の電話システムまたはオンプレミスのエンタープライズ ボイス) が組織のユーザーに適しているかを判断し、組織を公衆交換電話網 (PSTN) に接続する方法を決定するのに役立ちます。

![Microsoft テレフォニー ソリューションのポスターのサムネイル](media/microsoft-telephony-solutions-thumb.png) <br/>
[PDF](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.pdf) | [Visio](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.vsdx) 

詳細については、このポスターの記事を参照してください: [Microsoft テレフォニー ソリューション](https://docs.microsoft.com/ja-JP/SkypeForBusiness/hybrid/msft-telephony-solutions)。
  
<a name="msd"> </a>
### <a name="deploy-a-modern-and-secure-desktop-with-microsoft"></a>Microsoft の最新のセキュリティで保護されたデスクトップの展開

Windows 10 での Office 365 ProPlus の更新プログラムの展開と管理について IT アーキテクトが知る必要のある事柄。
  
|**アイテム**|**説明**|
|:-----|:-----|
|[![Microsoft の最新のセキュリティで保護されたデスクトップの展開に関するモデルのサムネイル](media/321dd59c-d992-4c7a-a7b6-c23a783858bd.png)          ](https://www.microsoft.com/download/details.aspx?id=55987) <br/> [PDF](http://download.microsoft.com/download/4/E/9/4E90E227-770A-41D1-99FE-925A64D81A55/MSFT_modern_secure_desktop.pdf)  \| [Visio](http://download.microsoft.com/download/4/E/9/4E90E227-770A-41D1-99FE-925A64D81A55/MSFT_modern_secure_desktop.vsdx) <br/> | このモデルには次のものが含まれています。 <ul><li>  Microsoft Cloud から Windows 10 と Office ProPlus を展開する </li><li>  System Center Configuration Manager を使用して Windows 10 と Office ProPlus を展開する </li><li>  Microsoft Cloud から Windows 10 と Office ProPlus の更新プログラムを管理する </li><li>  System Center Configuration Manager を使用して Windows 10 と Office ProPlus の更新プログラムを管理する </li><li>  Windows 10 のすぐに使用可能な追加保護機能 </li></ul><br/> |
   
## <a name="see-also"></a>関連項目

[SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[セキュリティ ソリューション](security-solutions.md)
  
[ハイブリッド ソリューション](hybrid-solutions.md)

