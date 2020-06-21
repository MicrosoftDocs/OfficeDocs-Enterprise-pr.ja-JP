---
title: Microsoft 365 アカウントを管理するためのツール
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Microsoft 365 ユーザーを管理するためにどのようなツールを使用するか、およびどのように使用できるかについては、ユーザー id の管理方法によって異なります。 '
ms.openlocfilehash: 6decaa941f5997cd2ee1617f428f93985428dde4
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774502"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a>Microsoft 365 アカウントを管理するためのツール

構成に応じて、さまざまな方法で Microsoft 365 ユーザーを管理することができます。 [Microsoft 365 管理センター](https://admin.microsoft.com)、Windows PowerShell、社内ディレクトリ、または Azure Active directory 管理ポータルでユーザーを管理できます。 Microsoft 365 を購入すると、管理センターと Windows PowerShell を使用してアカウントを管理できるようになります。 クラウド id を管理する場合、組織内のすべてのユーザーには、Microsoft 365 に対して個別のユーザー ID とパスワードがあります。 オンプレミスのインフラストラクチャと統合し、ユーザーアカウントを Microsoft 365 と同期させる場合は、Azure Active Directory Connect を使用して id の同期を提供し、必要に応じてパスワード同期または完全なシングルサインオン機能を提供することができます。
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>ユーザーアカウントを管理する場所と方法を計画します。

ユーザーアカウントを管理する場所と方法は、Microsoft 365 で使用する id モデルによって異なります。 これらのモデル全体は、クラウド認証とフェデレーション認証です。
  
### <a name="cloud-authentication"></a>クラウド認証

- クラウド認証-管理センターでユーザーを作成および管理します。また、Windows PowerShell または Azure Active Directory を使用してユーザーを管理することもできます。 
    
- シームレスなシングルサインオンを使用したパスワードハッシュ同期 Azure AD でオンプレミスのディレクトリオブジェクトの認証を有効にする最も簡単な方法です。 パスワードハッシュ同期 (PHS) を使用して、オンプレミスの Active Directory ユーザーアカウントオブジェクトを Microsoft 365 と同期し、オンプレミスでユーザーを管理します。 
    
- シームレスなシングルサインオンを使用したパススルー認証-1 つ以上のオンプレミスサーバー上で実行されているソフトウェアエージェントを使用して、オンプレミスの Active Directory と直接ユーザーを検証することで、Azure AD 認証サービスの簡単なパスワード検証を提供します。 
    
### <a name="federated-authentication"></a>フェデレーション認証

- フェデレーション認証オプション-主に、より複雑な認証要件を持つ大規模なエンタープライズ組織では、オンプレミスのディレクトリオブジェクトは Microsoft 365 と同期され、ユーザーアカウントは社内で管理されます。 
    
- [サードパーティの認証および id プロバイダー](about-office-365-identity.md) -オンプレミスのディレクトリオブジェクトは、Microsoft 365 に同期される場合があります。また、クラウドリソースへのアクセスは、主にサードパーティの id プロバイダー (IdP) によって管理されます。 
    
## <a name="managing-accounts"></a>アカウントの管理

組織がアカウントを作成および管理する方法を決定するときは、次の点を考慮してください。
  
- Microsoft 365 とオンプレミスのディレクトリ間で id を接続するには、ディレクトリ同期ソフトウェアを社内環境内のサーバーにインストールする必要があります。
    
- SSO オプションを含むディレクトリ同期オプションでは、オンプレミスのディレクトリ属性が標準に適合している必要があります。 ディレクトリ同期を使用して、「 [Microsoft 365 へのディレクトリ同期によってユーザーをプロビジョニングする](prepare-for-directory-synchronization.md)」で説明されている、ディレクトリで使用されている属性と、必要に応じてクリーンアップを行う方法について説明します。 IdFix を使用してディレクトリのクリーンアップを自動化する方法について[は、「Microsoft 365 idfix ツールをダウンロードして実行](install-and-run-idfix.md)する」を参照してください。 
    
- Microsoft 365 アカウントを作成する方法を計画します。
    
    次の表に、さまざまなアカウント管理ツールを示します。
    
|**オプション**|**メモ**|
|:-----|:-----|
|管理センター  <br/> |[ユーザーを個別にまたは一括して追加する](https://docs.microsoft.com/microsoft-365/admin/add-users/add-users) <br/>  ユーザーアカウントを追加および変更するための簡単な web インターフェイスを提供します。  <br/>  ディレクトリ同期が有効になっている場合、ユーザーの変更には使用できません (場所およびライセンスの割り当てを設定できます)。  <br/>  SSO オプションを使用することはできません。  <br/> |
|Windows PowerShell  <br/> |[Windows PowerShell を使用して Microsoft 365 を管理する](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Windows PowerShell スクリプトを使用して、ユーザーを一括ユーザーで追加できるようにします。  <br/>  アカウントの作成方法に関係なく、アカウントに場所とライセンスを割り当てるために使用できます。  <br/> |
|一括インポート  <br/> |[同時に複数のユーザーを追加する](add-several-users-at-the-same-time.md) <br/>  CSV ファイルをインポートして、ユーザーのグループを Microsoft 365 に追加できるようにします。  <br/>  SSO オプションを使用することはできません。  <br/> |
|Azure Active Directory  <br/> |Microsoft 365 サブスクリプションを使用して、Azure Active Directory の無料エディションを入手できます。 クラウドユーザーのセルフサービスによるパスワードのリセットなどの機能を実行したり、無料版を使用してサインインページとアクセスパネルページをカスタマイズしたりすることができます。 拡張機能を利用するには、basic edition または premium edition のいずれかにアップグレードできます。 サポートされている機能の一覧については、「 [Azure Active Directory のエディション](https://go.microsoft.com/fwlink/p/?LinkId=698465)」を参照してください。  <br/> |
|ディレクトリ同期  <br/> |[オンプレミス id と Azure Active Directory の統合](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  パスワード同期の有無にかかわらずディレクトリ同期を行うには、 [AZURE AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537)を使用します。  <br/>  複数のフォレストおよび SSO オプションでは、 [AZURE AD Connect のカスタムインストール](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。  <br/>  SSO を有効にするために必要なインフラストラクチャを提供します。  <br/>  多くのハイブリッドシナリオに必要です。  <br/>  段階的な移行  <br/>  ハイブリッド Exchange  <br/>  オンプレミスのディレクトリからセキュリティおよびメールが有効なグループを同期します。  <br/> |
   
- ユーザーアカウントを Microsoft 365 に追加する方法に関係なく、ライセンスの割り当て、場所の指定など、いくつかのアカウント機能を管理する必要があります。 これらの機能は、管理センターから長期的に管理することも、 [Office 365 PowerShell を使用してユーザーアカウントを作成](https://go.microsoft.com/fwlink/p/?LinkId=717083)することもできます。
    
    管理センターを使用してすべてのユーザーの追加と管理を選択する場合は、Microsoft 365 アカウントを作成するときと同時に、場所を指定してライセンスを割り当てます。 そのため、計画はあまり必要ありません。
    
    > [!IMPORTANT]
    > Microsoft 365 で、ライセンスを割り当てずに (たとえば SharePoint Online に) アカウントを作成することは、アカウント所有者が Microsoft 365 管理センターを表示することはできますが、会社のサブスクリプション内のサービスにアクセスできないことを意味します。 場所とライセンスを割り当てた後、割り当てたサービスにアカウントがレプリケートされます。 ユーザーは、自分のアカウントにサインインして、自分に割り当てられているサービスを使用することができます。 
  
## <a name="next-steps"></a>次の手順

[Microsoft 365 とオンプレミス環境との統合](office-365-integration.md)
  
## <a name="see-also"></a>関連項目

[Microsoft 365 でユーザーとグループを管理する](https://docs.microsoft.com/microsoft-365/admin/add-users)
  

