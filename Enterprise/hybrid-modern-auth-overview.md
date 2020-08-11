---
title: ハイブリッド先進認証の概要とオンプレミスの Skype for Business および Exchange サーバーで使用する前提条件
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
ms.date: 04/15/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: この記事では、ハイブリッド先進認証と、オンプレミスの Skype for Business および Exchange サーバーで使用するための前提条件について説明します。
ms.openlocfilehash: 81ffdb7175673c81917e34c98a2d162529a0efc9
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605733"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>ハイブリッド先進認証の概要とオンプレミスの Skype for Business および Exchange サーバーで使用する前提条件

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

_先進認証_ は、より安全なユーザー認証と承認を提供する ID 管理の方法です。 これは、オンプレミスの Skype for Business サーバーとオンプレミスの Exchange サーバーの Office 365 ハイブリッド展開、および分割ドメインの Skype for Business ハイブリッドにも利用できます。 この記事は、前提条件についての関連ドキュメント、先進認証の設定/無効化にリンクし、関連するクライアント (例: Outlook および Skype クライアント) 情報にリンクします。
  
- [先進認証とは何ですか?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [先進認証を使用すると、どのような変更がありますか?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [オンプレミス環境の先進認証状態を確認する](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [先進認証の前提条件を満たしていますか?](#do-you-meet-modern-authentication-prerequisites)
- [始める前に把握しておくべき情報はありますか?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>先進認証とは何ですか?
<a name="BKMK_WhatisModAuth"> </a>

先進認証は、クライアント （ラップトップや携帯電話など） とサーバーの間の認証と承認の方法の組み合わせた包括的な用語であり、使用している可能性のあるアクセスポリシーに依存するいくつかのセキュリティ対策です。 内容は以下のとおりです:
  
- **認証方法**: 多要素認証 (MFA)、スマート カード認証、クライアント証明書ベースの認証
- **承認方法**: Microsoft が提供する Open Authorization (OAuth) の実装
- **条件付きアクセスポリシー**: モバイル アプリケーション管理 (MAM) と Azure Active Directory (Azure AD) の条件付きアクセス

先進認証を使用してユーザー ID を管理すると、管理者はさまざまなツールを使用して、リソースを保護することができます。また、オンプレミス (Exchange と Skype for Business)、Exchange ハイブリッド、Skype for Business のハイブリッド/分割ドメインのシナリオにもより安全な ID 管理方法を提供します。
  
Skype for Business は Exchange と緊密に連携しているため、Skype for Business クライアント ユーザーのログイン動作は、Exchange の先進認証状態によって影響を受けます。 これは、Skype for Business の _分割ドメイン_ ハイブリッド アーキテクチャがあり、Skype for Business Online と Skype for Business オンプレミスの両方が含まれていて、ユーザーが両方の場所に所属している場合にも適用されます。

Office 365 の先進認証の詳細については、[「Office 365 クライアント アプリ サポート - 先進認証」](office-365-client-support-modern-authentication.md) を参照してください。
  
> [!IMPORTANT]
> 2017 年 8 月に、Skype for Business Online と Exchange Online を含むすべての新しい Office 365 テナントは、既定で先進認証が有効になります。 既存のテナントの既定の MA 状態は変更されませんが、すべての新しいテナントは、上記の一覧に表示されている ID 機能の拡張セットを自動的にサポートします。 MA 状態を確認するには、[「オンプレミス環境の先進認証状態を確認する」](hybrid-modern-auth-overview.md#BKMK_CheckStatus) セクションを参照してください。
  
## <a name="what-changes-when-i-use-modern-authentication"></a>先進認証を使用すると、どのような変更がありますか?
<a name="BKMK_WhatChanges"> </a>

オンプレミスの Skype for Business または Exchange サーバーで先進認証を使用する場合、オンプレミスのユーザーは引き続き * 認証* されますが、リソース (ファイルやメールなど) へのアクセスを *承認* するストーリーは変わります。 最新の認証はクライアントとサーバーの通信に関するものですが、これは、MA の構成中に実行される手順により、evoSTS （Azure AD で使用されるセキュリティ トークン サービス） が、Skype for Business および Exchange サーバーのオンプレミスの認証サーバーとして設定されるためです。
  
evoSTS への変更により、オンプレミス サーバーはクライアントを承認するために OAuth (トークン発行) を利用でき、オンプレミスはクラウドで一般的なセキュリティ方法 (多要素認証など) を使用できます。 さらに、evoSTSは、ユーザーが要求の一部としてパスワードを提供しなくても、リソースへのアクセスを要求できるトークンを発行します。 ユーザーのホーム (オンラインまたはオンプレミス)、必要なリソースをホストしている場所に関係なく、EvoSTS は、先進認証が構成されたら、ユーザーとクライアントを承認する中核になります。
  
たとえば、Skype for Business クライアントがユーザーの代わりにExchange サーバーにアクセスして予定表情報を取得する必要がある場合、Active Directory 認証ライブラリ （ADAL） を使用してそれを行います。 ADAL は、OAuth セキュリティ トークンを使用してクライアント アプリケーションがディレクトリ内の保護されたリソースを利用できるように設計されたコード ライブラリです。 ADAL は OAuth と連携して、クレームを検証し、（パスワードではなく） トークンを交換して、リソースへのユーザー アクセスを許可します。 以前は、このようなトランザクションの権限 （ユーザーの要求を検証し、必要なトークンを発行する方法を理解しているサーバー） は、オンプレミスのセキュリティ トークン サービス、または Active Directory フェデレーション サービスでさえあった可能性があります。 ただし、先進認証では、Azure AD を使用してその権限を集中化します。
  
これは、Exchange サーバーおよび Skype for Business 環境が完全にオンプレミスであっても、承認サーバーがオンラインになることを意味します。オンプレミス環境には、クラウド内の Office 365 サブスクリプション （およびサブスクリプションがディレクトリとして使用する Azure AD インスタンス） への接続を作成および維持する機能が必要です。
  
何が変更されないのでしょうか? 分割ドメイン ハイブリッドを使用している場合でも、Skype for Business および Exchange サーバーをオンプレミスで使用している場合でも、すべてのユーザーは最初に *オンプレミス* で認証する必要があります。 先進認証のハイブリッド実装では、_Lyncdiscovery_ と _Autodiscovery_ の両方がオンプレミス サーバーを指しています。
  
> [!IMPORTANT]
> MA でサポートされている Skype for Business の特定のトポロジについて理解する必要がある場合は、[ここに](https://technet.microsoft.com/library/mt803262.aspx) 記載されています。
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>オンプレミス環境の先進認証状態を確認する
<a name="BKMK_CheckStatus"> </a>

先進認証は、サービスが OAuth/S2S を利用するときに使用する承認サーバーを変更するので、オンプレミスの Skype for Business と Exchange 環境で先進認証が有効になっているかどうかを確認する必要があります。 次の PowerShell コマンドを実行して、Exchange サーバーの状態を確認できます:

```powershell
Get-OrganizationConfig | ft OAuth*
```

_OAuth2ClientProfileEnabled_ プロパティの値が **False**の場合、先進認証は無効になります。

Get-OrganizationConfig cmdlet の詳細については、[Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/get-organizationconfig) を参照してください。

次の PowerShell コマンドを実行して、Skype for Business サーバーを確認できます:

```powershell
Get-CSOAuthConfiguration
```

コマンドが空の _OAuthServers_ プロパティを返す場合、または _ClientADALAuthOverride_ プロパティの値が **許可されていない** 場合は、先進認証は無効になります。

Get-CsOAuthConfiguration コマンドレットの詳細については、[Get-CsOAuthConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csoauthconfiguration) を参照してください。
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>先進認証の前提条件を満たしていますか?

続けるには、リストから次の項目を検証および確認します:
  
- **Skype for Business 固有**
  - Skype for Business Server 2015 以降には、すべてのサーバーに2017 年 5 月の累積的な更新プログラム (CU5) が含まれる必要があります。
    - **例外** - Survivability Branch Appliance (SBA) は現在のバージョン (Lync 2013 に基づく) にすることができます
  - Office 365 のフェデレーション ドメインとして SIP ドメインが追加されています
  - すべての SFB フロント エンドには、インターネット、Office 365 認証URL （TCP 443）、および [Office 365 の URL と IP アドレスの範囲](urls-and-ip-address-ranges.md) の「Microsoft 365 Common and Office」セクションの 56 行目と 125 行目に記載されている既知の証明書ルート CRL （TCP 80） への接続が必要です。 
  
- **ハイブリッド Office 365 環境の Skype for Business オンプレミス**
  - Skype for Business Server 2019 の展開には、Skype for Business Server 2019 を実行するすべてのサーバーが含まれています。
  - Skype for Business Server 2015 の展開には、Skype for Business Server 2015 を実行するすべてのサーバーが含まれています。
  - 次に示す最大 2 つの異なるサーバー バージョンの展開:
    - Skype for Business Server 2015
    - Skype for Business Server 2019
  - Skype for Business のすべてのサーバーには、最新の累積更新プログラムがインストールされている必要があります。[「Skype for Business Server の更新」](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) を参照して、利用可能なすべての更新プログラムを見つけて管理してください。
  - ハイブリッド環境に Lync Server 2010 または 2013 はありません。

>[!NOTE]
>Skype for Business フロントエンド サーバーでインターネット アクセスにプロキシ サーバーを使用している場合は、使用されるプロキシ サーバーの IP アドレスとポート番号を、各フロント エンドの web.config ファイルの構成セクションに入力する必要があります。
  
- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config
- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> [Office 365 の URL と IP アドレス範囲](urls-and-ip-address-ranges.md) の RSS フィードを購読して、必要な URL のリストを最新の状態に維持してください。
  
- **Exchange Server 固有**
  - Exchange Server 2013 CU19 以降、Exchange Server 2016 CU8 以降、または Exchange Server 2019 CU1 以降のいずれかを使用しています。
  - 環境に Exchange Server 2010 はありません。
  - SSL オフローディングが構成されていません。 SSL の終了と再暗号化がサポートされています。
  - 環境がプロキシ サーバー インフラストラクチャを利用してサーバーがインターネットに接続できるようにする場合は、すべてのExchange サーバーに [InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) プロパティでプロキシ サーバーが定義されていることを確認してください。
  
- **ハイブリッド Office 365 環境の Exchange Server オンプレミス**

  - Exchange Server 2013 を使用している場合は、少なくとも 1 つのサーバーに、メールボックスとクライアント アクセス サーバーの役割がインストールされている必要があります。 メールボックスの役割とクライアント アクセスの役割を別々のサーバーにインストールすることもできますが、信頼性を高め、パフォーマンスの向上を図るには、同じサーバーに両方の役割をインストールすることを強くお勧めします。
  - Exchange Server 2016 以降のバージョンを使用している場合は、少なくとも 1 つのサーバーに、メールボックス サーバーの役割がインストールされている必要があります。
  - ハイブリッド環境に Exchange Server 2007 または 2010 はありません。
  - すべての Exchange サーバーには、最新の累積更新プログラムがインストールされている必要があります。[「最新の累積更新プログラムで Exchange をアップグレードする」](https://docs.microsoft.com/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) を参照して、利用可能なすべての更新プログラムを見つけて管理してください。

- **Exchange クライアントとプロトコルの要件**
  
  - 次のクライアントは先進認証をサポートします:

  |**クライアント**|**プライマリ プロトコル**|**メモ**|
  |:-----|:-----|:-----|
  |Outlook 2013、Outlook 2016  <br/> |MAPI over HTTP  <br/> |これらのクライアントで先進認証を利用にするには、Exchange 内で MAPI over HTTP を有効にする必要があります (通常、Exchange 2013 Service Pack 1 以降の新規インストールでは有効または True です)。詳細については、[「Office 2013 および Office 2016 クライアント アプリの先進認証のしくみ」](https://docs.microsoft.com/office365/enterprise/modern-auth-for-office-2013-and-2016) を参照してください。  <br/> Outlook の最小限必要なビルドを実行していることを確認します。[「Windows インストーラー (MSI) を使用する Outlook のバージョンの最新の更新プログラム」](https://docs.microsoft.com/officeupdates/outlook-updates-msi) を参照してください。  <br/> |
  |Outlook 2016 for Mac  <br/> |Exchange Web サービス  <br/> |  <br/> |
  |iOS および Android 用の Outlook  <br/> |  <br/> |詳細については、[「iOS および Android 用の Outlook でのハイブリッド先進認証の使用」](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) を参照してください。  <br/> |
  |Exchange ActiveSync クライアント (例: iOS11 メール)  <br/> |Exchange ActiveSync  <br/> |先進認証をサポートしている Exchange ActiveSync クライアントの場合、基本認証から先進認証に切り替えるには、プロファイルを再作成する必要があります。  <br/> |

- **一般的な前提条件**
  - AD FS を使用している場合、フェデレーションには Windows 2012 R2 AD FS 3.0 以上が必要です。
  - ID の構成は、パスワード ハッシュ同期、パススルー認証、Office 365 でサポートされるオンプレミス STS など、Azure AD Connect でサポートされるタイプのいずれかです。
  - ユーザー レプリケーションと同期のために、Azure AD Connect が構成され機能しています。
  - オンプレミスと Office 365 環境との間で、Exchange の従来のハイブリッド トポロジ モードを使用してハイブリッドが構成されていることを確認します。 Exchange ハイブリッドの公式サポート声明によると、現在の CU または現在の CU - 1 のいずれかが必要です。
    > [!NOTE]
    > ハイブリッド先進認証は、[ハイブリッド エージェント](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent) でサポートされていません。

  - オンプレミスのテスト ユーザー、および Office 365 に含まれているハイブリッド テスト ユーザーが、Skype for Business デスクトップ クライアント (Skype で先進認証を使用する場合) と Microsoft Outlook (Exchange で先進認証を使用する場合) にログインできることを確認します。

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>始める前に把握しておくべき情報はありますか?
<a name="BKMK_Whatelse"> </a>

- オンプレミス サーバーのすべてのシナリオでは、オンプレミスの先進認証が設定されています (実際には、Skype for Business では、サポートされているトポロジの一覧があります)。認証および承認を行うサーバーは Microsoft Cloud （「evoSTS」と呼ばれる Azure AD のセキュリティ トークン サービス） にあり、Skype for Business または Exchange のオンプレミス インストールで使用される URL または名前空間について Azure AD を更新します。 そのため、オンプレミス サーバーは、Microsoft Cloud の依存関係を利用します。 このアクションを実行することは、「ハイブリッド認証」の構成と見なすことができます。
- この記事では、サポートされている先進認証トポロジ (Skype for Business にのみ必要) の選択や、Exchange オンプレミスおよび Skype for Business オンプレミスのセットアップ手順、または先進認証を無効にする手順の概要について説明します。 サーバー環境で先進認証を使用するために、ホームベースが必要な場合は、このページをブラウザーでお気に入りに追加します。

## <a name="related-topics"></a>関連トピック
<a name="BKMK_URLListforMA"> </a>

- [Exchange Server をオンプレミスで構成して、先進認証を使用する方法](configure-exchange-server-for-hybrid-modern-authentication.md)
- [先進認証でサポートされている Skype for Business トポロジ](https://technet.microsoft.com/library/mt803262.aspx)
- [Skype for Business をオンプレミスで構成して、先進認証を使用する方法](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
