---
title: "テスト ラボ ガイド Exchange、Lync、および SharePoint 統合テスト ラボの構成"
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: "概要: Exchange Server 2013 を実行するサーバー、Lync Server 2013 を実行するサーバー、および SharePoint Server 2013 を実行するサーバーを持つ、統合テスト ラボの作成方法について説明します。"
ms.openlocfilehash: 6fc3bc05db0d28bc4de2be77671ccf5e8fc55926
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="752b3-103">テスト ラボ ガイド: Exchange、Lync、および SharePoint 統合テスト ラボの構成</span><span class="sxs-lookup"><span data-stu-id="752b3-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="752b3-104">**概要:** Exchange Server 2013 を実行するサーバー、Lync Server 2013 を実行するサーバー、および SharePoint Server 2013 を実行するサーバーを持つ、統合テスト ラボの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="752b3-104">Summary: Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="752b3-105">この構成には全 3 種類のサーバー同士のサーバー間認証が含まれており、この構成で作成されるテスト ラボでは、Exchange Server 2013 を実行するサーバー、Lync Server 2013 を実行するサーバー、SharePoint Server 2013 を実行するサーバーを使用する複数製品のシナリオとソリューションを構築して、デモンストレーションすることができます。</span><span class="sxs-lookup"><span data-stu-id="752b3-105">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="752b3-106">このドキュメントには、次のことを行うための手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="752b3-106">This document contains instructions for the following:</span></span>
  
1. <span data-ttu-id="752b3-107">Windows Server 2012 の基本構成テスト ラボの構成。</span><span class="sxs-lookup"><span data-stu-id="752b3-107">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="752b3-108">SQL1 という名前の新しいサーバーのインストールおよび構成。</span><span class="sxs-lookup"><span data-stu-id="752b3-108">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="752b3-109">SQL1 サーバーへの SQL Server 2012 のインストール。</span><span class="sxs-lookup"><span data-stu-id="752b3-109">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="752b3-110">CLIENT2 という名前の新しいクライアント コンピューターのインストールおよび構成。</span><span class="sxs-lookup"><span data-stu-id="752b3-110">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="752b3-111">EX1 への Exchange Server 2013 のインストールおよび構成。</span><span class="sxs-lookup"><span data-stu-id="752b3-111">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="752b3-112">LYNC1 という名前の新しいサーバーのインストールおよび構成。</span><span class="sxs-lookup"><span data-stu-id="752b3-112">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="752b3-113">LYNC1 への Lync Server 2013 Standard Edition のインストール。</span><span class="sxs-lookup"><span data-stu-id="752b3-113">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="752b3-114">SP1 への SharePoint Server 2013 のインストール。</span><span class="sxs-lookup"><span data-stu-id="752b3-114">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="752b3-115">EX1、LYNC1、および SP1 間の統合の構成。</span><span class="sxs-lookup"><span data-stu-id="752b3-115">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="752b3-116">**Exchange、Lync、および SharePoint の統合テスト ラボのガイドの概要ビデオを見る**</span><span class="sxs-lookup"><span data-stu-id="752b3-116">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

![ビデオ (再生ボタン) アイコン](images/mod_icon_video_M.png)
  
<span data-ttu-id="752b3-118">Hyper-V でこのテスト ラボを構成する方法の詳細については、「[Windows Server 2012 Hyper-V で Exchange、Lync、および SharePoint 統合テスト ラボをホストする](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="752b3-118">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="752b3-119">テスト ラボ ガイドをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="752b3-119">Download the test lab guide</span></span>

<span data-ttu-id="752b3-120">[テスト ラボ ガイド: Exchange、Lync、および SharePoint 統合テスト ラボの構成](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="752b3-120">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="752b3-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="752b3-121">See Also</span></span>

[<span data-ttu-id="752b3-122">テスト ラボ ガイド</span><span class="sxs-lookup"><span data-stu-id="752b3-122">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




