---
title: クラウド導入のテスト ラボ ガイド (TLG) を使用した Office 365 のテスト
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/23/2018
ms.audience: ITPro
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
description: '概要: これらのクラウド導入のテスト ラボ ガイド (TLG) を使用して、Office 365、Dynamics 365、Office Server 製品のデモンストレーション、概念実証、開発/テスト環境を設定します。'
ms.openlocfilehash: 796d34294ef92702214df30ca5553759554996d3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "23041501"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a><span data-ttu-id="0e6cc-103">クラウド導入のテスト ラボ ガイド (TLG) を使用した Office 365 のテスト</span><span class="sxs-lookup"><span data-stu-id="0e6cc-103">Test Office 365 with cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="0e6cc-104">**概要:** これらのクラウド導入のテスト ラボ ガイド (TLG) を使用して、Office 365、Dynamics 365、Office Server 製品のデモンストレーション、概念実証、開発/テスト環境を設定します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365, Enterprise Mobility + Security (EMS), Dynamics 365, and Office Server products.</span></span>
  
<span data-ttu-id="0e6cc-p101">TLG では短時間で Microsoft 製品について学習できます。あるテクノロジや構成について、それが特定の状況に適しているかどうかを決定したり、テクノロジをユーザーにロールアウトするために、事前に評価が必要な場合に最適です。この実地体験型ガイドにより、新しい製品やソリューションの展開要件を理解し、運用環境でホストする計画を立てやすくなります。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you or before you roll it out to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="0e6cc-108">また、TLG は、アプリケーションの開発およびテスト用の典型的な環境を作成します。これは、開発/テスト環境とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Microsoft Cloud のテスト ラボ ガイド](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
<span data-ttu-id="0e6cc-110">開始する前に、これらの追加のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-110">See these additional resources before diving in:</span></span>
  
- <span data-ttu-id="0e6cc-111">Microsoft Virtual Academy セッションの「[クラウド導入のテスト ラボ ガイドを使用した Microsoft Cloud を試す](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 )」(22 分) を視聴してください。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-111">View the [Experience the Microsoft Cloud with Cloud Adoption Test Lab Guides](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy session (only 22 minutes).</span></span>
    
- <span data-ttu-id="0e6cc-112">
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="office-365-devtest-environment"></a><span data-ttu-id="0e6cc-113">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-113">Office 365 dev/test environment</span></span>

<span data-ttu-id="0e6cc-114">Office 365 の開発/テスト環境を構築するのに、次の記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-114">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="0e6cc-115">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-115">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-p102">Microsoft Azure インフラストラクチャ サービスで実行される簡易型のイントラネットを作成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="0e6cc-118">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-118">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-119">Office 365 Enterprise E5 試用版サブスクリプションを作成します。これは、使用中のコンピューターから、または Azure インフラストラクチャ サービスで実行される簡易型のイントラネットから実行できます。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-119">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="0e6cc-120">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="0e6cc-120">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-p103">Azure AD Connect をインストールして、ディレクトリ同期をパスワード同期と共に実行するように構成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-p103">Install and configure Azure AD Connect for directory synchronization with password synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="0e6cc-123">Office 365 の開発/テスト環境では、Office 365 のエンタープライズ機能をデモンストレーションするために次の記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-123">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="0e6cc-124">Office 365 開発/テスト環境用の多要素認証</span><span class="sxs-lookup"><span data-stu-id="0e6cc-124">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-125">Office 365 サブスクリプションのアカウントに対応するスマートフォンに送信されたテキスト メッセージを使用して、セカンダリ認証を構成してテストします。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-125">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="0e6cc-126">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="0e6cc-126">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-127">Windows Server Active Directory ドメインのアカウントを使用してフェデレーション認証を構成し、デモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-127">Configure and demonstrate federated authentication with the accounts of a Windows Server Active Directory domain.</span></span>
    
- [<span data-ttu-id="0e6cc-128">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="0e6cc-128">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-129">Office 365 Cloud App Security の構成とデモンストレーションを行い、Office 365 サブスクリプションでの不審なアクティビティを監視し、通知するポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-129">Configure and demonstrate Office 365 Cloud App Security, which allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="0e6cc-130">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="0e6cc-130">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-131">Advanced Threat Protection の構成とデモンストレーションを行います。これは Exchange Online Protection (EOP) の機能であり、マルウェアからメールを保護します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-131">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>
    
- [<span data-ttu-id="0e6cc-132">Office 365 の開発/テスト環境のアドバンスト eDiscovery</span><span class="sxs-lookup"><span data-stu-id="0e6cc-132">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-133">サンプル データを追加して Advanced eDiscovery のデモンストレーションを行います。これにより、メールやドキュメントなどの Office 365 に格納されているデータをすばやく見つけて分析できます。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-133">Add example data and demonstrate Advanced eDiscovery, which allows you to quickly find and analyze the data that is stored in Office 365, including email and documents.</span></span>
    
- [<span data-ttu-id="0e6cc-134">Office 365 の開発/テスト環境での機密性の高いファイルの保護</span><span class="sxs-lookup"><span data-stu-id="0e6cc-134">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-135">機密文書を誤って間違ったドキュメント フォルダーに投稿した場合でも、中のデータが保護されるようにするために、Office 365 Information Rights Management を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-135">Demonstrate how you can use Office 365 Information Rights Management to protect the data in sensitive documents, even when they are accidentally posted in the wrong document folders.</span></span>
    
- [<span data-ttu-id="0e6cc-136">Office 365 開発/テスト環境でのデータ分類とラベルの作成</span><span class="sxs-lookup"><span data-stu-id="0e6cc-136">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-137">Azure Information Protection (AIP) クライアントを使用して、さまざまなレベルのセキュリティでドキュメントを分類する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-137">Demonstrate how the Azure Information Protection (AIP) client can be used to classify documents with various levels of security.</span></span>
    
- [<span data-ttu-id="0e6cc-138">Office 365 開発/テスト環境での分離した SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="0e6cc-138">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-139">重要なリソースや機密性の高いリソース用に、組織の他の部分から分離されている SharePoint Online チーム サイトを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-139">Demonstrate how to create a SharePoint Online team site that is isolated from the rest of the organization for sensitive or highly confidential resources.</span></span>
    
## <a name="the-microsoft-365-enterprise-test-environment"></a><span data-ttu-id="0e6cc-140">Microsoft 365 Enterprise テスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-140">The Microsoft 365 Enterprise dev/test environment</span></span>

<span data-ttu-id="0e6cc-141">[これらの記事](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)を利用して [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) のテスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-141">Create a dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) scenarios with these articles:</span></span>
 
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="0e6cc-142">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-142">Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="0e6cc-143">以下の記事で、Dynamics 365 試用版サブスクリプションを追加し、Office 365 と Dynamics 365 の統合された機能とシナリオをテストします。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-143">Add a Dynamics 365 trial subscription and test Office 365 and Dynamics 365 integrated features and scenarios with these articles:</span></span>
  
- [<span data-ttu-id="0e6cc-144">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-144">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
    <span data-ttu-id="0e6cc-145">Dynamics 365 試用版サブスクリプションと Dynamics 365 ライセンス、およびアクセス許可をユーザー アカウントに追加します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-145">Add a Dynamics 365 trial subscription and Dynamics 365 licences and permissions to your user accounts.</span></span>
    
- [<span data-ttu-id="0e6cc-146">Office 365 と Dynamics 365 の開発/テスト環境の Exchange Online 統合</span><span class="sxs-lookup"><span data-stu-id="0e6cc-146">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    <span data-ttu-id="0e6cc-147">Exchange Online のメールボックスで Office 365 と Dynamics 365 を併用するための構成と方法ついて説明します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-147">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes.</span></span>
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="0e6cc-148">One Microsoft Cloud 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-148">The One Microsoft Cloud dev/test environment</span></span>

<span data-ttu-id="0e6cc-p104">次の Microsoft のクラウド サービスすべてを含む開発/テスト環境を作成します:Office 365、Azure、EMS、Dynamics 365。詳しい手順については、「[One Microsoft Cloud 開発/テスト環境](the-one-microsoft-cloud-dev-test-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-p104">Create a dev/test environment that includes all of Microsoft's cloud offerings: Office 365, Azure, EMS, and Dynamics 365. See [The One Microsoft Cloud dev/test environment](the-one-microsoft-cloud-dev-test-environment.md) for the step-by-step instructions.</span></span>
  
## <a name="simulated-cross-premises-devtest-environments"></a><span data-ttu-id="0e6cc-151">シミュレートされたクロスプレミスの開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-151">Simulated cross-premises dev/test environments</span></span>

<span data-ttu-id="0e6cc-152">以下の記事で、Azure 仮想ネットワークやシミュレートされたオンプレミス ネットワークが含まれている、クロスプレミスの開発/テスト環境を作成できます。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-152">You can create a cross-premises dev/test environment, which includes an Azure virtual network and a simulated on-premises network, with these articles:</span></span>
  
- [<span data-ttu-id="0e6cc-153">Azure でのシミュレートされたクロスプレミスの仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="0e6cc-153">Simulated cross-premises virtual network in Azure</span></span>](simulated-cross-premises-virtual-network-in-azure.md)
    
    <span data-ttu-id="0e6cc-154">シミュレートされたイントラネットを作成し、ハイブリッド クラウド構成で Azure Virtual Network に接続します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-154">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
- [<span data-ttu-id="0e6cc-155">Azure 開発/テスト環境でのイントラネット SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="0e6cc-155">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    <span data-ttu-id="0e6cc-156">Azure 仮想ネットワークに単一のサーバー SharePoint Server 2016 ファームを作成して、シミュレートされたオンプレミス ネットワークからの接続と管理をテストします。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-156">Create a single-server SharePoint Server 2016 farm in the Azure virtual network and test connectivity and administration from the simulated on-premises network.</span></span>
    
## <a name="additional-cloud-based-devtest-environments"></a><span data-ttu-id="0e6cc-157">クラウド ベースの他の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-157">Additional cloud-based dev/test environments</span></span>

<span data-ttu-id="0e6cc-158">Azure インフラストラクチャ サービス内に作成できる、クラウド ベースのその他の開発/テスト環境は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-158">Here are additional cloud-based dev/test environments that you can create in Azure infrastructure services:</span></span>
  
- [<span data-ttu-id="0e6cc-159">Azure における SharePoint Server 2016 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-159">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt723354.aspx)
    
    <span data-ttu-id="0e6cc-160">Azure インフラストラクチャ サービスに単一サーバーの SharePoint Server 2016 ファームを構築します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-160">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="0e6cc-161">Azure における Exchange 2016 開発およびテスト環境</span><span class="sxs-lookup"><span data-stu-id="0e6cc-161">Exchange 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    <span data-ttu-id="0e6cc-162">単一の Exchange 2016 サーバーを Azure インフラストラクチャ サービスに構築します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-162">Build a single Exchange 2016 server in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="0e6cc-163">SharePoint Server 2013 dev/test environments in Azure</span><span class="sxs-lookup"><span data-stu-id="0e6cc-163">SharePoint Server 2013 dev/test environments in Azure</span></span>](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    <span data-ttu-id="0e6cc-164">基本および高可用性の SharePoint Server 2013 ファームを Azure インフラストラクチャ サービスに構築します。</span><span class="sxs-lookup"><span data-stu-id="0e6cc-164">Build basic and high-availability SharePoint Server 2013 farms in Azure infrastructure services.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="0e6cc-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e6cc-165">See Also</span></span>

[<span data-ttu-id="0e6cc-166">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="0e6cc-166">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="0e6cc-167">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="0e6cc-167">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="0e6cc-168">SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル</span><span class="sxs-lookup"><span data-stu-id="0e6cc-168">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="0e6cc-169">ハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="0e6cc-169">Hybrid solutions</span></span>](hybrid-solutions.md)


