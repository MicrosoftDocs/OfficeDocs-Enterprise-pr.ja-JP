---
title: ハイブリッド先進認証の概要と、オンプレミスの Skype for business および Exchange サーバーで使用するための前提条件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: ''
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: モダン認証は、よりセキュリティで保護されたユーザー認証と承認を提供する id 管理の方法です。 このサービスは、オンプレミスの skype for business server とオンプレミスの Exchange server のハイブリッド展開、およびスプリットドメインの skype for business ハイブリッドで利用できます。 この記事では、前提条件に関する関連ドキュメント、先進認証のセットアップ/無効化、および関連するクライアントのいくつか (例) へのリンクを示します。 Outlook および Skype クライアント) 情報。
ms.openlocfilehash: 26efa77e3c98c0395188e6ca7a2f65cd3b8b939e
ms.sourcegitcommit: 19f0deee26b6cf2eef316c742054572bb9d98b84
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "30458347"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>ハイブリッド先進認証の概要と、オンプレミスの Skype for business および Exchange サーバーで使用するための前提条件

モダン認証は、よりセキュリティで保護されたユーザー認証と承認を提供する id 管理の方法です。 これは、オンプレミスの skype for business server とオンプレミスの Exchange server の Office 365 ハイブリッド展開、およびスプリットドメイン skype for business ハイブリッドで利用できます。 この記事では、前提条件に関する関連ドキュメント、先進認証のセットアップ/無効化、および関連するクライアントのいくつか (例) へのリンクを示します。 Outlook および Skype クライアント) 情報。 
  
- [先進認証とは](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [モダン認証を使用した場合の変更点](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [オンプレミス環境の先進認証の状態を確認する](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [先進認証の前提条件を満たしているか。](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [開始する前に知っておくべきその他の情報](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [モダン認証 url の一覧](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>先進認証とは
<a name="BKMK_WhatisModAuth"> </a>

クライアント (たとえば、ラップトップまたは電話) とサーバー間の通信について話す際、Microsoft では "モダン認証" という語句を使用しています。
  
先進認証は、認証方法と承認方法の組み合わせに加えて、既に熟知している可能性のあるアクセスポリシーに依存するいくつかのセキュリティ対策をするための包括的な用語です。 次のとおりです。
  
- **認証方法**: 多要素認証。クライアント証明書ベースの認証。Active Directory 認証ライブラリ ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx))。
    
- **承認方法**: Microsoft がオープン認証を実装しています (OAuth)。 
    
- **条件付きアクセスポリシー**: モバイルアプリケーション管理 (MAM) と Azure Active Directory の条件付きアクセス。 
    
モダン認証を使用してユーザー id を管理すると、リソースを保護し、オンプレミス (exchange と Skype for business) の両方により安全な id 管理方法を提供するために、さまざまなツールを管理者に提供できます。、Skype for business ハイブリッド/スプリットドメインシナリオ。
  
skype for business は exchange と密接に連携するため、skype for business クライアントユーザーに表示されるログイン動作は、exchange の先進認証状態によって影響を受けることに注意してください。 このことは、Skype for business の分割ドメインハイブリッドを使用している場合にも適用されます。 また、先進認証の使用をサポートする Skype for business ハイブリッドの種類は、「スプリットドメイン」と呼ばれます (スプリットドメインでは、skype for business Online と skype for business の両方がオンプレミスで使用され、ユーザーは両方の場所に所属しています)。
  
> [!IMPORTANT]
> 2017年8月現在、Skype for business online と Exchange online を含むすべての新しい Office 365 テナントでは、既定で先進認証が有効になっていることをご存知ですか? 既存のテナントは既定の MA 状態に変更されませんが、すべての新しいテナントは上記に示した一連の拡張された id 機能を自動的にサポートしています。 skype for business online の MA の状態を確認するには、グローバル管理者の資格情報で skype for business online PowerShell を使用することができます。 を`Get-CsOAuthConfiguration`実行して、-ClientADALAuthOverride の出力を確認します。 -ClientADALAuthOverride が ' Allowed ' の場合は、先進認証が有効になります。 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>モダン認証を使用した場合の変更点
<a name="BKMK_WhatChanges"> </a>

オンプレミスの Skype for business または Exchange server で先進認証を使用している場合でも、オンプレミスのユーザーを*認証*していますが、リソースへのアクセスを*承認*するためのストーリー (ファイルまたはメールなど) が変更されています。 このため、先進認証はクライアントとサーバーの通信に関するものですが、evosts (Azure AD によって使用されるセキュリティトークンサービス) では、認証サーバーとしてオンプレミスとして設定されているように、MA (Azure AD によって使用されるセキュリティトークンサービス) として設定されています。 
  
evosts への変更により、オンプレミスのサーバーは、クライアントを承認するために OAuth (トークンの発行) を利用したり、オンプレミスのクラウドに共通のセキュリティメソッド (多要素認証など) を使用したりすることができます。 また、evosts はトークンを発行して、ユーザーが要求の一部としてパスワードを入力せずに、リソースへのアクセスを要求できるようにします。 ユーザーの所属先 (オンラインまたはオンプレミス) に関係なく、どの場所が必要なリソースをホストしているかにかかわらず、evosts は、先進認証が構成されたときにユーザーとクライアントを承認する中心になります。
  
ここでの例を次に示します。 ユーザーに代わって予定表情報を取得するために Skype for business クライアントが Exchange server にアクセスする必要がある場合は、Active Directory 認証ライブラリ (ADAL) を使用します。 ADAL は、OAuth セキュリティトークンを使用して、クライアントアプリケーションがディレクトリ内のセキュリティで保護されたリソースを使用できるようにするためのコードライブラリです。 ADAL は OAuth と連携して、クレームを検証し、パスワードではなく exchange トークンを使用して、ユーザーがリソースにアクセスできるようにします。 以前は、このようなトランザクションの権限は、ユーザーの要求を検証し、必要なトークンを発行する方法を知っているサーバーであり、オンプレミスのセキュリティトークンサービス、または Active Directory フェデレーションサービスであった可能性があります。 ただし、先進認証は、クラウド内の azure Active Directory (azure AD) を使用して、この権限を集中化します。
  
これは、Exchange サーバーと Skype for business 環境が完全にオンプレミスになっている場合でも、認証サーバーがオンラインになり、オンプレミスの環境で Office への接続を作成して管理できるようにする必要があることを意味します。クラウド内の365サブスクリプション (およびサブスクリプションがディレクトリとして使用する Azure Active Directory インスタンス)。
  
変更されないのはなぜですか? 分割ドメインハイブリッドにいるか、オンプレミスの Skype for business と Exchange server を使用しているかにかかわらず、すべてのユーザーは最初*にオンプレミスで*認証する必要があります。 先進認証のハイブリッド実装では、Lyncdiscovery と Autodiscovery はオンプレミスサーバーを指します。 
  
> [!IMPORTANT]
> MA でサポートされている特定の Skype for business のトポロジを知る必要がある場合は、[ここに記載](https://technet.microsoft.com/en-us/library/mt803262.aspx)されています。
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>オンプレミス環境の先進認証の状態を確認する
<a name="BKMK_CheckStatus"> </a>

モダン認証は、サービスが OAuth/S2S を利用する際に使用される認証サーバーを変更するため、Skype for business と Exchange 環境で先進認証がオンまたはオフになっているかどうかを知る必要があります。 PowerShell で`Get-CSOAuthConfiguration`コマンドを実行することにより、オンプレミスの Exchange サーバーまたは Skype for business サーバーの状態を確認できます。 コマンドが空の ' oauthservers ' プロパティを返す場合、モダン認証は無効になります。
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>先進認証の前提条件を満たしているか。

続行する前に、リストからこれらの項目を確認して確認してください。
  
- **Skype for business 固有**
    
  - すべてのサーバーに sfb Server 2015 CU5 以降がインストールされている必要があります。
    
  - **例外**-存続性 Branch Appliance (SBA) は現在のバージョンになります (Lync 2013 に基づいて)。 
    
  - Office 365 でフェデレーションドメインとして追加された SIP ドメイン
    
  - すべての sfb フロントエンドは、インターネットへの接続を、office 365 認証 url (tcp 443) および既知の証明書ルート crl (tcp 80) のように、「office の制限[url および IP」セクションの「Microsoft 125 Common and Office Online」に記載されているとおりに設定する必要があります。アドレス範囲](urls-and-ip-address-ranges.md)。
    
 **メモ**Skype for business フロントエンドサーバーがインターネットアクセスにプロキシサーバーを使用している場合は、使用するプロキシサーバーの IP アドレスとポート番号を、各フロントエンドの web.config ファイルの構成セクションに入力する必要があります。 
  
- C:\Program Files\Skype for Business Server 2015 (Web Components\Web ticket\int\web.config
    
- C:\Program Files\Skype for Business Server 2015 (Web Components\Web ticket\ext\web.config
    
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
> [Office 365 の url と IP アドレス範囲](urls-and-ip-address-ranges.md)の RSS フィードを購読して、必要な url の最新リストを最新の状態に保つようにしてください。 
  
- **Exchange Server 固有**
    
  - exchange server 2013 cu19 以上と up、または exchange server 2016 CU8 と up のどちらかを使用している。
    
  - 環境内に Exchange server 2010 がありません。
    
  - SSL オフロードが構成されていません。 SSL の終了と再暗号化がサポートされています。
    
  - 環境がプロキシサーバーインフラストラクチャを利用して、サーバーをインターネットに接続できるようにする場合は、すべての Exchange サーバーに[internetwebproxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx)プロパティで定義されたプロキシサーバーがあることを確認してください。
    
- **Exchange クライアントとプロトコルの要件**
  
  - 先進認証をサポートしているクライアントは次のとおりです。

  |**クライアント**|**プライマリプロトコル**|**メモ**|
  |:-----|:-----|:-----|
  |Outlook 2013、Outlook 2016  <br/> |MAPI over HTTP  <br/> |これらのクライアントとの先進認証を利用するには、exchange 内で MAPI over HTTP を有効にする必要があります (通常、exchange 2013 Service Pack 1 以降の新規インストールでは有効または True)。詳細については[、「office 2013 および office 2016 クライアントアプリでの先進認証のしくみ](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)」を参照してください。  <br/> 最低限必要な Outlook のビルドを実行していることを確認します。[Windows インストーラー (MSI) を使用するバージョンの Outlook については、「最新の更新プログラム」を](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)参照してください。  <br/> |
  |Outlook 2016 for Mac  <br/> |Exchange Web サービス  <br/> |  <br/> |
  |iOS および Android 用の Outlook  <br/> |  <br/> |詳細については[、「iOS および Android 用の Outlook でのハイブリッド先進認証の使用](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)」を参照してください。  <br/> |
  |Exchange ActiveSync クライアント (たとえば、iOS11 メール)  <br/> |Exchange ActiveSync  <br/> |先進認証をサポートする Exchange ActiveSync クライアントでは、基本認証からモダン認証に切り替えるためにプロファイルを再作成する必要があります。  <br/> |

- **一般的な前提条件**
    
  - ADFS を使用する場合は、フェデレーションに Windows 2012 R2 ADFS 3.0 以降が必要です。
    
  - id 構成は、AAD Connect (パスワードハッシュ同期、パススルー認証、Office 365 でサポートされているオンプレミス STS、et cetera など) でサポートされている任意の種類のいずれかです。
    
  - ユーザーのレプリケーションと同期のために、AAD Connect が構成され、機能している。
    
  - オンプレミスの環境と Office 365 環境の間で、Exchange の従来のハイブリッドトポロジモードを使用してハイブリッドが構成されていることを確認していること。 Exchange ハイブリッドの公式サポートステートメントは、現在の cu または現在の cu-1 のいずれかが必要であることを示しています。
    
    > [!Note]
    > ハイブリッドの先進認証は、[ハイブリッドエージェント](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)ではサポートされていません。
    
  - オンプレミスのテストユーザーと、Office 365 に所属するハイブリッドテストユーザーの両方が skype for business デスクトップクライアント (skype で先進認証を使用する場合) と Microsoft Outlook (必要な場合) にログインできることを確認してください。Exchange)。
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>開始する前に知っておくべきその他の情報
<a name="BKMK_Whatelse"> </a>

1. オンプレミスサーバーのすべてのシナリオには、オンプレミスの先進認証のセットアップが含まれています (実際には、サポートされるトポロジのリストがあります)。これにより、認証と承認を担当するサーバーが Microsoft Cloud (aad のセキュリティトークンサービスを ' evosts ' と呼びます)、Skype for business または Exchange のオンプレミスインストールで使用される url または名前空間に関する Azure Active Directory (AAD) を更新します。 そのため、オンプレミスサーバーは Microsoft クラウドの依存関係を利用します。 この操作を実行すると、' hybrid auth ' を構成することになります。
    
2. この記事では、サポートされている先進認証トポロジ (Skype for business にのみ必要) を選択するのに役立つ他のユーザーや、セットアップ手順の概要または先進認証を無効にするための手順について説明する、Exchange オンプレミスの操作方法に関する記事にリンクしています。およびオンプレミスの Skype for business。 サーバー環境で先進認証を使用するために、ホームベースが必要になる場合は、このページをブラウザーでお気に入りにしてください。
    
## <a name="list-of-modern-authentication-urls"></a>モダン認証 url の一覧
<a name="BKMK_URLListforMA"> </a>

- [モダン認証を使用するようにオンプレミスの Exchange Server を構成する方法](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [先進認証でサポートされている Skype for business のトポロジ](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [Skype for business のオンプレミスで先進認証を使用するように構成する方法](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Skype for business と Exchange からハイブリッド先進認証を削除または無効にする](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

