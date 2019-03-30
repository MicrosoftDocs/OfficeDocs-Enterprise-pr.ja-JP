---
title: Office 365 ID と Azure Active Directory について
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Office 365 でユーザー id を管理する方法について説明します。
ms.openlocfilehash: c9dff7e17e4c0dcceb7cdeab86c1acdd40e01205
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001560"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Office 365 ID と Azure Active Directory について

Office 365 は、クラウドベースのユーザー id と認証サービス azure Active Directory (azure AD) を使用してユーザーを管理します。 オンプレミスの組織と Office 365 の間で id 管理が構成されているかどうかを選択することは、クラウドインフラストラクチャの基礎の1つである初期の決定です。 後でこの構成を変更するのは困難な場合があるため、組織のニーズに最適に動作する方法を決定するオプションを慎重に検討してください。 Office 365 では、2つの主要な認証モデルから選択して、ユーザーアカウントの設定と管理を行うことができます。**クラウド認証**と**フェデレーション認証**。
  
これらの認証と id モデルのどちらを使用して起動し、実行するのかを慎重に検討することが重要です。 各認証および id オプションを実装して管理するための時間、既存の複雑さ、コストについて考えてください。 これらの要素は、すべての組織によって異なります。また、展開に使用する認証と id モデルを選択するのに役立つ、id オプションの主要な概念を理解しておく必要があります。
  
## <a name="cloud-authentication"></a>クラウド認証

オンプレミスの既存の Active Directory 環境を所有しているかどうかに応じて、Office 365 を使用してユーザーの認証と id サービスを管理するためのいくつかのオプションがあります。
  
### <a name="cloud-only"></a>クラウド専用

クラウドのみのモデルでは、Office 365 でユーザーアカウントを管理します。 オンプレミスサーバーは必要ありません。これはすべて Azure AD によってクラウドで処理されます。 [Microsoft 365 管理センター](https://admin.microsoft.com)でユーザーを作成して管理するか、Windows powershell [powershell コマンドレット](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell)を使用して id と認証が Azure AD によってクラウド内で完全に処理されます。 通常、クラウドのみのモデルは次のような場合に適しています。 
  
- その他のオンプレミスのユーザーディレクトリはありません。
    
- 非常に複雑なオンプレミスのディレクトリを使用していて、単にそれと統合する作業を回避したいと考えています。
    
- 既存のオンプレミスディレクトリがありますが、Office 365 の試用版またはパイロット版を実行したい場合。 後で、オンプレミスのディレクトリに接続する準備が整ったときに、クラウドユーザーをオンプレミスのユーザーに対応させることができます。
    
クラウド id を使い始めるには、「 [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)」を参照してください。
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>シームレスなシングルサインオンを使用したパスワードハッシュ同期

Azure AD でオンプレミスのディレクトリオブジェクトの認証を有効にする最も簡単な方法です。 パスワードハッシュ同期 (phs) を使用して、オンプレミスの Active Directory ユーザーアカウントオブジェクトを Office 365 と同期し、オンプレミスでユーザーを管理します。 ユーザーパスワードのハッシュは、オンプレミスの Active Directory から Azure AD に同期されるため、ユーザーは社内とクラウドの両方で同じパスワードを使用できます。 パスワードが変更されるか、オンプレミスでリセットされると、新しいパスワードハッシュが Azure AD に同期されるため、ユーザーは常にクラウドリソースとオンプレミスのリソースに対して同じパスワードを使用できます。 パスワードが azure ad に送信されることや、クリアテキストで azure ad に保存されることはありません。 id 保護などの Azure AD の一部のプレミアム機能は、どの認証方法が選択されているかに関係なく、phs を必要とします。 シームレスなシングルサインオンを使用すると、ユーザーが会社のデバイスを使用して企業ネットワークに接続されている場合に、Azure AD に自動的にサインインします。
  
[パスワードハッシュ同期](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)および[シームレスなシングルサインオンの](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)選択の詳細について説明します。
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>シームレスなシングルサインオンを使用したパススルー認証

1つまたは複数のオンプレミスサーバーで実行されているソフトウェアエージェントを使用して、社内の Active Directory と直接ユーザーを検証することにより、Azure AD 認証サービスの簡単なパスワード検証を提供します。 パススルー認証 (pta) を使用して、オンプレミスの Active Directory ユーザーアカウントオブジェクトを Office 365 と同期し、オンプレミスでユーザーを管理します。 オンプレミスのアカウントとパスワードを使用して、オンプレミスと Office 365 の両方のリソースとアプリケーションの両方にサインインすることをユーザーに許可します。 この構成では、Office 365 にパスワードハッシュを送信せずに、ユーザーのパスワードをオンプレミスの Active Directory に対して直接検証します。 オンプレミスのユーザーアカウントの状態、パスワードポリシー、およびログオン時間を即時に適用するセキュリティ要件を持つ企業は、この認証方法を使用します。 シームレスなシングルサインオンを使用すると、ユーザーが会社のデバイスを使用して企業ネットワークに接続されている場合に、Azure AD に自動的にサインインします。
  
[パススルー認証](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)および[シームレスなシングルサインオンの](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)選択の詳細について説明します。
  
## <a name="federated-authentication-options"></a>フェデレーション認証オプション

オンプレミスの既存の Active Directory 環境がある場合は、フェデレーション認証を使用して office 365 をディレクトリと統合し、office 365 でユーザーの認証と id サービスを管理することができます。
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Active Directory フェデレーションサービス (AD FS) を使用したフェデレーション id

主に、より複雑な認証要件を持つ大規模なエンタープライズ組織では、社内ディレクトリオブジェクトは Office 365 と同期され、ユーザーアカウントは社内で管理されます。 AD FS を使用すると、ユーザーは社内とクラウドの両方で同じパスワードを持つことができ、Office 365 を使用するために再度サインインする必要はありません。 このフェデレーション認証モデルでは、スマートカードベースの認証やサードパーティの多要素認証など、追加の認証要件を提供できます。通常は、組織で認証要件がある場合に必要になります。Azure AD ではネイティブにサポートされていません。
  
[AD FS でフェデレーション id を選択](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)する方法について説明します。
  
### <a name="third-party-authentication-and-identity-providers"></a>サードパーティの認証および id プロバイダー

オンプレミスのディレクトリオブジェクトは Office 365 に同期され、クラウドリソースアクセスは主にサードパーティの id プロバイダー (IdP) によって管理されます。 組織でサードパーティのフェデレーションソリューションを使用している場合は、サードパーティ製のフェデレーションソリューションが Azure AD と互換性があることを前提として、Office 365 でそのソリューションを使用してサインオンを構成できます。
  
詳細については、「 [Azure AD フェデレーションの互換性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)」を参照してください。
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Office 365 を使用して id と認証を構成する

オンプレミスディレクトリと Office 365 との統合は、 [azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)によって簡略化されています。 Azure AD Connect は、ディレクトリを接続するための最適な方法であり、組織がユーザーをクラウドに同期するための Microsoft の推奨事項です。
  
azure ad[接続アドバイザー](https://aka.ms/aadconnectpwsync)、 [ad FS 展開アドバイザー](https://aka.ms/adfsguidance)、および[azure ad Premium セットアップガイド](https://aka.ms/aadpguidance)を使用することもできます。
  
## <a name="video-training"></a>ビデオ トレーニング

詳細については、「 [Office 365: Azure AD Connect を使用して id を管理](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)する」を参照してください。
