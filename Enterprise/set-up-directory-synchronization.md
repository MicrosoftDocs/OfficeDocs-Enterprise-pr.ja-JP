---
title: Microsoft 365 のディレクトリ同期をセットアップする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/15/2020
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Microsoft 365 とオンプレミスの Active Directory との間のディレクトリ同期をセットアップする方法について説明します。
ms.openlocfilehash: 775ff04976c92d7e937ddc018e0e1dd617c8fca3
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735992"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>Microsoft 365 のディレクトリ同期をセットアップする

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Microsoft 365 では、Azure Active Directory (Azure AD) テナントを使用して、クラウドベースのリソースにアクセスするための id を認証およびアクセス許可用に保存および管理します。 

オンプレミスの Active Directory ドメインサービス (AD DS) がある場合は、AD DS のユーザーアカウント、グループ、および連絡先を Microsoft 365 サブスクリプションの Azure AD テナントと同期させることができます。 これは、Microsoft 365 のハイブリッド id です。 そのコンポーネントは次のとおりです。

![Microsoft 365 のディレクトリ同期のコンポーネント](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect はオンプレミスのサーバー上で実行され、AD DS を Azure AD テナントと同期します。 ディレクトリ同期と共に、次の認証オプションを指定することもできます。

- パスワードハッシュの同期 (PHS)

  Azure AD は認証自体を実行します。

- パススルー認証 (PTA)

  Azure AD は、AD DS で認証を実行しています。

- フェデレーション認証

  Azure AD は、別の id プロバイダーに接続するための認証を要求しているクライアントコンピューターをリダイレクトします。

詳細については、「[ハイブリッド id](plan-for-directory-synchronization.md) 」を参照してください。
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Azure AD Connect の前提条件を確認する

Microsoft 365 サブスクリプションを使用して、Azure AD サブスクリプションを無料で入手できます。 ディレクトリ同期をセットアップすると、オンプレミスのサーバーの1つに Azure AD Connect がインストールされます。
  
Microsoft 365 については、次のことを行う必要があります。
  
- オンプレミスのドメインを確認します。 Azure AD Connect ウィザードに従って、このことを確認できます。
- Microsoft 365 テナントおよび AD DS の管理者アカウントのユーザー名とパスワードを取得します。

Azure AD Connect をインストールするオンプレミスのサーバーでは、次のものが必要になります。
  
|**サーバー OS**|**その他のソフトウェア**|
|:-----|:-----|
|Windows Server 2012 R2 以降 | -PowerShell は既定でインストールされます。既定では、アクションは必要ありません。  <br> -Net 4.5.1 以降のリリースは、Windows Update を通じて提供されます。 コントロールパネルで、Windows Server に最新の更新プログラムがインストールされていることを確認してください。 |
|Windows Server 2008 R2 Service Pack 1 (SP1) * * または Windows Server 2012 | -最新バージョンの PowerShell は、Windows Management Framework 4.0 で利用できます。 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で検索します。  <br> -.Net 4.5.1 以降のリリースは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)から入手できます。 |
|Windows Server 2008 | -最新サポートされている PowerShell のバージョンは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能な Windows Management Framework 3.0 で利用できます。  <br> -.Net 4.5.1 以降のリリースは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)から入手できます。 |

ハードウェア、ソフトウェア、アカウントとアクセス許可の要件、SSL 証明書の要件、および Azure AD Connect のオブジェクト制限の詳細については、「 [Azure Active Directory 接続の前提条件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites)」を参照してください。
  
また、Azure AD Connect[バージョンのリリース履歴](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)で、各リリースに含まれているものを確認することもできます。

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Azure AD Connect をインストールしてディレクトリ同期を構成する

開始する前に、以下のことを確認してください。

- Microsoft 365 グローバル管理者のユーザー名とパスワード
- AD DS ドメイン管理者のユーザー名とパスワード
- どの認証方法 (PHS、PTA、フェデレーション)
- [AZURE AD のシームレスなシングルサインオン (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)を使用するかどうか

次の手順を実行します。

1. [Microsoft 365 管理センター](https://admin.microsoft.com)にサインインし、 https://admin.microsoft.com) 左側のナビゲーションで [**ユーザー** \> の**アクティブなユーザー** ] を選択します。
2. [**アクティブなユーザー** ] ページで、[ **More** (3 つのドット) \> **ディレクトリ同期**] を選択します。
  
3. [ **Azure Active Directory の準備**] ページで、[**ダウンロードセンターに移動して azure AD Connect ツールの**リンクを取得する] を選択して、作業を開始します。 
4. 「 [AZURE Ad connect と AZURE Ad Connect 正常性インストールのロードマップ](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)」の手順を実行します。

## <a name="3-finish-setting-up-domains"></a>3. ドメインの設定を終了する

「 [CREATE dns records For Microsoft 365](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) 」の手順に従って、dns レコードを管理し、ドメインの設定を完了します。

## <a name="next-step"></a>次の手順

[ユーザー アカウントにライセンスを割り当てる](assign-licenses-to-user-accounts.md)
