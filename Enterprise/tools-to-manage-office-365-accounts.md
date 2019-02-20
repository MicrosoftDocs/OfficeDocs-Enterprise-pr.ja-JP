---
title: Office 365 アカウントを管理するツール
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
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
description: 'Office 365 ユーザーを管理するためにどのようなツールを使用するか、およびどのように使用できるかについては、ユーザー id の管理方法によって異なります。 '
ms.openlocfilehash: e13b6a998aa6de433d85ef3be60f08703eb914d4
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085386"
---
# <a name="tools-to-manage-office-365-accounts"></a>Office 365 アカウントを管理するツール

構成に応じて、さまざまな方法で Office 365 ユーザーを管理することができます。Office 365 管理センター、Windows PowerShell、オンプレミスディレクトリ、または Azure Active directory 管理ポータルでユーザーを管理できます。 

Office 365 を購入するとすぐに、管理センターと Windows PowerShell を使用してアカウントを管理できるようになります。クラウド id を管理する際には、組織内のすべてのユーザーが Office 365 に対して個別のユーザー ID とパスワードを使用します。オンプレミスのインフラストラクチャと統合して、ユーザーアカウントを Office 365 と同期させる場合は、Azure Active Directory Connect を使用して id の同期を提供し、必要に応じてパスワード同期を提供できます。または、完全シングルサインオン機能。
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>ユーザーアカウントを管理する場所と方法を計画します。

ユーザーアカウントを管理する場所と方法は、Office 365 で使用する id モデルによって異なります。これらのモデル全体は、クラウド認証とフェデレーション認証です。
  
### <a name="cloud-authentication"></a>クラウド認証

- [office 365 Identity](about-office-365-identity.md) -ユーザーの作成と管理 office 365 管理センターでは、Windows PowerShell または Azure Active Directory を使用してユーザーを管理することもできます。
- [シームレスなシングルサインオンを使用したパスワードハッシュ同期](about-office-365-identity.md)Azure AD でオンプレミスのディレクトリオブジェクトの認証を有効にする最も簡単な方法です。パスワードハッシュ同期 (phs) を使用して、オンプレミスの Active Directory ユーザーアカウントオブジェクトを Office 365 と同期し、オンプレミスでユーザーを管理します。 
- [シームレスなシングルサインオンを使用したパススルー認証](about-office-365-identity.md)-1 つまたは複数のオンプレミスサーバーで実行されているソフトウェアエージェントを使用して Azure AD 認証サービスのパスワード検証を行い、ユーザーの直接の確認をオンプレミスの Active Directory。 
    
### <a name="federated-authentication"></a>フェデレーション認証

- [office 365 id](about-office-365-identity.md) -主に、より複雑な認証要件を持つ大規模なエンタープライズ組織の場合、社内ディレクトリオブジェクトは Office 365 と同期され、ユーザーアカウントは社内で管理されます。 
- [サードパーティの認証および id プロバイダー](about-office-365-identity.md) -オンプレミスのディレクトリオブジェクトは、Office 365 に同期される場合があります。また、クラウドリソースへのアクセスは、主にサードパーティの id プロバイダー (IdP) によって管理されます。 
    
## <a name="managing-accounts"></a>アカウントの管理

組織がアカウントを作成および管理する方法を決定するときは、次の点を考慮してください。
  
- Office 365 とオンプレミスのディレクトリ間で id を接続するには、ディレクトリ同期ソフトウェアをオンプレミス環境のサーバーにインストールする必要があります。
- SSO オプションを含むディレクトリ同期オプションでは、オンプレミスのディレクトリ属性が標準に適合している必要があります。ディレクトリ同期を使用して、「 [Office 365 へのディレクトリ同期を通してユーザーをプロビジョニングする](prepare-for-directory-synchronization.md)」で説明されている、ディレクトリで使用されている属性と、必要に応じてクリーンアップを実行する方法について説明します。idfix を使用してディレクトリのクリーンアップを自動化する方法については[、「Install and run the Office 365 idfix tool](install-and-run-idfix.md) 」を参照してください。 
    
## <a name="plan-how-you-are-going-to-create-office-365-accounts"></a>Office 365 アカウントを作成する方法を計画する
次の表に、さまざまなアカウント管理ツールを示します。
    
|**オプション**|**メモ**|
|:-----|:-----|
|**Office 365 admin center** | - [Office 365 にユーザーを個別にまたは一括して追加する-管理者向けヘルプ](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> -ユーザーアカウントを追加および変更するための簡単な web インターフェイスを提供します。 <br> ディレクトリ同期が有効になっている場合、ユーザーの変更には使用できません (場所およびライセンスの割り当てを設定できます)。 <br> -SSO オプションでは使用できません。 <br> |
|**Windows PowerShell** | - [Windows PowerShell を使用して Office 365 を管理する](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> -Windows PowerShell スクリプトを使用して、ユーザーを一括ユーザーで追加できるようにします。 <br> -アカウントの作成方法に関係なく、アカウントに場所とライセンスを割り当てるために使用できます。 <br> |
|**一括インポート** | - [Office 365 に同時に複数のユーザーを追加する-管理者ヘルプ](add-several-users-at-the-same-time.md) <br> -CSV ファイルをインポートして、Office 365 にユーザーのグループを追加できるようにします。 <br> -SSO オプションでは使用できません。 <br> |
|**Azure Active Directory** | -Office 365 サブスクリプションを使用して、Azure Active Directory の無料エディションを取得します。-クラウドユーザーのセルフサービスによるパスワードのリセットなどの機能を実行したり、無料版を使用してサインインページとアクセスパネルページをカスタマイズしたりすることができます。<br> -拡張機能を利用するには、basic edition または premium edition にアップグレードします。サポートされている機能の一覧については、「 [Azure Active Directory のエディション](https://go.microsoft.com/fwlink/p/?LinkId=698465)」を参照してください。<br> |
|**ディレクトリ同期** | - [オンプレミス id と Azure Active Directory の統合](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> -パスワード同期の有無にかかわらずディレクトリ同期を行うには、 [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537)を使用します。  <br>  -複数のフォレストおよび SSO オプションの場合は、 [Azure AD Connect のカスタムインストール](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。 <br> -SSO を有効にするために必要なインフラストラクチャを提供します。 <br> -多くのハイブリッドシナリオで必要 (段階的な移行、ハイブリッド Exchange) <br> -セキュリティおよびメールが有効なグループをオンプレミスのディレクトリから同期します。 <br> |
   
Office 365 にユーザーアカウントを追加する方法に関係なく、ライセンスの割り当て、場所の指定など、いくつかのアカウント機能を管理する必要があります。これらの機能は、office 365 管理センターから長期間において管理することも、 [office 365 PowerShell を使用してユーザーアカウントを作成](https://go.microsoft.com/fwlink/p/?LinkId=717083)することもできます。
    
office 365 管理センターを使用してすべてのユーザーの追加と管理を選択する場合は、office 365 アカウントを作成するときと同時に、場所を指定してライセンスを割り当てます。そのため、計画はあまり必要ありません。
    
> [!IMPORTANT]
> office 365 で、ライセンスを割り当てずにアカウントを作成する (SharePoint Online の場合) とは、アカウント所有者が office 365 ポータルを表示できるが、会社のサブスクリプション内のサービスにアクセスできないことを意味します。場所とライセンスを割り当てた後、割り当てたサービスにアカウントがレプリケートされます。ユーザーは、自分のアカウントにサインインして、自分に割り当てられているサービスを使用することができます。