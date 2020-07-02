---
title: 電子情報開示用にファイル収集を自動化する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 概要:電子情報開示用にユーザーのコンピューターのファイル収集を自動化する方法について説明します。
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997978"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="79ad5-103">電子情報開示用にファイル収集を自動化する</span><span class="sxs-lookup"><span data-stu-id="79ad5-103">Automate file collection for eDiscovery</span></span>

<span data-ttu-id="79ad5-104">All companies face the potential of lawsuits or other types of legal action.</span><span class="sxs-lookup"><span data-stu-id="79ad5-104">All companies face the potential of lawsuits or other types of legal action.</span></span> <span data-ttu-id="79ad5-105">While legal departments work to reduce that exposure, litigation is a fact of business life.</span><span class="sxs-lookup"><span data-stu-id="79ad5-105">While legal departments work to reduce that exposure, litigation is a fact of business life.</span></span> <span data-ttu-id="79ad5-106">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span><span class="sxs-lookup"><span data-stu-id="79ad5-106">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="79ad5-107">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span><span class="sxs-lookup"><span data-stu-id="79ad5-107">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span></span> <span data-ttu-id="79ad5-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span><span class="sxs-lookup"><span data-stu-id="79ad5-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span></span> <span data-ttu-id="79ad5-109">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span><span class="sxs-lookup"><span data-stu-id="79ad5-109">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="79ad5-110">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span><span class="sxs-lookup"><span data-stu-id="79ad5-110">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span></span> <span data-ttu-id="79ad5-111">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="79ad5-111">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span></span> <span data-ttu-id="79ad5-112">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span><span class="sxs-lookup"><span data-stu-id="79ad5-112">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="79ad5-113">このソリューションで行うこと</span><span class="sxs-lookup"><span data-stu-id="79ad5-113">What this solution does</span></span>

<span data-ttu-id="79ad5-114">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span><span class="sxs-lookup"><span data-stu-id="79ad5-114">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span></span> <span data-ttu-id="79ad5-115">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="79ad5-115">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span></span> <span data-ttu-id="79ad5-116">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="79ad5-116">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span></span> <span data-ttu-id="79ad5-117">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="79ad5-117">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="79ad5-118">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span><span class="sxs-lookup"><span data-stu-id="79ad5-118">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span></span> <span data-ttu-id="79ad5-119">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span><span class="sxs-lookup"><span data-stu-id="79ad5-119">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span></span> <span data-ttu-id="79ad5-120">You will have to collect them manually.</span><span class="sxs-lookup"><span data-stu-id="79ad5-120">You will have to collect them manually.</span></span> <span data-ttu-id="79ad5-121">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span><span class="sxs-lookup"><span data-stu-id="79ad5-121">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="79ad5-122">次の図は、ソリューションのすべての手順と要素を順を追って説明しています。</span><span class="sxs-lookup"><span data-stu-id="79ad5-122">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![自動ファイル コレクション ソリューションの概要](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="79ad5-124">\*\*\*\*凡例\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="79ad5-124">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![マゼンタの吹き出し 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="79ad5-126">グループ ポリシー オブジェクト (GPO) を作成し、コレクションのログオン スクリプトと関連付ける。</span><span class="sxs-lookup"><span data-stu-id="79ad5-126">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![マゼンタの吹き出し 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="79ad5-128">  GPO セキュリティ フィルターを構成して、管理者グループにのみ GPO を適用する</span><span class="sxs-lookup"><span data-stu-id="79ad5-128">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![マゼンタの吹き出し 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="79ad5-130">保管担当者がログオンし、GPO が実行され、コレクションのログオン スクリプトが呼び出される。</span><span class="sxs-lookup"><span data-stu-id="79ad5-130">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![マゼンタの吹き出し 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="79ad5-132">コレクションのログオン スクリプトは、保管担当者のコンピューターにローカルにアタッチされたドライブのすべてのインベントリを作成し、目的のファイルを検索し、その場所を記録します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-132">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![マゼンタの吹き出し 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="79ad5-134">コレクションのログオン スクリプトは、ステージング サーバー上の非表示のファイル共有に、インベントリが作成されたファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="79ad5-134">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![マゼンタの吹き出し 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="79ad5-136">(オプション A) PST インポート スクリプトを手動で実行して、収集した PST ファイルを Exchange Server 2013 にインポートします。</span><span class="sxs-lookup"><span data-stu-id="79ad5-136">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![マゼンタの吹き出し 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="79ad5-138">(オプション B)Microsoft 365 インポートツールとプロセスを使用して、収集した PST ファイルを Exchange Online にインポートします。</span><span class="sxs-lookup"><span data-stu-id="79ad5-138">(Option B) Using the Microsoft 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![マゼンタの吹き出し 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="79ad5-140">MoveToColdStorageSystem Center Orchestrator 2012 R2 Runbook での長期保存用に、収集したファイルをすべて Azure ファイル共有に移動します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-140">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![マゼンタの吹き出し 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="79ad5-142">SharePoint 2013 によりコールド ストレージ ファイル共有にファイルのインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-142">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![マゼンタの吹き出し 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="79ad5-144">コールド ストレージとオンプレミスの Exchange Server 2013 のコンテンツで eDiscovery を実行します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-144">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![マゼンタの吹き出し 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="79ad5-146">Microsoft 365 のコンテンツに対して電子情報開示を実行します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-146">Perform eDiscovery on content in Microsoft 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="79ad5-147">前提条件</span><span class="sxs-lookup"><span data-stu-id="79ad5-147">Prerequisites</span></span>

<span data-ttu-id="79ad5-148">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="79ad5-148">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span></span> <span data-ttu-id="79ad5-149">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span><span class="sxs-lookup"><span data-stu-id="79ad5-149">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span></span> <span data-ttu-id="79ad5-150">You must have the base configuration in place before you configure the solution itself.</span><span class="sxs-lookup"><span data-stu-id="79ad5-150">You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="79ad5-151">基本構成</span><span class="sxs-lookup"><span data-stu-id="79ad5-151">Base configuration</span></span>

|<span data-ttu-id="79ad5-152">**要素**</span><span class="sxs-lookup"><span data-stu-id="79ad5-152">**Element**</span></span>|<span data-ttu-id="79ad5-153">**リンク**</span><span class="sxs-lookup"><span data-stu-id="79ad5-153">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="79ad5-154">Active Directory ドメイン サービス (AD DS) ドメイン</span><span class="sxs-lookup"><span data-stu-id="79ad5-154">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="79ad5-155">オンプレミス ネットワークからのインターネット接続</span><span class="sxs-lookup"><span data-stu-id="79ad5-155">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="79ad5-156">SharePoint 2013 と System Center Orchestrator 2012 R2 をサポートする SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="79ad5-156">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="79ad5-157">System Center 2012 - Orchestrator の展開</span><span class="sxs-lookup"><span data-stu-id="79ad5-157">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="79ad5-158">eDiscovery 用のオンプレミスまたは Azure ベースの SharePoint 2013 (オプション A で必要)</span><span class="sxs-lookup"><span data-stu-id="79ad5-158">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="79ad5-159">ステージング用のオンプレミス ファイル共有サーバー</span><span class="sxs-lookup"><span data-stu-id="79ad5-159">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="79ad5-160">オプション A の PST をインポートするためのオンプレミス Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="79ad5-160">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="79ad5-161">CU5 (15.913.22) は、「[CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)」で入手できます。</span><span class="sxs-lookup"><span data-stu-id="79ad5-161">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="79ad5-162">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="79ad5-162">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="79ad5-163">System Center 2012 - Orchestrator の展開</span><span class="sxs-lookup"><span data-stu-id="79ad5-163">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="79ad5-164">Microsoft 365 E3 with Exchange Online および SharePoint Online (オプション B に必要)</span><span class="sxs-lookup"><span data-stu-id="79ad5-164">Microsoft 365 E3 with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="79ad5-165">Microsoft 365 E3 サブスクリプションにサインアップするには、「 [microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79ad5-165">To sign up for a Microsoft 365 E3 subscription, see [Microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span></span>  <br/> |
|<span data-ttu-id="79ad5-166">仮想マシンでの Azure サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="79ad5-166">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="79ad5-167">Azure にサインアップするには、「[Microsoft Azure をサブスクライブする](https://go.microsoft.com/fwlink/p/?LinkId=512010)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79ad5-167">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="79ad5-168">オンプレミス ネットワークと Azure サブスクリプションの間の VPN 接続</span><span class="sxs-lookup"><span data-stu-id="79ad5-168">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="79ad5-169">Azure サブスクリプションとオンプレミス ネットワークの間に VPN トンネルをセット アップするには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](https://go.microsoft.com/fwlink/p/?LinkId=613507)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79ad5-169">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="79ad5-170">SharePoint 2013SharePoint と Exchange Server 2013、および必要に応じて Lync Server 2013 の間で検索するように eDiscovery を構成</span><span class="sxs-lookup"><span data-stu-id="79ad5-170">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="79ad5-171">この方法で eDiscovery を構成するには、「[電子情報開示を構成する (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=613508)」および「[テスト ラボ ガイド: Exchange、Lync、SharePoint、Windows のファイル共有テスト ラボの電子情報開示を構成する](https://go.microsoft.com/fwlink/p/?LinkId=393130)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79ad5-171">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="79ad5-172">Microsoft 365 の電子情報開示 (SharePoint Online および Exchange Online)</span><span class="sxs-lookup"><span data-stu-id="79ad5-172">eDiscovery in Microsoft 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="79ad5-173">Microsoft 365 で電子情報開示を構成するには、「 [SharePoint Online で電子情報開示センターをセットアップ](https://go.microsoft.com/fwlink/p/?LinkId=613628)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79ad5-173">To configure eDiscovery in Microsoft 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="79ad5-174">環境を構成する</span><span class="sxs-lookup"><span data-stu-id="79ad5-174">Configure the environment</span></span>

<span data-ttu-id="79ad5-175">基本構成の準備が整ったので、 ソリューション自体の構成に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="79ad5-175">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="79ad5-176">ステージング ファイル共有</span><span class="sxs-lookup"><span data-stu-id="79ad5-176">Staging file share</span></span>

1. <span data-ttu-id="79ad5-177">オンプレミス ドメインで、Custodians という名前のグローバル セキュリティ グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-177">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="79ad5-178">Create a hidden file share for the files that are collected from Custodians computers.</span><span class="sxs-lookup"><span data-stu-id="79ad5-178">Create a hidden file share for the files that are collected from Custodians computers.</span></span> <span data-ttu-id="79ad5-179">This should be on an on-premises server.</span><span class="sxs-lookup"><span data-stu-id="79ad5-179">This should be on an on-premises server.</span></span> <span data-ttu-id="79ad5-180">For example, on a server called Staging, create a file share called Cases$.</span><span class="sxs-lookup"><span data-stu-id="79ad5-180">For example, on a server called Staging, create a file share called Cases$.</span></span> <span data-ttu-id="79ad5-181">The **$** is required to make this a hidden share.</span><span class="sxs-lookup"><span data-stu-id="79ad5-181">The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="79ad5-182">次の共有アクセス許可を設定します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-182">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="79ad5-183">保管担当者:変更、読み取り</span><span class="sxs-lookup"><span data-stu-id="79ad5-183">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="79ad5-184">管理者 :フル コントロール</span><span class="sxs-lookup"><span data-stu-id="79ad5-184">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="79ad5-185">Exchange Trusted Subsystem:変更、読み取り</span><span class="sxs-lookup"><span data-stu-id="79ad5-185">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="79ad5-186">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="79ad5-186">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span></span> <span data-ttu-id="79ad5-187">Set the following permissions for the Custodians group:</span><span class="sxs-lookup"><span data-stu-id="79ad5-187">Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="79ad5-188">**種類:拒否**</span><span class="sxs-lookup"><span data-stu-id="79ad5-188">**Type: Deny**</span></span>
    
  - <span data-ttu-id="79ad5-189">**適用対象:このフォルダー、サブフォルダー、およびファイル**</span><span class="sxs-lookup"><span data-stu-id="79ad5-189">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="79ad5-190">**[高度なアクセス許可]** をクリックし、以下を選びます。</span><span class="sxs-lookup"><span data-stu-id="79ad5-190">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="79ad5-191">**属性の読み取り**</span><span class="sxs-lookup"><span data-stu-id="79ad5-191">**Read attributes**</span></span>
    
  - <span data-ttu-id="79ad5-192">**拡張属性の読み取り**</span><span class="sxs-lookup"><span data-stu-id="79ad5-192">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="79ad5-193">**アクセス許可の読み取り**</span><span class="sxs-lookup"><span data-stu-id="79ad5-193">**Read permissions**</span></span>
    
6. <span data-ttu-id="79ad5-194">以下を実行して、Cases$ ファイル共有にテスト アクセスします。</span><span class="sxs-lookup"><span data-stu-id="79ad5-194">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="79ad5-195">保管担当者グループにユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-195">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="79ad5-196">Cases$ フォルダーにファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-196">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="79ad5-197">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span><span class="sxs-lookup"><span data-stu-id="79ad5-197">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span></span> <span data-ttu-id="79ad5-198">You shouldn't see the **Cases$** share listed.</span><span class="sxs-lookup"><span data-stu-id="79ad5-198">You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="79ad5-199">Manually type the full path to the Cases$ share into Explorer.</span><span class="sxs-lookup"><span data-stu-id="79ad5-199">Manually type the full path to the Cases$ share into Explorer.</span></span> <span data-ttu-id="79ad5-200">This should open the Cases$ share.</span><span class="sxs-lookup"><span data-stu-id="79ad5-200">This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="79ad5-201">Try to open the file you previously placed in the share.</span><span class="sxs-lookup"><span data-stu-id="79ad5-201">Try to open the file you previously placed in the share.</span></span> <span data-ttu-id="79ad5-202">This should fail.</span><span class="sxs-lookup"><span data-stu-id="79ad5-202">This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="79ad5-203">ログオン スクリプト</span><span class="sxs-lookup"><span data-stu-id="79ad5-203">Logon script</span></span>

1. <span data-ttu-id="79ad5-204">この Windows PowerShell スクリプトをコピーして、メモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="79ad5-204">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. <span data-ttu-id="79ad5-205">上記のスクリプトを、CollectionScript.ps1 として、C:\\AFCScripts などの見つけやすい場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-205">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="79ad5-206">Use the Go To feature in Notepad.</span><span class="sxs-lookup"><span data-stu-id="79ad5-206">Use the Go To feature in Notepad.</span></span> <span data-ttu-id="79ad5-207">Make the following changes, as needed:</span><span class="sxs-lookup"><span data-stu-id="79ad5-207">Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="79ad5-208">**行番号**</span><span class="sxs-lookup"><span data-stu-id="79ad5-208">**Line #**</span></span>|<span data-ttu-id="79ad5-209">**変更するために必要な事柄**</span><span class="sxs-lookup"><span data-stu-id="79ad5-209">**What you need to change**</span></span>|<span data-ttu-id="79ad5-210">**必須かどうか**</span><span class="sxs-lookup"><span data-stu-id="79ad5-210">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="79ad5-211">71</span><span class="sxs-lookup"><span data-stu-id="79ad5-211">71</span></span>  <br/> |<span data-ttu-id="79ad5-212">**$FileTypes** variable.</span><span class="sxs-lookup"><span data-stu-id="79ad5-212">**$FileTypes** variable.</span></span> <span data-ttu-id="79ad5-213">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span><span class="sxs-lookup"><span data-stu-id="79ad5-213">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span></span> <br/> |<span data-ttu-id="79ad5-214">オプション</span><span class="sxs-lookup"><span data-stu-id="79ad5-214">Optional</span></span>  <br/> |
|<span data-ttu-id="79ad5-215">76 と 77</span><span class="sxs-lookup"><span data-stu-id="79ad5-215">76 and 77</span></span>  <br/> |<span data-ttu-id="79ad5-216">Change the way the **$CaseNo** variable is built to suit your needs.</span><span class="sxs-lookup"><span data-stu-id="79ad5-216">Change the way the **$CaseNo** variable is built to suit your needs.</span></span> <span data-ttu-id="79ad5-217">The script captures the current date and time and appends the user name to it.</span><span class="sxs-lookup"><span data-stu-id="79ad5-217">The script captures the current date and time and appends the user name to it.</span></span> <br/> |<span data-ttu-id="79ad5-218">オプション</span><span class="sxs-lookup"><span data-stu-id="79ad5-218">Optional</span></span>  <br/> |
|<span data-ttu-id="79ad5-219">80</span><span class="sxs-lookup"><span data-stu-id="79ad5-219">80</span></span>  <br/> |<span data-ttu-id="79ad5-220">**$CaseRootLocation** 変数は、ステージング サーバー コレクション ファイル共有に設定する必要があります。例: **\\\\Staging\\Cases$**</span><span class="sxs-lookup"><span data-stu-id="79ad5-220">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="79ad5-221">必須</span><span class="sxs-lookup"><span data-stu-id="79ad5-221">Required</span></span>  <br/> |
   
4. <span data-ttu-id="79ad5-222">ドメイン コントローラーの Netlogon ファイル共有に CollectionScript.ps1 ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-222">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="79ad5-223">ログオン スクリプトと保管担当者グループの GPO を構成します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-223">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="79ad5-224">トピック「[グループ ポリシーで起動、シャットダウン、ログオン、ログオフ スクリプトを使用する](https://go.microsoft.com/fwlink/p/?LinkId=614844)」の「ユーザー ログオン スクリプトを割り当てる方法」セクションに従って、保管担当者グループに対してログオン スクリプトを構成します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-224">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="79ad5-225">**セキュリティ フィルター** から認証ユーザーを削除し、保管担当者グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-225">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="79ad5-226">PST インポートのオプション A (Exchange Server 2013 用のスクリプト)</span><span class="sxs-lookup"><span data-stu-id="79ad5-226">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="79ad5-227">次の Windows PowerShell スクリプトをコピーして、メモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="79ad5-227">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. <span data-ttu-id="79ad5-228">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span><span class="sxs-lookup"><span data-stu-id="79ad5-228">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span></span> <span data-ttu-id="79ad5-229">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span><span class="sxs-lookup"><span data-stu-id="79ad5-229">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="79ad5-230">メモ帳の移動機能を使用して、必要に応じて次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="79ad5-230">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="79ad5-231">**行番号**</span><span class="sxs-lookup"><span data-stu-id="79ad5-231">**Line #**</span></span>|<span data-ttu-id="79ad5-232">**変更するために必要な事柄**</span><span class="sxs-lookup"><span data-stu-id="79ad5-232">**What you need to change**</span></span>|<span data-ttu-id="79ad5-233">**必須かどうか**</span><span class="sxs-lookup"><span data-stu-id="79ad5-233">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="79ad5-234">12 </span><span class="sxs-lookup"><span data-stu-id="79ad5-234">12</span></span>  <br/> |<span data-ttu-id="79ad5-235">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span><span class="sxs-lookup"><span data-stu-id="79ad5-235">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span></span> <span data-ttu-id="79ad5-236">Change this if necessary.</span><span class="sxs-lookup"><span data-stu-id="79ad5-236">Change this if necessary.</span></span> <br/> |<span data-ttu-id="79ad5-237">省略可能</span><span class="sxs-lookup"><span data-stu-id="79ad5-237">Optional</span></span>  <br/> |
|<span data-ttu-id="79ad5-238">17 </span><span class="sxs-lookup"><span data-stu-id="79ad5-238">17</span></span>  <br/> |<span data-ttu-id="79ad5-239">**$ConnectionUri** は独自のサーバーに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79ad5-239">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="79ad5-240">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span><span class="sxs-lookup"><span data-stu-id="79ad5-240">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span></span> <span data-ttu-id="79ad5-241">It won't work with https:.</span><span class="sxs-lookup"><span data-stu-id="79ad5-241">It won't work with https:.</span></span>          |<span data-ttu-id="79ad5-242">必須</span><span class="sxs-lookup"><span data-stu-id="79ad5-242">Required</span></span>  <br/> |
   
4. <span data-ttu-id="79ad5-243">Exchange Trusted Subsystem アカウントに、\\\\Staging\\Cases$ 共有に対する読み取り、書き込み、実行のアクセス許可があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-243">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="79ad5-244">PST インポート スクリプトには、次の 2 つの入力パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="79ad5-244">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="79ad5-245">**$SourcePath** たとえば \\\\Staging\\Cases$ などの、インポートする PST ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="79ad5-245">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="79ad5-246">**$MailboxAlias** インポートされたメール アイテムを受信するターゲット メールボックスのエイリアス</span><span class="sxs-lookup"><span data-stu-id="79ad5-246">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="79ad5-247">たとえば、すべての PST ファイルをパス \\Staging\Cases$ からエイリアス eDiscoveryMailbox を持つメールボックスにインポートする場合は、次のようなスクリプトを実行します `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`。</span><span class="sxs-lookup"><span data-stu-id="79ad5-247">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="79ad5-248">PST インポートのオプション B (Exchange Online の場合)</span><span class="sxs-lookup"><span data-stu-id="79ad5-248">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="79ad5-249">Create the mailbox structure to place the imported PST files into.</span><span class="sxs-lookup"><span data-stu-id="79ad5-249">Create the mailbox structure to place the imported PST files into.</span></span> <span data-ttu-id="79ad5-250">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="79ad5-250">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="79ad5-251">コールド ストレージ</span><span class="sxs-lookup"><span data-stu-id="79ad5-251">Cold storage</span></span>

1. <span data-ttu-id="79ad5-252">Azure Virtual Machine にファイル共有を作成します。ここに収集したすべてのファイルを配置します。例: \\\\AZFile1\\ContentColdStorage</span><span class="sxs-lookup"><span data-stu-id="79ad5-252">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="79ad5-253">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span><span class="sxs-lookup"><span data-stu-id="79ad5-253">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span></span> <span data-ttu-id="79ad5-254">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span><span class="sxs-lookup"><span data-stu-id="79ad5-254">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="79ad5-255">PST ファイルを \\\\AZFile1\\ContentColdStorage からインポートすることを見込んでいる場合は、Exchange Trusted Subsystem に対して共有への読み取り、書き込み、実行のアクセス許可を付与します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-255">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="79ad5-256">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="79ad5-256">Orchestrator</span></span>

1. <span data-ttu-id="79ad5-257">Microsoft ダウンロード センターから、[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="79ad5-257">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="79ad5-258">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span><span class="sxs-lookup"><span data-stu-id="79ad5-258">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span></span> <span data-ttu-id="79ad5-259">Click the **Actions** menu, and the click **Import**.</span><span class="sxs-lookup"><span data-stu-id="79ad5-259">Click the **Actions** menu, and the click **Import**.</span></span> <span data-ttu-id="79ad5-260">The **Import** dialog box appears.</span><span class="sxs-lookup"><span data-stu-id="79ad5-260">The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="79ad5-261">**[ファイルの場所]** ボックスで、インポートする Runbook のパスとファイル名を入力するか、省略記号 ( **...**) をクリックしてインポートするファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-261">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="79ad5-262">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span><span class="sxs-lookup"><span data-stu-id="79ad5-262">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span></span> <span data-ttu-id="79ad5-263">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span><span class="sxs-lookup"><span data-stu-id="79ad5-263">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="79ad5-264">[ **完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79ad5-264">Click **Finish**.</span></span>
    
6. <span data-ttu-id="79ad5-265">**MoveFilesToColdStorage** Runbook を次のように編集します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-265">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="79ad5-266">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span><span class="sxs-lookup"><span data-stu-id="79ad5-266">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="79ad5-267">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="79ad5-267">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="79ad5-268">Select **Create a file with a unique name**.</span><span class="sxs-lookup"><span data-stu-id="79ad5-268">Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="79ad5-269">**[フォルダーの削除]** アクティビティ - **[パス]** をコレクション ファイル共有 (例: \\\\Staging\\cases$\\*) に設定し、 **[すべてのファイルとサブフォルダーを削除する]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="79ad5-269">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="79ad5-270">「[Runbook の展開](https://go.microsoft.com/fwlink/p/?LinkId=615120)」にある手順を使用して、 **MoveToColdStorage** Runbook を展開します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-270">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="79ad5-271">コールド ストレージ用 SharePoint オンプレミス検索</span><span class="sxs-lookup"><span data-stu-id="79ad5-271">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="79ad5-272">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="79ad5-272">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="79ad5-273">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="79ad5-273">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="79ad5-274">Start a full crawl.</span><span class="sxs-lookup"><span data-stu-id="79ad5-274">Start a full crawl.</span></span> <span data-ttu-id="79ad5-275">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="79ad5-275">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="79ad5-276">ソリューションの使用</span><span class="sxs-lookup"><span data-stu-id="79ad5-276">Using the solution</span></span>

<span data-ttu-id="79ad5-277">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="79ad5-277">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span></span> <span data-ttu-id="79ad5-278">This section provides you with the procedures for all of them.</span><span class="sxs-lookup"><span data-stu-id="79ad5-278">This section provides you with the procedures for all of them.</span></span> <span data-ttu-id="79ad5-279">Your primary interaction with the solution will be in doing the following:</span><span class="sxs-lookup"><span data-stu-id="79ad5-279">Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="79ad5-280">保管担当者グループのユーザー メンバーシップを管理する。</span><span class="sxs-lookup"><span data-stu-id="79ad5-280">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="79ad5-281">Review the log files generated by the logon script.</span><span class="sxs-lookup"><span data-stu-id="79ad5-281">Review the log files generated by the logon script.</span></span> <span data-ttu-id="79ad5-282">The FileCopyErrors.log lists all the files that were not successfully copied.</span><span class="sxs-lookup"><span data-stu-id="79ad5-282">The FileCopyErrors.log lists all the files that were not successfully copied.</span></span> <span data-ttu-id="79ad5-283">You need to decide what you want to do with them</span><span class="sxs-lookup"><span data-stu-id="79ad5-283">You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="79ad5-284">PST のインポート プロセスを管理する。</span><span class="sxs-lookup"><span data-stu-id="79ad5-284">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="79ad5-285">コレクション ファイルをコールド ストレージに移動する。</span><span class="sxs-lookup"><span data-stu-id="79ad5-285">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="79ad5-286">他のすべての手順は、このソリューションに固有のものではありません。</span><span class="sxs-lookup"><span data-stu-id="79ad5-286">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="79ad5-287">SharePoint 2013、Microsoft 365、および Azure で実行する標準的な管理タスクです。</span><span class="sxs-lookup"><span data-stu-id="79ad5-287">They are standard administrative tasks that you perform in SharePoint 2013, Microsoft 365, and Azure.</span></span> <span data-ttu-id="79ad5-288">このソリューションでは、次のような会社のニーズに基づいて、解決する必要があるガイダンスが提供されていません。</span><span class="sxs-lookup"><span data-stu-id="79ad5-288">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="79ad5-289">eDiscovery のケースを追跡し、どの保管担当者がどのケースに関連付けられているかを追跡する。</span><span class="sxs-lookup"><span data-stu-id="79ad5-289">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="79ad5-290">どのファイル コレクションのセットがどの eDiscovery のケースに関連付けられているかを追跡する。</span><span class="sxs-lookup"><span data-stu-id="79ad5-290">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="79ad5-291">インポートのタイミングを調整し、コールド ストレージのステップに移動する。</span><span class="sxs-lookup"><span data-stu-id="79ad5-291">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="79ad5-292">Azure で使用するファイル領域を管理する。</span><span class="sxs-lookup"><span data-stu-id="79ad5-292">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="79ad5-293">PST のインポート先メールボックスを管理する。</span><span class="sxs-lookup"><span data-stu-id="79ad5-293">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="79ad5-294">すべてのオンプレミス データのバックアップおよび復元。</span><span class="sxs-lookup"><span data-stu-id="79ad5-294">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="79ad5-295">保管担当者管理</span><span class="sxs-lookup"><span data-stu-id="79ad5-295">Custodian management</span></span>

- <span data-ttu-id="79ad5-296">To start the automated file collection process for an individual user, add them to the Custodians group.</span><span class="sxs-lookup"><span data-stu-id="79ad5-296">To start the automated file collection process for an individual user, add them to the Custodians group.</span></span> <span data-ttu-id="79ad5-297">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span><span class="sxs-lookup"><span data-stu-id="79ad5-297">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="79ad5-298">収集ファイルの監視とログ ファイルの確認</span><span class="sxs-lookup"><span data-stu-id="79ad5-298">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="79ad5-299">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span><span class="sxs-lookup"><span data-stu-id="79ad5-299">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span></span> <span data-ttu-id="79ad5-300">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span><span class="sxs-lookup"><span data-stu-id="79ad5-300">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="79ad5-301">When the collection is completed, open the collection folder, and browse to the _Log folder.</span><span class="sxs-lookup"><span data-stu-id="79ad5-301">When the collection is completed, open the collection folder, and browse to the _Log folder.</span></span> <span data-ttu-id="79ad5-302">In the _Log folder, you will see the following:</span><span class="sxs-lookup"><span data-stu-id="79ad5-302">In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="79ad5-303">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span><span class="sxs-lookup"><span data-stu-id="79ad5-303">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span></span> <span data-ttu-id="79ad5-304">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span><span class="sxs-lookup"><span data-stu-id="79ad5-304">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="79ad5-305">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span><span class="sxs-lookup"><span data-stu-id="79ad5-305">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span></span> <span data-ttu-id="79ad5-306">It will not create an inventory entry for every file on the user's computer.</span><span class="sxs-lookup"><span data-stu-id="79ad5-306">It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="79ad5-307">One log file named FileCopyErrors.log for each collection run.</span><span class="sxs-lookup"><span data-stu-id="79ad5-307">One log file named FileCopyErrors.log for each collection run.</span></span> <span data-ttu-id="79ad5-308">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span><span class="sxs-lookup"><span data-stu-id="79ad5-308">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span></span> <span data-ttu-id="79ad5-309">You will need to review this and decide what actions to take for these missed files.</span><span class="sxs-lookup"><span data-stu-id="79ad5-309">You will need to review this and decide what actions to take for these missed files.</span></span> <span data-ttu-id="79ad5-310">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span><span class="sxs-lookup"><span data-stu-id="79ad5-310">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="79ad5-311">PST インポートのオプション A (Exchange Server 2013 の場合)</span><span class="sxs-lookup"><span data-stu-id="79ad5-311">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="79ad5-312">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79ad5-312">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span></span> <span data-ttu-id="79ad5-313">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="79ad5-313">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="79ad5-314">Set the Execution policy to Unrestricted .</span><span class="sxs-lookup"><span data-stu-id="79ad5-314">Set the Execution policy to Unrestricted .</span></span> <span data-ttu-id="79ad5-315">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span><span class="sxs-lookup"><span data-stu-id="79ad5-315">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="79ad5-316">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span><span class="sxs-lookup"><span data-stu-id="79ad5-316">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span></span> <span data-ttu-id="79ad5-317">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="79ad5-317">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="79ad5-318">エラーの出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-318">Review the output for errors.</span></span>
    
5. <span data-ttu-id="79ad5-319">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span><span class="sxs-lookup"><span data-stu-id="79ad5-319">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span></span> <span data-ttu-id="79ad5-320">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span><span class="sxs-lookup"><span data-stu-id="79ad5-320">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span></span> <span data-ttu-id="79ad5-321">You will be prompted to remove each individual request from the queue.</span><span class="sxs-lookup"><span data-stu-id="79ad5-321">You will be prompted to remove each individual request from the queue.</span></span> <span data-ttu-id="79ad5-322">Respond as needed.</span><span class="sxs-lookup"><span data-stu-id="79ad5-322">Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="79ad5-323">PST インポートのオプション B (Exchange Online の場合)</span><span class="sxs-lookup"><span data-stu-id="79ad5-323">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="79ad5-324">収集した PST ファイルを Exchange Online に配置するには、「Microsoft 365 へのファイルのインポートに[ネットワークアップロード](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files)を使用する」の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-324">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Microsoft 365 through [network upload](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="79ad5-325">コールド ストレージに移動</span><span class="sxs-lookup"><span data-stu-id="79ad5-325">Move to cold storage</span></span>

1. <span data-ttu-id="79ad5-326">[Runbook の実行](https://go.microsoft.com/fwlink/p/?LinkId=615123)に関する手順を使用して、 **Movetocoldstorage** runbook を実行します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-326">Run the **MoveToColdStorage** runbook using the procedures in [Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="79ad5-327">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span><span class="sxs-lookup"><span data-stu-id="79ad5-327">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="79ad5-328">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span><span class="sxs-lookup"><span data-stu-id="79ad5-328">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="79ad5-329">電子情報開示</span><span class="sxs-lookup"><span data-stu-id="79ad5-329">eDiscovery</span></span>

1. <span data-ttu-id="79ad5-330">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span><span class="sxs-lookup"><span data-stu-id="79ad5-330">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span></span> <span data-ttu-id="79ad5-331">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="79ad5-331">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="79ad5-332">PST ファイルのインポートにオプション A を使用した場合は、SharePoint 2013 に eDiscovery ケースを作成します。オプション B を使用した場合は、SharePoint Online に eDiscovery ケースを作成します。</span><span class="sxs-lookup"><span data-stu-id="79ad5-332">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

