---
title: クラウド導入のテスト ラボ ガイド (TLG) を使用した Office 365 のテスト
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/09/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 概要：これらのクラウド採用テストラボガイド（TLG）を使用して、Office 365のデモンストレーション、概念実証、または開発/テスト環境を設定します。
ms.openlocfilehash: a61716ae34d8dbe3f710696570c46cefd0f4aa4c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068143"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a><span data-ttu-id="52ed6-103">クラウド導入のテスト ラボ ガイド (TLG) を使用した Office 365 のテスト</span><span class="sxs-lookup"><span data-stu-id="52ed6-103">Test Office 365 with cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="52ed6-104">**概要：** これらのクラウド採用テストラボガイド（TLG）を使用して、Office 365のデモンストレーション、概念実証、または開発/テスト環境を設定します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365.</span></span>
  
<span data-ttu-id="52ed6-p101">TLG では短時間で Microsoft 製品について学習できます。あるテクノロジや構成について、それが特定の状況に適しているかどうかを決定し、デザイン、プランニングを行いテクノロジをユーザーにロールアウトするさいに、事前に評価が必要な場合に最適です。この実地体験型ガイドにより、新しい製品やソリューションの展開要件を理解し、運用環境でホストする計画を立てやすくなります。</span><span class="sxs-lookup"><span data-stu-id="52ed6-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you and before you begin the design, planning, and rollout to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="52ed6-108">また、TLG は、アプリケーションの開発およびテスト用の典型的な環境を作成します。これは、開発/テスト環境とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="52ed6-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Microsoft Cloud のテスト ラボ ガイド](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
<span data-ttu-id="52ed6-110">Office 365テストラボガイドスタックのすべての記事への視覚的なマップについては[ここを](http://aka.ms/catlgstack)クリックしてください。</span><span class="sxs-lookup"><span data-stu-id="52ed6-110">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
    
## <a name="office-365-devtest-environment"></a><span data-ttu-id="52ed6-111">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="52ed6-111">Office 365 dev/test environment</span></span>

<span data-ttu-id="52ed6-112">Office 365 の開発/テスト環境を構築するのに、次の記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-112">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="52ed6-113">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="52ed6-113">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-p102">Microsoft Azure インフラストラクチャ サービスで実行される簡易型のイントラネットを作成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="52ed6-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="52ed6-116">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="52ed6-116">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-117">Office 365 Enterprise E5 試用版サブスクリプションを作成します。これは、使用中のコンピューターから、または Azure インフラストラクチャ サービスで実行される簡易型のイントラネットから実行できます。</span><span class="sxs-lookup"><span data-stu-id="52ed6-117">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="52ed6-118">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="52ed6-118">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-p103">Azure AD Connect をインストールして、ディレクトリ同期をパスワード同期と共に実行するように構成します。このステップは省略可能で、シミュレートされたエンタープライズ構成を構築する場合は行ってください。</span><span class="sxs-lookup"><span data-stu-id="52ed6-p103">Install and configure Azure AD Connect for directory synchronization with password hash synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="52ed6-121">Office 365 の開発/テスト環境では、Office 365 のエンタープライズ機能をデモンストレーションするために次の記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-121">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="52ed6-122">Office 365 開発/テスト環境用の多要素認証</span><span class="sxs-lookup"><span data-stu-id="52ed6-122">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-123">Office 365 サブスクリプションのアカウントに対応するスマートフォンに送信されたテキスト メッセージを使用して、セカンダリ認証を構成してテストします。</span><span class="sxs-lookup"><span data-stu-id="52ed6-123">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="52ed6-124">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="52ed6-124">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-125">Active Directoryドメインサービス（AD DS）ドメインのアカウントを使用してフェデレーション認証を構成し、実演します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-125">Configure and demonstrate federated authentication with the accounts of an Active Directory Domain Services (AD DS) domain.</span></span>
    
- [<span data-ttu-id="52ed6-126">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="52ed6-126">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-127">Office 365 Cloud App Security の構成とデモンストレーションを行い、Office 365 サブスクリプションでの不審なアクティビティを監視し、通知するポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-127">Configure and demonstrate Office 365 Cloud App Security, which lets you create policies that monitor for and inform you of suspicious activities in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="52ed6-128">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="52ed6-128">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-129">Advanced Threat Protection の構成とデモンストレーションを行います。これは Exchange Online Protection (EOP) の機能であり、マルウェアからメールを保護します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-129">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>
    
- [<span data-ttu-id="52ed6-130">Office 365 の開発/テスト環境の Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="52ed6-130">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-131">サンプル データを追加して Advanced eDiscovery のデモンストレーションを行います。これにより、メールやドキュメントなどの Office 365 に格納されているデータをすばやく見つけて分析できます。</span><span class="sxs-lookup"><span data-stu-id="52ed6-131">Add example data and demonstrate Advanced eDiscovery, which lets you quickly find and analyze the data that is stored in Office 365, including email and documents.</span></span>
    
- [<span data-ttu-id="52ed6-132">Office 365 の開発/テスト環境での機密性の高いファイルの保護</span><span class="sxs-lookup"><span data-stu-id="52ed6-132">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-133">機密文書を誤って間違ったドキュメント フォルダーに投稿した場合でも、中のデータが保護されるようにするために、Office 365 Information Rights Management を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-133">Demonstrate how you can use Office 365 Information Rights Management to protect the data in sensitive documents, even when they are accidentally posted in the wrong document folders.</span></span>
    
- [<span data-ttu-id="52ed6-134">Office 365 開発/テスト環境でのデータ分類とラベルの作成</span><span class="sxs-lookup"><span data-stu-id="52ed6-134">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-135">Azure Information Protection クライアントを使用して、さまざまなレベルのセキュリティでドキュメントを分類する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-135">Demonstrate how the Azure Information Protection client can be used to classify documents with various levels of security.</span></span>
    
- [<span data-ttu-id="52ed6-136">開発/テスト環境での分離した SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="52ed6-136">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    <span data-ttu-id="52ed6-137">重要なリソースや機密性の高いリソース用に、組織の他の部分から分離されている SharePoint Online チーム サイトを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-137">Demonstrate how to create a SharePoint Online team site that is isolated from the rest of the organization for sensitive or highly confidential resources.</span></span>
    

## <a name="simulated-cross-premises-devtest-environments"></a><span data-ttu-id="52ed6-138">シミュレートされたクロスプレミスの開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="52ed6-138">Simulated cross-premises dev/test environments</span></span>

<span data-ttu-id="52ed6-139">以下の記事で、Azure 仮想ネットワークやシミュレートされたオンプレミス ネットワークが含まれている、クロスプレミスの開発/テスト環境を作成できます。</span><span class="sxs-lookup"><span data-stu-id="52ed6-139">You can create a cross-premises dev/test environment, which includes an Azure virtual network and a simulated on-premises network, with these articles:</span></span>
  
- [<span data-ttu-id="52ed6-140">Azure でのシミュレートされたクロスプレミスの仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="52ed6-140">Simulated cross-premises virtual network in Azure</span></span>](simulated-cross-premises-virtual-network-in-azure.md)
    
    <span data-ttu-id="52ed6-141">シミュレートされたイントラネットを作成し、ハイブリッド クラウド構成で Azure Virtual Network に接続します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-141">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
- [<span data-ttu-id="52ed6-142">Azure 開発/テスト環境でのイントラネット SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="52ed6-142">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    <span data-ttu-id="52ed6-143">Azure 仮想ネットワークに単一のサーバー SharePoint Server 2016 ファームを作成して、シミュレートされたオンプレミス ネットワークからの接続と管理をテストします。</span><span class="sxs-lookup"><span data-stu-id="52ed6-143">Create a single-server SharePoint Server 2016 farm in the Azure virtual network and test connectivity and administration from the simulated on-premises network.</span></span>
    
## <a name="sharepoint-server-2016-devtest-environments"></a><span data-ttu-id="52ed6-144">SharePoint Server 2016の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="52ed6-144">SharePoint Server 2016 dev/test environments</span></span>

<span data-ttu-id="52ed6-145">Azure インフラストラクチャ サービス内に作成できる、SharePoint Server 2016の開発/テスト環境は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="52ed6-145">Here are SharePoint Server 2016 dev/test environments that you can create in Azure infrastructure services:</span></span>
  
- [<span data-ttu-id="52ed6-146">Azure における SharePoint Server 2016 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="52ed6-146">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)
    
    <span data-ttu-id="52ed6-147">Azure インフラストラクチャ サービスに単一サーバーの SharePoint Server 2016 ファームを構築します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-147">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>

- [<span data-ttu-id="52ed6-148">Azure 開発/テスト環境でのイントラネット SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="52ed6-148">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)
    
    <span data-ttu-id="52ed6-149">Azureインフラストラクチャサービスで単一サーバーのSharePoint Server 2016ファームを構築し、シミュレートされたイントラネットからアクセスします。</span><span class="sxs-lookup"><span data-stu-id="52ed6-149">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services and access it from a simulated intranet.</span></span>


## <a name="the-microsoft-365-enterprise-devtest-environments"></a><span data-ttu-id="52ed6-150">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="52ed6-150">The Microsoft 365 Enterprise dev/test environments</span></span>

<span data-ttu-id="52ed6-151">[これらの記事](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)を利用して [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) のテスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="52ed6-151">Create dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) with [these articles](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="52ed6-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="52ed6-152">See Also</span></span>

[<span data-ttu-id="52ed6-153">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="52ed6-153">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="52ed6-154">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="52ed6-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="52ed6-155">SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル</span><span class="sxs-lookup"><span data-stu-id="52ed6-155">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="52ed6-156">ハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="52ed6-156">Hybrid solutions</span></span>](hybrid-solutions.md)
