---
title: 委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して顧客のテナント レポート データを取得する
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 概要:Microsoft Exchange Online のリモートの Windows PowerShell を使用して、個々の顧客のテナントからレポートを取得します。
ms.openlocfilehash: c1c5ca880d73cf226a5ae7dae79df89351b537f1
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071193"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="d95de-103">委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して顧客のテナント レポート データを取得する</span><span class="sxs-lookup"><span data-stu-id="d95de-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="d95de-104">**概要:** Microsoft Exchange Online用のリモートWindows PowerShellを使用して、個々の顧客テナントからレポートを取得します。</span><span class="sxs-lookup"><span data-stu-id="d95de-104">**Summary:** Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="d95de-p101">シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナー は、Exchange Online PowerShell のリモートの Windows PowerShell を経由して直接顧客のテナントのレポートを構成するデータにアクセスできます。これにより、パートナーはレポートのデータを収集および保存してから、その他の操作を実行できます。リモート接続を開いた後、顧客テナンシーに関するレポート データを取得することは、顧客テナンシーに対してなんらかのコマンドレットを実行することと同じです。</span><span class="sxs-lookup"><span data-stu-id="d95de-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="d95de-p102">この記事では、Exchange Online のリモートの Windows PowerShell を使用して、1 つの顧客テナンシーに接続してレポートを取得します。既定では、Windows PowerShell は複数の顧客テナンシーからレポート データを集約することをサポートしていません。この手順で取得するレポートは、接続先の  _DelegatedOrg_ のレポートのみです。</span><span class="sxs-lookup"><span data-stu-id="d95de-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="d95de-111">始める前に</span><span class="sxs-lookup"><span data-stu-id="d95de-111">Before you begin</span></span>

- <span data-ttu-id="d95de-p103">Exchange Online テナントへの接続は、リモートの Windows PowerShell を使用して行う必要があります。手順については、「[委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d95de-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="d95de-114">Get-StaleMailboxReport のサンプルを実行する</span><span class="sxs-lookup"><span data-stu-id="d95de-114">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="d95de-115">Exchange Online へのリモート セッションを開いた後、このコマンドを実行して、日付範囲が 03/25/2015 ～ 03/31/2015 の **Get-StaleMailboxReport** を取得します。</span><span class="sxs-lookup"><span data-stu-id="d95de-115">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="d95de-p104">Exchange Online、Lync Online、および SharePoint Online には使用できるその他多数のレポート コマンドレットだけでなく、使用できるその他のメッセージ追跡用コマンドレットもあります。使用可能なレポート コマンドレットと Office 365 レポート Web サービスの詳細については、次のセクションのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d95de-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d95de-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d95de-118">See also</span></span>

#### 

[<span data-ttu-id="d95de-119">Office 365 レポート Web サービス</span><span class="sxs-lookup"><span data-stu-id="d95de-119">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="d95de-120">Get-CsClientDeviceDetailReport</span><span class="sxs-lookup"><span data-stu-id="d95de-120">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="d95de-121">パートナーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="d95de-121">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

