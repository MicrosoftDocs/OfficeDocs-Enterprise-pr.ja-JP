---
title: "Contoso Corporation のサブスクリプション、ライセンス、およびユーザー アカウント"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "概要: は、contoso 社のクラウドのサブスクリプション、ライセンス、ユーザー アカウント、およびテナントの構造を理解します。"
ms.openlocfilehash: 0fdd72a697edb312be13c9794e543a81bf9a8e54
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a>Contoso Corporation のサブスクリプション、ライセンス、およびユーザー アカウント

 **の概要:**Contoso 社のクラウドのサブスクリプション、ライセンス、ユーザー アカウント、およびテナントの構造を理解します。
  
すべてのクラウド製品について ID の一貫した使用と課金を実現するために、Microsoft は、組織/サブスクリプション/ライセンス/ユーザー アカウントの階層を提供します。
  
- 組織
    
    Microsoft クラウド製品を使用しているビジネス エンティティ。通常は、パブリック DNS ドメイン名 (例: contoso.com) で識別されます。
    
- サブスクリプション
    
    マイクロソフトの SaaS では、製品 (Office 365、Intune と EMS では、Dynamics 365) をクラウドでのサブスクリプションは、特定の製品およびユーザー ライセンスの購入のセットです。Azure のサブスクリプションにより、組織に消費されたクラウド サービスの通話料金です。
    
- ライセンス
    
    マイクロソフト SaaS クラウド製品のライセンスにより、クラウド サービスを使用する特定のユーザー アカウントです。Azure のソフトウェア ・ ライセンスは、追加のソフトウェア ライセンスを購入する必要がありますが、サービスの料金に構築されています。
    
- ユーザー アカウント
    
    ユーザー アカウントは Azure AD テナントに格納され、Windows Server AD などのオンプレミスの ID プロバイダーから同期できます。
    
## <a name="contosos-structure"></a>Contoso 社の構造

Contoso 社では、組織とそのサブスクリプション、ライセンス、アカウント、テナントに対して、次の構造を決定しました。
  
**図 1: Contoso の組織、サブスクリプション、ライセンス、ユーザー アカウントおよびテナント**

![Contoso 社の組織、サブスクリプション、ライセンス、ユーザー アカウント、テナント](images/Contoso_Poster/Subscriptions.png)
  
図 1 は、Contoso 社の組織が、どのように複数のサブスクリプションを含み、contoso.com Windows Server AD フォレストから同期されたユーザー アカウントを含む共通の Azure AD テナントに関連付けられているかを示しています。
  
- **組織**コントソ株式会社は、そのパブリック ドメイン名 contoso.com によって識別されます。
    
  - **サブスクリプションとライセンス**コントソ株式会社は、次の使用しています。
    
  - 5,000 ライセンスで Office 365 エンタープライズ E3 製品
    
  - 200 個のライセンスがある Office 365 Enterprise E5 製品
    
  - EMS 製品 5,000 ライセンス
    
  - 100 のライセンスを持つ Dynamics 365 製品
    
  - 地域に基づく複数の Azure サブスクリプション
    
  - **ユーザー アカウント**一般的な Azure AD テナントには、ユーザー アカウントの一覧が含まれているし、Azure サブスクリプションにより、contoso 社のサブスクリプションでは、開発/テスト以外のすべてのグループを使用します。
    
Contoso 社のテナントの場合:
  
- Saas クラウドのテナントは、クラウド サービスを提供するサーバーを収容している地域の場所です。Contoso 社は、その Office 365、EMS、Dynamics 365 のテナントをホストするためのヨーロッパの地域を選択しました。 
    
- Azure PaaS サービスとアプリケーションおよび IaaS IT 作業負荷は、世界中に、Azure データ センター内のテナントを持つことができます。Azure AD、テナントは、Azure AD のアカウントおよびグループを含むの特定のインスタンスです。
    
- Contoso 社の Windows サーバー AD フォレストの同期されたアカウントを含む一般的な Azure AD テナントには、マイクロソフトのクラウド サービスの間での IDaaS が用意されています。
    
詳細については、[ライセンス、サブスクリプション、アカウント、およびマイクロソフトのクラウド サービスのテナント](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)を参照してください。
  
## <a name="contosos-azure-subscriptions"></a>Contoso 社の Azure サブスクリプション

図 2 は、contoso 社の Azure サブスクリプションの階層の設計を示しています。
  
**Azure サブスクリプションの contoso 社の構造を図 2:**

![Azure サブスクリプションの Contoso 社の構造](images/Contoso_Poster/Subscriptions_Nested.png)
  
- Microsoft とのエンタープライズ契約に基づき、Contoso 社は最上位です。
    
- 世界中の contoso 社の Windows サーバーの AD フォレストのドメインの Contoso 社のそれぞれの地域に対応するアカウントのセットがあります。
    
- 各領域内では、地域の開発、テスト、および運用展開のニーズに基づいて 1 つまたは複数のサブスクリプションがあります。
    
各 Azure サブスクリプションは、Azure サービスへの認証と承認のために、ユーザー アカウントとグループを含む単一の Azure AD テナントと関連付けることができます。運用サブスクリプションでは、Contoso 社の共通の Azure AD テナントを使用します。
  
## <a name="see-also"></a>関連項目

[Microsoft Cloud の Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)




