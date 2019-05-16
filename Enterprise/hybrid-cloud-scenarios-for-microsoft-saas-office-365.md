---
title: Microsoft SaaS (Office 365) のハイブリッド クラウドのシナリオ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: '概要: Microsoft の SaaS ベースのクラウド製品のハイブリッドアーキテクチャとシナリオについて説明します (Office 365)。'
ms.openlocfilehash: 84092fe419ab31fca7763f434e328eb855d46835
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067223"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Microsoft SaaS (Office 365) のハイブリッド クラウドのシナリオ

 **概要:** Microsoft の SaaS ベースのクラウド製品のハイブリッドアーキテクチャとシナリオについて説明します (Office 365)。
  
クラウド移行または長期的な統合戦略の一環として、Exchange、SharePoint、または Skype for Business のオンプレミスの展開を Office 365 の対応する組み合わせと組み合わせて使用します。
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Microsoft SaaS ハイブリッドシナリオアーキテクチャ

図1は、Office 365 の Microsoft SaaS ベースのハイブリッドシナリオのアーキテクチャを示しています。
  
**図 1: Microsoft SaaS ベースの Office 365 のハイブリッドシナリオ**

![Office 365 の Microsoft SaaS ベースのハイブリッドシナリオ](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
アーキテクチャの各レイヤーについて:
  
- アプリとシナリオ
    
    さまざまな SaaS ベースのハイブリッドシナリオでは、Office Server 製品と Office 365 に対応しています。
    
  - Exchange Server と Exchange Online の組み合わせ (Exchange Server ハイブリッド)
    
  - Skype for business Server と Skype for business Online との組み合わせ、新しいクラウド PBX および Cloud Connector エディションのシナリオ
    
  - Sharepoint Server 2019、SharePoint Server 2016、または sharepoint Server 2013 と SharePoint Online の組み合わせ (複数のシナリオ)
    
    また、クロス積ハイブリッドシナリオであるオンプレミスの Skype for Business Server を使用した Exchange Online もあります。
    
- ID
    
    オンプレミスの Active Directory ドメインサービス (AD DS) とのディレクトリ同期を含めることができます。 または、サードパーティの id プロバイダーとフェデレーションを行うように Azure AD を構成することもできます。
    
- ネットワーク
    
    既存のインターネットパイプ、または Office 365 または Dynamics 365 用の Microsoft ピアリングを備えた ExpressRoute 接続から構成されます。
    
- 社内
    
    Exchange、SharePoint、および Skype for Business の既存のサーバーから構成することができます。これは、最新のバージョンに更新する必要があります。 その後、ハイブリッドシナリオ用の Office 365 と組み合わせて使用することができます。
    
独自の Office 365 開発/テスト環境をセットアップするには、「 [office 365 のテストラボガイド](cloud-adoption-test-lab-guides-tlgs.md)」を参照してください。
  
## <a name="skype-for-business-hybrid"></a>Skype for Business ハイブリッド

Skype for Business ハイブリッドを使用すると、既存のオンプレミス展開と Skype for Business Online を組み合わせることができます。 一部のユーザーはオンプレミスに所属しており、一部のユーザーはオンラインに所属していますが、ユーザーは contoso.com などの同じセッション開始プロトコル (SIP) ドメインを共有しています。 このハイブリッド構成を使用して、オンプレミスから Office 365 への移行をスケジュールで行うことができます。 また、Skype for Business を[Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)と統合することもできます。
  
**図 2: Skype for Business のハイブリッド構成**

![Skype for Business のハイブリッド構成](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
図2は、Office 365 で Skype for business Online と通信するオンプレミスの Skype for Business フロントエンドプールとエッジサーバーで構成される Skype for Business ハイブリッド構成を示しています。
  
詳細については、「 [skype For Business Server と skype for Business Online の間のハイブリッド接続を計画](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)する」を参照してください。
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Skype for Business Server を使用したクラウド PBX

クラウド PBX と Skype for business Server を使用すると、既存の Skype for Business Server のオンプレミス展開を、オンプレミスの公衆交換電話網 (PSTN) 接続を備えたトポロジに移行できます。 
  
**図 3: Skype for Business Server を使用したクラウド PBX**

![Skype for Business Server を使用したクラウド PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
図3は、オンプレミスの既存の PBX または電気通信ゲートウェイ、Skype for Business Server、および Office 365 の Microsoft クラウド PBX に接続された PSTN (Skype for business を含む) で構成される、Skype for Business Server の構成を含むクラウド PBX を示しています。オンライン。
  
クラウドに所属している組織内のユーザーは、信号とボイスメールを含む Microsoft cloud から構内交換 (PBX) サービスを受けることができますが、オンプレミスのエンタープライズ Voip を介して PSTN 接続 (ダイヤルトーン) が提供されます。Skype for Business Server の展開。
  
これは、クラウドベースのサービスに段階的に移行できるハイブリッド構成の良い例です。 Skype for Business Online への移行を開始するときに、ユーザーの音声機能を保持することができます。 ユーザーが所属している場所にかかわらず、自分の音声機能が続行されることを確認して、自分のペースでユーザーを移動することができます。 
  
詳細については、「 [skype For Business Server と skype for Business Online の間のハイブリッド接続を計画](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)する」を参照してください。
  
既存の Lync Server または Skype for Business Server の展開をまだ持っていない場合は、Skype for Business Cloud Connector エディションを使用できます。これは、クラウド PBX でオンプレミスの PSTN 接続を実装するパッケージ化された仮想マシン (Vm) のセットです。
  
詳細については、「 [Plan For Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)」を参照してください。

  
## <a name="sharepoint-hybrid"></a>SharePoint ハイブリッド

SharePoint ハイブリッドは、Office 365 の SharePoint Online とオンプレミスの SharePoint ファームを組み合わせて、接続された機能を最大限に活用しています。
  
**図 4: SharePoint ハイブリッド構成**

![SharePoint ハイブリッド構成](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
図4は、Office 365 で SharePoint Online と通信するオンプレミスの SharePoint ファームで構成される SharePoint ハイブリッド構成を示しています。
  
SharePoint ハイブリッドシナリオ:
  
- [ハイブリッドの OneDrive for Business](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [ハイブリッドエクストラネットの B2B](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [ハイブリッド検索](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [ハイブリッド プロファイル](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [ハイブリッドピッカー](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    Office 365 の SharePoint Online 管理センターから利用できるハイブリッド構成を自動化するウィザードを使用して、ハイブリッドシナリオを有効にすることが容易になります。
    
- [拡張ハイブリッド アプリ起動ツール](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    オンプレミスの SharePoint ファームのページ内で、ユーザーが Office 365 video および Delve アプリとエクスペリエンスを表示して使用できるようにします。
    
これらの SharePoint ハイブリッドシナリオは、拡張可能なハイブリッドアプリ起動ツールを除くすべて、SharePoint 2016 ユーザーと SharePoint 2013 ユーザーの両方で使用できます。
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 ハイブリッド

Exchange Server 2016 ハイブリッドを使用すると、オンプレミスのユーザーが既存の Exchange Server インフラストラクチャを引き続き使用している間に、Office 365 での Exchange Online の利点を実感することができます。 
  
**図 5: Exchange 2016 ハイブリッド構成**

![Exchange 2016 ハイブリッド構成](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
図5は、Office 365 の Exchange Online Protection とメールボックスと通信するオンプレミスの Exchange メールボックスサーバーで構成される Exchange 2016 ハイブリッド構成を示しています。
  
一部のユーザーはオンプレミスの電子メールサーバーを所有しており、一部のユーザーは Exchange Online を使用していますが、すべてのユーザーが同じ電子メールアドレススペースを共有しています。 
  
このハイブリッド構成:
  
- 時間の経過とともに、お客様のスケジュールに基づいて Exchange Online に移行する際に、既存の Exchange Server インフラストラクチャを活用できます。
    
- ブランチオフィスのインフラストラクチャに投資することなく、リモートサイトをサポートできます。
    
- Office 365 で Exchange Online Protection 経由で受信インターネットメールをルーティングできるようにします。
    
- データをオンプレミスで使用する必要がある子会社を持つ多国籍企業のニーズに対応します。
    
このハイブリッド構成は、Skype for Business Online や SharePoint Online など、他の Microsoft Office 365 アプリケーションと統合することもできます。
  
詳細については、「 [Exchange Server のハイブリッド展開](https://docs.microsoft.com/exchange/exchange-hybrid)」を参照してください。
  
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

