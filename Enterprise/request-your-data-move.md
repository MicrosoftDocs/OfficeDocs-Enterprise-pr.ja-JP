---
title: データ移行をリクエストする方法
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
f1.keywords:
- NOCSH
description: 既存の Office 365 のお客様は、Office 365 サービスに参加しているお客様のデータを新しい geo へ移行するために、お住まいの国の期限より前にリクエストを送信する必要があります。
ms.openlocfilehash: 506943ce802adbd8d443cfb69212834b9c552f61
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106228"
---
# <a name="how-to-request-your-data-move"></a>データ移行をリクエストする方法

> [!NOTE]
> このページの情報は、geo で新しいデータセンターが開設される前に、既存の Office 365 テナントを使用していたお客様にのみ適用されます。 
  
既存の Office 365 のお客様は、組織の主要な顧客データ全体の移行を事前に要請することができます。  
  
## <a name="when-can-i-request-a-move"></a>いつ移行をリクエストできますか?

|**国がサインアップしているお客様**|**リクエスト期間の開始**|**リクエストの期限**|
|:-----|:-----|:-----|
|日本  <br/> |2020年1月1日  <br/> |2020年6月30日  <br/> |
|オーストラリア、ニュージーランド、フィジー  <br/> |2020年1月1日  <br/> |2020年6月30日  <br/> |
|インド  <br/> |2020年1月1日  <br/> |2020年6月30日  <br/> |
|カナダ  <br/> |2020年1月1日  <br/> |2020年6月30日  <br/> |
|英国  <br/> |2020年1月1日  <br/> |2020年6月30日  <br/> |
|韓国  <br/> |2020年1月1日  <br/> |2020年6月30日  <br/> |
|フランス  <br/> |2020年1月1日  <br/> |2020年6月30日  <br/> |
|アラブ首長国連邦  <br/> |2019 年 7 月 15 日  <br/> |2020年6月30日  <br/> |
|南アフリカ  <br/> |2019 年 7 月 25 日  <br/> |2020年6月30日  <br/> |
|スイス、リヒテンシュタイン  <br/> |2019 年 12 月 10 日  <br/> |2020年6月30日  <br/> |
|ドイツ  <br/> |計画  <br/> |計画  <br/> |
   
## <a name="how-to-request-a-move"></a>移行をリクエストする方法

対象となるお客様には、 [Microsoft 365 管理センター](https://aka.ms/365admin)にページが表示されます。これにより、お客様は自社のコア顧客データを新しいデータセンターリージョンに移動するよう要求できます。  
  
Microsoft 365 管理センターのページにアクセスするには、左側のナビゲーションウィンドウで [**設定**] を展開し、[**設定**] をクリックします。
[] タブ [**組織] プロファイル**を選択し、[ **Data レジデンシー**] オプションを選択します。
  
**次のいずれかに該当する場合は、このセクションは表示されません**。
- テナントは Office 365 Move プログラムの対象外です。  資格は、テナントのサインアップ国によって決まります。
- Rest における主要な顧客データはすべて、既に新しい geo に配置されています (ページの [データの場所] セクションを参照してください)。 
  
データ常駐の要件があり、事前に移行を依頼する必要がある組織の場合は、セクションの右上にある [**オプトイン**] をクリックします。 画面の右側に、Office 365 Move プログラムの詳細を説明する新しいセクションが表示されます。 テキストの横にあるトグルボタンを選択して、[**組織のコア顧客データを**保存する] を選択します。 次に、 **[保存]** をクリックします。
  
![データセンターのオプトイン操作画面](media/dataresidencyflyoutae.jpg)
  
「 **Data レジデンシー** 」セクションのテキストが、**組織がコア顧客データの移行を要求**したことを示すように変更されます。 メッセージ センターにも確認メッセージが届きます。 これにより、移行が正常にリクエストされたことを確認できます。 


  
## <a name="what-happens-after-requesting-a-move"></a>移行をリクエストした後はどうなりますか?

移行をリクエストした後、運用上の制約が許容されるように、をすばやく移行することを計画します。 予測不可能な性質の制約が数多くあるため、移行が実施される特定の日付や時間帯を共有することはできません。 移行が完了した後、お客様に通知が表示されます。
  
移行を完了するには、お住まいの国のリクエストの期限から最大 24 か月かかる場合があります。
  
## <a name="microsoft-teams"></a>Microsoft Teams

2020年1月の間、対象となる Office 365 諸国のお客様は、Microsoft Teams chat service データの移行をオプトインできます。  オプトインタイムラインは、対象となるすべての国に対して再オープンまたは拡張されています。これにより、お客様は、Microsoft Teams のスコープ内で初期移行プログラムを検討する機会を得ることができます。   

## <a name="optional-actions-before-you-request-a-move"></a>移行をリクエストする前に選択可能なアクション

必要に応じて、以下の手順を実行します。
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a>IP ベースのファイアウォールを使用している場合は、新しい IP アドレスの許可ルールを追加する

IP アドレスではなく、DNS フィルターをファイアウォールに使用するようお勧めします。新しい DNS エントリは必要ありません。
  
IP ベースのファイアウォールをインターネット接続に使用する場合には、移行先のデータセンター geo のための新しい IP アドレスの許可ルールを追加する必要があります。新しいサーバーに加え、新しいデータセンター geo の IP アドレスは、「[Office 365 の URL と IP アドレスの範囲](https://go.microsoft.com/fwlink/p/?LinkId=229631)」に継続的に追加されます。
  
許可ルール (ホワイトリストとも呼ばれる) の追加方法については、ファイアウォールのドキュメントを参照してください。
  
IP アドレスを追加した後には、新しいデータセンター geo への接続をテストするとよいでしょう。これを実行するため、新しいデータセンター geo が利用可能になったらすぐに、[新しくなった無料の 30 日間の試用版テナント](https://go.microsoft.com/fwlink/?LinkId=522463)を作成するようお勧めします。 
  
### <a name="test-using-a-new-tenant"></a>新しいテナントを使ってテストする

移行前に接続をテストする場合、新しいデータセンター geo が利用可能になった後に、[新しくなった無料の 30 日間の試用版テナント](https://go.microsoft.com/fwlink/?LinkId=522463)を設定し、それを使用して、新しいデータセンター geo でホストされる Office 365 を操作することができます。 
  
試用版テナントを既存のテナントと結合することはできません。
  
- ユーザーはテストのために別個の試用版アカウントを使用する必要があります。
    
- テナント間でデータを移行する方法はありません。
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a>モバイル デバイス上の古い Exchange 設定を更新するようユーザーに通知する

Exchange Server が**m.outlook.com**または**podxxxxx.outlook.com**に設定されているモバイルデバイスをユーザーが所有している場合は、「[セットアップするモバイルデバイスをアカウントと同期](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3)させる」の手順に従って、 **outlook.office365.com**に切り替えることをお勧めします。

## <a name="related-topics"></a>関連項目

[コア データを新しい Office 365 データ センター geo に移行する](moving-data-to-new-datacenter-geos.md)

[データ移行についての一般的な FAQ](data-move-faq.md)

[Microsoft Dynamics CRM Online の新しいデータ センター geo](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure のリージョン](https://azure.microsoft.com/regions/)
  

