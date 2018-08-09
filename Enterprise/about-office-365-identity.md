---
title: Office 365 の id と Azure Active Directory を理解します。
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/1/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Office 365 のユーザー id を管理する方法について説明します。
ms.openlocfilehash: cdd0ab2306e9a966f308006761a83cda8989b898
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "22213125"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Office 365 の id と Azure Active Directory を理解します。

Office 365 は、ユーザーを管理するのにクラウド ベースのユーザー id と認証サービス Azure Active Directory (AD の Azure) を使用します。選択する id 管理は、設置型の組織と Office 365 の間で構成されている場合は、初期の決定であり、クラウド インフラストラクチャの基盤の 1 つは。後でこの構成を変更することは難しい場合があるため、組織のニーズに最適を決定するためのオプションを慎重に検討します。設定し、自動的にユーザー アカウントを管理するのには Office 365 で 2 つの主要な認証モデルから選択することができます。クラウドの認証と統合認証します。
  
認証と id 取得するためにモデルを慎重に検討する重要であり、実行中です。時間、既存の複雑性、および実装し、それぞれの認証と id のオプションを維持するコストを考えてください。これらの要素は組織ごとに異なります展開に使用する認証と識別情報モデルを選択するためのユーザー オプションの重要な概念を理解する必要があります。
  
## <a name="cloud-authentication"></a>クラウドの認証

によって Office 365 でユーザーの認証と id のサービスを管理するためのいくつかのオプションがある場合は、または、既存 Active Directory 環境の設置型を持っていない、します。
  
### <a name="cloud-only"></a>クラウドのみ

クラウド専用モデルでは、Office 365 でユーザーのアカウントは、のみを管理します。設置必要はありません。すべてによって処理される、クラウドで Azure AD。作成し、Office 365 の管理センターでユーザーを管理するか、Windows PowerShell を使用して[PowerShell コマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=698471)と id と認証は完全にクラウドで Azure AD。クラウド専用のモデルは、通常、適切な選択肢の場合です。 
  
- 他のオンプレミス ユーザーのディレクトリがあるありません。
    
- オンプレミスで非常に複雑なディレクトリがあるし、単に統合できるので、作業は避けたいです。
    
- 設置型の既存のディレクトリがあるが、試用版または Office 365 のパイロットを実行します。以降では、オンプレミス ディレクトリに接続する準備ができたら、クラウド ユーザーはオンプレミス ユーザーを照合できます。
    
クラウド id を使用して開始するには、[ビジネス向けの Office 365 のセットアップ](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)を参照してください。
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>シームレスなシングル サインオンとパスワード ハッシュの同期

Azure AD で設置ディレクトリ オブジェクトの認証を有効にする最も簡単な方法です。パスワード ハッシュ (PHS)、同期に、オンプレミスの Active Directory ユーザー アカウント オブジェクトを Office 365 と同期して、ユーザーの設置型の管理します。ユーザーのパスワードのハッシュは、ユーザーが、同じパスワードを設置できるようにし、雲の中に、オンプレミスの Active Directory から Azure AD に同期されます。パスワードが変更された、設置型をリセットするときは、クラウド リソースおよび設置型リソースのユーザーが同じパスワードを常に使用できるように Azure AD に新しいパスワードのハッシュが同期されます。パスワードは Azure AD に送信またはクリア テキストで Azure AD に格納しないでください。Azure AD、アイデンティティの保護などのいくつかのプレミアム機能には、どの認証方法が選択されている PHS が必要です。シームレスなシングル サインオン、ユーザーに自動的にサインインしている Azure の AD に、企業内のデバイス上にあるし、企業ネットワークに接続されています。
  
[パスワード ハッシュの同期を選択して](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn)、[シームレスなシングル サインオン](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-sso)の詳細を表示します。
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>シームレスなシングル サインオンでのパススルー認証

Azure AD 認証サービスが、オンプレミスの Active Directory に直接ユーザーを検証するために 1 つまたは複数のオンプレミスのサーバーで実行されているソフトウェア ・ エージェントを使用して単純なパスワードの検証を提供します。パススルー認証 (PTA) では、オンプレミスの Active Directory ユーザー アカウント オブジェクトを Office 365 と同期して、ユーザーの設置型の管理します。により、ユーザーは、オンプレミスと Office 365 のリソースとアプリケーションの両方に設置型のアカウントとパスワードを使用してにサインインします。この構成では、Office 365 のパスワード ハッシュを送信することがなく、オンプレミスの Active Directory に対して直接ユーザーのパスワードを検証します。パスワード ポリシー、およびログオン時間は、この認証方式を使用は、オンプレミスのユーザー アカウントをすぐに適用するセキュリティ要件を持つ企業を示しています。シームレスなシングル サインオン、ユーザーに自動的にサインインしている Azure の AD に、企業内のデバイス上にあるし、企業ネットワークに接続されています。
  
[パススルー認証を選択して](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn)、[シームレスなシングル サインオン](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-sso)の詳細について説明します。
  
## <a name="federated-authentication-options"></a>フェデレーションの認証オプション

既存 Active Directory 環境設置の場合は、Office 365 でユーザーの認証と id のサービスを管理するためにフェデレーション認証を使用して、ディレクトリを Office 365 に統合できます。
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Active Directory フェデレーション サービス (AD FS) のフェデレーション id

複雑な認証要件を持つ大規模な企業組織では、主に設置型のディレクトリ オブジェクトは、Office 365 と同期し、ユーザー アカウントは、管理対象の設置型です。AD FS では、ユーザーがある、同じパスワード、オンプレミスとクラウドで、もう一度サインインして Office 365 を使用するにはありません。このフェデレーション認証モデルは、スマート カード ベースの認証またはサード ・ パーティ製の多要素認証などの他の認証要件を提供することができ、組織で、認証の要件がある場合に通常必要とAzure AD でネイティブにサポートされています。
  
[AD FS のフェデレーション id の選択](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn)の詳細を表示します。
  
### <a name="third-party-authentication-and-identity-providers"></a>サード ・ パーティ製の認証と id プロバイダー

設置ディレクトリ オブジェクトは、Office 365 に同期させる可能性があり、クラウド リソースへのアクセスは、主に、サードパーティの id プロバイダー (IdP) によって管理されます。組織は、フェデレーションのサード ・ パーティ製ソリューションを使用している場合を構成できますサインオン ソリューションを Office 365 のフェデレーションのサード ・ パーティ製ソリューションが Azure AD と互換性があります。
  
[Azure AD フェデレーションの互換性](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)の詳細を表示します。
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Office 365 の id と認証を構成します。

設置ディレクトリは、Office 365 と Azure AD との統合が単純化され[Azure AD 接続](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect)とします。Azure AD 接続は、ディレクトリに接続する最良の方法で、ユーザーは、クラウドを同期するのには組織では、マイクロソフトの推奨です。
  
Azure AD アドバイザーを使用することもできます: [Azure AD 接続アドバイザー](https://aka.ms/aadconnectpwsync) [AD FS 展開のアドバイザー](https://aka.ms/adfsguidance)では、 [Azure AD のプレミアム ・ セットアップ ・ ガイド](https://aka.ms/aadpguidance)です。
  
## <a name="video-training"></a>ビデオ ・ トレーニング

詳細については、ビデオのコースを参照してください[Office 365: Azure を使用してユーザーの管理の AD 接続](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)、LinkedIn の学習で。
  
## <a name="see-also"></a>関連項目

[Office 365 へのディレクトリ同期を通してユーザーをプロビジョニングするための準備](https://support.office.com/article/prepare-to-provision-users-through-directory-synchronization-to-office-365-01920974-9e6f-4331-a370-13aea4e82b3e)
  
[PowerShell を Office 365 サービスに接続します。](https://support.office.com/article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
  
[Office 365 のディレクトリ同期の問題を解決します。](https://support.office.com/article/fixing-problems-with-directory-synchronization-for-office-365-79c43023-5a47-45ae-8068-d8a26eee6bc2d)
  

