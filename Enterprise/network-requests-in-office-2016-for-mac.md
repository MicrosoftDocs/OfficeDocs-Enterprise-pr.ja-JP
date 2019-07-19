---
title: Office for Mac でのネットワーク要求
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Office for Mac アプリケーションは、macOS プラットフォームでネイティブのアプリ環境を提供します。 各アプリは、ネットワークアクセスが利用できない場合の状態など、さまざまなシナリオで動作するように設計されています。 コンピューターがネットワークに接続されている場合、アプリケーションは自動的に一連の web ベースのサービスに接続して、強化された機能を提供します。 このホワイトペーパーでは、アプリケーションが到達しようとしているエンドポイントと Url、および提供されるサービスについて説明します。 この情報は、ネットワーク構成の問題をトラブルシューティングしたり、ネットワークプロキシサーバーのポリシーを設定するときに役立ちます。 この記事の詳細は、「Office 365 の URL とアドレスの範囲」の記事を補完することを目的としています。
ms.openlocfilehash: 44acbc83b2bb32e60a470dc5d3ba27f13cbd033c
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2019
ms.locfileid: "35781957"
---
# <a name="network-requests-in-office-for-mac"></a>Office for Mac でのネットワーク要求

Office for Mac アプリケーションは、macOS プラットフォームでネイティブのアプリ環境を提供します。 各アプリは、ネットワークアクセスが利用できない場合の状態など、さまざまなシナリオで動作するように設計されています。 コンピューターがネットワークに接続されている場合、アプリケーションは自動的に一連の web ベースのサービスに接続して、強化された機能を提供します。 次の情報は、アプリケーションが到達しようとしているエンドポイントと Url、および提供されているサービスについて説明しています。 この情報は、ネットワーク構成の問題をトラブルシューティングし、ネットワークプロキシサーバーのポリシーを設定するときに役立ちます。 この記事の詳細は、Microsoft Windows を実行しているコンピューターのエンドポイントを含む[Office 365 の URL とアドレス範囲の記事](urls-and-ip-address-ranges.md)を補完することを目的としています。 記載されていない限り、この記事の情報は Office 2019 for Mac および Office 2016 for Mac にも適用されます。これは、小売店からのワンタイム購入またはボリュームライセンス契約を通じて利用できます。 

  
この記事のほとんどは、ネットワーク Url、種類、およびそのエンドポイントによって提供される機能の説明を詳述している表です。 各 Office アプリは、サービスとエンドポイントの使用状況によって異なる場合があります。 以下の表では、次のアプリが定義されています。
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
URL の種類は次のように定義されています。
  
- ST: Static-URL はクライアントアプリケーションにハードコーディングされます。
    
- SS: 準静的-URL は web ページまたはリダイレクターの一部としてエンコードされます。
    
- CS: Config Service-URL は Office 構成サービスの一部として返されます。

    
## <a name="office-for-mac-default-configuration"></a>Office for Mac の既定の構成

 **インストールと更新**
  
次のネットワークエンドポイントを使用して、Microsoft コンテンツ配信ネットワーク (CDN) から Office for Mac インストールプログラムをダウンロードします。
  
|**URL**|**型**|**説明**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |停止  <br/> |Office 365 インストールポータルの転送リンクサービスを最新のインストールパッケージに移動します。  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |秒  <br/> |コンテンツ配信ネットワーク上のインストールパッケージの場所。  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |秒  <br/> |コンテンツ配信ネットワーク上のインストールパッケージの場所。  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |停止  <br/> |Microsoft AutoUpdate の管理制御エンドポイント  <br/> |
   
 **最初のアプリの起動**
  
Office アプリを初めて起動したときに、次のネットワークエンドポイントに連絡します。 これらのエンドポイントは、ユーザーに対して Office の機能が強化されており、ライセンスの種類 (ボリュームライセンスのインストールを含む) に関係なく、Url に連絡します。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPS ON  <br/> |停止  <br/> |' Flighting ' 構成-機能が明るくなり、実験ができます。  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPS ON  <br/> |停止  <br/> |' Flighting ' ネットワーク構成テスト  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPS ON  <br/> |停止  <br/> |' Flighting ' ネットワーク構成テスト  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPS ON  <br/> |停止  <br/> |Office 構成サービス-サービスエンドポイントのマスターリスト。  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPS ON  <br/> |停止  <br/> |Office ルールテレメトリダウンロード-テレメトリサービスにアップロードするデータとイベントについてクライアントに通知します。  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |座標  <br/> |OneNote テレメトリサービス  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPS ON  <br/> |停止  <br/> |Office テレメトリアップロードのレポート-クライアント上で発生する "Heartbeart" およびエラーイベントがテレメトリサービスにアップロードされます。  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |座標  <br/> |Office テンプレートサービス-ユーザーにオンラインドキュメントテンプレートを提供します。  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |座標  <br/> |Office テンプレートのダウンロード-PNG テンプレートイメージの保存。  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |座標  <br/> |Office アプリの構成を保存します。  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |座標  <br/> |Office Document Integration Services Catalog (サービスとエンドポイントの一覧) およびホーム領域の検出。  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPS ON  <br/> |座標  <br/> |ホーム領域検出 v2 のリソース (15.40 以降)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPS ON  <br/> |停止  <br/> |Microsoft AutoUpdate マニフェスト-利用可能な更新プログラムがあるかどうかを確認します。  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |秒  <br/> |Microsoft Ajax JavaScript ライブラリ  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |秒  <br/> |Office の構成とリソースのウィキペディアアプリ。  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |秒  <br/> |Office の構成とリソース用の Bing マップアプリ。  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |秒  <br/> |Office の構成とリソース用の People Graph アプリ。  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |停止  <br/> |OneNote の新しいコンテンツ。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |停止  <br/> |OneNote の新しいコンテンツ。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |秒  <br/> |OneNote の新しい画像について説明します。  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |停止  <br/> |アプリ内サポートサービス。  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |停止  <br/> |電子メールアカウント検出サービス。  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |停止  <br/> |Outlook 自動検出  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |停止  <br/> |Office 365 サービス用の Outlook エンドポイント。  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |停止  <br/> |Outlook アドインのアイコン。  <br/> |
   
> [!NOTE]
> Office 構成サービスは、Mac だけでなく、すべての Microsoft Office クライアントに対して自動検出サービスとして機能します。 応答で返されたエンドポイントは、その変更では非常に静的なので、それでも可能です。 
  
 **サインイン**
  
クラウドベースのストレージにサインインするときに、次のネットワークエンドポイントに連絡します。 アカウントの種類に応じて、異なるサービスに連絡することができます。 次に例を示します。
  
- **MSA: Microsoft アカウント**-一般に、コンシューマーおよびリテールシナリオで使用されます。 
    
- **Orgid: 組織アカウント**-一般に、商業シナリオで使用されます。 
    
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPS ON  <br/> |停止  <br/> |Windows 認証サービス  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPS ON  <br/> |停止  <br/> |Office 365 ログインサービス (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPS ON  <br/> |停止  <br/> |Microsoft アカウントログインサービス (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPS ON  <br/> |座標  <br/> |Microsoft アカウントログインサービスヘルパー (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPS ON  <br/> |秒  <br/> |Office 365 ログインブランド化 (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |座標  <br/> |ドキュメントと場所のストレージロケーター  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |座標  <br/> |最近使用した (MRU) ドキュメントサービス  <br/> |
   
> [!NOTE]
> サブスクリプションベースおよびリテールライセンスの場合、両方のサインインで製品がアクティブ化され、OneDrive などのクラウドリソースにアクセスできるようになります。 ボリュームライセンスがインストールされている場合、ユーザーは (既定では) サインインを求められますが、その製品は既にアクティブ化されているので、クラウドリソースにアクセスする場合にのみ必要になります。 
  
 **製品のライセンス認証**
  
次のネットワークエンドポイントは、Office 365 のサブスクリプションとリテールライセンスのライセンス認証に適用されます。 具体的には、ボリュームライセンスのインストールには適用されません。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPS ON  <br/> |座標  <br/> |Office Licensing Service  <br/> |
   
 **新しいコンテンツ**
  
次のネットワークエンドポイントは、Office 365 のサブスクリプションにのみ適用されます。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |秒  <br/> |新しい JSON ページのコンテンツ。  <br/> |
   
 **リサーチ ツール**
  
次のネットワークエンドポイントは、Office 365 のサブスクリプションにのみ適用されます。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |座標  <br/> |リサーチ Web サービス  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |座標  <br/> |リサーチの静的コンテンツ  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |座標  <br/> |リサーチコンテンツプロバイダー  <br/> |
   
 **スマート検索**
  
次のネットワークエンドポイントは、Office 365 サブスクリプションとリテール/ボリュームライセンスのライセンス認証の両方に適用されます。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |座標  <br/> |Insights Web サービス  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |座標  <br/> |JQuery ライブラリ  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |座標  <br/> |JavaScript ライブラリをサポートする  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |座標  <br/> |Insights コンテンツプロバイダー  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |座標  <br/> |Insights コンテンツプロバイダー  <br/> |
   
 **PowerPoint デザイナー**
  
次のネットワークエンドポイントは、Office 365 のサブスクリプションにのみ適用されます。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |座標  <br/> |PowerPoint Designer web サービス  <br/> |
   
 **PowerPoint クイックスターター**
  
次のネットワークエンドポイントは、Office 365 のサブスクリプションにのみ適用されます。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |座標  <br/> |PowerPoint クイックスターター web サービス  <br/> |
   
 **スマイル/Frown を送信する**
  
次のネットワークエンドポイントは、Office 365 サブスクリプションとリテール/ボリュームライセンスのライセンス認証の両方に適用されます。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPS ON  <br/> |座標  <br/> |スマイルサービスを送信する  <br/> |
   
 **サポートに問い合わせる**
  
次のネットワークエンドポイントは、Office 365 サブスクリプションとリテール/ボリュームライセンスのライセンス認証の両方に適用されます。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |座標  <br/> |サポートサービスに問い合わせる  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |座標  <br/> |アプリ内サポートサービス  <br/> |
   
 **PDF として保存**
  
次のネットワークエンドポイントは、Office 365 サブスクリプションとリテール/ボリュームライセンスのライセンス認証の両方に適用されます。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |座標  <br/> |Word 文書変換サービス (PDF)  <br/> |
   
 **Office アプリ (別名: アドイン)**
  
次のネットワークエンドポイントは、office アプリアドインが信頼されている場合に、Office 365 サブスクリプションとリテール/ボリュームライセンスのライセンス認証の両方に適用されます。
  
|**URL**|**アプリ**|**型**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |座標  <br/> |Office アプリストアの構成  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |秒  <br/> |ウィキペディアアプリのリソース  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |秒  <br/> |Bing マップアプリのリソース  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |秒  <br/> |ユーザーグラフアプリのリソース  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |秒  <br/> |Office リダイレクトサービス  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |秒  <br/> |Office JavaScript ライブラリ  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |秒  <br/> |Office アプリのテレメトリおよび Reporting Service  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |秒  <br/> |Microsoft Ajax JavaScript ライブラリ  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |秒  <br/> |Microsoft Ajax JavaScript ライブラリ  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |秒  <br/> |Office JavaScript ライブラリ  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |秒  <br/> |サポートリソース  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |秒  <br/> |サポートリソース  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |秒  <br/> |サポートリソース  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |秒  <br/> |JavaScript ライブラリ  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |秒  <br/> |エラー報告  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |秒  <br/> |フォントリソース  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |秒  <br/> |テレメトリサービス  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |秒  <br/> |テレメトリレポート  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |秒  <br/> |Microsoft Store アセットライブラリ  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |秒  <br/> |ウィキペディアページのリソース  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |秒  <br/> |ウィキペディアメディアリソース  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |秒  <br/> |ウィキペディアサンドボックスフレーム  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |秒  <br/> |マップテンプレート  <br/> |
   
 **安全なリンク**
  
次のネットワークエンドポイントは、Office 365 のすべてのサブスクリプションに対してのみ適用されます。
  
|**URL**|**型**|**説明**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |座標  <br/> |Microsoft セーフリンクサービス  <br/> |
   
 **クラッシュの報告**
  
次のネットワークエンドポイントは、Office 365 のサブスクリプションとリテール/ボリュームライセンスのライセンス認証の両方において、すべての Office アプリケーションに適用されます。 プロセスが予期せずクラッシュすると、レポートが生成され、Watson サービスに送信されます。
  
|**URL**|**型**|**説明**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |停止  <br/> |Microsoft エラー報告サービス  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |停止  <br/> |Office 共同作業インサイトサービス  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>ネットワーク要求およびトラフィックを減らすためのオプション

Office for Mac の既定の構成では、機能の観点からコンピューターを最新の状態に保つことが最高のユーザー環境を提供します。 シナリオによっては、アプリケーションがネットワークエンドポイントに接続できないようにする必要があります。 このセクションでは、そのためのオプションについて説明します。
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>クラウドサインインと Office アドインを無効にする
  
ボリュームライセンスのお客様には、クラウドベースのストレージにドキュメントを保存するための厳しいポリシーがあります。 次のアプリケーションごとの設定を設定して、MSA/OrgID サインインを無効にし、Office アドインにアクセスすることができます。
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

ユーザーがサインイン機能にアクセスしようとすると、ネットワーク接続が存在しないというエラーが表示されます。 この優先順位は、オンラインでの製品のライセンス認証もブロックするため、ボリュームライセンスのインストールにのみ使用してください。 具体的には、この設定を使用すると、Office アプリケーションは次のエンドポイントにアクセスできなくなります。
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- 上記の「サインイン」セクションにリストされているすべてのエンドポイント。
    
- 上記の「スマートルックアップ」セクションにリストされているすべてのエンドポイント。
    
- 上記の「製品のライセンス認証」セクションにリストされているすべてのエンドポイント。
    
- 上記の「Office アプリ (別名: アドイン)」に記載されているすべてのエンドポイント。
    
ユーザーのすべての機能を再確立するには、優先度を ' 2 ' に設定するか削除します。
  
> [!NOTE]
> この設定には、Office for Mac ビルド 15.25 [160726] 以降が必要です。 
  
### <a name="telemetry"></a>テレメトリ
  
Office for Mac は、一定の間隔でテレメトリ情報を Microsoft に送り返します。 データは ' ' の ' ' ' の ' のエンドポイントにアップロードされます。 テレメトリデータは、エンジニアリングチームが各 Office アプリの正常性と予期しない動作を評価する際に役に立ちます。 テレメトリには、次の2つのカテゴリがあります。
  
- **ハートビート**には、バージョンとライセンスの情報が含まれています。 このデータは、アプリの起動時に直ちに送信されます。 
    
- **使用状況**には、アプリの使用方法と致命的ではないエラーに関する情報が含まれています。 このデータは、60分ごとに送信されます。 
    
Microsoft は、プライバシーを非常に真剣に受け止めています。 Microsoft のデータ収集ポリシーについては、 [https://privacy.microsoft.com](https://privacy.microsoft.com)「」を参照してください。 アプリケーションが ' Usage ' テレメトリを送信しないようにするには、 **SendAllTelemetryEnabled**の設定を調整します。 この優先順位はアプリケーションごとに設定され、macOS 構成プロファイルまたは手動でターミナルから設定できます。 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

ハートビートテレメトリは常に送信され、無効にすることはできません。
  
### <a name="crash-reporting"></a>クラッシュの報告
  
致命的なアプリケーションエラーが発生すると、アプリケーションは予期せず終了し、クラッシュレポートを ' Watson ' サービスにアップロードします。 クラッシュレポートは、クラッシュにつながる前にアプリケーションが処理していた手順の一覧である呼び出し履歴で構成されます。 これらの手順は、エンジニアリングチームが、失敗した正確な関数とその理由を特定するのに役立ちます。
  
場合によっては、ドキュメントのコンテンツが原因でアプリケーションがクラッシュすることがあります。 アプリでドキュメントが原因として識別された場合、ドキュメントを呼び出し履歴と共に送信することができているかどうかをユーザーに確認します。 ユーザーは、この質問に関する情報を選択することができます。 IT 管理者は、ドキュメントの送信に関して厳密な要件を持つ場合があり、ドキュメントを送信しないことをユーザーに代わって判断します。 ドキュメントが送信されないようにするには、次のように設定する必要があります。また、ユーザーへのプロンプトを表示しないように設定することもできます。
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> **SendAllTelemetryEnabled**が**FALSE**に設定されている場合、そのプロセスのすべてのクラッシュレポートが無効になります。 利用状況統計情報を送信せずにクラッシュレポートを有効にするには、次の設定を行うことができます。```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>更新プログラム
  
Microsoft は、通常の間隔 (月に1回) で Office for Mac の更新プログラムをリリースします。 最新のセキュリティ修正プログラムがインストールされていることを確認するために、ユーザーと IT 管理者にコンピューターを最新の状態に保つよう強くお勧めします。 IT 管理者がコンピューターの更新を細かく制御して管理しようとしている場合は、次の設定を行って、自動検出の製品更新プログラムが自動的に検出されて提供されないようにすることができます。
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>ファイアウォール/プロキシを使用して要求をブロックする
  
組織がファイアウォールまたはプロキシサーバー経由で Url への要求をブロックしている場合は、このドキュメントに記載されている Url を許可するか、または40X 応答 (403 または404など) で一覧表示する必要があります。 40X 応答を使用すると、Office アプリケーションは、リソースにアクセスできないことを適切に受け入れることができます。また、単に接続を切断するだけでなく、クライアントの再試行を行うことができます。
  
プロキシサーバーで認証が必要な場合は、407応答がクライアントに返されます。 最良の結果を得るために、NTLM および Kerberos サーバーを使用するための特定の修正プログラムが含まれている場合は、Office for Mac ビルド15.27 以降を使用していることを確認してください。
  
  
## <a name="see-also"></a>関連項目

[Office 365 URL および IP アドレス範囲](urls-and-ip-address-ranges.md)

