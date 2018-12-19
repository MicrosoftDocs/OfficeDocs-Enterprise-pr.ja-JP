---
title: ハイブリッド現代の認証の概要とビジネスと Exchange サーバーの設置型の Skype で使用するための前提条件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 10/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: '現代の認証より安全なユーザー認証と承認を提供する id 管理の方法です。ビジネス サーバー設置型 Exchange サーバー設置とビジネスの混成のドメインを分割 Skype の Skype のハイブリッド展開で使用可能になります。この資料へのリンクでは、ドキュメントに関する最新の認証のセットアップと無効化の前提条件と関連するクライアント (例: Outlook、Skype クライアント) の情報の一部に関連します。'
ms.openlocfilehash: c10e5660d43ccce50497fccfd9d830d31ac07d55
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371111"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>ハイブリッド現代の認証の概要とビジネスと Exchange サーバーの設置型の Skype で使用するための前提条件

現代の認証より安全なユーザー認証と承認を提供する id 管理の方法です。ビジネス サーバー設置と Exchange サーバーの設置型と同様、分割ドメインの Skype ビジネス混成の Skype の Office 365 のハイブリッド展開で使用可能になります。この資料へのリンクでは、ドキュメントに関する最新の認証のセットアップと無効化の前提条件と関連するクライアント (例: Outlook、Skype クライアント) の情報の一部に関連します。 
  
- [現代の認証とは何ですか。](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [現代の認証を使用すると、変更は何ですか。](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [オンプレミス環境の最新の認証状態を確認します。](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [現代の認証の前提条件を満たしているか。](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [始める前に他に何が必要でしょうか。](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [現代の認証 Url の一覧](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>現代の認証とは何ですか。
<a name="BKMK_WhatisModAuth"> </a>

(ノート型コンピューターや携帯電話などの) クライアントとサーバー間の通信を話題にする場合、マイクロソフトは、'現代 ' の認証の語句を使用します。
  
現代の認証は、認証と承認の方法と同様の場合によく使われるアクセス ポリシーに依存するいくつかのセキュリティ対策の組み合わせを総称する用語です。含まれています。
  
- **認証方法**: 多要素認証です。クライアント証明書ベースの認証です。Active Directory 認証ライブラリ ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx))。
    
- **認証方式**: オープン認証 (OAuth) のマイクロソフトの実装です。 
    
- **条件付きアクセス ポリシー**: モバイル アプリケーションの管理 (MAM) と Azure Active Directory の条件付きアクセスします。 
    
管理者は多くのさまざまなツールとリソースをセキュリティで保護するのには両方設置 (Exchange およびビジネス用の Skype) に id 管理のより安全な方法が用意されていますを使用して、ハイブリッドを交換する、最新の認証とユーザー id を管理します。、およびビジネスのハイブリッド/分割ドメインのシナリオの Skype です。
  
ビジネス用の Skype は、Exchange と緊密に動作をするためのログイン動作 Skype ビジネス クライアントのユーザーが参照してくださいの影響を受ける Exchange の最新の認証状態があります。これは、ビジネス ドメインを分割ハイブリッドに、Skype がある場合にも適用されます。また、Skype の最新の認証の使用をサポートしているビジネスのハイブリッドの種類とも呼ばれます、' 分割ドメイン ' (分割・ ドメインで、ビジネス オンラインの Skype とのビジネス上の prem、Skype の両方があり、ユーザーが両方の場所に置かれている)。
  
> [!IMPORTANT]
> 2017 年 8 月の現在オンライン ビジネスの Skype を含めるし、オンラインで交換できるすべての新しい Office 365 テナントが現代の認証が既定で有効になっているとご存知ですか。既存のテナントでは、既定の MA 状態の変更がありませんが、すべての新しいテナントは、上記を参照してくださいユーザー機能の拡張セットを自動的にサポートします。オンライン ビジネスの Skype の MA の状態を確認するには、グローバル管理者の資格情報を持つビジネス オンラインの PowerShell の Skype を使用できます。実行`Get-CsOAuthConfiguration`- ClientADALAuthOverride の出力を確認します。-ClientADALAuthOverride が可能な場合' '、現在の認証には。 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>現代の認証を使用すると、変更は何ですか。
<a name="BKMK_WhatChanges"> </a>

ビジネスまたは Exchange サーバーの設置型の Skype で最新の認証を使用すると、あなたはまだ*認証*ユーザー設置が*承認する*ストーリー (ファイル、電子メールなど) のリソースの変更へのアクセス。これは最新の認証については、クライアントとサーバーの通信では、MA の結果を evoSTS (セキュリティ トークン サービス Azure AD で使用される) の構成中に実行される手順を実行、理由は、Skype のビジネスおよび Exchange サーバーの設置型の認証サーバーとして設定されています。 
  
EvoSTS への変更は、活用する OAuth (トークンの発行)、クライアントを認証するサーバーでの設置し、設置使用セキュリティ共通のメソッドのような多要素認証) の雲の中にもできます。さらに、evoSTS は、ユーザー要求の一部として、パスワードを入力しなくても、リソースへのアクセスを要求できるようにするためのトークンを発行します。ユーザーが置かれている場所に関係なく (オンラインのまたは設置型)、どの場所では、必要なリソースをホストしているに関係なく EvoSTS は現代の認証を構成したら、ユーザーとクライアントを承認するコアになります。
  
ここでは、何かの例です。ビジネス クライアント用の Skype は、ユーザーの代理として予定表の情報を取得するのに Exchange サーバーにアクセスするのに必要がある、Active Directory 認証ライブラリ (ADAL) がこれを行うに使用されます。ADAL コード ライブラリは、OAuth のセキュリティ トークンを使用するクライアント アプリケーションに使用可能なディレクトリにセキュリティで保護されたリソースを作成です。ADAL OAuth トークン (パスワードの代わり)、リソースへのユーザー アクセスを許可するを交換してクレームを確認するのには。以前は、このような-- ユーザーの要求を検証し、必要なトークンを発行する方法を知っているサーバー--トランザクションの権限あった可能性がありますセキュリティ トークン サービスの設置型、または Active Directory フェデレーション サービスもします。ただし、最新の認証では、クラウド内の Azure Active Directory (Azure AD) とは、その機関が集中化されます。
  
つまり、Exchange サーバーと Skype のビジネス環境が完全に設置型でも、認証サーバーがオンラインにして、オンプレミス環境を作成し、Office への接続を維持することが必要クラウド (と、Azure Active Directory インスタンスのディレクトリとして、サブスクリプションを使用する) で 365 サブスクリプション。
  
何が変わらないか。分割ドメイン ハイブリッドまたは Skype を使用して、ビジネスおよび Exchange サーバーの設置型の中には、かどうかすべてのユーザーは最初*設置*を認証する必要があります。認証の最新のハイブリッド実装では、Lyncdiscovery 自動検出は、オンプレミスのサーバーをポイントします。 
  
> [!IMPORTANT]
> MA でサポートされているビジネス ・ トポロジーの特定の Skype を知っている場合は、[右側には、ここに記載されている](https://technet.microsoft.com/en-us/library/mt803262.aspx)です。
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>オンプレミス環境の最新の認証状態を確認します。
<a name="BKMK_CheckStatus"> </a>

現代の認証は、サービスが OAuth と S2S を活用するときに使用される認証サーバーを変更、ためには、最新の認証がオンまたはオフのビジネス環境、Skype の知っている必要があります。ビジネス上のサーバーを設置型では、Exchange または Skype のステータスをチェックするには実行することによって、`Get-CSOAuthConfiguration`の PowerShell コマンドです。コマンドには、空の 'OAuthServers' プロパティが返されます、現代の認証が無効です。
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>現代の認証の前提条件を満たしているか。

確認し、続行する前に、一覧からこれらの項目を確認します。
  
- **Skype ビジネスの特定の**
    
  - すべてのサーバーはデバイス サーバー 2015 CU5 を持つ必要がありますまたはそれ以降
    
  - **例外**の存続可能性ブランチ アプライアンス (SBA) は、(Lync 2013 に基づく) の現在のバージョンにすることができます 
    
  - SIP ドメインが Office 365 のフェデレーション ドメインとして追加されます。
    
  - Office 365 認証 Url (TCP 443) に、インターネットへの送信接続を持つ必要がありますすべてデバイス フロント エンドし、Office 365 の Url と IP 行 56 と ' 365 一般的な Microsoft Office オンライン '」の[の 125 でよく知られている証明書のルート Crl (TCP 80) が表示されます。アドレス範囲](urls-and-ip-address-ranges.md)。
    
 **メモ**ビジネスのフロント エンド サーバーについて、Skype は、インターネット アクセスにプロキシ サーバーを使用、する場合は、各フロント エンド用の web.config ファイルの構成セクションで使用されるプロキシ サーバーの IP とポート番号を入力してください。 
  
- ビジネス サーバー ・ 2015\Web ・ Components\Web の C:\Program Files\Skype ticket\int\web.config
    
- ビジネス サーバー ・ 2015\Web ・ Components\Web の C:\Program Files\Skype ticket\ext\web.config
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> [Office 365 の Url と IP アドレスの範囲](urls-and-ip-address-ranges.md)に必要な Url の最新の番組で最新の RSS フィードを購読することを確認します。 
  
- **Exchange Server の特定**
    
  - いずれかの Exchange server 2013 CU19 を使用している、またはサーバー 2016 CU8 を交換し、アップします。
    
  - 環境内の Exchange server 2010 ではありません。
    
  - SSL オフロードが構成されていません。SSL ターミネーションと再暗号化がサポートされています。
    
  - お客様の環境は、サーバーがインターネットに接続できるようにするのにはプロキシ サーバーのインフラストラクチャを利用して、イベントには、 [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx)プロパティで定義されているプロキシ サーバーをすべての Exchange サーバーがあることを確認します。
    
- **Exchange クライアントとプロトコルの要件**
  
  - 以下のクライアントでは、最新の認証をサポートします。

  |**クライアント**|**プライマリ プロトコル**|**メモ**|
  |:-----|:-----|:-----|
  |Outlook 2013、Outlook 2016  <br/> |MAPI over HTTP  <br/> |HTTP 経由で MAPI は Exchange 内で通常有効になっている (true を設定して、Exchange 2013 の Service Pack 1 の上に新規インストール) は、これらのクライアントを最新の認証を利用するために有効にする必要があります。詳細については、 [Office 2013 および Office 2016 のクライアント アプリケーションの現在の認証のしくみ](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)を参照してください。  <br/> Outlook での最低限必要なビルドを実行していることを確認します。[Windows インストーラー (MSI) を使用する Outlook のバージョンの最新の更新プログラム](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)を参照してください。  <br/> |
  |Outlook 2016 for Mac  <br/> |Exchange Web サービス  <br/> |  <br/> |
  |iOS および Android 用の Outlook  <br/> |  <br/> |詳細について[を使用するハイブリッド iOS および Android は、Outlook を使用して現代の認証](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)を参照してください。  <br/> |
  |Exchange ActiveSync クライアント (たとえば、iOS11 のメール)  <br/> |Exchange ActiveSync  <br/> |現代の認証をサポートする Exchange ActiveSync クライアントは、最新の認証に基本認証から切り替えるには、プロファイルを作り直す必要があります。  <br/> |

- **一般的な前提条件**
    
  - ADFS を使用する場合 Windows 2012 R2 の ad FS の 3.0年が必要以上のフェデレーション
    
  - 識別情報の構成は、AAD の接続がサポートする型のいずれか (など、パスワード ハッシュの同期、パススルー認証は、オンプレミス Office 365 でサポートされている STS、et cetera)。
    
  - AAD 接続の構成し、ユーザーの複製と同期の機能があります。
    
  - そのハイブリッドは、オンプレミスと Office 365 の間で正常に動作を確認しました。
    
  - Exchange ハイブリッドの公式なサポート ステートメントでは、現在 CU または現在 CU - 1 のいずれかする必要があります。
    
  - 作成ことを確認両方ハイブリッド テスト ユーザーと同様に、オンプレミスのテスト ユーザーが、Office 365 でホーム ログインできるように、Skype のビジネス デスクトップ クライアントの場合 Skype で最新の認証を使用するには) および Microsoft Outlook (そのために最新の認証を使用する場合交換)。
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>始める前に他に何が必要でしょうか。
<a name="BKMK_Whatelse"> </a>

1. 設置型サーバーのすべてのシナリオを含む最新の認証の設置型の設定 (実際には、ビジネス用の Skype はサポートされているトポロジの一覧があります) のサーバーの認証と承認を担当するが、マイクロソフトのクラウド (になるようAAD のセキュリティ トークン サービス、'evoSTS' と呼ばれる)、Azure Active Directory (AAD) の Url または、設置、Skype のビジネスや Exchange によって使用される名前空間についての更新とします。したがって、オンプレミスのサーバーは、マイクロソフトのクラウドの依存関係をとる。この操作を実行すると考えることが 'ハイブリッド認証' を構成します。
    
2. この資料へのリンクを他のユーザーを選択するために (Skype ビジネスのためにのみ必要)、現代の認証のトポロジと操作方法がサポートされているセットアップ手順では、そのアウトラインを記事や手順、最新の認証を無効にする Exchange の設置型およびビジネス用の Skype 設置します。好きなサーバー環境の最新の認証を使用するため、本拠地を必要とする場合、お使いのブラウザーでこのページです。
    
## <a name="list-of-modern-authentication-urls"></a>現代の認証 Url の一覧
<a name="BKMK_URLListforMA"> </a>

- [現代の認証を使用するオンプレミスの Exchange Server を構成する方法](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [現代の認証でサポートされているビジネス ・ トポロジーの Skype](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [現代の認証を使用する設置型のビジネスの Skype を構成する方法](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

