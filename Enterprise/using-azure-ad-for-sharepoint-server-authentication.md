---
title: "Azure AD を使用して SharePoint サーバーの認証"
ms.author: tracyp
author: MSFTTracyP
ms.reviewer:
- kirke
- josephd
- kirks
manager: laurawi
ms.date: 3/2/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: 
description: "概要: は、Azure アクセス制御サービスを使用しないし、Azure Active Directory で、SharePoint サーバーのユーザーの認証に SAML 1.1 を使用する方法を説明します。"
ms.openlocfilehash: e57414c3ed5af5c02b719d0c3639542e154be5bf
ms.sourcegitcommit: fbf33e74fd74c4ad6d60b2214329a3bbbdb3cc7c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Azure AD を使用して SharePoint サーバーの認証

 **の概要:**SharePoint サーバー 2016 Azure Active Directory でユーザーを認証する方法について説明します。
  
> [!NOTE]
> この資料は、カーク Evans、マイクロソフトのプリンシパル プログラム マネージャーの作業に基づいています。 

<blockquote>
<p>この資料では、Azure Active Directory のグラフと対話するためのコード サンプルを参照します。コード サンプルをダウンロードすることができます[ここ](https://github.com/kaevans/spsaml11/tree/master/scripts)。</p>
</blockquote>

SharePoint サーバー 2016年には、信頼できるが、他のユーザーを管理する別の id プロバイダーとそれらを認証することによって、ユーザーを管理しやすく、クレーム ベース認証を使用してユーザーを認証する機能が用意されています。たとえば、Active Directory ドメイン サービス (AD DS) を使用したユーザー認証を管理するのではなく Azure Active Directory (AD の Azure) を使用して認証するユーザーを有効にする可能性があります。こうと、ユーザー名で onmicrosoft.com サフィックスを持つクラウド専用のユーザーの認証、ユーザーは、オンプレミスのディレクトリと同期しその他のディレクトリからのゲスト ユーザーを招待します。多要素認証と高度なレポート作成機能など、Azure AD 機能を活用することもできます。

> [!IMPORTANT]
> この資料で説明するソリューションは、SharePoint Server 2013 はでも使用できます。ただし、SharePoint Server 2013 がメイン ストリーム サポート終了に近づいていることに留意してください。詳細については、[マイクロソフト ライフ サイクル ポリシー](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) 」および「 [SharePoint 2013 製品のサービス ポリシーの更新](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)を参照してください。

この資料では、Azure AD、設置型ではなく、ユーザーを認証するために使用する方法について説明 AD DS です。この構成では、Azure AD は、SharePoint サーバーの 2016年の信頼できる id プロバイダーになります。この構成では、SharePoint サーバーの 2016年インストール自体で使用される AD DS の認証とは別のユーザー認証方法を追加します。、この資料を活用する必要があります WS フェデレーションとします。詳細については、 [Ws-federation の理解](https://go.microsoft.com/fwlink/p/?linkid=188052)を参照してください。

![Azure AD を使用して SharePoint の認証のため](images/SAML11/fig1-architecture.png)

以前は、この構成を持つ必要がなど Azure アクセス制御サービス (ACS)、クラウド環境にフェデレーション サービスをホストしている Active Directory フェデレーション サービス (AD FS) を SAML 1.1 から SAML 2.0 トークンに変換します。Azure AD を今すぐ発行元の SAML 1.1 トークンを使用すると、この変換は必要ではありません。上の図では、この変換を実行する中間層の要件が不要になったことを示すこの構成では、SharePoint の 2016年ユーザーの認証のしくみを示しています。

> [!NOTE]
> この構成では、Azure の仮想マシンまたは設置型の SharePoint ファームがホストされているかどうかを機能します。ユーザーを確認する追加のファイアウォール ポートを開くと Azure Active Directory をブラウザーからアクセスできることは不要です。

SharePoint 2016 のアクセシビリティ機能については、 [SharePoint サーバーの 2016年のユーザー補助ガイドライン](https://go.microsoft.com/fwlink/p/?LinkId=393123)を参照してください。

## <a name="configuration-overview"></a>構成の概要

Azure AD を SharePoint サーバーの 2016年の id プロバイダーとして使用する環境を設定するのには、次の一般的な手順に従います。

1. 新しい Azure AD ディレクトリか、既存のディレクトリを使用します。
2. SSL を使用するのには、Azure AD のセキュリティで保護する web アプリケーションのゾーンが構成されていることを確認します。
3. Azure AD では、新しいエンタープライズ アプリケーションを作成します。
4. SharePoint サーバー 2016年には、新しい信頼できる id プロバイダーを構成します。
5. Web アプリケーションのアクセス許可を設定します。
6. Azure AD では、SAML 1.1 トークンの発行ポリシーを追加します。
7. 新しいプロバイダーを確認します。

次のセクションでは、これらのタスクを実行する方法について説明します。

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>ステップ 1: 作成、新しい Azure AD ディレクトリか、既存のディレクトリを使用します。

Azure ポータル ([https://portal.azure.com](https://portal.azure.com))、新しいディレクトリを作成します。組織名、最初のドメイン名、および国や地域を提供します。

![ディレクトリを作成します。](images/SAML11/fig2-createdirectory.png) 

 など、Microsoft Office 365 または、Microsoft Azure サブスクリプションに使用される 1 つのディレクトリがある場合は、そのディレクトリを代わりに使用することができます。ディレクトリにアプリケーションを登録するアクセス許可が必要です。

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>手順 2: は、SSL を使用するのには、Azure AD のセキュリティで保護する web アプリケーションのゾーンが構成されていることを確認します。

[Azure 内の SharePoint サーバーの 2016年ファームの高可用性を実行](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)することで、リファレンス ・ アーキテクチャを使用してこの資料が記述されています。記事の付属するスクリプトを使用して[この資料](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)で説明するソリューションを展開するは、SSL を使用しないサイトを作成します。  

SAML を使用するには、SSL を使用するアプリケーションを構成する必要があります。SSL を使用する SharePoint web アプリケーションが構成されていない場合は、SSL 用の web アプリケーションを構成するのには新しい自己署名証明書を作成するのには次の手順を使用します。この構成では、ラボ環境のだけを目的とし、本番用のものではありません。本番環境では、署名証明書を使用してください。

1. **サーバーの全体管理**に移動 > **アプリケーション管理** > **Web アプリケーションの管理**では、SSL を使用するように拡張する必要がある web アプリケーション] をクリックします。Web アプリケーションを選択し、**移動できるようにするリボン**のボタンをクリックします。同じ URL を使用してくださいが、ポート 443 の SSL を使用する web アプリケーションを拡張します。</br>![別の IIS サイトに web アプリケーションを拡張します。](images/SAML11/fig3-extendwebapptoiis.png)</br>
2. IIS マネージャー で、[ **サーバー証明書**] をダブルクリックします。
3. [**操作**] ウィンドウには、**自己署名証明書の作成**をクリックします。[証明書] ボックスで、表示名を指定します、証明書のフレンドリ名を入力し、[ **OK**] をクリックします。
4. **サイト バインドの編集**] ダイアログ ボックスで、ホスト名が確認、フレンドリ名と同じ次の図に示すようにします。</br>![IIS でサイトのバインドを編集](images/SAML11/fig4-editsitebinding.png)</br>

IIS でサイトのバインド用の証明書を構成する SharePoint ファーム内の web フロント エンド サーバーのそれぞれが必要です。


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>手順 3: Azure AD で新しいエンタープライズ アプリケーションを作成します。

1. Azure ポータル ([https://portal.azure.com](https://portal.azure.com)) で、Azure AD ディレクトリを開きます。**エンタープライズ ・ アプリケーション**をクリックし、[**新しいアプリケーション**] をクリックします。**非ギャラリー アプリケーション**を選択します。*SharePoint SAML の統合*などの名前を指定し、[**追加**] をクリックします。</br>![新しいギャラリーではないアプリケーションを追加します。](images/SAML11/fig5-addnongalleryapp.png)</br>
2. アプリケーションを構成するのにはナビゲーション ウィンドウで 1 つの記号でリンクをクリックします。**SAML ベース サインオン**SAML の構成アプリケーションのプロパティを表示するには、**シングル ・ サインオン ・ モード**のドロップダウン リストを変更します。次のプロパティを構成します。</br>
    - 識別子:`urn:sharepoint:portal.contoso.local`
    - 返信の URL:`https://portal.contoso.local/_trust/default.aspx`
    - サインオン URL:`https://portal.contoso.local/_trust/default.aspx`
    - ユーザー識別子。`user.userprincipalname`</br>
    - 注意: *portal.contoso.local*をセキュリティで保護する SharePoint サイトの URL に置き換えることによって、Url を変更します。</br>
3. 次の行を含むテーブルを (次の表 1 のような) を設定します。</br> 
    - レルム
    - SAML の署名証明書ファイルへの完全パス
    - SAML シングル サインオン サービスの URL ( */wsfed*と*/saml2*を置き換え)
    - アプリケーション オブジェクトの id です。 </br>
*識別子*の値をテーブル (「表 1 の下) に*領域*のプロパティにコピーします。
4. 変更を保存します。
5. サインオンの構成] ページにアクセスする**(アプリケーション名) を構成する**] リンクをクリックします。</br>![ページで、シングル ・ サインオンを構成します。](images/SAML11/fig7-configssopage.png)</br> 
    -  SAML の署名証明書を .cer の拡張子が付いたファイルとしてダウンロードする**SAML の署名証明書の生**のリンクをクリックします。コピーし、テーブルにダウンロードしたファイルへの完全パスを貼り付けます。
    - コピーし、SAML シングル サインオン サービスの URL リンクを貼り付けるには、URL の*/saml2*の部分を*/wsfed*に置き換えます。</br>
6.  アプリケーションの [**プロパティ**] ウィンドウに移動します。コピーし、手順 3 で設定したテーブルにオブジェクト ID の値を貼り付けます。</br>![アプリケーションのプロパティ] ウィンドウ](images/SAML11/fig8-propertiespane.png)</br>
7. キャプチャした値を使用して、手順 3 で設定した表次の表 1 のようになるかどうかを確認します。


| 表 1: 値の取得  |  |
|---------|---------|
|レルム | `urn:sharepoint:portal.contoso.local` |
|SAML の署名証明書ファイルへの完全パス | `C:/temp/SharePoint SAML Integration.cer`  |
|SAML シングル サインオン サービスの URL (/saml2 は/wsfed に置き換えてください) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|アプリケーションのオブジェクト ID | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> URL に*/saml2*の値を*/wsfed*に置き換えます。*/Saml2*エンドポイントでは、SAML 2.0 トークンを処理します。*/Wsfed*エンドポイントでは、処理 SAML 1.1 トークンを有効にし、SharePoint 2016 SAML フェデレーションに必要です。

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>ステップ 4: SharePoint サーバーの 2016年の新しい信頼できる id プロバイダーを構成します。

サーバー 2016 の SharePoint サーバーにサインインし、2016年の SharePoint 管理シェルを開きます。$Realm、$wsfedurl、および表 1 から $filepath の値を入力し、新しい信頼できる id プロバイダーを構成するのには次のコマンドを実行します。

> [!TIP]
> PowerShell を使用するにした場合、または PowerShell のしくみについてより詳しく知りたい場合は、 [SharePoint の PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps)を参照してください。 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"
```

次に、以下の手順を実行、アプリケーションの信頼できる id プロバイダーを有効にします。
1. サーバーの全体管理では、 **Web アプリケーションの管理**に移動し、Azure AD を使用してセキュリティ保護する web アプリケーションを選択します。 
2. リボンでは、[**認証プロバイダー** ] をクリックしを使用するゾーンを選択します。
3. **信頼できる Id プロバイダー**を選択し、登録した*AzureAD*をという名前を識別するプロバイダーを選択します。  
4. サインイン ページの URL の設定では、**ユーザー設定のサインイン ページ**を選択し、"/_trust/"の値を提供します。 
5. [ **OK**] をクリックします。

![認証プロバイダーを構成します。](images/SAML11/fig10-configauthprovider.png)

## <a name="step-5-set-the-permissions"></a>手順 5: アクセス許可を設定します。

Azure AD にログインし、SharePoint にアクセスするユーザーには、アプリケーションへのアクセスを与える必要があります。 

1. Azure ポータルでは、Azure AD ディレクトリを開きます。**エンタープライズ ・ アプリケーション**をクリックし、[**すべてのアプリケーション**] をクリックします。以前に作成したアプリケーションをクリックして (SharePoint SAML 統合)。
2. **ユーザーとグループ**] をクリックします。 
3. Azure AD を使用して SharePoint にログインするアクセス許可を持つグループまたはユーザーを追加する**ユーザーを追加**をクリックします。
4. ユーザーまたはグループを選択し、[**割り当て**] をクリックします。
 
ユーザーは Azure AD は、のアクセス許可が与えられてが、また、SharePoint のアクセス許可を与える必要があります。Web アプリケーションにアクセスするのにアクセス許可を設定するのにには、次の手順を使用します。

1. サーバーの全体管理で、[ **アプリケーション構成の管理**] をクリックします。
2. [ **アプリケーション構成の管理**] ページの [ **Web アプリケーション**] セクションで、[ **Web アプリケーションの管理**] をクリックします。
3. 適切な Web アプリケーションをクリックし、[ **ユーザー ポリシー**] をクリックします。
4. Web アプリケーションのポリシー]、 **[ユーザーの追加**をクリックします。</br>![その名の要求によって、ユーザーの検索](images/SAML11/fig11-searchbynameclaim.png)</br>
5. [ **ユーザーの追加**] ダイアログ ボックスの [ **領域**] で適切な領域をクリックし、[ **次へ**] をクリックします。
6. **Web アプリケーションのポリシー** ] ダイアログ ボックスの [**ユーザーの選択**] セクションで、[**参照**] アイコンをクリックします。
7. [**検索**] ボックスで、ディレクトリ内のユーザーのサインイン名を入力し、[**検索**] をクリックします。 </br>例: *demouser@blueskyabove.onmicrosoft.com*。
8. リスト ビューで [AzureAD] 見出しの下 name プロパティを選択して [**追加**] をクリックし、ダイアログ ボックスを閉じます**[ok]**をクリックします。
9. アクセス許可] では、**フル コントロール**をクリックします。</br>![クレーム ユーザーにフル コントロールを付与します。](images/SAML11/fig12-grantfullcontrol.png)</br>
10. [ **完了**]、[ **OK**] の順にクリックします。

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>手順 6: Azure AD で SAML 1.1 トークンの発行ポリシーを追加します。

ポータルで AD の Azure アプリケーションが作成されると、SAML 2.0 を使用して既定になります。SharePoint サーバー 2016年には、SAML 1.1 トークン形式が必要です。次のスクリプトは SAML 2.0 の既定のポリシーを削除し、問題の SAML 1.1 トークンに新しいポリシーを追加します。このコードでは、付属の[Azure Active Directory のグラフとの対話を示すサンプル](https://github.com/kaevans/spsaml11/tree/master/scripts)をダウンロードする必要があります。 


```
Import-Module <file path of Initialize.ps1> 
$objectid = "<Application Object ID from Table 1>"
$saml2policyid = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $objectid | ?{$_.displayName -EQ "TokenIssuancePolicy"} | select objectId
Remove-PolicyFromServicePrincipal -policyId $saml2policyid -servicePrincipalId $objectid
$policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $objectid
```
> 実行するのには重要であることに注意してください、`Import-Module`コマンドを次の使用例に示すようにします。これは、表示されるコマンドを含む依存するモジュールをロードします。これらのコマンドを正常に実行するのには管理者特権のコマンド プロンプトを開きする必要があります。

次の PowerShell コマンドの例では、グラフの API に対してクエリを実行する方法の例を示します。Azure AD でトークンの発行ポリシーの詳細については、[ポリシーの操作のためのグラフの API リファレンス](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy)を参照してください。

## <a name="step-7-verify-the-new-provider"></a>手順 7: 新しいプロバイダーを確認します。

前の手順で構成した web アプリケーションの URL にブラウザーを開きます。Azure AD へのサインインにリダイレクトされます。

![フェデレーション用に構成された Azure の AD へのサインイン](images/SAML11/fig13-examplesignin.png)

サインイン状態を継続するかどうかが求められます。

![サインアウトしますか。](images/SAML11/fig14-staysignedin.png)

最後に、Azure Active Directory のテナントのユーザーとしてログインしてサイトにアクセスできます。

![ユーザーが SharePoint に署名](images/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>証明書の管理
上記の手順 4 で信頼できる id プロバイダーに対して構成された署名証明書が有効期限の更新が必要であることを理解する重要です。証明書の書き換えでは、[フェデレーション シングル サインオン Azure Active Directory 内の証明書を管理](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs)についての資料を参照してください。Azure AD で証明書が書き換えられている場合後、は、ローカル ファイルへのダウンロードし、更新された署名証明書を信頼できる id プロバイダーを構成するのには次のスクリプトを使用してください。 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```

## <a name="fixing-people-picker"></a>ユーザー選択ウィンドウを修正します。
Azure AD からの id を使用して SharePoint 2016 には、ユーザーはログオンできますようになりましたが、ユーザー エクスペリエンスの改善の機会はまだあります。たとえば、ユーザーを検索すると、ユーザー選択ウィンドウで複数の検索結果が表示されます。要求のマッピングで作成された 3 つのクレームの種類ごとに検索結果があります。ユーザー選択ウィンドウを使用してユーザーを選択するには、必要があるには、ユーザー名を正確に入力し、**名前**要求の結果を選択します。

![クレームの検索結果](images/SAML11/fig16-claimssearchresults.png)

スペル ミスにつながることが、検索する値の検証がないか要求の**姓**などを割り当てるの種類を誤って、間違った選択をするユーザーを要求します。正常にリソースへのアクセスをこのユーザーを防ぐことができます。

このシナリオでは、支援するのには、オープン ソース ソリューションが SharePoint 2016 のカスタム クレーム プロバイダーを提供する[AzureCP](https://yvand.github.io/AzureCP/)と呼ばれます。Azure AD グラフを使用すると、解決するにはどのようなユーザーを入力し、実行してが検証されます。[AzureCP](https://yvand.github.io/AzureCP/)で詳しく説明します。 

## <a name="additional-resources"></a>その他の技術情報

[WS-Federation について](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>ディスカッションへの参加

|**お問い合わせ**|**説明**|
|:-----|:-----|
|**必要なソリューション** <br/> |複数の Microsoft 製品やサービスにまたがるソリューションに関するコンテンツを作成しています。[MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) に電子メールを送信して、サーバー間のソリューションに関するご意見や、特定のソリューションに関するご質問をお寄せください。<br/> |
|**ソリューションのディスカッションへの参加** <br/> |クラウドベースのソリューションに関して強い関心がある場合は、Cloud Adoption Advisory Board (CAAB) に参加して、大規模で活発な Microsoft コンテンツ開発者、業界プロフェッショナル、および世界中のお客様の大規模で活発なコミュニティとつながることを検討してください。参加するには、Microsoft Tech Community の [CAAB (Cloud Adoption Advisory Board) スペース](https://aka.ms/caab)のメンバーとしてご自分を追加し、[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!) 宛に電子メールを送信してください。[CAAB ブログ](https://blogs.technet.com/b/solutions_advisory_board/)でコミュニティ関連のコンテンツをだれでも読むことができます。ただし、CAAB のメンバーになると、新しいクラウド導入のリソースやソリューションについての非公開 Web セミナーへの招待が送られます。<br/> |
|**記載されているアートの取得方法** <br/> |この記事にあるアートの編集可能なコピーが必要な方には、喜んでお送りします。アートの URL とタイトルを記述した電子メールを [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20) に送信してください。<br/> |
   

