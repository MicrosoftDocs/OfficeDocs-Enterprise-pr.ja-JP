---
title: "委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して顧客のテナント レポート データを取得する"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: "概要:Microsoft Exchange Online のリモートの Windows PowerShell を使用して、個々の顧客のテナントからレポートを取得します。"
ms.openlocfilehash: d764f34b89ee55fd7015f01c0c48446fc73a6ac0
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して顧客のテナント レポート データを取得する

 **概要:** Microsoft Exchange Online のリモートの Windows PowerShell を使用して、個々の顧客のテナントからレポートを取得します。
  
シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナー は、Exchange Online PowerShell のリモートの Windows PowerShell を経由して直接顧客のテナントのレポートを構成するデータにアクセスできます。これにより、パートナーはレポートのデータを収集および保存してから、その他の操作を実行できます。リモート接続を開いた後、顧客テナンシーに関するレポート データを取得することは、顧客テナンシーに対してなんらかのコマンドレットを実行することと同じです。
  
この記事では、Exchange Online のリモートの Windows PowerShell を使用して、1 つの顧客テナンシーに接続してレポートを取得します。既定では、Windows PowerShell は複数の顧客テナンシーからレポート データを集約することをサポートしていません。この手順で取得するレポートは、接続先の  _DelegatedOrg_ のレポートのみです。
  
すべての顧客テナンシーに関するレポートを 1 つにして取得する場合は、「[委任アクセス許可 (DAP) パートナー用 Windows PowerShell 経由で顧客レポート データを集約する](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md)」にこれを実行するためのサンプル スクリプトがあります。
  
## <a name="before-you-begin"></a>はじめに

- Exchange Online テナントへの接続は、リモートの Windows PowerShell を使用して行う必要があります。手順については、「[委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)」を参照してください。
    
## <a name="run-the-get-stalemailboxreport-sample"></a>Get-StaleMailboxReport のサンプルを実行する

Exchange Online へのリモート セッションを開いた後、このコマンドを実行して、日付範囲が 03/25/2015 ～ 03/31/2015 の **Get-StaleMailboxReport** を取得します。
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Exchange Online、Lync Online、および SharePoint Online には使用できるその他多数のレポート コマンドレットだけでなく、使用できるその他のメッセージ追跡用コマンドレットもあります。使用可能なレポート コマンドレットと Office 365 レポート Web サービスの詳細については、次のセクションのトピックを参照してください。
  
## <a name="see-also"></a>関連項目

#### 

[Office 365 レポート Web サービス](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Get-CsClientDeviceDetailReport](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[パートナーのヘルプ](https://go.microsoft.com/fwlink/p/?LinkID=533477)

