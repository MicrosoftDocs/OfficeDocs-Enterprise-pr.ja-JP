---
title: Azure AD for SharePoint サーバー認証の使用
ms.author: tracyp
author: MSFTTracyP
ms.reviewer: kirke, josephd, kirks
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: '概要: azure Access Control Service をバイパスし、SAML 1.1 を使用して Azure Active Directory を使用して SharePoint Server ユーザーを認証する方法について説明します。'
ms.openlocfilehash: c2c9f33aa5e095a8b7fdde08e80cb1a61e88f3eb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070793"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Azure AD for SharePoint サーバー認証の使用

 **概要:** Azure Active Directory を使用して SharePoint Server 2016 ユーザーを認証する方法について説明します。 

<blockquote>
<p>この記事では、Azure Active Directory のグラフと対話するためのコードサンプルを示します。 このコードサンプルは、[ここ](https://github.com/kaevans/spsaml11/tree/master/scripts)からダウンロードできます。</p>
</blockquote>

SharePoint Server 2016 では、クレームベース認証を使用してユーザーを認証する機能が提供されています。これにより、ユーザーは、信頼できる別の id プロバイダーを使用して認証することにより、ユーザーを簡単に管理できます。 たとえば、Active Directory ドメインサービス (AD DS) を介してユーザー認証を管理する代わりに、Azure Active Directory (Azure AD) を使用してユーザーを認証できるようにすることができます。 これにより、ユーザー名に onmicrosoft.com サフィックスを持つクラウド専用ユーザー、オンプレミスディレクトリと同期されたユーザー、他のディレクトリからゲストユーザーを招待することができます。 また、多要素認証や高度なレポート機能などの Azure AD の機能を活用することもできます。

> [!IMPORTANT]
> この記事で説明するソリューションは、SharePoint Server 2013 でも使用できます。ただし、SharePoint Server 2013 は、メインストリームサポートの最後に近づいていることに注意してください。 詳細については、「 [Microsoft ライフサイクルポリシー](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) 」および「[更新された製品サービスポリシー (SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx))」を参照してください。

この記事では、オンプレミス AD DS の代わりに Azure AD を使用してユーザーを認証する方法について説明します。 この構成では、Azure AD は SharePoint Server 2016 の信頼できる id プロバイダーになります。 この構成では、SharePoint Server 2016 のインストール自体で使用される AD DS 認証とは別のユーザー認証方法が追加されます。 この記事を活用するには、WS-Federation を理解しておく必要があります。 詳しくは、「[WS-Federation について](https://go.microsoft.com/fwlink/p/?linkid=188052)」をご覧ください。 オンプレミスの SharePoint と Azure Active Directory との統合の詳細については、[専用チュートリアル](https://docs.microsoft.com/azure/active-directory/saas-apps/sharepoint-on-premises-tutorial)を参照してください。

![Azure AD for SharePoint 認証の使用](media/SAML11/fig1-architecture.png)

以前は、この構成には、クラウド内の Azure Access Control Service (ACS)、または Active Directory フェデレーションサービス (AD FS) をホストする環境で、SAML 2.0 から SAML 1.1 にトークンを変換するためのフェデレーションサービスが必要になりました。 Azure AD が SAML 1.1 トークンの発行を有効にするため、この変換は不要になりました。 上記の図は、この構成における SharePoint 2016 ユーザーに対する認証のしくみを示しています。これは、仲介者がこの変換を実行する必要がなくなったことを示しています。

> [!NOTE]
> この構成は、SharePoint ファームが Azure 仮想マシンとオンプレミスのどちらでホストされているかにかかわらず機能します。 ユーザーがブラウザーから Azure Active Directory にアクセスすることを保証する以外に、追加のファイアウォールポートを開く必要はありません。

SharePoint 2016 アクセシビリティの詳細については、「 [Sharepoint Server 2016 のアクセシビリティガイドライン](https://go.microsoft.com/fwlink/p/?LinkId=393123)」を参照してください。

## <a name="configuration-overview"></a>構成の概要

Azure AD を SharePoint Server 2016 id プロバイダーとして使用する環境をセットアップするには、次の一般的な手順を実行します。

1. 新しい Azure AD ディレクトリを作成するか、既存のディレクトリを使用します。
2. Azure AD でセキュリティ保護する web アプリケーションの領域が SSL を使用するように構成されていることを確認します。
3. Azure AD で新しいエンタープライズアプリケーションを作成します。
4. SharePoint Server 2016 で、新しい信頼できる id プロバイダーを構成します。
5. Web アプリケーションのアクセス許可を設定します。
6. Azure AD に SAML 1.1 トークン発行ポリシーを追加します。
7. 新しいプロバイダーを確認します。

次のセクションでは、これらのタスクを実行する方法について説明します。

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>手順 1: 新しい Azure AD ディレクトリを作成するか、既存のディレクトリを使用する

Azure Portal ([https://portal.azure.com](https://portal.azure.com)) で、新しいディレクトリを作成します。 組織名、最初のドメイン名、および国または地域を指定します。

![ディレクトリを作成する](media/SAML11/fig2-createdirectory.png) 

 Microsoft Office 365 または Microsoft Azure サブスクリプションで使用されているディレクトリなどのディレクトリが既にある場合は、代わりにそのディレクトリを使用できます。 ディレクトリにアプリケーションを登録する権限を持っている必要があります。

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>手順 2: Azure AD でセキュリティ保護する web アプリケーションの領域が SSL を使用するように構成されていることを確認する

この記事は、「 [Azure の高可用性 SharePoint Server 2016 ファームを実行する](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)」の参照アーキテクチャを使用して記述されています。 [この記事](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)で説明しているソリューションの展開に使用される記事の付属スクリプトでは、SSL を使用しないサイトを作成します。  

SAML を使用するには、アプリケーションが SSL を使用するように構成されている必要があります。 SharePoint web アプリケーションが SSL を使用するように構成されていない場合は、次の手順を使用して新しい自己署名証明書を作成し、SSL 用に web アプリケーションを構成します。 この構成は、ラボ環境のみを対象としており、運用のためのものではありません。 運用環境では、署名された証明書を使用する必要があります。

1. サーバーの**全体管理** > の [**アプリケーション** > 構成の管理] に移動して、**web アプリケーションを管理**し、SSL を使用するように拡張する必要がある web アプリケーションを選択します。 Web アプリケーションを選択し、[**リボンの拡張**] ボタンをクリックします。 同じ URL を使用し、ポート443で SSL を使用するように web アプリケーションを拡張します。<br/>![Web アプリを別の IIS サイトに拡張する](media/SAML11/fig3-extendwebapptoiis.png)<br/>
2. IIS マネージャー で、[ **サーバー証明書**] をダブルクリックします。
3. [ **操作**] ウィンドウの [ **自己署名入り証明書の作成**] をクリックします。 [ 証明書のフレンドリ名を指定してください] ボックスに証明書のフレンドリ名を入力して、[ **OK**] をクリックします。
4. [**サイトバインドの編集**] ダイアログボックスで、次の図に示されているように、ホスト名がフレンドリ名と同じであることを確認します。<br/>![IIS でサイトバインドを編集する](media/SAML11/fig4-editsitebinding.png)<br/>

SharePoint ファーム内の各 web フロントエンドサーバーには、IIS でサイトバインドの証明書を構成する必要があります。


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>手順 3: Azure AD で新しいエンタープライズアプリケーションを作成する

1. Azure Portal ([https://portal.azure.com](https://portal.azure.com)) で、azure AD ディレクトリを開きます。 [**エンタープライズアプリケーション**] をクリックし、[**新しいアプリケーション**] をクリックします。 [**ギャラリー以外のアプリケーション**] を選択します。 *SHAREPOINT SAML 統合*などの名前を入力し、[**追加**] をクリックします。<br/>![新しい非ギャラリーアプリケーションを追加する](media/SAML11/fig5-addnongalleryapp.png)<br/>
2. ナビゲーションウィンドウで [シングルサインオン] リンクをクリックして、アプリケーションを構成します。 **シングルサインオンモード**ドロップダウンを **[Saml ベースのサインオン**] に変更して、アプリケーションの SAML 構成プロパティを表示します。 次のプロパティを使用して構成します。<br/>
    - 識別子`urn:sharepoint:portal.contoso.local`
    - 応答 URL:`https://portal.contoso.local/_trust/default.aspx`
    - サインオン URL:`https://portal.contoso.local/_trust/default.aspx`
    - ユーザー識別子:`user.userprincipalname`<br/>
    - 注: セキュリティで保護する SharePoint サイトの** url を使用して、url を変更することを忘れないでください。<br/>
3. 次の行を含むテーブル (表1のような) を設定します。<br/> 
    - Realm
    - SAML 署名証明書ファイルへの完全なパス
    - SAML シングルサインオンサービス URL (/に置き換えられる/ *saml2*を */ws給紙*)
    - アプリケーションオブジェクト ID。 <br/>
*識別子*の値を*Realm*プロパティにテーブルにコピーします (以下の表1を参照してください)。
4. 変更内容を保存します。
5. [ **Configure (app name)** ] リンクをクリックして、[サインオンの構成] ページにアクセスします。<br/>![シングルサインオンページを構成する](media/SAML11/fig7-configssopage.png)<br/> 
    -  Saml 署名証明書 **-Raw**リンクをクリックして、Saml 署名証明書を .cer 拡張子のファイルとしてダウンロードします。 ダウンロードしたファイルへの完全なパスをコピーして、テーブルに貼り付けます。
    - SAML シングルサインオンサービス URL のリンクをコピーしてに貼り付け、URL の */saml2*部分を */ws給紙*で置き換えます。<br/>
6.  アプリケーションの [**プロパティ**] ウィンドウに移動します。 オブジェクト ID の値をコピーして、手順3で設定したテーブルに貼り付けます。<br/>![アプリケーションの [プロパティ] ウィンドウ](media/SAML11/fig8-propertiespane.png)<br/>
7. 取得した値を使用して、手順3で設定したテーブルが次の表1のようになっていることを確認します。


| 表 1: 取得した値  |  |
|---------|---------|
|Realm | `urn:sharepoint:portal.contoso.local` |
|SAML 署名証明書ファイルへの完全なパス | `C:/temp/SharePoint SAML Integration.cer`  |
|SAML シングルサインオンサービスの URL (/に置き換えて、saml2 を/ws給紙) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|アプリケーションオブジェクト ID | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> URL の */saml2*の値を */ws給紙*に置き換えます。 */Saml2*エンドポイントは、SAML 2.0 トークンを処理します。 */Ws給紙*エンドポイントを使用すると、saml 1.1 トークンが処理され、SHAREPOINT 2016 SAML フェデレーションに必要になります。

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>手順 4: SharePoint Server 2016 で新しい信頼できる id プロバイダーを構成する

SharePoint Server 2016 サーバーにサインインし、SharePoint 2016 管理シェルを開きます。 表1の $realm、$wsfedurl、および $filepath の値を入力し、次のコマンドを実行して、新しい信頼できる id プロバイダーを構成します。

> [!TIP]
> PowerShell を初めて使用する場合や、PowerShell のしくみの詳細については、「 [SharePoint powershell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps)」を参照してください。 

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

次に、以下の手順に従って、アプリケーションに対して信頼できる id プロバイダーを有効にします。
1. サーバーの全体管理で、[ **Web アプリケーションの管理**] に移動し、Azure AD でセキュリティ保護する web アプリケーションを選択します。 
2. リボンで [**認証プロバイダー** ] をクリックし、使用する領域を選択します。
3. [**信頼できる id プロバイダー** ] を選択し、 *AzureAD*という名前で登録したプロバイダーを選択します。  
4. [サインインページの URL] 設定で、[**カスタムサインインページ**] を選択し、値 "//trust/" を指定します。 
5. **[OK]** をクリックします。

![認証プロバイダを構成する](media/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> 表示されているように、カスタムのサインインページを "/" trust/"に設定するなど、すべての手順に従うことが重要です。 すべての手順に従っていない限り、構成は正しく機能しません。

## <a name="step-5-set-the-permissions"></a>手順 5: アクセス許可を設定する

Azure AD にログインし、SharePoint にアクセスするユーザーには、アプリケーションへのアクセス権が付与されている必要があります。 

1. Azure Portal で Azure AD ディレクトリを開きます。 [**エンタープライズアプリケーション**] をクリックし、[**すべてのアプリケーション**] をクリックします。 以前に作成したアプリケーション (SharePoint SAML 統合) をクリックします。
2. [**ユーザーとグループ] を**クリックします。 
3. Azure AD を使用して SharePoint にログインするためのアクセス許可を持つユーザーまたはグループを追加するには、[**ユーザーの追加**] をクリックします。
4. ユーザーまたはグループを選択し、[**割り当て**] をクリックします。
 
ユーザーには Azure AD でのアクセス許可が付与されていますが、SharePoint でアクセス許可を付与する必要もあります。 以下のステップを使用して、Web アプリケーションにアクセスするためのアクセス許可を設定します。

1. サーバーの全体管理で、 **[アプリケーション構成の管理]** をクリックします。
2. [ **アプリケーション構成の管理**] ページの [ **Web アプリケーション**] セクションで、[ **Web アプリケーションの管理**] をクリックします。
3. 適切な Web アプリケーションをクリックし、[ **ユーザー ポリシー**] をクリックします。
4. [Web アプリケーションのポリシー] で、[**ユーザーの追加**] をクリックします。<br/>![ユーザーを名前クレームで検索する](media/SAML11/fig11-searchbynameclaim.png)<br/>
5. [ **ユーザーの追加**] ダイアログ ボックスの [ **領域**] で適切な領域をクリックし、[ **次へ**] をクリックします。
6. [ **Web アプリケーションのポリシー** ] ダイアログボックスの [**ユーザーの選択**] セクションで、[**参照**] アイコンをクリックします。
7. [**検索**] テキストボックスに、ディレクトリ内のユーザーのサインイン名を入力し、[**検索**] をクリックします。 <br/>例: *demouser@blueskyabove.onmicrosoft.com*。
8. リストビューの AzureAD 見出しの下で、[名前] プロパティを選択し、[**追加**]、[ **OK** ] の順にクリックしてダイアログを閉じます。
9. [アクセス許可] で、[**フルコントロール**] をクリックします。<br/>![クレームユーザーにフルコントロールを付与する](media/SAML11/fig12-grantfullcontrol.png)<br/>
10. [ **完了**]、[ **OK**] の順にクリックします。

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>手順 6: Azure AD で SAML 1.1 トークン発行ポリシーを追加する

Azure AD アプリケーションがポータルで作成されると、既定では SAML 2.0 が使用されます。 SharePoint Server 2016 には、SAML 1.1 トークン形式が必要です。 次のスクリプトは、既定の SAML 2.0 ポリシーを削除し、SAML 1.1 トークンを発行するための新しいポリシーを追加します。 

> このコードでは、 [Azure Active Directory のグラフと対話](https://github.com/kaevans/spsaml11/tree/master/scripts)することを示す付属のサンプルをダウンロードする必要があります。 GitHub から Windows デスクトップにスクリプトを ZIP ファイルとしてダウンロードする場合は、スクリプトモジュールファイルおよび`MSGraphTokenLifetimePolicy.psm1` `Initialize.ps1`スクリプトファイルのブロックを解除してください ([プロパティ] を右クリックし、[ブロック解除] をクリックし、[OK] をクリックします)。 
![ダウンロードしたファイルのブロック解除](media/SAML11/fig17-unblock.png)

サンプルスクリプトをダウンロードした後、次のコードを使用して新しい PowerShell スクリプトを作成します。プレースホルダーは、ローカル`Initialize.ps1`コンピューターにダウンロードされたファイルのパスに置き換えられます。 Application オブジェクト ID プレースホルダーを、表1に入力したアプリケーションオブジェクト ID に置き換えます。 作成したら、PowerShell スクリプトを実行します。 

```
function AssignSaml11PolicyToAppPrincipal
{
    Param(
        [Parameter(Mandatory=$true)]
        [string]$pathToInitializeScriptFile, 
        [Parameter(Mandatory=$true)]
        [string]$appObjectid
    )

    $folder = Split-Path $pathToInitializeScriptFile
    Push-Location $folder

    #Loads the dependent ADAL module used to acquire tokens
    Import-Module $pathToInitializeScriptFile 

    #Gets the existing token issuance policy
    $existingTokenIssuancePolicy = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $appObjectid | ?{$_.type -EQ "TokenIssuancePolicy"} 
    Write-Host "The following TokenIssuancePolicy policies are assigned to the service principal." -ForegroundColor Green
    Write-Host $existingTokenIssuancePolicy -ForegroundColor White
    $policyId = $existingTokenIssuancePolicy.objectId

    #Removes existing token issuance policy
    Write-Host "Only a single policy can be assigned to the service principal. Removing the existing policy with ID $policyId" -ForegroundColor Green
    Remove-PolicyFromServicePrincipal -policyId $policyId -servicePrincipalId $appObjectid

    #Creates a new token issuance policy and assigns to the service principal
    Write-Host "Adding the new SAML 1.1 TokenIssuancePolicy" -ForegroundColor Green
    $policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
    Write-Host "Assigning the new SAML 1.1 TokenIssuancePolicy $policy.objectId to the service principal $appObjectid" -ForegroundColor Green
    Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $appObjectid
    Pop-Location
}

#Only edit the following two variables
$pathToInitializeScriptFile = "<file path of Initialize.ps1>"
$appObjectid = "<Application Object ID from Table 1>"

AssignSaml11PolicyToAppPrincipal $pathToInitializeScriptFile $appObjectid
```
> [!IMPORTANT]
> PowerShell スクリプトが署名されていないため、実行ポリシーを設定するように求めるメッセージが表示される場合があります。 実行ポリシーの詳細については、「[実行ポリシーについ](http://go.microsoft.com/fwlink/?LinkID=135170)て」を参照してください。 また、サンプルスクリプトに含まれているコマンドを正常に実行するために、管理者特権のコマンドプロンプトを開く必要がある場合があります。

これらの PowerShell コマンドの例は、Graph API に対してクエリを実行する方法の例です。 Azure AD でのトークン発行ポリシーの詳細については、「 [GRAPH API reference for operations on policy](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy)」を参照してください。

## <a name="step-7-verify-the-new-provider"></a>手順 7: 新しいプロバイダーを確認する

前の手順で構成した web アプリケーションの URL に対してブラウザーを開きます。 Azure AD にサインインするようにリダイレクトされます。

![フェデレーション用に構成された Azure AD へのサインイン](media/SAML11/fig13-examplesignin.png)

サインインしたままにするかどうかを確認するメッセージが表示されます。

![サインイン状態を維持するかどうか](media/SAML11/fig14-staysignedin.png)

最後に、Azure Active Directory テナントから、ユーザーとしてログインしているサイトにアクセスできます。

![SharePoint にサインインしているユーザー](media/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>証明書の管理
上記の手順4で信頼できる id プロバイダーに対して構成されている署名証明書には有効期限があり、更新する必要があることを理解しておくことが重要です。 証明書の更新については、「 [Azure Active Directory でフェデレーションシングルサインオンの証明書を管理](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs)する」を参照してください。 Azure AD で証明書が更新されたら、ローカルファイルにダウンロードし、次のスクリプトを使用して、更新された署名証明書を使用して信頼できる id プロバイダーを構成します。 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>複数の web アプリケーションに対して1つの信頼できる id プロバイダーを構成する
構成は単一の web アプリケーションに対して機能しますが、複数の web アプリケーションに同じ信頼できる id プロバイダーを使用する場合は、追加の構成が必要です。 たとえば、URL `https://portal.contoso.local`を使用するように web アプリケーションを拡張し、ユーザーを`https://sales.contoso.local`認証するためにも使用するとします。 これを行うには、id プロバイダーを更新して WReply パラメーターに従って、応答 URL を追加するように Azure AD のアプリケーション登録を更新する必要があります。

1. Azure Portal で Azure AD ディレクトリを開きます。 [**アプリの登録**] をクリックし、[**すべてのアプリケーションの表示**] をクリックします。 以前に作成したアプリケーション (SharePoint SAML 統合) をクリックします。
2. [**設定**] をクリックします。
3. [設定] ブレードで、[ **url の応答**] をクリックします。 
4. その URL に追加する web アプリケーション`/_trust/default.aspx`の url (など`https://sales.contoso.local/_trust/default.aspx`) を追加し、[**保存**] をクリックします。 
5. SharePoint server で、 **sharepoint 2016 管理シェル**を開き、以前に使用した信頼できる id トークンの発行元の名前を使用して、次のコマンドを実行します。

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. サーバーの全体管理で、web アプリケーションに移動し、既存の信頼できる id プロバイダーを有効にします。 サインインページの URL も、カスタムのサインインページ`/_trust/`として構成することを忘れないでください。
7. サーバーの全体管理で、web アプリケーションをクリックし、[**ユーザーポリシー**] を選択します。 この記事で前述したように、適切なアクセス許可を持つユーザーを追加します。

## <a name="fixing-people-picker"></a>ユーザー選択ウィンドウの修正
ユーザーは Azure AD から id を使用して SharePoint 2016 にログインできるようになりましたが、ユーザーエクスペリエンスの向上にはまだ機会があります。 たとえば、ユーザーの検索では、ユーザー選択ウィンドウに複数の検索結果が表示されます。 クレームマッピングで作成された3つのクレームの種類ごとに検索結果があります。 ユーザー選択ウィンドウを使用してユーザーを選択するには、ユーザー名を正確に入力し、クレーム結果の**名前**を選択する必要があります。

![クレーム検索の結果](media/SAML11/fig16-claimssearchresults.png)

検索する値に検証はありません。これにより、スペルミスやユーザーが、**姓**の要求など、誤ったクレームの種類を誤って選択してしまう可能性があります。 これにより、ユーザーがリソースに正常にアクセスできなくなることがあります。

このシナリオを支援するために、SharePoint 2016 用のカスタムクレームプロバイダーを提供する[AzureCP](https://yvand.github.io/AzureCP/)という名前のオープンソースソリューションがあります。 Azure AD Graph を使用して、ユーザーが入力して検証を実行する対象を解決します。 詳細については、「 [AzureCP](https://yvand.github.io/AzureCP/)」を参照してください。 

## <a name="additional-resources"></a>追加リソース

[WS-Federation について](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>ディスカッションへの参加

|**お問い合わせ**|**説明**|
|:-----|:-----|
|**必要なソリューション** <br/> |複数の Microsoft クラウド プラットフォームおよびサービスにまたがるクラウド導入のコンテンツを作成しています。クラウド導入のコンテンツについてのご意見や特定のコンテンツの依頼を、電子メールで [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 宛にお寄せください。<br/> |
|**ソリューションのディスカッションへの参加** <br/> |クラウドベースのソリューションに関して強い関心がある場合は、Cloud Adoption Advisory Board (CAAB) に参加して、大規模で活発な Microsoft コンテンツ開発者、業界プロフェッショナル、および世界中のお客様の大規模で活発なコミュニティとつながることを検討してください。参加するには、Microsoft Tech Community の [CAAB (Cloud Adoption Advisory Board) スペース](https://aka.ms/caab)のメンバーとしてご自分を追加し、[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!) 宛に電子メールを送信してください。[CAAB ブログ](https://blogs.technet.com/b/solutions_advisory_board/)でコミュニティ関連のコンテンツをだれでも読むことができます。ただし、CAAB のメンバーになると、新しいクラウド導入のリソースやソリューションについての非公開 Web セミナーへの招待が送られます。<br/> |
|**記載されているアートの取得方法** <br/> |この記事にあるアートの編集可能なコピーが必要な方には、喜んでお送りします。アートの URL とタイトルを記述した電子メールを [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20) に送信してください。<br/> |
   

