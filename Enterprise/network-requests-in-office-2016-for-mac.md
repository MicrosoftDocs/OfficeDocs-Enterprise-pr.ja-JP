---
title: Office 2016 for Mac でのネットワーク要求
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: For Mac アプリケーションの Office 2016 は、macOS のプラットフォーム上でネイティブ アプリケーション エクスペリエンスを提供します。各アプリケーションは、さまざまなシナリオでは、ネットワーク アクセスが利用できないときは、国を含むで動作する設計されています。マシンがネットワークに接続されているときに一連の拡張機能を提供する web ベースのサービス アプリケーションが自動的に接続します。このホワイト ペーパーでは、どのエンドポイントと、到達しようとしているアプリケーションの Url で提供されるサービスについて説明します。この情報は、トラブルシューティング、ネットワーク構成の問題、およびネットワークのプロキシ サーバーにポリシーを設定するときに便利です。詳細についてこの資料では、Office 365 の URL とアドレス範囲の資料を補完するものです。
ms.openlocfilehash: b94b77a0ff8cd37b0fa1c881ba590853615bfe93
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541767"
---
# <a name="network-requests-in-office-2016-for-mac"></a>Office 2016 for Mac でのネットワーク要求

For Mac アプリケーションの Office 2016 は、macOS のプラットフォーム上でネイティブ アプリケーション エクスペリエンスを提供します。各アプリケーションは、さまざまなシナリオでは、ネットワーク アクセスが利用できないときは、国を含むで動作する設計されています。マシンがネットワークに接続されているときに一連の拡張機能を提供する web ベースのサービス アプリケーションが自動的に接続します。このホワイト ペーパーでは、どのエンドポイントと、到達しようとしているアプリケーションの Url で提供されるサービスについて説明します。この情報は、ネットワーク構成の問題とネットワークのプロキシ サーバーのポリシーの設定のトラブルシューティングを行う場合に便利です。詳細についてこの資料では、 [Office 365 の URL とアドレスの範囲の資料](urls-and-ip-address-ranges.md)、Microsoft Windows を実行しているコンピューターのエンドポイントを含むを補完する目的としています。
  
この記事の大半は、ネットワークの Url、種類、およびサービスまたはエンドポイントによって提供される機能の説明の詳細を示す表です。サービスとエンドポイントの使用状況で Office アプリケーションの各に異なる場合があります。次の表には、次のアプリケーションが定義されています。
  
- W: 単語
- P: PowerPoint
- X: Excel
- O: outlook
- N: OneNote
   
URL の種類の定義は次のとおりです。
  
- ST: 静的 - URL は、クライアント アプリケーションにハードコーディングします。
    
- SS: 準静的-の URL は、web ページまたはリダイレクターの一部としてエンコードされます。
    
- CS: サービスの構成に、URL が返されます、Office の構成サービスの一部として。
    
## <a name="office-2016-for-mac-default-configuration"></a>Mac の既定の構成の Office の 2016 年

 **インストールと更新プログラム**
  
Microsoft コンテンツ配信ネットワーク (CDN) から Mac のインストール プログラムの Office 2016 をダウンロードするには、次のネットワーク エンドポイントを使用します。
  
|**URL**|**種類**|**説明**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |最新のインストール パッケージを office 365 ポータルのインストールのリンク サービス。  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |コンテンツ配信ネットワーク上のインストール パッケージの場所です。  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |コンテンツ配信ネットワーク上のインストール パッケージの場所です。  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |マイクロソフトの自動更新の管理制御のエンドポイント  <br/> |
   
 **最初のアプリケーションの起動**
  
次のネットワーク エンドポイントには、Office アプリケーションの初回起動時に接続します。これらのエンドポイントは、ユーザーに対して Office 機能の強化を提供し、(ボリューム ライセンスのインストールを含む)、ライセンスの種類に関係なく Url に接続されます。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' の構成で機能ライト アップおよび実験できます。  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' のネットワーク構成のテスト  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' のネットワーク構成のテスト  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office の構成サービスのサービス エンドポイントの一覧をマスターします。  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office の遠隔測定の規則のダウンロード - は、データおよび遠隔測定のサービスにアップロードするのにはイベントをクライアントに通知します。  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote の遠隔測定サービス  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office の遠隔測定レポートの"Heartbeart"をアップロードして、クライアントで発生するエラー イベントは、「遠隔測定」のサービスにアップロードされます。  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office オンラインのテンプレート サービスのオンライン ドキュメントのテンプレートをユーザーに提供します。  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office テンプレートのダウンロード - テンプレートの PNG イメージのストレージです。  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office アプリケーションの構成を保存します。  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office ドキュメントの統合サービス カタログ (サービスおよびエンドポイントのリスト)、ホーム領域の検出。  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |ホーム領域の検出の v2 (15.40 とそれ以降) のためのリソース  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |マイクロソフトの自動更新のマニフェスト ・ チェックを使用可能な更新プログラムがあるかどうかを参照してください。  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft Ajax JavaScript ライブラリ  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Office の構成とリソースの Wikipedia アプリケーションです。  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Office の構成とリソースの Bing マップ アプリケーションです。  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |ユーザーが Office の構成とリソースのグラフのアプリケーションです。  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |OneNote の新しいコンテンツとは何です。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |OneNote の新しいコンテンツです。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |OneNote の新しいイメージとは何です。  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |アプリケーションのサポート サービスです。  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |電子メール アカウントの検出サービスです。  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook の自動検出  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Office 365 サービスのエンドポイントを outlook です。  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Outlook アドイン用のアイコンです。  <br/> |
   
> [!NOTE]
> Office 構成サービスは、Microsoft Office のすべてのクライアントだけではなく for mac は、自動検出サービスとして機能します。応答で返されたエンドポイントは、準静的な変更では、非常にまれですが、こともあります。 
  
 **サインインする**
  
次のネットワーク エンドポイントは、クラウド ・ ベースのストレージへのサインイン時に接続します。アカウントの種類に応じてさまざまなサービスに接続があります。例えば：
  
- **MSA: Microsoft アカウント**- 消費者と小売のシナリオで一般的に使用されます。 
    
- **OrgID: 組織のアカウント**- 商用のシナリオで一般的に使用されます。 
    
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows 認証サービス  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 365 ログイン サービス (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |ログイン サービスの Microsoft アカウント (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft アカウントのログイン サービス ヘルパー (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |(OrgID) をブランド化する office 365 ログイン  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |ドキュメントおよびストレージ ・ ロケーターの場所  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |ほとんどの最近使用した (MRU) のドキュメント サービス  <br/> |
   
> [!NOTE]
> サブスクリプション ・ ベースおよび販売店のライセンスの両方の署名は製品をアクティブにし、OneDrive などのクラウド リソースへのアクセスを有効にします。ボリューム ライセンス インストールの場合、ユーザー入力を求められます (既定) でのサインインがのみ製品が既にアクティブ化されるように、クラウド リソースへのアクセスに必要な。 
  
 **製品のライセンス認証**
  
次のネットワーク エンドポイントは、Office 365 のサブスクリプションとリテール ライセンスのアクティブ化に適用されます。具体的には、ボリューム ライセンスのインストールにこれは当てはまりません。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office Licensing Service  <br/> |
   
 **新しいコンテンツとは**
  
次のネットワーク エンドポイントは、Office 365 のサブスクリプションにのみ適用されます。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |新しい JSON ページ コンテンツとは何です。  <br/> |
   
 **リサーチ ツール**
  
次のネットワーク エンドポイントは、両方の Office 365 サブスクリプションに適用されます。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |研究者の Web サービス  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |研究者の静的なコンテンツ  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |コンテンツ プロバイダーの研究者  <br/> |
   
 **スマート検索**
  
次のネットワーク エンドポイントは、Office 365 のサブスクリプションとリテールまたはボリューム ライセンスのアクティブ化に適用されます。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Web サービスの情報  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |JQuery ライブラリ  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |JavaScript ライブラリをサポートしています。  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |コンテンツ プロバイダーの情報  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |コンテンツ プロバイダーの情報  <br/> |
   
 **PowerPoint デザイナー**
  
次のネットワーク エンドポイントは、Office 365 のサブスクリプションにのみ適用されます。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint のデザイナーの web サービス  <br/> |
   
 **PowerPoint クイックスターター**
  
次のネットワーク エンドポイントは、Office 365 のサブスクリプションにのみ適用されます。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint QuickStarter web サービス  <br/> |
   
 **笑顔としかめつらを送信します。**
  
次のネットワーク エンドポイントは、Office 365 のサブスクリプションとリテールまたはボリューム ライセンスのアクティブ化に適用されます。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |笑顔サービスに送信します。  <br/> |
   
 **サポートに問い合わせて**
  
次のネットワーク エンドポイントは、Office 365 のサブスクリプションとリテールまたはボリューム ライセンスのアクティブ化に適用されます。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |サポート サービスにお問い合わせください。  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |アプリケーションのサポート サービス  <br/> |
   
 **PDF として保存します。**
  
次のネットワーク エンドポイントは、Office 365 のサブスクリプションとリテールまたはボリューム ライセンスのアクティブ化に適用されます。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Word のドキュメント変換サービス (PDF)  <br/> |
   
 **Office アプリケーション (別名アドインの場合)**
  
次のネットワーク エンドポイントは、Office アプリケーションのアドインが信頼されている場合、Office 365 のサブスクリプションとリテールまたはボリューム ライセンスのアクティブ化に適用されます。
  
|**URL**|**アプリ**|**種類**|**説明**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Office アプリケーションの [設定の保存  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia アプリケーション リソース  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing マップ アプリケーションのリソース  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |ユーザー グラフのアプリケーションのリソース  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office リダイレクト サービス  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office JavaScript ライブラリ  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |遠隔操作」と、Office アプリケーション エラー報告サービス  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Microsoft Ajax JavaScript ライブラリ  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft Ajax JavaScript ライブラリ  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office JavaScript ライブラリ  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |サポート リソース  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |サポート リソース  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |サポート リソース  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |JavaScript ライブラリ  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |エラー報告  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |フォント リソース  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |遠隔測定サービス  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |「遠隔測定」の報告  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |マイクロソフト ストアの [アセット ライブラリ  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia ページのリソース  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia メディア リソース  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia サンド ボックス フレーム  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |マップのテンプレート  <br/> |
   
 **リンク保護**
  
2016 の Office アプリケーションに、次のネットワーク エンドポイントに適用されます。
  
|**URL**|**種類**|**説明**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |マイクロソフトの安全なリンク サービス  <br/> |
   
 **レポートがクラッシュします。**
  
次のネットワーク エンドポイントは、すべての Office 2016 アプリケーションとライセンスの種類に適用されます。プロセスが予期せずクラッシュすると、レポートが生成され、ワトソンのサービスに送信します。
  
|**URL**|**種類**|**説明**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Microsoft エラー報告サービス  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office コラボレーション情報サービス  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>ネットワーク要求し、トラフィックを削減するためのオプション

For Mac Office の 2016 年の既定の構成では、両方の機能と、コンピューターを常に最新の状態に保つという点では最高のユーザー エクスペリエンスを提供します。一部のシナリオでは、アプリケーションがネットワークのエンドポイントに接続しないようにすることもできます。このセクションでは、これを行うためのオプションについて説明します。
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>クラウドにサインインし、Office のアドインを無効にします。
  
ボリューム ライセンスのお客様は、クラウド ・ ベース ・ ストレージへの文書の保存に関する厳格なポリシーがあります。MSA/OrgID サインインを無効にして、Office アドインへのアクセスには、以下のアプリケーションごとの設定を設定できます。
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

ユーザーは、サインインの機能にアクセスすると、ネットワーク接続が存在しないこと、エラーが表示されます。この設定は、オンラインの製品のライセンス認証をブロックするため、ボリューム ライセンス インストールの場合のみ使用する必要があります。具体的には、この設定を使用すると、Office アプリケーションが次のエンドポイントにアクセスします。
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- 'サインイン' 項に記載されているすべてのエンドポイントです。
    
- 'スマート検索' に記載されているすべてのエンドポイントです。
    
- ' 製品のライセンス認証] に記載されているすべてのエンドポイントです。
    
- ' Office アプリケーション (別名アドイン)' に記載されているすべてのエンドポイントです。
    
'2' にプリファレンスを設定して、ユーザーの完全な機能を再確立するには、いずれかまたはそれを削除します。
  
> [!NOTE]
> この設定する必要があります 2016 の Office for Mac ビルド 15.25 [160726] またはそれ以降です。 
  
### <a name="telemetry"></a>「遠隔測定」
  
For Mac Office 2016 は、定期的に、マイクロソフトに「遠隔測定」の情報をを送信します。'ネクサス' のエンドポイントには、データがアップロードされます。遠隔測定データは、稼働状態と各 Office アプリケーションのすべての予期しない動作の評価、エンジニア リング チームに役立ちます。「遠隔測定」の 2 つに分類されます。
  
- **ハートビートには**、バージョン情報およびライセンス情報が含まれています。このデータは、アプリケーションの起動時にすぐに送信されます。 
    
- **使用法**には、アプリケーションの使用方法に関する情報と、致命的でないエラーが含まれています。このデータは 60 分ごとに送信されます。 
    
マイクロソフトでは、お客様のプライバシーを非常に真剣には。については、マイクロソフトのデータ収集ポリシーを読むことができます[https://privacy.microsoft.com](https://privacy.microsoft.com)。'使用' の遠隔測定の送信からアプリケーションを防ぐためには、 **SendAllTelemetryEnabled**の優先順位を調整できます。優先順位はアプリケーションごとのであり、macOS 構成のプロファイルを使用してまたはターミナルから手動に設定することができます。 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

ハートビートの遠隔測定は、常に送信され、無効にすることはできません。
  
### <a name="crash-reporting"></a>レポートがクラッシュします。
  
致命的なアプリケーション エラーが発生した場合、アプリケーションが予期せず終了し、'ワトソン' のサービスをクラッシュ レポートをアップロードします。クラッシュ レポートは、コール スタック、アプリケーションのクラッシュにつながる処理の手順の一覧であるので構成されます。次の手順のため、エンジニア リング チームが失敗した正確な関数を識別してその理由です。
  
場合によっては、ドキュメントの内容が、アプリケーションがクラッシュすると発生します。アプリケーションでは、原因としてドキュメントを識別する場合はユーザーにたずねるかどうかは、コール スタックの付属ドキュメントを送信しても問題がないです。ユーザーは、この質問に十分な情報に基づいて選択を行うことができます。IT 管理者は、ドキュメントの送信に関する厳格な要件があります、ドキュメントを送信しないユーザーのための意思決定を下すことがあります。ドキュメントが、送信されないようにするのには、ユーザーにプロンプトを非表示にして、次の優先順位を設定できます。
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> **SendAllTelemetryEnabled**を**FALSE**に設定すると、すべてがクラッシュ レポート作成のプロセスが無効になっています。クラッシュが遠隔測定の使用状況を送信せずにレポートを有効にするには、次の優先順位を設定できます。```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>更新プログラム
  
マイクロソフトでは、定期的に (通常 1 回 1 か月) の Mac の更新プログラムの Office 2016 を解放します。ユーザーを強くお勧めし、IT 管理者は、コンピューターを最新のセキュリティ修正プログラムを確実に最新の状態に保つには、インストールされています。厳密に制御し、コンピューターの更新プログラムを管理する IT 管理者が必要な場合、自動更新プロセスを自動的に検出して製品の更新プログラムを提供することを防ぐために次の優先順位を設定できます。
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>ファイアウォール/プロキシの要求をブロックします。
  
ファイアウォールまたはプロキシ サーバー経由で、組織のブロックが Url を要求した場合が許可されているいずれかの方法としては、このドキュメントに記載されている Url を構成するか、ブロック 40 X 応答例: 403 (404) を一覧表示します。40 X 応答は、Office アプリケーションのリソースにアクセスできないことを問題なく受け入れるし、だけで、接続は、クライアントが再試行すると次に、削除するより高速なユーザー エクスペリエンスを提供します。
  
プロキシ サーバーで認証が必要な場合は、407 応答がクライアントに返されます。最高のエクスペリエンスでは、NTLM および Kerberos サーバーを操作するための特定の修正プログラムが含まれている、Office 2016 のビルド 15.27 以降が使用していることを確認します。
  
  
## <a name="see-also"></a>関連項目

[Office 365 URL および IP アドレス範囲](urls-and-ip-address-ranges.md)

