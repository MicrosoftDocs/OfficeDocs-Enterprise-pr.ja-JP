---
title: "Contoso Corporation の ID"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: "Contoso 社の IDaaS を利用して地理的に分散、冗長化されたユーザーと認証の概要を理解します。"
ms.openlocfilehash: a0de29ac7e73216e04fe02c680f2557e9f402883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="identity-for-the-contoso-corporation"></a>Contoso Corporation の ID

 **の概要:**Contoso 社の IDaaS を利用して地理的に分散、冗長化されたユーザーと認証を理解します。
  
マイクロソフトは、サービス (IDaaS) として、クラウド サービスの間で Id を提供します。クラウドの包括的なインフラストラクチャを導入するには、contoso 社の IDaaS ソリューション必要があります、設置型の id プロバイダーを活用を既存の信頼できる、サードパーティの id プロバイダーとのフェデレーションの認証が含まれてできます。
  
## <a name="contosos-windows-server-ad-forest"></a>Contoso 社の Windows サーバーの AD フォレスト

Contoso 社では、contoso.com の 7 つのドメインがあり、世界の地域ごとに 1 つの単一の Windows サーバー ・ Active Directory (AD) フォレストを使用します。本社、地域のハブのオフィス、サテライト オフィスなどには、ローカルの認証と承認のためのドメイン コント ローラーが含まれています。
  
**図 1: contoso 社のフォレストとドメインの世界**

![世界各地の Contoso 社の Windows サーバーの AD フォレストとドメイン](images/Contoso_Poster/Contoso_WW_ID.png)
  
図 1 では、地域ハブを含む世界各地の地域ドメインを持つ Contoso 社のフォレストを示しています。
  
Contoso 社では、クラウドベースのアプリおよびワークロードの認証と承認のために、contoso.com フォレストのアカウントとグループを使用することを望んでいます。
  
## <a name="contosos-federated-authentication-infrastructure"></a>Contoso 社のフェデレーション認証インフラストラクチャ

Contoso を使用します。
  
- 顧客は Microsoft、Facebook、または Google のメール アカウントを使用してパブリック Web サイトにサインインできます。
    
- ベンダーおよびパートナーは、LinkedIn、Salesforce、または Google のメール アカウントを使用してパートナー エクストラネットにサインインできます。
    
**図 2: contoso 社のお客様とパートナーのフェデレーション認証サポート**

![顧客とパートナーのフェデレーション認証をサポートする Contoso 社の既存のインフラストラクチャ](images/Contoso_Poster/Federated_ID.png)
  
図 2 は、公開 Web サイト、パートナーのエクストラネット、および AD FS サーバーのセットを含む Contoso 社の DMZ を示しています。DMZ は、顧客、パートナー、およびインターネット サービスを含むインターネットに接続されています。
  
DMZ の Active Directory フェデレーション サービス (AD FS) サーバーは、パブリック Web サイトにアクセスするための顧客資格情報、およびパートナー エクストラネットにアクセスするためのパートナー資格情報を認証します。
  
Contoso 社では、Azure の Web アプリケーションやビジネス パートナーのエクストラネットに Dynamics 365 にパブリック web サイトを移行と、の顧客やパートナーのこれらのサードパーティの id プロバイダーを使用して続行します。Contoso Azure AD テナントとこれらのサードパーティの id プロバイダーとの間のフェデレーションを構成することによってこれを達成します。
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a>Contoso 社の Windows サーバーの AD フォレストのディレクトリの同期

Contoso 社は、パリのデータ センター内のサーバーのクラスターに AD の Azure 接続ツールを導入しました。Azure AD 接続では、contoso 社の Office 365、EMS、Dynamics 365 で、Azure サブスクリプションで共有する Azure AD テナント contoso.com フォレストの Windows サーバーの AD への変更を同期します。サブスクリプション、ライセンス、ユーザー アカウント、およびテナントの詳細については、[サブスクリプション、ライセンス、および Contoso 社のユーザー アカウント](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)を参照してください。
  
**図 3: contoso 社のディレクトリ同期のインフラストラクチャ**

![Contoso 社のディレクトリ同期インフラストラクチャ](images/Contoso_Poster/DirSync.png)
  
図 3 は、Azure AD テナントで Contoso 社の Windows Server AD フォレストを同期する Azure AD Connect を実行するサーバーのクラスターを示しています。
  
Contoso 社では、contoso 社の作業者のシングル サインオンを提供する、共通の認証を構成しました。Contoso.com フォレストの Windows サーバーの AD に既にサインインしているユーザーは、マイクロソフトの SaaS や PaaS クラウド リソースをアクセスする場合、いない求められますパスワードの。
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a>Contoso 社の認証トラフィックの地理的分布

Contoso 社は、モバイル ワーカーやリモート ワーカーのサポートを強化するには、地域のオフィスでの認証サーバーのセットを導入しました。このインフラストラクチャでは、負荷分散し、共通の Azure AD テナントを使用しているマイクロソフトのクラウド サービスにアクセスするためのユーザーの資格情報を認証するとき、冗長性とパフォーマンスの向上を提供します。
  
認証要求の負荷を分散するために、Contoso 社は、パフォーマンス ルーティング方法を使用するプロファイルを使用して Azure Traffic Manager を構成しました。この方法では、認証クライアントを地域の最も近い認証サーバーのセットにルーティングします。  
  
**地域オフィスの認証トラフィックの地理的分布を図 4:**

![Contoso 社の支社のための認証トラフィックの地理的分布](images/Contoso_Poster/Auth_GeoDist.png)
  
図 4 では、地域のオフィスでのクライアント コンピューター、Azure Traffic Manager、および認証サーバーのレイヤーを示します。それぞれの地域のオフィスは Web プロキシおよび AD FS サーバーを使用して、Windows Server AD ドメイン コントローラーとユーザーの資格情報を認証します。
  
認証プロセスの例:
  
1. クライアント コンピューターなどの通信の web ページに Office 365 テナントにヨーロッパで (sharepoint.contoso.com) を開始します。
    
2. Office 365 は、認証の証明を送信する要求を送り返します。要求には、認証のために連絡する URL が含まれています。
    
3. クライアント コンピューターは、URL 内の DNS 名を IP アドレスに解決しようとします。
    
4. Azure Traffic Manager は DNS クエリを受信し、クライアント コンピューターに最も近い地域オフィスの Web アプリケーション プロキシ サーバーの IP アドレスを持つクライアント コンピューターに応答します。
    
5.  クライアント コンピューターでは、AD FS サーバーに要求を転送する、web のアプリケーションのプロキシ サーバーに認証要求を送信します。
    
6. AD FS サーバーは、クライアント コンピューターからユーザー資格情報を要求します。
    
7. クライアント コンピューターは、ユーザーに確認せずにユーザー資格情報を送信します。
    
8. AD FS サーバーは、地域オフィスの Windows Server AD ドメイン コントローラーによって資格情報を検証し、クライアント コンピューターにセキュリティ トークンを返します。
    
9. クライアント コンピューターは、セキュリティ トークンを Office 365 に送信します。
    
10. 検証に成功したら、Office 365 はセキュリティ トークンをキャッシュし、手順 1 で要求された Web ページをクライアント コンピューターに送信します。
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a>Azure IaaS における本社の認証インフラストラクチャの冗長性

15,000 の作業者を含むパリ本社のリモートおよびモバイル ワーカーの冗長性を提供する、contoso 社は、アプリケーション プロキシと Azure IaaS に AD FS サーバーの 2 番目のセットを導入しました。
  
**Azure IaaS に冗長化された認証インフラストラクチャを図 5:**

![パリ本社の Azure IaaS における冗長認証インフラストラクチャ](images/Contoso_Poster/Paris_Auth_Redun.png)
  
図 5 は、DMZ にある Web プロキシと AD FS サーバー、およびクロスプレミスの Azure 仮想ネットワークごとの追加のセットを示しています。
  
本社 DMZ 内の主要な認証サーバーが利用できなくなると、IT スタッフは Azure IaaS で展開されている冗長セットに切り替えます。パリのオフィスのコンピューターからの後続の認証要求は、可用性の問題が修正されるまで Azure IaaS のセットを使用します。
  
切り替えを行うために、Contoso 社はパリ地域の Azure Traffic Manager プロファイルを更新して、Web アプリケーション プロキシに次の異なる IP アドレスのセットを使用します。
  
- DMZ の認証サーバーが使用できる場合は、DMZ 内のサーバーの IP アドレスを使用します。
    
- DMZ 認証サーバーを使用できない場合は、Azure IaaS のサーバーの IP アドレスを使用します。
    
## <a name="see-also"></a>See Also

[Microsoft Cloud の Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[エンタープライズ設計者の識別情報をマイクロソフトのクラウド](http://aka.ms/cloudarchidentity)
  
[Office 365 の ID とデバイス保護](http://aka.ms/o365protect_device)
  
[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)



