---
title: "SharePoint 2013 認証に Microsoft Azure Active Directory を使用する"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: "概要: Azure Access Control Service を使用して、SharePoint Server 2013 ユーザーを Azure Active Directory で認証する方法について説明します。"
---

# SharePoint 2013 認証に Microsoft Azure Active Directory を使用する

 **概要:** Azure Access Control Service を使用して、SharePoint Server 2013 ユーザーを Azure Active Directory で認証する方法について説明します。
  
異なる ID プロバイダーを使用してユーザーを認証すると、ユーザーの管理がより簡単になります。信頼性のある、他人が管理する ID プロバイダーを使用できると非常に便利です。たとえば、クラウドで SharePoint Server 2013 にアクセスするユーザーの認証と、オンプレミス環境の SharePoint 2013 ユーザー用の認証にそれぞれ別のものを使用できます。Azure Access Control Service を使用すると、こうした選択が可能になります。
  
この記事では、Azure Access Control Service を使用して SharePoint 2013 ユーザーを、オンプレミスの Active Directory ではなく Azure AD で認証する方法について説明します。この構成の場合、Azure AD が SharePoint 2013 に対する信頼できる ID プロバイダーとなります。この構成では、SharePoint 2013 インストール自体で使用される Active Directory 認証とは別のユーザー認証方式が追加されます。この記事を活用するには、WS-Federation を理解しておく必要があります。詳しくは、「[WS-Federation について](https://go.microsoft.com/fwlink/p/?linkid=188052)」をご覧ください。
  
次の図は、この構成における SharePoint 2013 ユーザーに対する認証のしくみを示しています。
  
![Azure Active Directory で認証されたユーザー](images/SP_AzureAD.png)
  
この記事で使用されている例は、Azure CoE (Center of Excellence) の Microsoft 設計者である Kirk Evans によって提供されています。
  
SharePoint 2013 のアクセシビリティについては、「[SharePoint 2013 のアクセシビリティ](https://go.microsoft.com/fwlink/p/?LinkId=393123)」をご覧ください。
  
## 構成の概要

以下の一般的な手順を使用して、Azure AD を SharePoint 2013 ID プロバイダーとして使用する環境をセットアップします。
  
1. 新しい Azure AD テナントと名前空間を作成します。
    
2. WS-Federation ID プロバイダーを追加します。
    
3. SharePoint を証明書利用者アプリケーションとして追加します。
    
4. SSL に使用する自己署名入り証明書を作成します。
    
5. クレームベース認証の規則グループを作成します。
    
6. X.509 証明書を構成します。
    
7. クレーム マッピングを作成します。
    
8. 新しい ID プロバイダー用に SharePoint を構成します。
    
9. アクセス許可を設定します。
    
10. 新しいプロバイダーを確認します。
    
## Azure AD テナントと名前空間の作成

以下のステップを使用して、新しい Azure AD テナントと、関連する名前空間を作成します。この例の場合、「blueskyabove」という名前空間を使用します。
  
1. Azure 管理ポータルで、[ **Active Directory**] をクリックしてから新しい Azure AD テナントを作成します。
    
2. [ **Access Control 名前空間**] をクリックし、新しい名前空間を作成します。
    
3. 下部にあるバーで [ **管理**] をクリックします。これにより、 https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web が開くはずです。
    
4. Windows PowerShell を開きます。Windows PowerShell 用に Microsoft Online Services モジュールを使用します。このモジュールは、Azure for Windows PowerShell コマンドレットをインストールするための前提条件です。
    
5. Windows PowerShell コマンド プロンプトで、 `Connect-Msolservice` コマンドを入力してから、資格情報を入力します。
    
    > [!NOTE]
    > Azure for Windows PowerShell コマンドレットの使用方法について詳しくは、「[Windows PowerShell による Azure AD の管理](https://go.microsoft.com/fwlink/p/?LinkId=393124)」をご覧ください。 
  
6. Windows PowerShell コマンド プロンプトで、以下のコマンドを入力します。
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    次の図は、出力結果を示しています。
    
     ![作成中のサービス プリンシパル名](images/ServicePrincipalNames.jpg)
  
## 名前空間への WS-Federation IP プロバイダーの追加

以下のステップを使用して、新しい WS-Federation ID プロバイダーを blueskyabove 名前空間に追加します。
  
1. Azure 管理ポータルで [ **Active Directory**] > [ **Access Control 名前空間**] と移動し、[ **新しいインスタンスの作成**]、[ **管理**] の順にクリックします。
    
2. Azure Access Control ポータルで、次の図に示されているように [ **ID プロバイダー**] > [ **追加**] とクリックします。
    
     ![Azure の [ID プロバイダー] ダイアログ ボックス](images/Identity.jpg)
  
3. 次の図に示されているように、[ **WS-Federation ID プロバイダー**] をクリックしてから [ **次へ**] をクリックします。
    
     ![ID プロバイダー追加の設定](images/AddIdentity.jpg)
  
4. 表示名とログオン リンク テキストを記入し、[ **保存**] をクリックします。WS-Federation メタデータの URL には、https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml と入力します。以下の図にこの設定が示されています。
    
     ![フェデレーション ID プロバイダー](images/FederationIdentity.jpg)
  
## 証明書利用者アプリケーションとしての SharePoint の追加

以下のステップを実行して、SharePoint を証明書利用者アプリケーションとして追加します。
  
証明書利用者アプリケーションの設定について詳しくは、「[証明書利用者アプリケーション](https://go.microsoft.com/fwlink/p/?LinkId=393125)」をご覧ください。
  
1. Azure Access Control ポータルで、次の図に示されているように [ **証明書利用者アプリケーション**]、[ **追加**] の順にクリックします。
    
     ![台北の証明書利用者アプリケーションの設定](images/RelyingPartyApplications.jpg)
  
## SSL に使用するための自己署名入り証明書の作成

以下のステップを実行して、SSL を使用した保護された通信に使用する新しい自己署名入り証明書を作成します。
  
1. 次の図に示されているように、PublishingSite と同じ URL を使用するものの、ポート 443 で SSL を使用するように Web アプリケーションを拡張します。
    
     ![アプリケーションを拡張する設定](images/ExtendWebApp.jpg)
  
2. IIS マネージャー で、[ **サーバー証明書**] をダブルクリックします。
    
3. [ **操作**] ウィンドウの [ **自己署名入り証明書の作成**] をクリックします。[ **証明書のフレンドリ名を指定してください**] ボックスに証明書のフレンドリ名を入力して、[ **OK**] をクリックします。
    
4. [ **サイト バインドの編集**] ダイアログ ボックスで、次の図に示されているように、ホスト名がフレンドリ名と同じであることを確認します。
    
     ![自己署名証明書ウィザード](images/SelfSignedCert.jpg)
  
     ![[バインドの編集] ボックスに入力したホスト名](images/SelfSignedCert1.jpg)
  
5. Azure 管理ポータルで、構成対象の仮想マシンをクリックして [ **エンドポイント**] をクリックします。
    
6. [ **追加**]、[ **-->**] ([次へ]) の順にクリックします。
    
7. [ **名前**] に、エンドポイントの名前を入力します。
    
8. [ **パブリック ポート**] と [ **プライベート ポート**] には、使用するポート番号を入力し、チェックマークをクリックして完了します。これらの番号は異なっていても問題ありません。この記事の目的上、ここでは以下の図に示されているように 443 を使用しています。
    
     ![Azure のエンドポイント設定](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > Azure の仮想マシンにエンドポイントを追加する方法について詳しくは、「[仮想マシンに対してエンドポイントを設定する方法](https://go.microsoft.com/fwlink/p/?LinkId=393126)」をご覧ください。 
  
9. Access Control Services ポータルから、次の図に示されているように、証明書利用者を追加します。
    
     ![証明書利用者の追加アプリケーションの設定](images/AddRelyingParty.jpg)
  
## クレーム ベース認証のための規則グループの作成

以下のステップを使用して、クレーム ベース認証を制御するための新しい規則グループを作成します。
  
1. 左側のウィンドウで、[ **規則グループ**] 、[ **追加**] の順にクリックします。
    
2. 規則グループの名前を入力して [ **保存**] をクリックし、次に [ **生成**] をクリックします。この記事の目的上、次の図に示されているように、ここでは「 **Default Rule Group for. spvms.cloudapp.net** 」と入力します。
    
     ![Azure での規則グループの設定](images/RuleGroup.jpg)
  
     ![[生成] を選択した後の規則](images/GenerateRules.jpg)
  
    > [!NOTE]
    > 規則グループの作成方法について詳しくは、「[規則グループと規則](https://go.microsoft.com/fwlink/p/?LinkId=393128)」をご覧ください。 
  
3. 変更する規則グループをクリックし、次に変更するクレーム規則をクリックします。この記事の目的上、次の図に示されているように、ここでは **name** を **upn** として渡すクレーム規則をグループに追加します。
    
     ![Azure アクセス制御の要求規則](images/ClaimRules.jpg)
  
4. 次の図に示されているように、 **upn** という名前のクレーム規則を削除し、 **Name Claim to UPN** 規則を中止します。
    
     ![Azure アクセス制御の規則設定](images/ClaimToUPN.jpg)
  
## X.509 証明書の構成

以下のステップを使用して、トークンの署名に使用する X.509 証明書を構成します。
  
1. Access Control Service ウィンドウの [ **開発**] で、[ **アプリケーション統合**] をクリックします。
    
2. [ **エンドポイント参照**] で、Azure に関連付けられている **Federation.xml** を特定し、ブラウザーのアドレス バーにその場所をコピーします。
    
3. **Federation.xml** ファイルで **RoleDescriptor** セクションを特定し、次の図に示されているように、 _<X509Certificate>_ 要素の情報をコピーします。
    
     ![Federation.xml  ファイルの X509 証明書要素](images/X509Cert.jpg)
  
4. ドライブ C:\\ のルートに、 **Certificates** という名前のフォルダーを作成します。
    
5. X509Certificate 情報を、フォルダー C:\\Certificates に **AcsTokenSigning.cer** というファイル名で保存します。
    
    > [!NOTE]
    > このファイル名は, .cer 拡張子を付けて保存する必要があります。 
  
     ![X509Certificate 要素をファイルとして保存する](images/X509Cert_Save.jpg)
  
## Windows PowerShell によるクレーム マッピングの作成

以下のステップを使用して、Windows PowerShell によってクレーム マッピングを作成します。
  
次のメンバーシップがあることを確認してください。
  
1. SQL Server インスタンスにおける **securityadmin** 固定サーバー ロール。
    
2. 更新されるすべてのデータベースに対する **db_owner** 固定データベース ロール。
    
3. Windows PowerShell コマンドレットを実行するサーバーでの Administrators グループ。
    
管理者は **Add-SPShellAdmin** コマンドレットを使用して、SharePoint 2013のコマンドレットを使用する権限を付与できます。
  
> [!NOTE]
> アクセス許可がない場合、セットアップ管理者または SQL Server 管理者に連絡してアクセス許可を要求してください。Windows PowerShell アクセス許可について詳しくは、「[Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx)」をご覧ください。 
  
1. [ **スタート**] メニューから、[ **すべてのプログラム**] をクリックします。
    
2. [ **Microsoft SharePoint 2013 製品**] をクリックします。
    
3. [ **SharePoint 2013 管理シェル**] をクリックします。
    
4. Windows PowerShell コマンド プロンプトで、クレーム マッピングを作成するための次のコマンドを入力します。
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## 新しい ID プロバイダー用の SharePoint の構成

以下のステップを使用して、ご使用の SharePoint インストール環境を、Azure AD の新しい ID プロバイダーに対して構成します。
  
1. この手順を実行するユーザー アカウントが、ファーム管理者 SharePoint グループのメンバーであることを確認してください。
    
2. サーバーの全体管理 のホーム ページで [ **アプリケーション構成の管理**] をクリックします。
    
3. [ **アプリケーション構成の管理**] ページの [ **Web アプリケーション**] セクションで、[ **Web アプリケーションの管理**] をクリックします。
    
4. 適切な Web アプリケーションをクリックします。
    
5. リボンの [ **認証プロバイダー**] をクリックします。
    
6. [ **領域**] で、領域の名前をクリックします。たとえば、[ **既定**] などです。
    
7. [ **認証の編集**] ページの [ **クレーム認証の種類**] セクションで [ **信頼できる ID プロバイダー**] を選択し、プロバイダーの名前をクリックします。この記事では、「 **ACS Provider** 」をクリックします。次に、[ **OK**] をクリックします。
    
8. 次の図は、 **Trusted Provider** の設定を示しています。
    
![Web アプリの信頼できるプロバイダーの設定](images/AddProvider_Azure.jpg)
  
## アクセス許可の設定

以下のステップを使用して、Web アプリケーションにアクセスするためのアクセス許可を設定します。
  
1. サーバーの全体管理のホーム ページで、[ **アプリケーション構成の管理**] をクリックします。
    
2. [ **アプリケーション構成の管理**] ページの [ **Web アプリケーション**] セクションで、[ **Web アプリケーションの管理**] をクリックします。
    
3. 適切な Web アプリケーションをクリックし、[ **ユーザー ポリシー**] をクリックします。
    
4. [ **Web アプリケーションのポリシー**] で [ **ユーザーの追加**] をクリックします。
    
5. [ **ユーザーの追加**] ダイアログ ボックスの [ **領域**] で適切な領域をクリックし、[ **次へ**] をクリックします。
    
6. [ **ユーザーの追加**] ダイアログ ボックスに、user2@blueskyabove.onmicrosoft.com (ACS Provider) と入力します。
    
7. [ **アクセス許可**] で、[ **フル コントロール**] をクリックします。
    
8. [ **完了**]、[ **OK**] の順にクリックします。
    
次の図は、既存の Web アプリケーションの [ **ユーザーの追加**] セクションを示しています。
  
![既存の Web アプリにユーザーを追加する方法](images/AddUsers_Azure.jpg)
  
## 新しいプロバイダーの確認

以下のステップを使用して、新しい認証プロバイダーがサインイン プロンプトに表示されていることを確認し、新しい ID プロバイダーが動作していることを確かめます。
  
1. 次の図に示されているように、 **Blue Sky Above** という新しいプロバイダーを使用してサインインします。
    
     ![サインイン ダイアログ ボックスに新しい信頼できるプロバイダーが表示されている図](images/BlueSkyAbove.jpg)
  
## その他の技術情報

[WS-Federation について](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
**ディスカッションへの参加**

|**お問い合わせ**|**説明**|
|:-----|:-----|
|**必要なソリューション** <br/> |複数の Microsoft 製品やサービスにまたがるソリューションに関するコンテンツを作成しています。[MODAcontent@microsoft.com](mailto:modacontent@microsoft.com? Subject=[Solution%20Feedback]:%20) に電子メールを送信して、サーバー間のソリューションに関するご意見や、特定のソリューションに関するご質問をお寄せください。 <br/> |
|**ソリューションのディスカッションへの参加** <br/> |ソリューションについてご意見をお持ちの場合は、ソリューション アドバイザリ ボード (SAB) へ参加して、Microsoft ソリューション コンテンツの開発者、業界の専門家、世界中のお客様の大規模で活気に満ちたコミュニティに接続することをご検討ください。参加するには、電子メールを [SAB@microsoft.com](mailto:sab@microsoft.com?Subject=Request%20to%20join%20the%20Solutions%20Advisory%20Board) に送信してください。どなたでも[SAB のブログ](http://blogs.technet.com/b/solutions_advisory_board/)でコミュニティに関連するコンテンツをお読みいただけます。しかし、SAB のメンバーは、プライベートなソリューション ウェビナーにアクセスでき、SAB の Yammer ネットワークに参加できます。  <br/> |
|**記載されているアートの取得方法** <br/> |「[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)」のコンテンツ内にあるアートの編集可能なコピーが必要な方には、喜んでお送りします。アートの URL とタイトルを記述した電子メールを [MODAcontent@microsoft.com](mailto:modacontent@microsoft.com?subject=[Art%20Request]:%20) に送信してください。 <br/> |
   

