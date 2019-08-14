---
title: テスト ラボ ガイド (TLG) を使用して Office 365 をテストする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: '概要: 次に示すテスト ラボ ガイド (TLG) を使用して、Office 365 のデモンストレーション、概念実証、または開発/テスト環境をセットアップします。'
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302739"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a>テスト ラボ ガイド (TLG) を使用して Office 365 をテストする

 **概要**: 次に示す記事を使用して、Office 365 のデモンストレーション、概念実証、または開発/テスト環境をセットアップします。
  
TLG では短時間で Microsoft 製品について学習できます。あるテクノロジや構成について、それが特定の状況に適しているかどうかを決定し、デザイン、プランニングを行いテクノロジをユーザーにロールアウトするさいに、事前に評価が必要な場合に最適です。この実地体験型ガイドにより、新しい製品やソリューションの展開要件を理解し、運用環境でホストする計画を立てやすくなります。
  
また、TLG は、アプリケーションの開発およびテスト用の典型的な環境を作成します。これは、開発/テスト環境とも呼ばれます。
  
![Microsoft Cloud のテスト ラボ ガイド](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a>Office 365 開発/テスト環境

Office 365 の開発/テスト環境を構築するのに、次の記事を使用します。
  
- [基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
    
    Microsoft Azure インフラストラクチャ サービスで実行される簡易型のイントラネットを作成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。
    
- [Office 365 開発/テスト環境](office-365-dev-test-environment.md)
    
    Office 365 Enterprise E5 試用版サブスクリプションを作成します。これは、使用中のコンピューターから、または Azure インフラストラクチャ サービスで実行される簡易型のイントラネットから実行できます。
    
- [ディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)
    
    Azure AD Connect をインストールして、ディレクトリ同期をパスワード同期と共に実行するように構成します。このステップは省略可能で、シミュレートされたエンタープライズ構成を構築する場合は行ってください。
    
Office 365 の開発/テスト環境では、Office 365 のエンタープライズ機能をデモンストレーションするために次の記事を使用します。
  
- [多要素認証](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Office 365 サブスクリプションのアカウントに対応するスマートフォンに送信されたテキスト メッセージを使用して、セカンダリ認証を構成してテストします。
    
- [フェデレーション ID](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Active Directory Domain Services (AD DS) ドメインのアカウントを使用して、フェデレーション認証の構成とデモンストレーションを行います。
    
- [Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Advanced Threat Protection の構成とデモンストレーションを行います。これは Exchange Online Protection (EOP) の機能であり、マルウェアからメールを保護します。

## <a name="simulated-cross-premises-devtest-environment"></a>シミュレートされたクロスプレミスの開発/テスト環境

[シミュレートされたイントラネット](simulated-cross-premises-virtual-network-in-azure.md)を作成し、ハイブリッド クラウド構成で Azure Virtual Network に接続します。
    
## <a name="sharepoint-server-2016-devtest-environment"></a>SharePoint Server 2016 開発/テスト環境

Azure インフラストラクチャ サービスに[単一サーバーの SharePoint Server 2016 ファーム](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)を構築します。

## <a name="microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 開発/テスト環境

[Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides) の開発/テスト環境を作成します。  
    
## <a name="see-also"></a>関連項目

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)
  
[SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[ハイブリッド ソリューション](hybrid-solutions.md)
