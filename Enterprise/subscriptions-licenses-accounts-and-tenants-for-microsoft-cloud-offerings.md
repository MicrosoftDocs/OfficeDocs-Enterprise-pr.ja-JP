---
title: マイクロソフトのクラウド プランのサブスクリプション、ライセンス、アカウント、およびテナント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/25/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: '概要: Microsoft のクラウド プラン全体に渡る組織、サブスクリプション、ライセンス、ユーザー アカウント、およびテナントの関係について理解します。'
ms.openlocfilehash: 52857196f53a44196c96f60bd70564f5e3221b80
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906278"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>マイクロソフトのクラウド プランのサブスクリプション、ライセンス、アカウント、およびテナント

Microsoft は、クラウド プラン全体で ID の使用と課金の一貫性を維持するために、組織、サブスクリプション、ライセンス、ユーザー アカウントなどの階層を提供しています。
  
- Microsoft 365 および Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>階層の要素

階層の要素を以下に示します。
  
### <a name="organization"></a>組織

An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.
  
### <a name="subscriptions"></a>サブスクリプション

サブスクリプションとは、1 つ以上の Microsoft クラウドのプラットフォームやサービスを使用するための Microsoft との契約のことです。この契約では、ユーザー単位のライセンス料またはクラウドベースのリソース消費量に基づいて請求されます。 

- Microsoft のサービスとしてのソフトウェア (SaaS) ベースのクラウド製品 (Microsoft 365 および Dynamics 365) は、ユーザーごとのライセンス料金を請求します。 
- Microsoft のサービスとしてのプラットフォーム (PaaS) およびサービスとしてのインフラストラクチャ (IaaS) のクラウド サービス (Azure) では、クラウド リソースの消費量に基づいて請求されます。
 
You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.
  
組織は、Microsoft のクラウド商品の複数のサブスクリプションを所有できます。 図1は、複数の Microsoft 365 サブスクリプション、Dynamics 365 サブスクリプション、および複数の Azure サブスクリプションを持つ単一の組織を示しています。

**図 1: 1 つの組織に複数のサブスクリプションの例**

![Microsoft のクラウド プランの複数のサブスクリプションのある組織の例。](media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>ライセンス

Microsoft の SaaS クラウド商品の場合、1 つのライセンスで、1 つの特定のユーザー アカウントがクラウド商品のサービスを使用できるようになります。 サブスクリプションの一環として、月間の固定料金が課金されます。 管理者は、サブスクリプション内で個別のユーザー アカウントにライセンスを割り当てます。 図2の例では、Contoso Corporation に100ライセンスを適用した Microsoft 365 E5 サブスクリプションがあります。これにより、最大で100の個々のユーザーアカウントを使用して Microsoft の 365 E5 の機能とサービスを使用できます。
  
**図 2:1 つの組織の SaaS ベースのサブスクリプションに含まれるライセンス**

![Microsoft の SaaS ベース クラウド プランのサブスクリプション内の複数ライセンスの例。](media/Subscriptions/Subscriptions-Fig2.png)
  
Azure PaaS ベースのクラウド サービスの場合、サービス料金にソフトウェア ライセンスが組み込まれています。  
  
For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016. 
  
Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.
  
### <a name="user-accounts"></a>ユーザー アカウント

すべての Microsoft のクラウド商品のユーザー アカウントは、Azure Active Directory (Azure AD) テナントに保存されます。これには、ユーザー アカウントとグループが含まれます。 Azure AD テナントは、Windows サーバーベースのサービスである Azure AD Connect を使用して、既存の Active Directory Domain Services (AD DS) アカウントと同期できます。 これはディレクトリ同期と呼ばれます。
  
図 3 は、共通の Azure AD テナントを使用する組織の複数サブスクリプションの例を示しています。このテナントに組織のアカウントが格納されています。
  
**図 3:同じ Azure AD テナントを使用する組織の複数のサブスクリプション**

![すべてのサブスクリプションが同じ Azure AD テナントを使用する、複数のサブスクリプションのある組織の例。](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>テナント

SaaS クラウド商品の場合、テナントとはクラウド サービスを提供しているサーバーが収容された地域の場所のことです。 たとえば、Contoso 社では、Microsoft 365、EMS、および Dynamics 365 テナントをパリ本社の15000ワーカーに対してホストする地域を選択しました。
  
Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.
  
Azure AD テナントは、アカウントおよびグループを含む Azure AD の特定のインスタンスです。 Microsoft 365 または Dynamics 365 の有料または試用版サブスクリプションには、無料の Azure AD テナントが含まれています。 この Azure AD テナントには、他の Azure サービスは含まれていません。 Azure の試用版または有料版のサブスクリプションと同じではありません。
  
### <a name="summary-of-the-hierarchy"></a>階層の概要

ここに、簡単なまとめを示します。
  
- 1 つの組織には複数のサブスクリプションを含めることができる
    
  - 1 つのサブスクリプションには複数のライセンスを含めることができる
    
  - ライセンスは個別のユーザー アカウントに割り当てできる
    
  - ユーザー アカウントは Azure AD テナントに保存できる
    
組織、サブスクリプション、ライセンス、ユーザー アカウントの関係の例を示します。
  
- パブリック ドメイン名によって識別される組織。
    
  - ユーザーライセンスを持つ Microsoft 365 E3 サブスクリプション。
    
    ユーザーライセンスを持つ Microsoft 365 E5 サブスクリプション。
    
    ユーザー ライセンスがある Dynamics 365 サブスクリプション。
    
    複数の Azure サブスクリプション。
    
  - 共通の Azure AD テナントにある組織のユーザー アカウント。
    
複数の Microsoft クラウド商品のサブスクリプションは、同じ Azure AD テナントを使用できます。このテナントは、共通の ID プロバイダーとして機能します。 オンプレミスの AD DS の同期されたユーザー アカウントを収容しているセントラル Azure AD テナントを使用することで、組織にサービス (IDaaS) としてのクラウドベース ID が提供されます。 
  
**図 4: 同期されたオンプレミスのアカウントと組織の IDaaS**

![組織のサービスとしての ID (IaaS) IDaaS。](media/Subscriptions/Subscriptions-Fig4.png)
  
Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>複数の Microsoft クラウド プランのサブスクリプションの組み合わせ

次の表では、既に所有している 1 つの種類のクラウド商品のサブスクリプション (最初の列に列挙したラベル) と、追加する別の種類のクラウド商品のサブスクリプション (列間を横切る) に基づいた、複数の Microsoft クラウド商品の可能な組み合わせ方法について説明しています。
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |該当なし  <br/> |Azure ポータルから Azure のサブスクリプションを組織に追加します。  <br/> |Microsoft 365 管理センターから Dynamics 365 のサブスクリプションを組織に追加します。  <br/> |
|**Azure** <br/> |組織に Microsoft 365 サブスクリプションを追加します。  <br/> |該当なし  <br/> |Dynamics 365 サブスクリプションを組織に追加します。  <br/> |
|**Dynamics 365** <br/> |組織に Microsoft 365 サブスクリプションを追加します。  <br/> |Azure ポータルから Azure のサブスクリプションを組織に追加します。  <br/> |該当なし  <br/> |
   
Microsoft SaaS ベース サービスの場合は、管理センターを使用すると、組織にサブスクリプションを簡単に追加できます。
  
1. 全体管理者アカウントを使用して、Microsoft 365 管理センター ([https://admin.microsoft.com](https://admin.microsoft.com)) にサインインします。
    
2. **管理センター**のホームページ左側にあるナビゲーションで、**[課金]**、**[サービスを購入する]** の順にクリックします。
    
3. **[サービスを購入する]** ページで、新しいサブスクリプションを購入します。
    
管理センターは、Microsoft 365 サブスクリプションの組織と Azure AD テナントを、SaaS ベースのクラウド製品の新しいサブスクリプションに割り当てます。
  
Microsoft 365 サブスクリプションと同じ組織と Azure AD テナントを使用して Azure サブスクリプションを追加するには、次のようにします。
  
1. Microsoft 365 グローバル管理者アカウントを使用して、Azure portal () にサインインし [https://portal.azure.com](https://portal.azure.com) ます。
    
2. 左側のナビゲーションで、**[サブスクリプション]**、**[追加]** の順にクリックします。
    
3. **[サブスクリプションの追加]** ページでプランを選択し、支払情報を記入して契約します。
    
Azure と Microsoft 365 サブスクリプションを別々に購入しており、Azure サブスクリプションから Microsoft 365 Azure AD テナントにアクセスする場合は、「azure [Active Directory テナントに既存の azure サブスクリプションを追加](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)する」の手順を参照してください。
 
## <a name="see-also"></a>関連項目

[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)
  
[SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[ハイブリッド ソリューション](hybrid-solutions.md)

## <a name="next-step"></a>次の手順

[Microsoft 365 ネットワーク接続の評価](assessing-network-connectivity.md)
  
