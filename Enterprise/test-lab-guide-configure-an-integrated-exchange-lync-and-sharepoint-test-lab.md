---
title: テスト ラボ ガイド Exchange、Lync、および SharePoint 統合テスト ラボの構成
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
f1.keywords:
- NOCSH
description: '概要: Exchange Server 2013 を実行するサーバー、Lync Server 2013 を実行するサーバー、および SharePoint Server 2013 を実行するサーバーを持つ、統合テスト ラボの作成方法について説明します。'
ms.openlocfilehash: bfb2e1be3b9bb401514e736d38a6f1a2944940f0
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996521"
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="11158-103">テスト ラボ ガイド: Exchange、Lync、および SharePoint 統合テスト ラボの構成</span><span class="sxs-lookup"><span data-stu-id="11158-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="11158-104">Exchange Server 2013 を実行するサーバー、Lync Server 2013 を実行するサーバー、および SharePoint Server 2013 を実行するサーバーを持つ、統合テスト ラボの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11158-104">Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
 
<span data-ttu-id="11158-105">**Exchange、Lync、および SharePoint の統合テスト ラボのガイドの概要ビデオを見る**</span><span class="sxs-lookup"><span data-stu-id="11158-105">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
<span data-ttu-id="11158-106">この構成には全 3 種類のサーバー同士のサーバー間認証が含まれており、この構成で作成されるテスト ラボでは、Exchange Server 2013 を実行するサーバー、Lync Server 2013 を実行するサーバー、SharePoint Server 2013 を実行するサーバーを使用する複数製品のシナリオとソリューションを構築して、デモンストレーションすることができます。</span><span class="sxs-lookup"><span data-stu-id="11158-106">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="11158-107">このドキュメントには、以下の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="11158-107">This document contains instructions for:</span></span>
  
1. <span data-ttu-id="11158-108">Windows Server 2012 の基本構成テスト ラボの構成。</span><span class="sxs-lookup"><span data-stu-id="11158-108">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="11158-109">SQL1 という名前の新しいサーバーのインストールおよび構成。</span><span class="sxs-lookup"><span data-stu-id="11158-109">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="11158-110">SQL1 サーバーへの SQL Server 2012 のインストール。</span><span class="sxs-lookup"><span data-stu-id="11158-110">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="11158-111">CLIENT2 という名前の新しいクライアント コンピューターのインストールおよび構成。</span><span class="sxs-lookup"><span data-stu-id="11158-111">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="11158-112">EX1 への Exchange Server 2013 のインストールおよび構成。</span><span class="sxs-lookup"><span data-stu-id="11158-112">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="11158-113">LYNC1 という名前の新しいサーバーのインストールおよび構成。</span><span class="sxs-lookup"><span data-stu-id="11158-113">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="11158-114">LYNC1 への Lync Server 2013 Standard Edition のインストール。</span><span class="sxs-lookup"><span data-stu-id="11158-114">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="11158-115">SP1 への SharePoint Server 2013 のインストール。</span><span class="sxs-lookup"><span data-stu-id="11158-115">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="11158-116">EX1、LYNC1、および SP1 間の統合の構成。</span><span class="sxs-lookup"><span data-stu-id="11158-116">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="11158-117">Hyper-V でこのテスト ラボを構成する方法の詳細については、「[Windows Server 2012 Hyper-V で Exchange、Lync、および SharePoint 統合テスト ラボをホストする](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11158-117">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="11158-118">テスト ラボ ガイドをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="11158-118">Download the test lab guide</span></span>

<span data-ttu-id="11158-119">[テスト ラボ ガイド: Exchange、Lync、および SharePoint 統合テスト ラボの構成](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="11158-119">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="11158-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="11158-120">See Also</span></span>

[<span data-ttu-id="11158-121">テスト ラボ ガイド</span><span class="sxs-lookup"><span data-stu-id="11158-121">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




