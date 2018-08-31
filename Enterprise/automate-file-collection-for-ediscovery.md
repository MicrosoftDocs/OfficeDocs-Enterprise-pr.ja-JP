---
title: 電子情報開示用にファイル収集を自動化する
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 概要:電子情報開示用にユーザーのコンピューターのファイル収集を自動化する方法について説明します。
ms.openlocfilehash: 12d61d2c43a297001eecf463991654afbcfccb1a
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915752"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="f5779-103">電子情報開示用にファイル収集を自動化する</span><span class="sxs-lookup"><span data-stu-id="f5779-103">Automate file collection for eDiscovery</span></span>

 <span data-ttu-id="f5779-104">**概要:** 電子情報開示用にユーザーのコンピューターのファイル収集を自動化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5779-104">**Summary:** Learn how to automate file collection from user computers for eDiscovery.</span></span>
  
<span data-ttu-id="f5779-p101">すべての企業は、訴訟やその他の法的措置の可能性に直面しています。法務部門はリスクの軽減に努める一方で、訴訟はビジネス ライフの 1 つの現実です。企業は、必要とする法的措置に直面すると、法的証拠開示のプロセスを通じて、裁判所および相手方の弁護士にすべての関連資料を提供します。</span><span class="sxs-lookup"><span data-stu-id="f5779-p101">All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="f5779-p102">電子情報開示は、電子的な形式の関連資料を企業がインベントリ作成、検索、識別、保持、フィルター処理、使用可能化するプロセスです。 SharePoint 2013、Exchange Server 2013、Lync Server 2013、SharePoint Online、Exchange Online は、大量の文書コンテンツを保持できます。 これらの製品のバージョンによっては、eDiscovery とインプレース保持がサポートされています (Lync は Exchange Server 経由)。これにより、法務チームは、訴訟に最も関係のある内容のインデックスの作成、特定、保持、フィルター処理を行いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="f5779-p102">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="f5779-p103">多くのドキュメントは一元的に 1 つの場所にまとめられておらず、ユーザー (保管担当者) のローカル コンピューターに保存されています。このため、SharePoint 2013 は基本的に検索ができなくなり、検索ができないと eDiscovery に含めることができません。このソリューションでは、ログオン スクリプト、Exchange Server の System Center Orchestrator 2012 R2 および Windows PowerShell を使用して、ユーザーのコンピューターから資料の特定と収集を自動で行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f5779-p103">Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="f5779-114">このソリューションで行うこと</span><span class="sxs-lookup"><span data-stu-id="f5779-114">What this solution does</span></span>

<span data-ttu-id="f5779-p104">このソリューションでは、グローバル セキュリティ グループ、グループ ポリシー、Windows PowerShell スクリプトを使用して、ユーザーのローカル コンピューターから非表示のファイル共有に対してコンテンツと Outlook の個人用ストア (PST) ファイルの特定、インベントリ作成、収集を行います。PST ファイルは、ここから Exchange Server 2013 または Exchange Online のいずれかにインポートできます。すべてのファイルは、長期保存および SharePoint 2013 によるインデックス作成用に、System Center Orchestrator 2012 R2 Runbook を使用して Microsoft Azure の別のファイル共有に移動されます。次に、通常 eDiscovery を行うのと同じように、オンプレミスの SharePoint 2013 展開や SharePoint Online で eDiscovery センターを使用します。</span><span class="sxs-lookup"><span data-stu-id="f5779-p104">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="f5779-p105">このソリューションでは、robocopy を使用して、保管担当者のコンピューターから一元管理されたファイル共有にファイルをコピーします。robocopy では開いているまたはロックされているファイルはコピーされないため、PST ファイルを含め、保管担当者が開いているファイルは収集されません。そのようなものは手動で収集する必要があります。このソリューションでは、コピーできないファイルと各ファイルへの完全パスを明示的に識別する一覧が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f5779-p105">This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="f5779-123">次の図は、ソリューションのすべての手順と要素を順を追って説明しています。</span><span class="sxs-lookup"><span data-stu-id="f5779-123">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![自動ファイル コレクション ソリューションの概要](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="f5779-125">****凡例****</span><span class="sxs-lookup"><span data-stu-id="f5779-125">****Legend****</span></span>||
|:-----|:-----|
|![マゼンタの吹き出し 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="f5779-127">グループ ポリシー オブジェクト (GPO) を作成し、コレクションのログオン スクリプトと関連付ける。</span><span class="sxs-lookup"><span data-stu-id="f5779-127">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![マゼンタの吹き出し 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="f5779-129">  GPO セキュリティ フィルターを構成して、管理者グループにのみ GPO を適用する</span><span class="sxs-lookup"><span data-stu-id="f5779-129">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![マゼンタの吹き出し 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="f5779-131">保管担当者がログオンし、GPO が実行され、コレクションのログオン スクリプトが呼び出される。</span><span class="sxs-lookup"><span data-stu-id="f5779-131">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![マゼンタの吹き出し 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="f5779-133">コレクションのログオン スクリプトは、保管担当者のコンピューターにローカルにアタッチされたドライブのすべてのインベントリを作成し、目的のファイルを検索し、その場所を記録します。</span><span class="sxs-lookup"><span data-stu-id="f5779-133">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![マゼンタの吹き出し 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="f5779-135">コレクションのログオン スクリプトは、ステージング サーバー上の非表示のファイル共有に、インベントリが作成されたファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="f5779-135">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![マゼンタの吹き出し 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="f5779-137">(オプション A) PST インポート スクリプトを手動で実行して、収集した PST ファイルを Exchange Server 2013 にインポートします。</span><span class="sxs-lookup"><span data-stu-id="f5779-137">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![マゼンタの吹き出し 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="f5779-139">(オプション B) Office 365 インポート ツールとプロセスを使用して、収集した PST ファイルを Exchange Online にインポートします。</span><span class="sxs-lookup"><span data-stu-id="f5779-139">(Option B) Using the Office 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![マゼンタの吹き出し 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="f5779-141">MoveToColdStorageSystem Center Orchestrator 2012 R2 Runbook での長期保存用に、収集したファイルをすべて Azure ファイル共有に移動します。</span><span class="sxs-lookup"><span data-stu-id="f5779-141">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![マゼンタの吹き出し 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="f5779-143">SharePoint 2013 によりコールド ストレージ ファイル共有にファイルのインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f5779-143">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![マゼンタの吹き出し 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="f5779-145">コールド ストレージとオンプレミスの Exchange Server 2013 のコンテンツで eDiscovery を実行します。</span><span class="sxs-lookup"><span data-stu-id="f5779-145">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![マゼンタの吹き出し 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="f5779-147">Office 365 のコンテンツで eDiscovery を実行します。</span><span class="sxs-lookup"><span data-stu-id="f5779-147">Perform eDiscovery on content in Office 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="f5779-148">前提条件</span><span class="sxs-lookup"><span data-stu-id="f5779-148">Prerequisites</span></span>

<span data-ttu-id="f5779-p106">このソリューションの構成には、多くの 要素が 必要になります。eDiscovery を検討している場合、それらの要素の多くは既に配置され、構成されている可能性があります。ないかもしれない要素や、特定の構成を必要とする要素については、基本構成の構築に必要なリンクが用意されます。ソリューション自体を構成する前に、基本構成を整えておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5779-p106">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="f5779-152">基本構成</span><span class="sxs-lookup"><span data-stu-id="f5779-152">Base configuration</span></span>

|<span data-ttu-id="f5779-153">**要素**</span><span class="sxs-lookup"><span data-stu-id="f5779-153">**Element**</span></span>|<span data-ttu-id="f5779-154">**リンク**</span><span class="sxs-lookup"><span data-stu-id="f5779-154">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f5779-155">Active Directory ドメイン サービス (AD DS) ドメイン</span><span class="sxs-lookup"><span data-stu-id="f5779-155">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="f5779-156">オンプレミス ネットワークからのインターネット接続</span><span class="sxs-lookup"><span data-stu-id="f5779-156">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="f5779-157">SharePoint 2013 と System Center Orchestrator 2012 R2 をサポートする SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="f5779-157">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="f5779-158">System Center 2012 - Orchestrator の展開</span><span class="sxs-lookup"><span data-stu-id="f5779-158">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="f5779-159">eDiscovery 用のオンプレミスまたは Azure ベースの SharePoint 2013 (オプション A で必要)</span><span class="sxs-lookup"><span data-stu-id="f5779-159">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="f5779-160">ステージング用のオンプレミス ファイル共有サーバー</span><span class="sxs-lookup"><span data-stu-id="f5779-160">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="f5779-161">オプション A の PST をインポートするためのオンプレミス Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="f5779-161">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="f5779-162">CU5 (15.913.22) は、「[CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)」で入手できます。</span><span class="sxs-lookup"><span data-stu-id="f5779-162">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="f5779-163">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f5779-163">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="f5779-164">System Center 2012 - Orchestrator の展開</span><span class="sxs-lookup"><span data-stu-id="f5779-164">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="f5779-165">Exchange Online と SharePoint Online による Office 365 (E3 プラン) (オプション B で必要)</span><span class="sxs-lookup"><span data-stu-id="f5779-165">Office 365 (E3 Plan) with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="f5779-166">Office 365 E3 サブスクリプションにサインアップするには、「[Office 365 E3 サブスクリプション](https://go.microsoft.com/fwlink/p/?LinkId=613504)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-166">To sign up for an Office 365 E3 subscription, see [Office 365 E3 subscription](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span></span>  <br/> |
|<span data-ttu-id="f5779-167">仮想マシンでの Azure サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="f5779-167">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="f5779-168">Azure にサインアップするには、「[Microsoft Azure をサブスクライブする](https://go.microsoft.com/fwlink/p/?LinkId=512010)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-168">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="f5779-169">オンプレミス ネットワークと Azure サブスクリプションの間の VPN 接続</span><span class="sxs-lookup"><span data-stu-id="f5779-169">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="f5779-170">Azure サブスクリプションとオンプレミス ネットワークの間に VPN トンネルをセット アップするには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](https://go.microsoft.com/fwlink/p/?LinkId=613507)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-170">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="f5779-171">SharePoint 2013SharePoint と Exchange Server 2013、および必要に応じて Lync Server 2013 の間で検索するように eDiscovery を構成</span><span class="sxs-lookup"><span data-stu-id="f5779-171">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="f5779-172">この方法で eDiscovery を構成するには、「[電子情報開示を構成する (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=613508)」および「[テスト ラボ ガイド: Exchange、Lync、SharePoint、Windows のファイル共有テスト ラボの電子情報開示を構成する](https://go.microsoft.com/fwlink/p/?LinkId=393130)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-172">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="f5779-173">SharePoint Online と Exchange Online 用の Office 365 の eDiscovery</span><span class="sxs-lookup"><span data-stu-id="f5779-173">eDiscovery in Office 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="f5779-174">Office 365 の eDiscovery を構成するには、「[SharePoint Online で電子情報開示センターをセットアップする](https://go.microsoft.com/fwlink/p/?LinkId=613628)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-174">To configure eDiscovery in Office 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="f5779-175">環境を構成する</span><span class="sxs-lookup"><span data-stu-id="f5779-175">Configure the environment</span></span>

<span data-ttu-id="f5779-176">基本構成の準備が整ったので、 ソリューション自体の構成に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="f5779-176">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="f5779-177">ステージング ファイル共有</span><span class="sxs-lookup"><span data-stu-id="f5779-177">Staging file share</span></span>

1. <span data-ttu-id="f5779-178">オンプレミス ドメインで、Custodians という名前のグローバル セキュリティ グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="f5779-178">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="f5779-p107">保管担当者のコンピューターから収集されるファイルのために非表示のファイル共有を作成します。これはオンプレミス サーバー上に作成する必要があります。たとえば、Staging というサーバーに、Cases$ というファイル共有を作成します。非表示の共有にするには、 **$** が必要です。</span><span class="sxs-lookup"><span data-stu-id="f5779-p107">Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="f5779-183">次の共有アクセス許可を設定します。</span><span class="sxs-lookup"><span data-stu-id="f5779-183">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="f5779-184">保管担当者:変更、読み取り</span><span class="sxs-lookup"><span data-stu-id="f5779-184">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="f5779-185">管理者 :フル コントロール</span><span class="sxs-lookup"><span data-stu-id="f5779-185">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="f5779-186">Exchange Trusted Subsystem:変更、読み取り</span><span class="sxs-lookup"><span data-stu-id="f5779-186">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="f5779-p108">**[セキュリティ]** タブを開き、[保管担当者] グループを追加して、 **[詳細設定]** をクリックします。[保管担当者] グループに対して、次のアクセス許可を設定します。</span><span class="sxs-lookup"><span data-stu-id="f5779-p108">Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="f5779-189">**種類:拒否**</span><span class="sxs-lookup"><span data-stu-id="f5779-189">**Type: Deny**</span></span>
    
  - <span data-ttu-id="f5779-190">**適用対象:このフォルダー、サブフォルダー、およびファイル**</span><span class="sxs-lookup"><span data-stu-id="f5779-190">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="f5779-191">**[高度なアクセス許可]** をクリックし、以下を選びます。</span><span class="sxs-lookup"><span data-stu-id="f5779-191">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="f5779-192">**属性の読み取り**</span><span class="sxs-lookup"><span data-stu-id="f5779-192">**Read attributes**</span></span>
    
  - <span data-ttu-id="f5779-193">**拡張属性の読み取り**</span><span class="sxs-lookup"><span data-stu-id="f5779-193">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="f5779-194">**アクセス許可の読み取り**</span><span class="sxs-lookup"><span data-stu-id="f5779-194">**Read permissions**</span></span>
    
6. <span data-ttu-id="f5779-195">以下を実行して、Cases$ ファイル共有にテスト アクセスします。</span><span class="sxs-lookup"><span data-stu-id="f5779-195">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="f5779-196">保管担当者グループにユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="f5779-196">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="f5779-197">Cases$ フォルダーにファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="f5779-197">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="f5779-p109">ユーザーとして、ステージング サーバーを参照します。たとえば、\\\\Staging 共有を参照して、使用可能な共有を表示します。 **Cases$** 共有は一覧表示されないはずです。</span><span class="sxs-lookup"><span data-stu-id="f5779-p109">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="f5779-p110">Cases$ 共有への完全パスを手動で Explorer に入力します。これにより、Cases$ 共有が開きます。</span><span class="sxs-lookup"><span data-stu-id="f5779-p110">Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="f5779-p111">以前共有に配置したファイルを開いてみます。これは失敗するはずです。</span><span class="sxs-lookup"><span data-stu-id="f5779-p111">Try to open the file you previously placed in the share. This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="f5779-204">ログオン スクリプト</span><span class="sxs-lookup"><span data-stu-id="f5779-204">Logon script</span></span>

1. <span data-ttu-id="f5779-205">この Windows PowerShell スクリプトをコピーして、メモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f5779-205">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
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

2. <span data-ttu-id="f5779-206">上記のスクリプトを、CollectionScript.ps1 として、C:\\AFCScripts などの見つけやすい場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="f5779-206">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="f5779-p112">メモ帳の移動機能を使用して、必要に応じて次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="f5779-p112">Use the Go To feature in Notepad. Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="f5779-209">**行番号**</span><span class="sxs-lookup"><span data-stu-id="f5779-209">**Line #**</span></span>|<span data-ttu-id="f5779-210">**変更するために必要な事柄**</span><span class="sxs-lookup"><span data-stu-id="f5779-210">**What you need to change**</span></span>|<span data-ttu-id="f5779-211">**必須かどうか**</span><span class="sxs-lookup"><span data-stu-id="f5779-211">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f5779-212">71</span><span class="sxs-lookup"><span data-stu-id="f5779-212">71</span></span>  <br/> |<span data-ttu-id="f5779-p113">**$FileTypes** 変数。スクリプトがインベントリ作成と配列変数への収集を行うファイルの種類の拡張子がすべて含まれます。</span><span class="sxs-lookup"><span data-stu-id="f5779-p113">**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. </span></span><br/> |<span data-ttu-id="f5779-215">省略可能</span><span class="sxs-lookup"><span data-stu-id="f5779-215">Optional</span></span>  <br/> |
|<span data-ttu-id="f5779-216">76 と 77</span><span class="sxs-lookup"><span data-stu-id="f5779-216">76 and 77</span></span>  <br/> |<span data-ttu-id="f5779-p114">**$CaseNo** 変数を構築する方法をニーズに合わせて変更します。スクリプトは、現在の日時をキャプチャし、ユーザー名をそれに追加します。</span><span class="sxs-lookup"><span data-stu-id="f5779-p114">Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. </span></span><br/> |<span data-ttu-id="f5779-219">省略可能</span><span class="sxs-lookup"><span data-stu-id="f5779-219">Optional</span></span>  <br/> |
|<span data-ttu-id="f5779-220"> 
80 
</span><span class="sxs-lookup"><span data-stu-id="f5779-220">80</span></span>  <br/> |<span data-ttu-id="f5779-221">**$CaseRootLocation** 変数は、ステージング サーバー コレクション ファイル共有に設定する必要があります。例: **\\\\Staging\\Cases$**</span><span class="sxs-lookup"><span data-stu-id="f5779-221">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="f5779-222">必須</span><span class="sxs-lookup"><span data-stu-id="f5779-222">Required</span></span>  <br/> |
   
4. <span data-ttu-id="f5779-223">ドメイン コントローラーの Netlogon ファイル共有に CollectionScript.ps1 ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="f5779-223">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="f5779-224">ログオン スクリプトと保管担当者グループの GPO を構成します。</span><span class="sxs-lookup"><span data-stu-id="f5779-224">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="f5779-225">トピック「[グループ ポリシーで起動、シャットダウン、ログオン、ログオフ スクリプトを使用する](https://go.microsoft.com/fwlink/p/?LinkId=614844)」の「ユーザー ログオン スクリプトを割り当てる方法」セクションに従って、保管担当者グループに対してログオン スクリプトを構成します。</span><span class="sxs-lookup"><span data-stu-id="f5779-225">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="f5779-226">**セキュリティ フィルター** から認証ユーザーを削除し、保管担当者グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="f5779-226">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="f5779-227">PST インポートのオプション A (Exchange Server 2013 用のスクリプト)</span><span class="sxs-lookup"><span data-stu-id="f5779-227">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="f5779-228">次の Windows PowerShell スクリプトをコピーして、メモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f5779-228">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
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
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
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

2. <span data-ttu-id="f5779-p115">スクリプトを、PSTImportScript.ps1 という名前を付けて見つけやすい場所に保存します。例として、使いやすくするため、ステージング サーバーに \\\\Staging\\AFCScripts というフォルダーを作成して、そこに保存します。</span><span class="sxs-lookup"><span data-stu-id="f5779-p115">Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="f5779-231">メモ帳の移動機能を使用して、必要に応じて次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="f5779-231">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="f5779-232">**行番号**</span><span class="sxs-lookup"><span data-stu-id="f5779-232">**Line #**</span></span>|<span data-ttu-id="f5779-233">**変更するために必要な事柄**</span><span class="sxs-lookup"><span data-stu-id="f5779-233">**What you need to change**</span></span>|<span data-ttu-id="f5779-234">**必須かどうか**</span><span class="sxs-lookup"><span data-stu-id="f5779-234">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f5779-235">12</span><span class="sxs-lookup"><span data-stu-id="f5779-235">12</span></span>  <br/> |<span data-ttu-id="f5779-p116">**$FolderIdentifier** は、PST がインポートされるメールボックス フォルダーにタグを付けます。必要な場合は変更します。</span><span class="sxs-lookup"><span data-stu-id="f5779-p116">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. </span></span><br/> |<span data-ttu-id="f5779-238">省略可能</span><span class="sxs-lookup"><span data-stu-id="f5779-238">Optional</span></span>  <br/> |
|<span data-ttu-id="f5779-239">17</span><span class="sxs-lookup"><span data-stu-id="f5779-239">17</span></span>  <br/> |<span data-ttu-id="f5779-240">**$ConnectionUri** は独自のサーバーに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5779-240">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="f5779-p117">> [!IMPORTANT]> **$ConnectionUri** が https:// の場所ではなく http:// の場所を指し示していることをご確認ください。https:// では機能しません。</span><span class="sxs-lookup"><span data-stu-id="f5779-p117">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.</span></span>          |<span data-ttu-id="f5779-243">必須</span><span class="sxs-lookup"><span data-stu-id="f5779-243">Required</span></span>  <br/> |
   
4. <span data-ttu-id="f5779-244">Exchange Trusted Subsystem アカウントに、\\\\Staging\\Cases$ 共有に対する読み取り、書き込み、実行のアクセス許可があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f5779-244">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="f5779-245">PST インポート スクリプトには、次の 2 つの入力パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="f5779-245">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="f5779-246">**$SourcePath** たとえば \\\\Staging\\Cases$ などの、インポートする PST ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="f5779-246">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="f5779-247">**$MailboxAlias** インポートされたメール アイテムを受信するターゲット メールボックスのエイリアス</span><span class="sxs-lookup"><span data-stu-id="f5779-247">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="f5779-248">たとえば、すべての PST ファイルをパス \\Staging\Cases$ からエイリアス eDiscoveryMailbox を持つメールボックスにインポートする場合は、次のようなスクリプトを実行します `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`。</span><span class="sxs-lookup"><span data-stu-id="f5779-248">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="f5779-249">PST インポートのオプション B (Exchange Online の場合)</span><span class="sxs-lookup"><span data-stu-id="f5779-249">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="f5779-p118">インポートした PST ファイルを配置するメールボックス構造を作成します。Exchange Online にユーザーのメールボックスを作成する方法の詳細については、「[Exchange Online でユーザー メールボックスを作成する](https://go.microsoft.com/fwlink/p/?LinkId=615118)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-p118">Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="f5779-252">コールド ストレージ</span><span class="sxs-lookup"><span data-stu-id="f5779-252">Cold storage</span></span>

1. <span data-ttu-id="f5779-253">Azure Virtual Machine にファイル共有を作成します。ここに収集したすべてのファイルを配置します。例: \\\\AZFile1\\ContentColdStorage</span><span class="sxs-lookup"><span data-stu-id="f5779-253">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="f5779-p119">既定のコンテンツ アクセス アカウントに対して、少なくとも共有およびすべてのサブフォルダーとファイルへの読み取りのアクセス許可を付与します。SharePoint 2013 検索の構成の詳細については、「[SharePoint Server 2013 で Search Service アプリケーションを作成および構成する](https://go.microsoft.com/fwlink/p/?LinkId=614940)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-p119">Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="f5779-256">PST ファイルを \\\\AZFile1\\ContentColdStorage からインポートすることを見込んでいる場合は、Exchange Trusted Subsystem に対して共有への読み取り、書き込み、実行のアクセス許可を付与します。</span><span class="sxs-lookup"><span data-stu-id="f5779-256">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="f5779-257">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="f5779-257">Orchestrator</span></span>

1. <span data-ttu-id="f5779-258">Microsoft ダウンロード センターから、[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="f5779-258">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="f5779-p120">**Runbook Designer** を開き、 **[接続]** ウィンドウで、Runbook のインポート先のフォルダーをクリックします。 **[アクション]** メニューをクリックしてから、 **[インポート]** をクリックします。 **[インポート]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f5779-p120">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="f5779-262">**[ファイルの場所]** ボックスで、インポートする Runbook のパスとファイル名を入力するか、省略記号 ( **...**) をクリックしてインポートするファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="f5779-262">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="f5779-p121">**[Runbook のインポート]** と **[Orchestrator で暗号化されたデータのインポート]** を選びます。 **[カウンター]**、 **[スケジュール]**、 **[変数]**、 **[コンピューター グループ]**、 **[グローバル構成のインポート]**、 **[既存のグローバル設定の上書き]** をクリアします。</span><span class="sxs-lookup"><span data-stu-id="f5779-p121">Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="f5779-265">[ **完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5779-265">Click **Finish**.</span></span>
    
6. <span data-ttu-id="f5779-266">**MoveFilesToColdStorage** Runbook を次のように編集します。</span><span class="sxs-lookup"><span data-stu-id="f5779-266">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="f5779-p122">**[ファイルの移動]** アクティビティ - **[ソース ファイル]** のパスを、コレクション ファイル共有 (例: \\\\Staging\\cases$) に設定します。 **[移動先フォルダー]** を、Azure のコールド ストレージ ファイル共有 (例: \\\\AZFile1\\ContentColdStorage) に設定します。 **[一意の名前でファイルを作成する]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="f5779-p122">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="f5779-270">**[フォルダーの削除]** アクティビティ - **[パス]** をコレクション ファイル共有 (例: \\\\Staging\\cases$\\*) に設定し、 **[すべてのファイルとサブフォルダーを削除する]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="f5779-270">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="f5779-271">「[Runbook の展開](https://go.microsoft.com/fwlink/p/?LinkId=615120)」にある手順を使用して、 **MoveToColdStorage** Runbook を展開します。</span><span class="sxs-lookup"><span data-stu-id="f5779-271">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="f5779-272">コールド ストレージ用 SharePoint オンプレミス検索</span><span class="sxs-lookup"><span data-stu-id="f5779-272">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="f5779-p123">Azure のコールド ストレージ共有の SharePoint 2013 ファームに新しいコンテンツ ソースを作成します (例: \\\\AZFile1\\ContentColdStorage)。コンテンツ ソースの管理の詳細については、「[SharePoint Server 2013 でコンテンツ ソースを追加、編集、または削除する](https://go.microsoft.com/fwlink/p/?LinkId=615004)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-p123">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="f5779-p124">フル クロールを開始します。詳細については、「[SharePoint Server 2013 でクロールを開始、一時停止、再開、または停止する](https://go.microsoft.com/fwlink/p/?LinkId=615005)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-p124">Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="f5779-277">ソリューションの使用</span><span class="sxs-lookup"><span data-stu-id="f5779-277">Using the solution</span></span>

<span data-ttu-id="f5779-p125">Exchange Server 2013 と Exchange Online の両方に PST ファイルをインポートしないことを前提として、このソリューションの使用には主に 5 つのステップがあります。このセクションでは、このすべてのステップの手順について記載します。ソリューションでの主な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f5779-p125">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="f5779-281">保管担当者グループのユーザー メンバーシップを管理する。</span><span class="sxs-lookup"><span data-stu-id="f5779-281">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="f5779-p126">エラー</span><span class="sxs-lookup"><span data-stu-id="f5779-p126">Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="f5779-285">PST のインポート プロセスを管理する。</span><span class="sxs-lookup"><span data-stu-id="f5779-285">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="f5779-286">コレクション ファイルをコールド ストレージに移動する。</span><span class="sxs-lookup"><span data-stu-id="f5779-286">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="f5779-p127">その他すべてのステップはこのソリューション固有ではありません。SharePoint 2013、および Office 365 と Azure で実行する標準の管理タスクです。このソリューションでは、企業のニーズに基づいて作業する必要があるガイダンスを提供しない項目があります。それらは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f5779-p127">All the other steps are not specific to this solution. They are standard administrative tasks that you perform in SharePoint 2013, and Office 365 and Azure. There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="f5779-290">eDiscovery のケースを追跡し、どの保管担当者がどのケースに関連付けられているかを追跡する。</span><span class="sxs-lookup"><span data-stu-id="f5779-290">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="f5779-291">どのファイル コレクションのセットがどの eDiscovery のケースに関連付けられているかを追跡する。</span><span class="sxs-lookup"><span data-stu-id="f5779-291">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="f5779-292">インポートのタイミングを調整し、コールド ストレージのステップに移動する。</span><span class="sxs-lookup"><span data-stu-id="f5779-292">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="f5779-293">Azure で使用するファイル領域を管理する。</span><span class="sxs-lookup"><span data-stu-id="f5779-293">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="f5779-294">PST のインポート先メールボックスを管理する。</span><span class="sxs-lookup"><span data-stu-id="f5779-294">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="f5779-295">すべてのオンプレミス データのバックアップおよび復元。</span><span class="sxs-lookup"><span data-stu-id="f5779-295">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="f5779-296">保管担当者管理</span><span class="sxs-lookup"><span data-stu-id="f5779-296">Custodian management</span></span>

- <span data-ttu-id="f5779-p128">個々のユーザーに対して自動ファイル収集プロセスを開始するには、このユーザーを Custodian グループに追加します。 次回ユーザーがログオンすると、グループ ポリシーを介して Custodian グループに割り当てられているログオン スクリプトが実行されます。</span><span class="sxs-lookup"><span data-stu-id="f5779-p128">To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="f5779-299">収集ファイルの監視とログ ファイルの確認</span><span class="sxs-lookup"><span data-stu-id="f5779-299">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="f5779-p129">ユーザーのコレクション フォルダーのコレクション ファイル共有 (例: \\\\Staging\\cases$\\*) を監視します。フォルダーの名前は  *yyyyMMddHHmm_UserName*  のような形式になります。</span><span class="sxs-lookup"><span data-stu-id="f5779-p129">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="f5779-p130">収集が完了したら、コレクション フォルダーを開き、_Log フォルダーを参照します。_Log フォルダーに以下が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f5779-p130">When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="f5779-p131">ユーザーのコンピューターのローカル ドライブごとに 1 つの XML ファイル (例: **A.xml** 、 **C.xml** )。これらのファイルに含まれるインベントリ ドライブは、robocopy の操作にちなんだ名前が付けられ、その操作に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f5779-p131">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="f5779-p132">コレクション スクリプトは、スクリプト自体で定義したファイルの種類のインベントリ ファイルだけにエントリを作成します。ユーザーのコンピューター上のすべてのファイルにインベントリのエントリが作成されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f5779-p132">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="f5779-p133">コレクションごとに FileCopyErrors.log という名前の 1 つのログ ファイルが実行されます。このファイルには、robocopy がファイル コレクション共有にコピーできなかったファイルの一覧が含まれています (例: \\\\Staging\\cases$\\*)。これを確認し、これらの不足しているファイルに対して実行するアクションを決定する必要があります。通常、ファイルが必要な場合は手動で収集するか、ファイルは不要であるためコレクションから省略してもよいと決定することができます。</span><span class="sxs-lookup"><span data-stu-id="f5779-p133">One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="f5779-312">PST インポートのオプション A (Exchange Server 2013 の場合)</span><span class="sxs-lookup"><span data-stu-id="f5779-312">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="f5779-p134">コレクション ファイル共有をホストするサーバーにログオンしてから (例: **ステージング** )、Windows PowerShell を開きます。Windows PowerShell の開始の詳細については、「[Windows サーバー上で Windows PowerShell を開始する](https://go.microsoft.com/fwlink/p/?LinkId=615115)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-p134">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="f5779-p135">実行ポリシーを無制限に設定します。Windows PowerShell に  `Set-ExecutionPolicy Unrestricted -Scope Process` と入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f5779-p135">Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="f5779-p136">PSTImportScript.ps1 ファイルを実行し、 **$SourcePath** パラメーターと **$MailboxAlias** パラメーターを指定します。Windows PowerShell スクリプトの実行の詳細については、「[スクリプトの実行](https://go.microsoft.com/fwlink/p/?LinkID=615117)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-p136">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="f5779-319">エラーの出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="f5779-319">Review the output for errors.</span></span>
    
5. <span data-ttu-id="f5779-p137">同じメールボックスに同じ名前の PST ファイルをインポートしようとする前に、メールボックスのインポート要求を削除する必要があります。これを行うには、次のコマンドを実行します。 `Get-MailboxImportRequest | Remove-MailboxImportRequest`個々の要求をキューから削除するようにメッセージが表示されます。必要に応じて対処します。</span><span class="sxs-lookup"><span data-stu-id="f5779-p137">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="f5779-324">PST インポートのオプション B (Exchange Online の場合)</span><span class="sxs-lookup"><span data-stu-id="f5779-324">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="f5779-325">収集した PST ファイルを Exchange Online に配置するには、「[Office 365 インポート サービス](https://go.microsoft.com/fwlink/p/?LinkId=614938)」の「ネットワーク アップロードによりファイルを Office 365 にインポートする」セクションにある手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f5779-325">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Office 365 through the network upload section of [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="f5779-326">コールド ストレージに移動</span><span class="sxs-lookup"><span data-stu-id="f5779-326">Move to cold storage</span></span>

1. <span data-ttu-id="f5779-327">「[Runbook の実行](https://go.microsoft.com/fwlink/p/?LinkId=615123)」にある手順を使用して、 **MoveToColdStorage** Runbook を実行します。</span><span class="sxs-lookup"><span data-stu-id="f5779-327">Run the **MoveToColdStorage** runbook using the procedures in[Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="f5779-p138">長期保存用の Azure ファイル共有 (例: \\\\AZFile1\\ContentColdStorage) とオンプレミス コレクション ファイル共有 (例: \\\\Staging\\cases$) を監視します。ファイルとフォルダーがコールド ストレージのファイル共有に表示され、コレクション ファイル共有からは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="f5779-p138">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="f5779-330">電子情報開示</span><span class="sxs-lookup"><span data-stu-id="f5779-330">eDiscovery</span></span>

1. <span data-ttu-id="f5779-p139">コールド ストレージ ファイル共有のフル クロールをスケジュールとして実行できるようにするか、クロールを開始できるようにします。フル クロールまたは増分クロールの開始の詳細については、「[SharePoint Server 2013 でクロールを開始、一時停止、再開、または停止する](https://go.microsoft.com/fwlink/p/?LinkId=615005)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5779-p139">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="f5779-333">PST ファイルのインポートにオプション A を使用した場合は、SharePoint 2013 に eDiscovery ケースを作成します。オプション B を使用した場合は、SharePoint Online に eDiscovery ケースを作成します。</span><span class="sxs-lookup"><span data-stu-id="f5779-333">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

