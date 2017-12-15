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
ms.custom: DecEntMigration
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: "概要:Microsoft Exchange Online のリモートの Windows PowerShell を使用して、個々の顧客のテナントからレポートを取得します。"
ms.openlocfilehash: 40c1dedd8fb223ea6fa478b3a5c3e716fe07dd93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="79d18-103">委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して顧客のテナント レポート データを取得する</span><span class="sxs-lookup"><span data-stu-id="79d18-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="79d18-104">**の概要:**RemoteWindows Microsoft Exchange Online の PowerShell を使用すると、個々 の顧客のテナントからレポートを取得できます。</span><span class="sxs-lookup"><span data-stu-id="79d18-104">**Summary:** Use remoteWindows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="79d18-p101">シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナー は、Exchange Online PowerShell のリモートの Windows PowerShell を経由して直接顧客のテナントのレポートを構成するデータにアクセスできます。これにより、パートナーはレポートのデータを収集および保存してから、その他の操作を実行できます。リモート接続を開いた後、顧客テナンシーに関するレポート データを取得することは、顧客テナンシーに対してなんらかのコマンドレットを実行することと同じです。</span><span class="sxs-lookup"><span data-stu-id="79d18-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="79d18-p102">この記事では、Exchange Online のリモートの Windows PowerShell を使用して、1 つの顧客テナンシーに接続してレポートを取得します。既定では、Windows PowerShell は複数の顧客テナンシーからレポート データを集約することをサポートしていません。この手順で取得するレポートは、接続先の  _DelegatedOrg_ のレポートのみです。</span><span class="sxs-lookup"><span data-stu-id="79d18-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
<span data-ttu-id="79d18-111">すべての顧客テナンシーに関するレポートを 1 つにして取得する場合は、「[委任アクセス許可 (DAP) パートナー用 Windows PowerShell 経由で顧客レポート データを集約する](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md)」にこれを実行するためのサンプル スクリプトがあります。</span><span class="sxs-lookup"><span data-stu-id="79d18-111">If you want to retrieve a single report for all your customer tenancies, a sample script to do this can be found in [Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) .</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="79d18-112">開始する前に</span><span class="sxs-lookup"><span data-stu-id="79d18-112">Before you begin</span></span>

- <span data-ttu-id="79d18-p103">Exchange Online テナントへの接続は、リモートの Windows PowerShell を使用して行う必要があります。手順については、「[委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79d18-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="79d18-115">Get-StaleMailboxReport のサンプルを実行する</span><span class="sxs-lookup"><span data-stu-id="79d18-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="79d18-116">Exchange Online へのリモート セッションを開いた後、このコマンドを実行して、日付範囲が 03/25/2015 ～ 03/31/2015 の **Get-StaleMailboxReport** を取得します。</span><span class="sxs-lookup"><span data-stu-id="79d18-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="79d18-p104">Exchange Online、Lync Online、および SharePoint Online には使用できるその他多数のレポート コマンドレットだけでなく、使用できるその他のメッセージ追跡用コマンドレットもあります。使用可能なレポート コマンドレットと Office 365 レポート Web サービスの詳細については、次のセクションのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="79d18-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="79d18-119">See also</span><span class="sxs-lookup"><span data-stu-id="79d18-119">See also</span></span>

#### 

[<span data-ttu-id="79d18-120">Office 365 レポート Web サービス</span><span class="sxs-lookup"><span data-stu-id="79d18-120">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="79d18-121">Get-CsClientDeviceDetailReport</span><span class="sxs-lookup"><span data-stu-id="79d18-121">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="79d18-122">パートナーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="79d18-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

