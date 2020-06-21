---
title: データの移行中および移行後
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
f1.keywords:
- NOCSH
description: データの移行は、エンドユーザーへの影響を最小限に抑えたバックエンドの操作です。 Microsoft が各サービスとお客様のテナントの関連データを新しいデータセンター geo に移動する際には、何も行う必要はありません。 データの転送および検証は事前にバックグラウンドで行われ、ユーザーへの影響は最小限に抑えられます。
ms.openlocfilehash: d07c9c62a778ce23d2e088ddeb8b34346911a19a
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774492"
---
# <a name="during-and-after-your-data-move"></a>データの移行中および移行後

データの移行は、エンドユーザーへの影響を最小限に抑えたバックエンドの操作です。 Microsoft が各サービスとお客様のテナントの関連データを新しいデータセンター geo に移動する際には、何も行う必要はありません。 データの転送および検証は事前にバックグラウンドで行われ、ユーザーへの影響は最小限に抑えられます。
  
> [!NOTE]
> Moves occur at different times for each service. As a result, you'll see the described reduced functionality for each service at a different time. 
  
Exchange Online、SharePoint Online、Teams、および Skype for Business の各移行が完了したら、Microsoft 365 メッセージセンターで確認を行います。 次の表に示されているように、特定の geo 内のすべてのお客様について、要求されたすべてのデータの移動を完了するには、登録期間の終了後、最大 24 か月かかることがあります。 移行後にテナントに問題がある場合は、サポートに連絡して[サポート](https://go.microsoft.com/fwlink/p/?LinkID=522459)を受けてください。 
  

|**国がサインアップしているお客様**|**完了したすべての移動**|
|:-----|:-----|
|オーストラリア、ニュージーランド、フィジー  <br/> |2022年7月1日  <br/> |
|日本  <br/> |2022年7月1日  <br/> |
|インド  <br/> |2022年7月1日  <br/> |
|カナダ  <br/> |2022年7月1日  <br/> |
|韓国  <br/> |2022年7月1日  <br/> |
|英国  <br/> |2022年7月1日  <br/> |
|フランス  <br/> |2022年7月1日  <br/> |
|アラブ首長国連邦  <br/> |2022年7月1日  <br/> |
|南アフリカ  <br/> |2022年7月1日  <br/> |
|スイス、リヒテンシュタイン  <br/> |2022年7月1日  <br/> |
|ドイツ  <br/> |計画  <br/> |
|ノルウェー  <br/> |2022年11月1日  <br/> |

## <a name="exchange-online"></a>Exchange Online

各ユーザーをシングル テナントの新しいデータセンター geo に移動するのに時間がかかるため、移動中は一部のユーザーが古いデータセンター geo のまま、他のユーザーは新しいデータセンター geo という状態になります。 これは、複数のメールボックスへのアクセスを必要とする一部の機能が、移行プロセスの間に完全には機能しない場合があることを意味します。これは、先週まで可能です。 該当する機能については、この後のセクションで取り上げます。
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Outlook Web Access で "共有フォルダー" を開く

Some users open a shared mail folder from another mailbox (that the user has read or write permissions to) in Outlook Web Access using the "Shared Folder" feature. The following table describes how access to shared folders works during a mailbox move. Please note that users with full permissions to a shared mailbox can open the mailbox by using Outlook Web Access during the move. 
  
|**構成**|**説明**|
|:-----|:-----|
|別のメールボックスへのメールボックス フォルダー アクセス許可があるユーザー  <br/> |制限される可能性があります。  <br/> テナントの移動中にユーザー A とメールボックス B が同じ geo になく、ユーザー A が持っているアクセス許可がメールボックス B の特定のフォルダーに対してのみの場合、ユーザー A は Outlook Web Access でメールボックス B のフォルダーを開くことができません。  <br/> 共有フォルダーを追加するには、左側のナビゲーション ウィンドウでユーザー名を右クリックし、 **[共有フォルダーの追加]** を選択します。  <br/> |
|別のメールボックスへのメールボックス フル アクセス許可があるユーザー  <br/> |完全にサポートされます。  <br/> ユーザー A がメールボックス B に "フルアクセス" アクセス許可を持っている場合、ユーザー A は Outlook Web Access の左側のナビゲーションパネルで共有フォルダーをクリックして、メールボックス B が表示されているウィンドウを開くことができます。 ユーザーは、移動中に Outlook Web Access を使用して共有メールボックスを開くことができ、悪影響を与えることはありません。 制限は、メールボックス内のフォルダー レベルの共有だけに適用されます。           |
  
## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online を移行すると、以下のサービスのデータも移行されます。
  
- One Drive for Business
    
- Project Online
    
- Microsoft 365 のプロジェクト
    
- Microsoft 365 Video services
    
- S ブラウザーの Office
    
- Microsoft 365 Apps for enterprise
    
- Visio Pro for Microsoft 365
    
SharePoint Online データの移行が完了すると、次に示す影響が現れる可能性があります。
  
### <a name="microsoft-365-video-services"></a>Microsoft 365 Video Services

- ビデオのデータの移動は、SharePoint Online にある残りのコンテンツの移動より時間がかかります。
    
- SharePoint Online のコンテンツを移行すると、ビデオが再生できない時間が生じます。
    
- 以前のデータセンターからコード変換されたコピーを削除し、新しいデータセンターでコードを再変換しています。
    
### <a name="search"></a>Search

In the course of moving your SharePoint Online data, we migrate your search index and search settings to a new location. Until we've **completed** the move of your SharePoint Online data, we continue to serve your users from the index in the original location. In the new location, search automatically starts crawling your content after we've completed moving your SharePoint Online data. From this point and onwards we serve your users from the migrated index. Changes to your content that occurred after the migration aren't included in the migrated index until crawling picks them up. Most customers don't notice that results are less fresh right after we've completed moving their SharePoint Online data, but some customers might experience reduced freshness in the first 24-48 hours 
  
次の検索機能が影響を受けます。
  
- 検索結果と検索 Web パーツ:移行後に生じた変更は、クロールで反映されるまで結果に含まれません。 
    
- Delve:移行後に生じた変更は、クロールで反映されるまで Delve に含まれません。
    
- Popularity and Search Reports for the site: Counts for Excel reports in the new location only include migrated counts and counts from usage reports that have run after we completed moving your SharePoint Online data. Any counts from the interim period are lost and can't be recovered. This period is typically a couple of days. Some customers might experience shorter or longer losses.
    
- ビデオ ポータル:ビデオ ポータルの表示回数と統計情報は Excel レポートの統計情報に基づいているため、ビデオ ポータルの表示回数と統計情報は、Excel レポートと同じ期間失われます。
    
- 電子情報開示:移行中に変更されたアイテムは、クロールで変更が反映されるまでは表示されません。
    
- データ損失防止 (DLP):クロールで変更が反映されるまで、変更されたアイテムに対してポリシーは適用されません。

## <a name="microsoft-teams"></a>Microsoft Teams

Microsoft は、Exchange Online、SharePoint Online、OneDrive for Business に加えて、Teams データをローカルデータセンターに移行します。

- Teams のチャットメッセージ (プライベートメッセージやチャネルメッセージを含む)。
- チャットで使用される Teams 画像。

Teams ファイルは SharePoint Online に格納され、Teams チャットファイルは OneDrive for Business に保存されます。 ボイスメール、予定表、チャット履歴、および連絡先は、Exchange Online に格納されます。 多くの場合、Exchange Online、SharePoint Online、OneDrive for Business は、ローカルのデータセンター geo のお客様によって既に使用されており、資格のあるお客様の国の Microsoft 365 移行プログラムの一部でもあります。

## <a name="skype-for-business"></a>Skype for Business

Skype for Business の移動は、オーストラリア、日本、インド、カナダ、英国、および南韓国で利用できます。

All users will be signed out from the Skype for Business client software during cut-over. The automatic sign-in will reconnect users within two minutes.
  
|**全体の移動中に利用できる機能**|**移動中は機能が制限される場合があります**|
|:-----|:-----|
| インスタント メッセージングおよび音声呼び出し  <br/>  ユーザーは、連絡先の追加、連絡先グループの追加、会議の追加、自分の場所の設定、[今日はどんなことがありますか] の変更を実行できます。  <br/>  Audio Conferencing Provider (ACP) settings are copied to the target datacenter geo. If the ACP provider is present in the target datacenter, it will work. Otherwise, it will not.  <br/> | 管理者は、テナント管理者 TRPS (テナントのリモート PowerShell) を使用してセッションを作成できません。  <br/>  管理者は、テナント管理者 LAC を使用してサインインおよびユーザー設定の変更は行えません。  <br/> |
   
|**移行後**|
|:-----|
| 会議データ (アップロードされたプレゼンテーションなど) は移動されないため、再アップロードする必要があります。  <br/>  Lync 2010 クライアントや Lync for Mac 2011 クライアントなど、以前の Lync クライアントでは、サービスへの DNS 情報のキャッシュに起因するサインインの問題が発生することが確認されています。 ユーザーが最新の Skype for Business Windows クライアントではない場合、DNS キャッシュのクリアが必要になる可能性があります。 「 [Office 365 の Skype For Business Online の DNS 構成に関する問題のトラブルシューティング」を](https://docs.microsoft.com/skypeforbusiness/troubleshoot/online-configuration/dns-configuration-issue)参照してください。 Lync for Mac クライアントのユーザーは、[このリンクの手順](https://support.microsoft.com/kb/2629861)に従う必要があります。  <br/> |
   
### <a name="skype-for-business-moves-that-involve-a-third-party-audio-conferencing-provider"></a>サードパーティの電話会議プロバイダーを含む Skype for Business の移動
新しい geo 固有のデータセンターのユーザーは、Skype for Business 用のサードパーティの電話会議プロバイダーのアドオン サービスを使用することができません。  サードパーティの電話会議プロバイダーを使用している既存のお客様は、新しい geo 固有のデータセンターへの移動を要求する必要はありません。  新しい geo 固有のデータセンターの新規のお客様は、サードパーティの電話会議プロバイダーを使用するために、地域データセンターへの移動を要求する必要があります。
  
## <a name="related-topics"></a>関連項目 
 
[データ移行を申請する方法](request-your-data-move.md)
    
[データ移行についての一般的な FAQ](data-move-faq.md)
  
[Microsoft Dynamics CRM Online の新しいデータ センター geo](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure のリージョン](https://azure.microsoft.com/regions/)
