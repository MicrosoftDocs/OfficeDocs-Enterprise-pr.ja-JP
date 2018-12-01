---
title: Microsoft SaaS (Office 365) のハイブリッド クラウド シナリオ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: '概要: マイクロソフトの SaaS ベースの理解するハイブリッド アーキテクチャとシナリオ クラウドの製品 (Office 365)。'
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123414"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Microsoft SaaS (Office 365) のハイブリッド クラウドのシナリオ

 **の概要:** ハイブリッド アーキテクチャとシナリオを理解するマイクロソフトの SaaS ベースのクラウド ・ ソリューション (Office 365)。
  
クラウド移行または長期的な統合戦略の一環として、Exchange、SharePoint、または Skype for Business のオンプレミス展開を Office 365 内の対応する展開と組み合わせます。
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Microsoft SaaS のハイブリッド シナリオ アーキテクチャ

図 1 は、Microsoft SaaS ベースの Office 365 向けハイブリッド シナリオのアーキテクチャを示しています。
  
**図 1:Microsoft SaaS ベースの Office 365 向けハイブリッド シナリオ**

![Microsoft SaaS ベースの Office 365 向けハイブリッド シナリオ](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
アーキテクチャの各レイヤーについて:
  
- アプリとシナリオ
    
    SaaS ベースのさまざまなハイブリッド シナリオがあります。Office サーバー製品とそれに対応する Office 365 製品に沿って以下に示します。
    
  - Exchange Server を Exchange Online と組み合わせる (Exchange Server ハイブリッド)
    
  - Skype for Business Server を Skype for Business Online および新しいクラウド PBX とクラウド コネクタ エディションと組み合わせたシナリオ
    
  - SharePoint サーバー 2019年、SharePoint サーバーの 2016、または SharePoint Server 2013 は、SharePoint Online (複数の場合) と組み合わせる
    
    また、Exchange Online をオンプレミスの Skype for Business Server と組み合わせる製品間ハイブリッド シナリオもあります。
    
- ID
    
    オンプレミスの Windows Server AD とのディレクトリ同期を含めることができます。代わりに、サード パーティの ID プロバイダーとフェデレーションを行うように Azure AD を構成することもできます。
    
- ネットワーク
    
    Office 365 か Dynamics 365 用の既存のインターネット パイプか、Microsoft ピアリングとの ExpressRoute 接続で構成されています。
    
- オンプレミス
    
    Exchange、SharePoint、Skype for Business の既存のサーバーで構成でき、これらの製品は最新バージョンに更新する必要があります。その後、ハイブリッド シナリオで Office 365 の対応する製品と組み合わせることができます。
    
Office 365 の開発/テスト環境のセットアップは、 [Office 365 のテスト ラボ ガイド](cloud-adoption-test-lab-guides-tlgs.md)を参照してください。
  
## <a name="skype-for-business-hybrid"></a>Skype ビジネスのハイブリッド

ビジネスのハイブリッドの Skype を使用して、オンライン ビジネスの Skype で既存のオンプレミスの展開を結合できます。一部のユーザー ホーム設置型で、一部のユーザーがオンラインで置かれているにもかかわらず、ユーザーが contoso.com など、同じセッション開始プロトコル (SIP) ドメインを共有します。このハイブリッド構成を使用すると、スケジュールに時間の経過と共に Office 365 の設置から移行します。ビジネス用の Skype は、 [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)とも統合できます。
  
**図 2: ビジネスのハイブリッド構成の Skype**

![ビジネスのハイブリッド構成の Skype](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
ビジネスのフロント エンド プール、エッジ サーバーとの通信 Skype Office 365 のオンライン ビジネスのため、設置型 Skype から成るビジネス ハイブリッド構成では、Skype を図 2 に示します。
  
詳細については、[サーバーのビジネスとオンライン ビジネスの Skype の Skype 間のハイブリッド接続の計画](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)を参照してください。
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Skype for Business Server と組み合わされたクラウド PBX

クラウド ビジネス サーバーの Skype での PBX では、設置の公衆交換電話網 (PSTN) 接続を備えたビジネス サーバー設置型の展開トポロジを既存の Skype に移行することができます。 
  
**図 3:Skype for Business Server と組み合わされたクラウド PBX**

![Skype for Business Server と組み合わされたクラウド PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
図 3 は、Skype でクラウド PBX の設置では、Office 365 は、ビジネス用の Skype は、マイクロソフト クラウド PBX に接続されている既存の PBX または通信ゲートウェイ、ビジネスのサーバーで、Skype、PSTN のビジネス サーバー構成オンライン。
  
クラウドに所属する組織内のユーザーは、Microsoft クラウドから通知やボイスメールを含む構内交換機 (PBX) サービスを受信できますが、PSTN 接続 (ダイヤル トーン) はオンプレミスの Skype for Business Server 展開からエンタープライズ VoIP 経由で提供されます。
  
これは、段階的にクラウド ベースのサービスに移行することができるハイブリッド構成の優れた例です。ビジネス オンラインの Skype に移動を開始すると、ユーザーのボイス機能を保持できます。場所に置かれているペースで、音声機能がなしで続けることを知るだけで、ユーザーを移動することができます。 
  
詳細については、[サーバーのビジネスとオンライン ビジネスの Skype の Skype 間のハイブリッド接続の計画](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)を参照してください。
  
既存の Lync Server または Skype for Business Server 展開がまだない場合は、クラウド PBX とのオンプレミス PSTN 接続を実装するパッケージ化された仮想マシン (VM) のセットである、Skype for Business クラウド コネクタ エディションを使用できます。
  
詳細については、 [Skype ビジネス クラウド コネクタ ・ エディションの計画](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)を参照してください。

  
## <a name="sharepoint-hybrid"></a>SharePoint ハイブリッド

SharePoint ハイブリッドは、両方のメリットを活かした接続エクスペリエンスを実現するために、Office 365 の SharePoint Online をオンプレミスの SharePoint ファームと組み合わせます。

  
**図 4:SharePoint のハイブリッド構成**

![SharePoint のハイブリッド構成](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
図 4 は、SharePoint Online では、Office 365 との通信、設置型の SharePoint ファームで構成される、SharePoint のハイブリッド構成を示しています。
  
SharePoint ハイブリッド シナリオ
  
- ユーザーは SharePoint Server サイトと SharePoint Online サイトをフォローし、両者を 1 つのリストに統合して参照することができます。
    
- [エクストラネットの B2B のハイブリッド](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [ハイブリッド検索](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [ハイブリッド プロファイル](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [ハイブリッドの選択](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    ハイブリッド シナリオは、Office 365 の SharePoint Online 管理センターから入手できる、ハイブリッド構成を自動化するウィザードを使用して、簡単に有効にすることができます。
    
- [拡張ハイブリッド アプリ起動ツール](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    ユーザーは Office 365 ビデオや Delve アプリを表示および使用し、オンプレミスの SharePoint ファームのページ内で体験することができます。
    
これらのすべての SharePoint ハイブリッド シナリオは、拡張可能なハイブリッド アプリ起動ツールを除き、SharePoint 2016 と SharePoint 2013 の両方のユーザーが使用できます。
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 ハイブリッド

Exchange Server 2016 ハイブリッドを使用すると、オンライン ユーザーにとっての Office 365 の Exchange Online のメリットを実感できます。一方、オンプレミス ユーザーは既存の Exchange Server インフラストラクチャを引き続き使用します。  
  
**図 5:Exchange 2016 のハイブリッド構成**

![Exchange 2016 のハイブリッド構成](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
図 5 は、Exchange の 2016年ハイブリッドな構成、オンプレミスの Exchange メールボックス サーバーが Exchange のオンライン保護と Office 365 のメールボックスとの通信を示しています。
  
オンプレミスのメール サーバーを使用するユーザーと Exchange Online を使用するユーザーがいますが、すべてのユーザーは同じメール アドレス空間を共有しています。  
  
このハイブリッド構成の特徴は次のとおりです。
  
- スケジュールに従って段階的に Exchange Online に移行する間、既存の Exchange Server インフラストラクチャを活用します。



    
- 支店のインフラストラクチャに投資することなく、リモート サイトをサポートできます。
    
- Office 365 の Exchange Online Protection 経由で着信インターネット電子メールをルーティングできます。
    
- データをオンプレミスで保持する必要のある、子会社を持つ多国籍企業のニーズに対応します。
    
このハイブリッド構成は、Skype for Business Online や SharePoint Online などのその他の Microsoft Office 365 アプリケーションと統合することもできます。
  
詳細については、 [Exchange Server のハイブリッド展開](https://docs.microsoft.com/exchange/exchange-hybrid)を参照してください。
  
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

