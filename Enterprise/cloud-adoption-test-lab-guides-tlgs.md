---
title: "クラウド導入のテスト ラボ ガイド (TLG)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/6/2017
ms.audience: ITPro
ms.topic: hub-page
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
---

# クラウド導入のテスト ラボ ガイド (TLG)

 **概要:** これらのクラウド導入のテスト ラボ ガイド (TLG) を使用して、Office 365、Enterprise Mobility + Security (EMS)、Dynamics 365、Office Server 製品のデモンストレーション、概念実証、開発/テスト環境を設定します。
  
TLG では短時間で Microsoft 製品について学習できます。あるテクノロジや構成について、それが特定の状況に適しているかどうかを決定したり、テクノロジをユーザーにロールアウトするために、事前に評価が必要な場合に最適です。この実地体験型ガイドにより、新しい製品やソリューションの展開要件を理解し、運用環境でホストする計画を立てやすくなります。
  
また、TLG は、アプリケーションの開発およびテスト用の典型的な環境を作成します。これは、開発/テスト環境とも呼ばれます。
  
![Microsoft Cloud のテスト ラボ ガイド](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
開始する前に、これらの追加のリソースを参照してください。
  
- Microsoft Virtual Academy セッションの「[クラウド導入のテスト ラボ ガイドを使用した Microsoft Cloud を試す](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881)」(22 分) を視聴してください。
    
- [ここ](https://docs.com/officeitpro/4355/pdf-portal-ca-tlg-stack?c=ca4UTZ)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
    
## Office 365 開発/テスト環境
<a name="O365"> </a>

Office 365 の開発/テスト環境を構築するのに、次の記事を使用します。
  
- [基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
    
    Microsoft Azure インフラストラクチャ サービスで実行される簡易型のイントラネットを作成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。
    
- [Office 365 開発/テスト環境](office-365-dev-test-environment.md)
    
    Office 365 Enterprise E5 試用版サブスクリプションを作成します。これは、使用中のコンピューターから、または Azure インフラストラクチャ サービスで実行される簡易型のイントラネットから実行できます。
    
- [Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md)
    
    Azure AD Connect をインストールして、ディレクトリ同期をパスワード同期と共に実行するように構成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。
    
Office 365 の開発/テスト環境では、Office 365 のエンタープライズ機能をデモンストレーションするために次の記事を使用します。
  
- [Office 365 開発/テスト環境用の多要素認証](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Office 365 サブスクリプションのアカウントに対応するスマートフォンに送信されたテキスト メッセージを使用して、セカンダリ認証を構成してテストします。
    
- [Office 365 開発/テスト環境のフェデレーション ID](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Windows Server Active Directory ドメインのアカウントを使用してフェデレーション認証を構成し、デモンストレーションします。
    
- [Office 365 開発/テスト環境の Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Office 365 Cloud App Security の構成とデモンストレーションを行い、Office 365 サブスクリプションでの不審なアクティビティを監視し、通知するポリシーを作成します。
    
- [Office 365 開発/テスト環境の Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Advanced Threat Protection の構成とデモンストレーションを行います。これは Exchange Online Protection (EOP) の機能であり、マルウェアからメールを保護します。
    
- [Office 365 の開発/テスト環境のアドバンスト eDiscovery](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    サンプル データを追加して Advanced eDiscovery のデモンストレーションを行います。これにより、メールやドキュメントなどの Office 365 に格納されているデータをすばやく見つけて分析できます。
    
- [Office 365 の開発/テスト環境での機密性の高いファイルの保護](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    機密文書を誤って間違ったドキュメント フォルダーに投稿した場合でも、中のデータが保護されるようにするために、Office 365 Information Rights Management を使用する方法を示します。
    
- [Office 365 開発/テスト環境でのデータ分類とラベルの作成](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Azure Information Protection (AIP) クライアントを使用して、さまざまなレベルのセキュリティでドキュメントを分類する方法を示します。
    
- [Office 365 開発/テスト環境での分離した SharePoint Online チーム サイト](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    重要なリソースや機密性の高いリソース用に、組織の他の部分から分離されている SharePoint Online チーム サイトを作成する方法を示します。
    
## Microsoft 365 Enterprise 開発/テスト環境
<a name="O365"> </a>

これらの記事を利用して [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) シナリオ向けの開発/テスト環境を作成します。
  
- [Microsoft 365 Enterprise 開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)
    
    Office 365 E5、EMS E5、Windows 10 Enterprise を実行しているコンピューターが含まれる初期環境を作成します。
    
- [Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    iOS および Android デバイスのユーザー グループとモバイル アプリケーション管理 (MAM) のポリシーを作成します。
    
- [あっ、マイクロソフトのエンタープライズ 365 の開発/テスト環境でを登録します。](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    iOS または Android デバイスを登録し、それらをリモートで管理します。
    
## Office 365 と Dynamics 365 の開発/テスト環境
<a name="O365_D365"> </a>

以下の記事で、Dynamics 365 試用版サブスクリプションを追加し、Office 365 と Dynamics 365 の統合された機能とシナリオをテストします。
  
- [Office 365 と Dynamics 365 の開発/テスト環境](office-365-and-dynamics-365-dev-test-environment.md)
    
    Dynamics 365 試用版サブスクリプションと Dynamics 365 ライセンス、およびアクセス許可をユーザー アカウントに追加します。
    
- [Office 365 と Dynamics 365 の開発/テスト環境の Exchange Online 統合](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Exchange Online のメールボックスで Office 365 と Dynamics 365 を併用するための構成と方法ついて説明します。
    
## One Microsoft Cloud 開発/テスト環境
<a name="O365_D365"> </a>

次の Microsoft のクラウド サービスすべてを含む開発/テスト環境を作成します:Office 365、Azure、EMS、Dynamics 365。詳しい手順については、「[One Microsoft Cloud 開発/テスト環境](the-one-microsoft-cloud-dev-test-environment.md)」を参照してください。
  
## シミュレートされたクロスプレミスの開発/テスト環境
<a name="O365_D365"> </a>

以下の記事で、Azure 仮想ネットワークやシミュレートされたオンプレミス ネットワークが含まれている、クロスプレミスの開発/テスト環境を作成できます。
  
- [Azure でのシミュレートされたクロスプレミスの仮想ネットワーク](simulated-cross-premises-virtual-network-in-azure.md)
    
    シミュレートされたイントラネットを作成し、ハイブリッド クラウド構成で Azure Virtual Network に接続します。
    
- [Azure 開発/テスト環境でのイントラネット SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Azure 仮想ネットワークに単一のサーバー SharePoint Server 2016 ファームを作成して、シミュレートされたオンプレミス ネットワークからの接続と管理をテストします。
    
## クラウド ベースの他の開発/テスト環境
<a name="ADD_TLGs"> </a>

Azure インフラストラクチャ サービス内に作成できる、クラウド ベースのその他の開発/テスト環境は次のとおりです。
  
- [Azure における SharePoint Server 2016 の開発/テスト環境](https://technet.microsoft.com/ja-jp/library/mt723354.aspx)
    
    Azure インフラストラクチャ サービスに単一サーバーの SharePoint Server 2016 ファームを構築します。
    
- [Azure における Exchange 2016 開発およびテスト環境](https://technet.microsoft.com/ja-jp/library/mt733070%28v=exchg.160%29.aspx)
    
    単一の Exchange 2016 サーバーを Azure インフラストラクチャ サービスに構築します。
    
- [SharePoint Server 2013 dev/test environments in Azure](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    基本および高可用性の SharePoint Server 2013 ファームを Azure インフラストラクチャ サービスに構築します。
    
**ディスカッションへの参加**

|**お問い合わせ**|**説明**|
|:-----|:-----|
|**必要なソリューション** <br/> |複数の Microsoft 製品やサービスにまたがるソリューションに関するコンテンツを作成しています。[MODAcontent@microsoft.com](mailto:modacontent@microsoft.com? Subject=[Solution%20Feedback]:%20) に電子メールを送信して、サーバー間のソリューションに関するご意見や、特定のソリューションに関するご質問をお寄せください。 <br/> |
|**ソリューションのディスカッションへの参加** <br/> |ソリューションについてご意見をお持ちの場合は、ソリューション アドバイザリ ボード (SAB) へ参加して、Microsoft ソリューション コンテンツの開発者、業界の専門家、世界中のお客様の大規模で活気に満ちたコミュニティに接続することをご検討ください。参加するには、電子メールを [SAB@microsoft.com](mailto:sab@microsoft.com?Subject=Request%20to%20join%20the%20Solutions%20Advisory%20Board) に送信してください。どなたでも[SAB のブログ](http://blogs.technet.com/b/solutions_advisory_board/)でコミュニティに関連するコンテンツをお読みいただけます。しかし、SAB のメンバーは、プライベートなソリューション ウェビナーにアクセスでき、SAB の Yammer ネットワークに参加できます。  <br/> |
|**記載されているアートの取得方法** <br/> |「[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)」のコンテンツ内にあるアートの編集可能なコピーが必要な方には、喜んでお送りします。アートの URL とタイトルを記述した電子メールを [MODAcontent@microsoft.com](mailto:modacontent@microsoft.com?subject=[Art%20Request]:%20) に送信してください。 <br/> |
   
## See Also
<a name="ADD_TLGs"> </a>

#### 

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)
  
[SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[ハイブリッド ソリューション](hybrid-solutions.md)

