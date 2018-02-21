---
title: "ライセンス、サブスクリプション、アカウント、およびマイクロソフトのクラウド サービスのテナント"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: "概要: は、マイクロソフトのクラウド サービスの間で、組織、サブスクリプション、ライセンス、ユーザー アカウント、およびテナント間の関係を理解します。"
ms.openlocfilehash: a1bcc040d046e4e5674f16432aeffb0a34b9031b
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>ライセンス、サブスクリプション、アカウント、およびマイクロソフトのクラウド サービスのテナント

 **の概要:**マイクロソフトのクラウド サービスの間では、組織、サブスクリプション、ライセンス、ユーザー アカウント、およびテナント間の関係を理解します。
  
マイクロソフトでは、そのクラウド サービス間での id と請求の一貫した使用法の組織、サブスクリプション、ライセンス、およびユーザー アカウントの階層構造を提供します。
  
- Microsoft Office 365
    
    [ビジネス プランと価格設定](https://products.office.com/business/compare-office-365-for-business-plans)の詳細についてを参照してください。
    
- Microsoft Azure
    
    詳細については、 [Azure の価格](https://azure.microsoft.com/pricing/)を参照してください。
    
- Microsoft Intune と、エンタープライズ モビリティとセキュリティ (EMS)
    
    詳細については、 [Intune の価格](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)を参照してください。
    
- Microsoft Dynamics 365
    
    詳細については、 [Dynamics 365 の価格](https://dynamics.microsoft.com/)を参照してください。
    
## <a name="elements-of-the-hierarchy"></a>階層の要素

階層の要素を以下に示します。
  
### <a name="organization"></a>組織

組織は、Microsoft クラウド製品を使用しているビジネス エンティティを表します。通常は、パブリック ドメイン ネーム システム (DNS) のドメイン名 (例: contoso.com) で識別されます。組織は、サブスクリプションのコンテナーになります。
  
### <a name="subscriptions"></a>サブスクリプション

サブスクリプションは、1 つを使用するには、Microsoft と契約、またはユーザーごとのライセンス料金またはクラウド ベースのリソースの消費量に基づくさらにマイクロソフトのクラウド プラットフォームやサービス、諸費用を計上します。サービス (SaaS) としてマイクロソフトのソフトウェア ・ ベースのクラウド ・ サービス (Office 365、Intune と EMS では、Dynamics 365) は、ユーザーごとのライセンス料金を請求します。(PaaS) およびインフラストラクチャをクラウド リソースの消費量に基づくサービス (IaaS) クラウド製品 (Azure) 料としてマイクロソフトのプラットフォームです。
  
試用版サブスクリプションを使用することもできます。ただし、このサブスクリプションは、特定の期間を過ぎるか、特定の消費料金を超えると失効します。試用版サブスクリプションは、有料サブスクリプションに変更できます。
  
組織は、マイクロソフトのクラウド ソリューションの複数のサブスクリプションを持つことができます。例を図 1 に示します。
  
**組織の複数のサブスクリプションの使用例を図 1:**

![Microsoft のクラウド プランの複数のサブスクリプションのある組織の例。](images/Subscriptions/Subscriptions_Fig1.png)

  
図 1 は、複数の Office 365 サブスクリプション、1 つの Intune サブスクリプション、1 つの Dynamics 365 サブスクリプション、複数の Azure サブスクリプションを持つ単一の組織を示しています。
  
### <a name="licenses"></a>ライセンス

マイクロソフトの SaaS クラウド製品のライセンスにより、クラウドのサービスを使用する特定のユーザー アカウントを提供します。サブスクリプションの一部として、固定の月額料金が課金されます。管理者は、サブスクリプション内の個々 のユーザー アカウントにライセンスを割り当てます。図 2 の使用例は、Contoso 社のエンタープライズ E5 の機能とサービスを使用する最大 100 個の個別のユーザー アカウントに許可する、Office 365 エンタープライズ E5 サブスクリプション ライセンスでは 100、
  
**SaaS ベースのサブスクリプションを組織内の図 2: ライセンス**

![Microsoft の SaaS ベース クラウド プランのサブスクリプション内の複数ライセンスの例。](images/Subscriptions/Subscriptions_Fig2.png)
  
Azure PaaS ベースのクラウド サービスの場合、サービス料金にソフトウェア ライセンスが組み込まれています。  
  
Azure IaaS ベースの仮想マシン場合、仮想マシン イメージにインストールしたソフトウェアまたはアプリケーションを使用するために、追加ライセンスが必要になることがあります。一部の仮想マシン イメージにはライセンス付きバージョンのソフトウェアがインストールされていて、サーバーに対する分単位の料金が費用に含まれます。その例として、SQL Server 2014 および SQL Server 2016 の仮想マシン イメージが挙げられます。  
  
一部の仮想マシン イメージには、アプリケーションの試用版がインストールされていて、試用期間の経過後も使用する場合は追加のソフトウェア アプリケーション ライセンスが必要になります。たとえば、SharePoint Server 2016 試用版仮想マシン イメージには、プレインストールされた試用版の SharePoint Server 2016 が含まれています。試用期間後に SharePoint Server 2016 の使用を続けるには、SharePoint Server 2016 のライセンスとクライアントのライセンスを Microsoft から購入する必要があります。こうした課金は Azure サブスクリプションとは別であり、仮想マシンを実行する分単位の料金がそのまま適用されます。
  
### <a name="user-accounts"></a>ユーザー アカウント

マイクロソフトのクラウド ソリューションのすべてのユーザー アカウントは、ユーザー アカウントとグループが含まれている Azure Active Directory (AD) テナントに格納されます。Azure の AD 接続では、Windows サーバー ベースのサービスを使用して既存の Windows サーバーを AD アカウントには、Azure AD テナントを同期できます。これは、ディレクトリ同期 (DirSync) と呼ばれます。
  
図 3 は、共通の Azure AD テナントを使用する組織の複数サブスクリプションの例を示しています。このテナントに組織のアカウントが格納されています。
  
**図 3: 複数の組織を使用するサブスクリプション同じ Azure AD テナント**

![すべてのサブスクリプションが同じ Azure AD テナントを使用する、複数のサブスクリプションのある組織の例。](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a>テナント

SaaS クラウド商品の場合、テナントとはクラウド サービスを提供しているサーバーが収容された地域の場所のことです。たとえば、Contoso Corporation は、パリ本社の 15,000 人の従業員用の Office 365、EMS、および Dynamics 365 テナントのホストに欧州地域を選択しています。
  
Azure PaaS サービスと、Azure IaaS でホストされる仮想マシン ベースのワークロードは、世界中の Azure データセンターのテナントを持つことができます。場所と呼ばれる Azure データセンターは、Azure PaaS のアプリやサービスまたは IaaS ワークロードの要素を作成するときに、ユーザーが指定します。
  
Azure AD テナントは、アカウントおよびグループを収容する Azure AD の特定のインスタンスです。Office 365、Dynamics 365、または Intune/EMS の有料または試用版サブスクリプションには、無料の Azure AD テナントが含まれています。この Azure AD テナントには、その他の Azure サービスは含まれていません。これは、Azure の試用版または有料のサブスクリプションと同じものではありません。
  
### <a name="summary-of-the-hierarchy"></a>階層の概要

ここに、簡単なまとめを示します。
  
- 1 つの組織には複数のサブスクリプションを含めることができる
    
  - 1 つのサブスクリプションには複数のライセンスを含めることができる
    
  - ライセンスは個別のユーザー アカウントに割り当てできる
    
  - ユーザー アカウントは Azure AD テナントに保存できる
    
組織、サブスクリプション、ライセンス、ユーザー アカウントの関係の例を示します。
  
- パブリック ドメイン名によって識別される組織。
    
  - ユーザー ライセンスがある Office 365 Enterprise E3 サブスクリプション。
    
    ユーザー ライセンスがある Office 365 Enterprise E5 サブスクリプション。
    
    ユーザー ライセンスがある EMS サブスクリプション。
    
    ユーザー ライセンスがある Dynamics 365 サブスクリプション。
    
    複数の Azure サブスクリプション。
    
  - 共通の Azure AD テナントにある組織のユーザー アカウント。
    
複数の Microsoft クラウド製品のサブスクリプションは、同じ Azure AD テナントを使用できます。このテナントは、共通 ID プロバイダーとして機能します。オンプレミスの Windows Server AD の同期されたアカウントを収容する中央 Azure AD テナントを使用すると、クラウドをベースとしたサービスとしての ID (IDaaS) が組織に提供されます。これを図 4 に示します。
  
**図 4: アカウントの同期の設置型と組織の IDaaS**

![組織のサービスとしての ID (IaaS) IDaaS。](images/Subscriptions/Subscriptions_Fig4.png)
  
図 4 は、Microsoft の SaaS クラウド製品、Azure PaaS アプリ、Azure AD ドメイン サービスを使用する Azure IaaS の仮想マシンにより、共通の Azure AD テナントがどのように使用されるかを示します。Azure AD Connect は、オンプレミスの Windows Server AD フォレストを Azure AD テナントと同期します。
  
マイクロソフトのクラウド サービスの間でアイデンティティの統合の詳細については、[エンタープライズ設計者向けのマイクロソフトのクラウド Id](https://aka.ms/cloudarchidentity)を参照してください。
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>複数の Microsoft クラウド商品のサブスクリプションの組み合わせ

次の表では、既に所有している 1 つの種類のクラウド商品のサブスクリプション (最初の列に列挙したラベル) と、追加する別の種類のクラウド商品のサブスクリプション (列間を横切る) に基づいた、複数の Microsoft クラウド商品の可能な組み合わせ方法について説明しています。
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |該当なし  <br/> |Azure ポータルから Azure のサブスクリプションを組織に追加します。  <br/> |Office 365 ポータルから Intune/EMS のサブスクリプションを組織に追加します。  <br/> |Office 365 ポータルから Dynamics 365 のサブスクリプションを組織に追加します。  <br/> |
|**Azure** <br/> |Office 365 のサブスクリプションを組織に追加します。   <br/> |該当なし  <br/> |Intune/EMS サブスクリプションを組織に追加します。  <br/> |Dynamics 365 サブスクリプションを組織に追加します。  <br/> |
|**Intune/EMS** <br/> |Office 365 のサブスクリプションを組織に追加します。   <br/> |Azure ポータルから Azure のサブスクリプションを組織に追加します。  <br/> |該当なし  <br/> |Dynamics 365 サブスクリプションを組織に追加します。  <br/> |
|**Dynamics 365** <br/> |Office 365 のサブスクリプションを組織に追加します。   <br/> |Azure ポータルから Azure のサブスクリプションを組織に追加します。  <br/> |Intune/EMS サブスクリプションを組織に追加します。  <br/> |該当なし  <br/> |
   
Microsoft SaaS ベース サービスの場合は、Office 365 管理センターを使用すると、組織にサブスクリプションを簡単に追加できます。
  
1. グローバル管理者アカウントを Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインし、し、[**管理**] をクリックします。
    
2. **管理センター**ホーム ページの左側のナビゲーションから、**請求**、および、**購買サービス**をクリックします。
    
3. [**サービスの購入**] ページで、新しいサブスクリプションを購入します。
    
Office 365 管理センターは、Office 365 サブスクリプションの組織と Azure AD テナントを SaaS ベースのクラウド製品の新しいサブスクリプションに割り当てます。
  
Office 365 サブスクリプションと同じ組織および Azure AD テナントに Azure サブスクリプションを追加するには
  
1. Azure ポータル ([https://portal.azure.com](https://portal.azure.com))、Office 365 のグローバル管理者アカウントでサインインします。
    
2. 左側のナビゲーションでは、**サブスクリプション**をクリックし、し、[**追加**] をクリックします。
    
3. [**サブスクリプションの追加**] ページで、サービスを選択し、支払情報と契約を完了します。
    
Azure と Office 365 のサブスクリプションを個別に購入して、Azure サブスクリプションから Office 365 の Azure AD テナントにアクセスする場合は、 [Azure サブスクリプションの Office 365 テナントに関連付ける](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription)手順を参照してください。
  
## <a name="see-also"></a>関連項目

[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)
  
[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[ハイブリッド ソリューション](hybrid-solutions.md)
  
[Contoso Corporation のサブスクリプション、ライセンス、およびユーザー アカウント](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



