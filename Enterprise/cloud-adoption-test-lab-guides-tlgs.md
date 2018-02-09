---
title: "クラウド導入のテスト ラボ ガイド (TLG)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: "概要: これらのクラウド導入のテスト ラボ ガイド (TLG) を使用して、Office 365、Enterprise Mobility + Security (EMS)、Dynamics 365、Office Server 製品のデモンストレーション、概念実証、開発/テスト環境を設定します。"
ms.openlocfilehash: d13012ebbee05eea903d3ae2d6198b503ad2bf39
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a><span data-ttu-id="6b74f-103">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="6b74f-103">Cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="6b74f-104">**概要:** これらのクラウド導入のテスト ラボ ガイド (TLG) を使用して、Office 365、Enterprise Mobility + Security (EMS)、Dynamics 365、Office Server 製品のデモンストレーション、概念実証、開発/テスト環境を設定します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365, Enterprise Mobility + Security (EMS), Dynamics 365, and Office Server products.</span></span>
  
<span data-ttu-id="6b74f-p101">TLG では短時間で Microsoft 製品について学習できます。あるテクノロジや構成について、それが特定の状況に適しているかどうかを決定したり、テクノロジをユーザーにロールアウトするために、事前に評価が必要な場合に最適です。この実地体験型ガイドにより、新しい製品やソリューションの展開要件を理解し、運用環境でホストする計画を立てやすくなります。</span><span class="sxs-lookup"><span data-stu-id="6b74f-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you or before you roll it out to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="6b74f-108">また、TLG は、アプリケーションの開発およびテスト用の典型的な環境を作成します。これは、開発/テスト環境とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="6b74f-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Microsoft Cloud のテスト ラボ ガイド](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
<span data-ttu-id="6b74f-110">開始する前に、これらの追加のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b74f-110">See these additional resources before diving in:</span></span>
  
- <span data-ttu-id="6b74f-111">Microsoft Virtual Academy セッションの「[クラウド導入のテスト ラボ ガイドを使用した Microsoft Cloud を試す](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 )」(22 分) を視聴してください。</span><span class="sxs-lookup"><span data-stu-id="6b74f-111">View the [Experience the Microsoft Cloud with Cloud Adoption Test Lab Guides](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy session (only 22 minutes).</span></span>
    
- <span data-ttu-id="6b74f-112">
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="6b74f-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="office-365-devtest-environment"></a><span data-ttu-id="6b74f-113">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-113">Office 365 dev/test environment</span></span>
<span data-ttu-id="6b74f-114"><a name="O365"> </a></span><span class="sxs-lookup"><span data-stu-id="6b74f-114"><a name="O365"> </a></span></span>

<span data-ttu-id="6b74f-115">Office 365 の開発/テスト環境を構築するのに、次の記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-115">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="6b74f-116">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-116">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-p102">Microsoft Azure インフラストラクチャ サービスで実行される簡易型のイントラネットを作成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6b74f-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="6b74f-119">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-119">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-120">Office 365 Enterprise E5 試用版サブスクリプションを作成します。これは、使用中のコンピューターから、または Azure インフラストラクチャ サービスで実行される簡易型のイントラネットから実行できます。</span><span class="sxs-lookup"><span data-stu-id="6b74f-120">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="6b74f-121">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="6b74f-121">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-p103">Azure AD Connect をインストールして、ディレクトリ同期をパスワード同期と共に実行するように構成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6b74f-p103">Install and configure Azure AD Connect for directory synchronization with password synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="6b74f-124">Office 365 の開発/テスト環境では、Office 365 のエンタープライズ機能をデモンストレーションするために次の記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-124">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="6b74f-125">Office 365 開発/テスト環境用の多要素認証</span><span class="sxs-lookup"><span data-stu-id="6b74f-125">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-126">Office 365 サブスクリプションのアカウントに対応するスマートフォンに送信されたテキスト メッセージを使用して、セカンダリ認証を構成してテストします。</span><span class="sxs-lookup"><span data-stu-id="6b74f-126">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="6b74f-127">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="6b74f-127">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-128">Windows Server Active Directory ドメインのアカウントを使用してフェデレーション認証を構成し、デモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="6b74f-128">Configure and demonstrate federated authentication with the accounts of a Windows Server Active Directory domain.</span></span>
    
- [<span data-ttu-id="6b74f-129">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="6b74f-129">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-130">Office 365 Cloud App Security の構成とデモンストレーションを行い、Office 365 サブスクリプションでの不審なアクティビティを監視し、通知するポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-130">Configure and demonstrate Office 365 Cloud App Security, which allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="6b74f-131">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="6b74f-131">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-132">Advanced Threat Protection の構成とデモンストレーションを行います。これは Exchange Online Protection (EOP) の機能であり、マルウェアからメールを保護します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-132">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>
    
- [<span data-ttu-id="6b74f-133">Office 365 の開発/テスト環境のアドバンスト eDiscovery</span><span class="sxs-lookup"><span data-stu-id="6b74f-133">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-134">サンプル データを追加して Advanced eDiscovery のデモンストレーションを行います。これにより、メールやドキュメントなどの Office 365 に格納されているデータをすばやく見つけて分析できます。</span><span class="sxs-lookup"><span data-stu-id="6b74f-134">Add example data and demonstrate Advanced eDiscovery, which allows you to quickly find and analyze the data that is stored in Office 365, including email and documents.</span></span>
    
- [<span data-ttu-id="6b74f-135">Office 365 の開発/テスト環境での機密性の高いファイルの保護</span><span class="sxs-lookup"><span data-stu-id="6b74f-135">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-136">機密文書を誤って間違ったドキュメント フォルダーに投稿した場合でも、中のデータが保護されるようにするために、Office 365 Information Rights Management を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-136">Demonstrate how you can use Office 365 Information Rights Management to protect the data in sensitive documents, even when they are accidentally posted in the wrong document folders.</span></span>
    
- [<span data-ttu-id="6b74f-137">Office 365 開発/テスト環境でのデータ分類とラベルの作成</span><span class="sxs-lookup"><span data-stu-id="6b74f-137">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-138">Azure Information Protection (AIP) クライアントを使用して、さまざまなレベルのセキュリティでドキュメントを分類する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-138">Demonstrate how the Azure Information Protection (AIP) client can be used to classify documents with various levels of security.</span></span>
    
- [<span data-ttu-id="6b74f-139">Office 365 開発/テスト環境での分離した SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="6b74f-139">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-140">重要なリソースや機密性の高いリソース用に、組織の他の部分から分離されている SharePoint Online チーム サイトを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-140">Demonstrate how to create a SharePoint Online team site that is isolated from the rest of the organization for sensitive or highly confidential resources.</span></span>
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="6b74f-141">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-141">The Microsoft 365 Enterprise dev/test environment</span></span>
<span data-ttu-id="6b74f-142"><a name="O365"> </a></span><span class="sxs-lookup"><span data-stu-id="6b74f-142"><a name="O365"> </a></span></span>

<span data-ttu-id="6b74f-143">これらの記事を利用して [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) シナリオ向けの開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-143">Create a dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) scenarios with these articles:</span></span>
  
- [<span data-ttu-id="6b74f-144">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-144">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-145">Office 365 E5、EMS E5、Windows 10 Enterprise を実行しているコンピューターが含まれる初期環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-145">Create the initial environment that includes Office 365 E5, EMS E5, and a computer running Windows 10 Enterprise.</span></span>
    
- [<span data-ttu-id="6b74f-146">Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー</span><span class="sxs-lookup"><span data-stu-id="6b74f-146">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-147">iOS および Android デバイスのユーザー グループとモバイル アプリケーション管理 (MAM) のポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-147">Create user groups and mobile application management (MAM) policies for ioS and Android devices.</span></span>
    
- [<span data-ttu-id="6b74f-148">あっ、マイクロソフトのエンタープライズ 365 の開発/テスト環境でを登録します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-148">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    <span data-ttu-id="6b74f-149">iOS または Android デバイスを登録し、それらをリモートで管理します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-149">Enroll iOS or Android devices and manage them remotely.</span></span>
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="6b74f-150">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-150">Office 365 and Dynamics 365 dev/test environment</span></span>
<span data-ttu-id="6b74f-151"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="6b74f-151"><a name="O365_D365"> </a></span></span>

<span data-ttu-id="6b74f-152">以下の記事で、Dynamics 365 試用版サブスクリプションを追加し、Office 365 と Dynamics 365 の統合された機能とシナリオをテストします。</span><span class="sxs-lookup"><span data-stu-id="6b74f-152">Add a Dynamics 365 trial subscription and test Office 365 and Dynamics 365 integrated features and scenarios with these articles:</span></span>
  
- [<span data-ttu-id="6b74f-153">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-153">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
    <span data-ttu-id="6b74f-154">Dynamics 365 試用版サブスクリプションと Dynamics 365 ライセンス、およびアクセス許可をユーザー アカウントに追加します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-154">Add a Dynamics 365 trial subscription and Dynamics 365 licences and permissions to your user accounts.</span></span>
    
- [<span data-ttu-id="6b74f-155">Office 365 と Dynamics 365 の開発/テスト環境の Exchange Online 統合</span><span class="sxs-lookup"><span data-stu-id="6b74f-155">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    <span data-ttu-id="6b74f-156">Exchange Online のメールボックスで Office 365 と Dynamics 365 を併用するための構成と方法ついて説明します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-156">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes.</span></span>
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="6b74f-157">One Microsoft Cloud 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-157">The One Microsoft Cloud dev/test environment</span></span>
<span data-ttu-id="6b74f-158"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="6b74f-158"><a name="O365_D365"> </a></span></span>

<span data-ttu-id="6b74f-p104">次の Microsoft のクラウド サービスすべてを含む開発/テスト環境を作成します:Office 365、Azure、EMS、Dynamics 365。詳しい手順については、「[One Microsoft Cloud 開発/テスト環境](the-one-microsoft-cloud-dev-test-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b74f-p104">Create a dev/test environment that includes all of Microsoft's cloud offerings: Office 365, Azure, EMS, and Dynamics 365. See [The One Microsoft Cloud dev/test environment](the-one-microsoft-cloud-dev-test-environment.md) for the step-by-step instructions.</span></span>
  
## <a name="simulated-cross-premises-devtest-environments"></a><span data-ttu-id="6b74f-161">シミュレートされたクロスプレミスの開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-161">Simulated cross-premises dev/test environments</span></span>
<span data-ttu-id="6b74f-162"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="6b74f-162"><a name="O365_D365"> </a></span></span>

<span data-ttu-id="6b74f-163">以下の記事で、Azure 仮想ネットワークやシミュレートされたオンプレミス ネットワークが含まれている、クロスプレミスの開発/テスト環境を作成できます。</span><span class="sxs-lookup"><span data-stu-id="6b74f-163">You can create a cross-premises dev/test environment, which includes an Azure virtual network and a simulated on-premises network, with these articles:</span></span>
  
- [<span data-ttu-id="6b74f-164">Azure でのシミュレートされたクロスプレミスの仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="6b74f-164">Simulated cross-premises virtual network in Azure</span></span>](simulated-cross-premises-virtual-network-in-azure.md)
    
    <span data-ttu-id="6b74f-165">シミュレートされたイントラネットを作成し、ハイブリッド クラウド構成で Azure Virtual Network に接続します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-165">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
- [<span data-ttu-id="6b74f-166">Azure 開発/テスト環境でのイントラネット SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="6b74f-166">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    <span data-ttu-id="6b74f-167">Azure 仮想ネットワークに単一のサーバー SharePoint Server 2016 ファームを作成して、シミュレートされたオンプレミス ネットワークからの接続と管理をテストします。</span><span class="sxs-lookup"><span data-stu-id="6b74f-167">Create a single-server SharePoint Server 2016 farm in the Azure virtual network and test connectivity and administration from the simulated on-premises network.</span></span>
    
## <a name="additional-cloud-based-devtest-environments"></a><span data-ttu-id="6b74f-168">クラウド ベースの他の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-168">Additional cloud-based dev/test environments</span></span>
<span data-ttu-id="6b74f-169"><a name="ADD_TLGs"> </a></span><span class="sxs-lookup"><span data-stu-id="6b74f-169"><a name="ADD_TLGs"> </a></span></span>

<span data-ttu-id="6b74f-170">Azure インフラストラクチャ サービス内に作成できる、クラウド ベースのその他の開発/テスト環境は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6b74f-170">Here are additional cloud-based dev/test environments that you can create in Azure infrastructure services:</span></span>
  
- [<span data-ttu-id="6b74f-171">Azure における SharePoint Server 2016 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-171">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt723354.aspx)
    
    <span data-ttu-id="6b74f-172">Azure インフラストラクチャ サービスに単一サーバーの SharePoint Server 2016 ファームを構築します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-172">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="6b74f-173">Azure における Exchange 2016 開発およびテスト環境</span><span class="sxs-lookup"><span data-stu-id="6b74f-173">Exchange 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    <span data-ttu-id="6b74f-174">単一の Exchange 2016 サーバーを Azure インフラストラクチャ サービスに構築します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-174">Build a single Exchange 2016 server in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="6b74f-175">SharePoint Server 2013 dev/test environments in Azure</span><span class="sxs-lookup"><span data-stu-id="6b74f-175">SharePoint Server 2013 dev/test environments in Azure</span></span>](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    <span data-ttu-id="6b74f-176">基本および高可用性の SharePoint Server 2013 ファームを Azure インフラストラクチャ サービスに構築します。</span><span class="sxs-lookup"><span data-stu-id="6b74f-176">Build basic and high-availability SharePoint Server 2013 farms in Azure infrastructure services.</span></span>
    
<span data-ttu-id="6b74f-177">**ディスカッションへの参加**</span><span class="sxs-lookup"><span data-stu-id="6b74f-177">**Join the discussion**</span></span>

|<span data-ttu-id="6b74f-178">**お問い合わせ**</span><span class="sxs-lookup"><span data-stu-id="6b74f-178">**Contact us**</span></span>|<span data-ttu-id="6b74f-179">**説明**</span><span class="sxs-lookup"><span data-stu-id="6b74f-179">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6b74f-180">**必要なソリューション**</span><span class="sxs-lookup"><span data-stu-id="6b74f-180">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="6b74f-p105">複数の Microsoft 製品やサービスにまたがるソリューションに関するコンテンツを作成しています。[MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) に電子メールを送信して、サーバー間のソリューションに関するご意見や、特定のソリューションに関するご質問をお寄せください。</span><span class="sxs-lookup"><span data-stu-id="6b74f-p105">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="6b74f-183">**ソリューションのディスカッションへの参加**</span><span class="sxs-lookup"><span data-stu-id="6b74f-183">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="6b74f-p106">クラウドベースのソリューションに関して強い関心がある場合は、Cloud Adoption Advisory Board (CAAB) に参加して、大規模で活発な Microsoft コンテンツ開発者、業界プロフェッショナル、および世界中のお客様の大規模で活発なコミュニティとつながることを検討してください。参加するには、Microsoft Tech Community の [CAAB (Cloud Adoption Advisory Board) スペース](https://aka.ms/caab)のメンバーとしてご自分を追加し、[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!) 宛に電子メールを送信してください。[CAAB ブログ](https://blogs.technet.com/b/solutions_advisory_board/)でコミュニティ関連のコンテンツをだれでも読むことができます。ただし、CAAB のメンバーになると、新しいクラウド導入のリソースやソリューションについての非公開 Web セミナーへの招待が送られます。</span><span class="sxs-lookup"><span data-stu-id="6b74f-p106">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="6b74f-187">**記載されているアートの取得方法**</span><span class="sxs-lookup"><span data-stu-id="6b74f-187">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="6b74f-p107">この記事にあるアートの編集可能なコピーが必要な方には、喜んでお送りします。アートの URL とタイトルを記述した電子メールを [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20) に送信してください。</span><span class="sxs-lookup"><span data-stu-id="6b74f-p107">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="6b74f-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b74f-190">See Also</span></span>

<span data-ttu-id="6b74f-191"><a name="ADD_TLGs"> </a></span><span class="sxs-lookup"><span data-stu-id="6b74f-191"><a name="ADD_TLGs"> </a></span></span>

[<span data-ttu-id="6b74f-192">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="6b74f-192">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="6b74f-193">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="6b74f-193">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="6b74f-194">SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル</span><span class="sxs-lookup"><span data-stu-id="6b74f-194">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="6b74f-195">ハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="6b74f-195">Hybrid solutions</span></span>](hybrid-solutions.md)


