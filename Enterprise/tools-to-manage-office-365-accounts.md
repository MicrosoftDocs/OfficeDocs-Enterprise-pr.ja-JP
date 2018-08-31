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
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: '使用して、Office 365 のユーザーとユーザーの id を管理する方法に依存して使用することができる方法を管理するには、どのようなツールについて説明します。 '
ms.openlocfilehash: 62467fb031090a521d0b9e067582b56fabe9e5fd
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541580"
---
# <a name="tools-to-manage-office-365-accounts"></a>Office 365 アカウントを管理するツール

構成によって、さまざまな方法で Office 365 のユーザーを管理できます。Office 365 管理センターで、Windows PowerShell では、設置型、ディレクトリ、または Active Directory の Azure 管理ポータルでユーザーを管理することができます。 

Office 365 を購入するとすぐに、管理センターと Windows PowerShell は、アカウントを管理するために使用できます。クラウド id を管理する場合、組織内のすべての人は、個別のユーザー ID とパスワード Office 365 のです。オンプレミス インフラストラクチャと統合し、ユーザー アカウントが存在する場合は、Office 365 と同期して、使用できます Azure Active Directory の接続 id の同期を提供し、必要に応じてパスワード同期を提供したり、完全なシングル サインオン機能します。
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>ユーザー アカウントを管理する場所と方法の計画

ユーザー アカウントを管理することができます場所や方法は、Office 365 を使用する識別情報モデルによって異なります。2 つの全体的なモデルは、クラウドの認証と統合認証です。
  
### <a name="cloud-authentication"></a>クラウドの認証

<<<<<<< 見出し
- [クラウド認証](about-office-365-identity.md#cloud-authentication)- を作成し、Office 365 の管理センターでユーザーの管理、ユーザーを管理するために、Windows PowerShell、または Active Directory の Azure を使用することもできます。 
    
=======
- [Office 365 の Id](about-office-365-identity.md)を作成し、Office 365 の管理センターでユーザーの管理、ユーザーを管理するために、Windows PowerShell、または Active Directory の Azure を使用することもできます。
>>>>>>> robmazz 変換
- [シームレスなシングル サインオンとパスワードのハッシュが同期](about-office-365-identity.md)の Azure AD で設置ディレクトリ オブジェクトの認証を有効にする簡単な方法です。パスワード ハッシュ (PHS)、同期に、オンプレミスの Active Directory ユーザー アカウント オブジェクトを Office 365 と同期して、ユーザーの設置型の管理します。 
- Azure AD の認証サービスと直接ユーザーを検証するためにソフトウェア エージェントは、1 つまたは複数のオンプレミスのサーバーで実行されているを使用して単純なパスワードの検証を提供する[シームレスなシングル サインオンでのパススルー認証](about-office-365-identity.md)が、Active Directory を設置します。 
    
### <a name="federated-authentication"></a>フェデレーション認証

<<<<<<< 見出し
- [シームレスなシングル サインオンでのパススルー認証](about-office-365-identity.md#pass-through-authentication-with-seamless-single-sign-on)をより複雑な認証の要件を持つ大規模な企業組織を主に設置型のディレクトリ オブジェクトは、Office 365 と同期し、ユーザー アカウントを管理設置します。 
    
=======
- [Office 365 の Id](about-office-365-identity.md)でさらに複雑な認証の要件を持つ大規模な企業組織の主な設置ディレクトリ オブジェクトは、Office 365 と同期され、ユーザー アカウントは、管理対象の設置型です。 
>>>>>>> robmazz 変換
- [サード ・ パーティ製の認証と id プロバイダー](about-office-365-identity.md)の設置型のディレクトリ オブジェクトが Office 365 に同期させることがあり、クラウドのリソースへのアクセスは、主にサードパーティの id プロバイダー (IdP) によって管理されます。 
    
## <a name="managing-accounts"></a>アカウントを管理します。

組織は作成され、アカウントの管理方法を決定するときは、以下を考慮します。
  
- ディレクトリ同期ソフトウェアは、Office 365 との設置ディレクトリとの間の id を接続するのには、オンプレミス環境でサーバーにインストールする必要があります。
- SSO オプションを含めて、ディレクトリ同期のオプションでは、オンプレミスのディレクトリの属性は、基準を満たす必要があります。[Office 365 ディレクトリ同期によってユーザーを提供する準備](prepare-for-directory-synchronization.md)は、ディレクトリにどのような属性を使用して、(存在する場合) は、どのようなクリーンアップが必要なの詳細を説明します。IdFix を使用して、ディレクトリのクリーンアップを自動化する方法について[をインストールして Office 365 の IdFix ツールの実行](install-and-run-idfix.md)を参照してください。 
    
## <a name="plan-how-you-are-going-to-create-office-365-accounts"></a>Office 365 アカウントの作成を行う方法を計画します。
次の表は、別のアカウントの管理ツールを一覧します。
    
|**オプション**|**メモ**|
|:-----|:-----|
|**Office 365 管理センター** | - [ユーザー個別にまたは一括で Office 365 に追加の管理のヘルプ](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> -を追加し、ユーザー アカウントを変更する単純な web インターフェイスを提供します。 <br> がディレクトリ同期が有効になっている場合は、ユーザーを変更するのには使用不可 (場所およびライセンスの割り当てを設定することができます)。 <br> が SSO オプションを使用して使用不可。 <br> |
|**Windows PowerShell** | - [Windows PowerShell では、Office 365 を管理します。](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> -を使用すると、Windows PowerShell スクリプトを使用してユーザーを一括でユーザーを追加できます。 <br> がアカウントの作成方法に関係なく、アカウントの場所およびライセンスを割り当てるには使用できます。 <br> |
|**一括インポート** | - [Office 365 の管理者のヘルプを同時に複数のユーザーを追加します。](add-several-users-at-the-same-time.md) <br> -使用すると、Office 365 にユーザーのグループを追加するのには CSV ファイルをインポートできます。 <br> が SSO オプションを使用して使用不可。 <br> |
|**Azure Active Directory** | -は、Office 365 サブスクリプションで、Azure Active Directory の無料版を取得します。-セルフ サービス パスワードのリセット、クラウド ユーザーとサインインし、アクセス パネルのページのカスタマイズの無料版を使用して、ような機能を実行できます。<br> -拡張機能を取得するには基本的なエディション、またはプレミアム ・ エディションのいずれかにアップグレードできます。サポートされている機能の一覧については、 [Azure Active Directory のエディション](https://go.microsoft.com/fwlink/p/?LinkId=698465)を参照してください。<br> |
|**ディレクトリ同期** | - [Azure Active Directory で、設置型の id を統合します。](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> -ディレクトリ同期パスワード同期の有無にかかわらず、[高速の設定を使用して、Azure の AD 接続](https://go.microsoft.com/fwlink/p/?LinkID=698537)を使用します。  <br>  -複数のフォレストと SSO のオプションの[カスタム インストールの Azure AD 接続](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。 <br> SSO を有効にするために必要なインフラストラクチャを提供します。 <br> 必要な多くのハイブリッド シナリオ (段階的な移行、ハイブリッド交換)。 <br> -セキュリティおよび設置ディレクトリからのメールが有効なグループを同期します。 <br> |
   
Office 365 にユーザー アカウントを追加する方法に関係なく、場所を指定する、ライセンスを割り当てるなど、いくつかのアカウント機能を管理するためにする必要があります。これらの機能から管理できる長期的な Office 365 の管理者センターまたは[Office 365 の PowerShell でのユーザー アカウントを作成](https://go.microsoft.com/fwlink/p/?LinkId=717083)することもできます。
    
追加し、Office 365 管理センターを使用してすべてのユーザーを管理する場合は、場所を指定して Office 365 のアカウントを作成すると同時にライセンスを割り当てます。その結果、あまり多くない計画が必要です。
    
> [!IMPORTANT]
> (SharePoint Online に、たとえば) のライセンスを割り当てることには、Office 365 ポータルですがアカウントの所有者を表示することを意味せずに Office 365 のアカウントを作成すると、会社のサブスクリプション内のサービスのいずれかアクセスできません。場所と、ライセンスを割り当てると、サービスまたはサービスに割り当てたアカウントが複製されます。ユーザーは、自分のアカウントにサインインし、それらに割り当てられたサービスを使用できます。