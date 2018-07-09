---
title: クラウド導入のテスト ラボ ガイド (TLG)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: '概要: これらのクラウド導入のテスト ラボ ガイド (TLG) を使用して、Office 365、Enterprise Mobility + Security (EMS)、Dynamics 365、Office Server 製品のデモンストレーション、概念実証、開発/テスト環境を設定します。'
ms.openlocfilehash: ac48a9d3d0941b1152aa2bc22a8d9aa5dde7ad77
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188165"
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a><span data-ttu-id="b9584-103">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="b9584-103">Cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="b9584-104">**概要:** これらのクラウド導入のテスト ラボ ガイド (TLG) を使用して、Office 365、Enterprise Mobility + Security (EMS)、Dynamics 365、Office Server 製品のデモンストレーション、概念実証、開発/テスト環境を設定します。</span><span class="sxs-lookup"><span data-stu-id="b9584-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365, Enterprise Mobility + Security (EMS), Dynamics 365, and Office Server products.</span></span>
  
<span data-ttu-id="b9584-p101">TLG では短時間で Microsoft 製品について学習できます。あるテクノロジや構成について、それが特定の状況に適しているかどうかを決定したり、テクノロジをユーザーにロールアウトするために、事前に評価が必要な場合に最適です。この実地体験型ガイドにより、新しい製品やソリューションの展開要件を理解し、運用環境でホストする計画を立てやすくなります。</span><span class="sxs-lookup"><span data-stu-id="b9584-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you or before you roll it out to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="b9584-108">また、TLG は、アプリケーションの開発およびテスト用の典型的な環境を作成します。これは、開発/テスト環境とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b9584-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Microsoft Cloud のテスト ラボ ガイド](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
<span data-ttu-id="b9584-110">開始する前に、これらの追加のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9584-110">See these additional resources before diving in:</span></span>
  
- <span data-ttu-id="b9584-111">Microsoft Virtual Academy セッションの「[クラウド導入のテスト ラボ ガイドを使用した Microsoft Cloud を試す](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 )」(22 分) を視聴してください。</span><span class="sxs-lookup"><span data-stu-id="b9584-111">View the [Experience the Microsoft Cloud with Cloud Adoption Test Lab Guides](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy session (only 22 minutes).</span></span>
    
- <span data-ttu-id="b9584-112">
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="b9584-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="office-365-devtest-environment"></a><span data-ttu-id="b9584-113">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-113">Office 365 dev/test environment</span></span>

<span data-ttu-id="b9584-114">Office 365 の開発/テスト環境を構築するのに、次の記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9584-114">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="b9584-115">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-115">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="b9584-p102">Microsoft Azure インフラストラクチャ サービスで実行される簡易型のイントラネットを作成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="b9584-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="b9584-118">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-118">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="b9584-119">Office 365 Enterprise E5 試用版サブスクリプションを作成します。これは、使用中のコンピューターから、または Azure インフラストラクチャ サービスで実行される簡易型のイントラネットから実行できます。</span><span class="sxs-lookup"><span data-stu-id="b9584-119">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="b9584-120">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="b9584-120">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b9584-p103">Azure AD Connect をインストールして、ディレクトリ同期をパスワード同期と共に実行するように構成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="b9584-p103">Install and configure Azure AD Connect for directory synchronization with password synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="b9584-123">Office 365 の開発/テスト環境では、Office 365 のエンタープライズ機能をデモンストレーションするために次の記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9584-123">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="b9584-124">Office 365 開発/テスト環境用の多要素認証</span><span class="sxs-lookup"><span data-stu-id="b9584-124">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b9584-125">Office 365 サブスクリプションのアカウントに対応するスマートフォンに送信されたテキスト メッセージを使用して、セカンダリ認証を構成してテストします。</span><span class="sxs-lookup"><span data-stu-id="b9584-125">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="b9584-126">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="b9584-126">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b9584-127">Windows Server Active Directory ドメインのアカウントを使用してフェデレーション認証を構成し、デモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="b9584-127">Configure and demonstrate federated authentication with the accounts of a Windows Server Active Directory domain.</span></span>
    
- [<span data-ttu-id="b9584-128">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="b9584-128">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b9584-129">Office 365 Cloud App Security の構成とデモンストレーションを行い、Office 365 サブスクリプションでの不審なアクティビティを監視し、通知するポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9584-129">Configure and demonstrate Office 365 Cloud App Security, which allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="b9584-130">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="b9584-130">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b9584-131">Advanced Threat Protection の構成とデモンストレーションを行います。これは Exchange Online Protection (EOP) の機能であり、マルウェアからメールを保護します。</span><span class="sxs-lookup"><span data-stu-id="b9584-131">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>
    
- [<span data-ttu-id="b9584-132">Office 365 の開発/テスト環境のアドバンスト eDiscovery</span><span class="sxs-lookup"><span data-stu-id="b9584-132">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b9584-133">サンプル データを追加して Advanced eDiscovery のデモンストレーションを行います。これにより、メールやドキュメントなどの Office 365 に格納されているデータをすばやく見つけて分析できます。</span><span class="sxs-lookup"><span data-stu-id="b9584-133">Add example data and demonstrate Advanced eDiscovery, which allows you to quickly find and analyze the data that is stored in Office 365, including email and documents.</span></span>
    
- [<span data-ttu-id="b9584-134">Office 365 の開発/テスト環境での機密性の高いファイルの保護</span><span class="sxs-lookup"><span data-stu-id="b9584-134">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b9584-135">機密文書を誤って間違ったドキュメント フォルダーに投稿した場合でも、中のデータが保護されるようにするために、Office 365 Information Rights Management を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9584-135">Demonstrate how you can use Office 365 Information Rights Management to protect the data in sensitive documents, even when they are accidentally posted in the wrong document folders.</span></span>
    
- [<span data-ttu-id="b9584-136">Office 365 開発/テスト環境でのデータ分類とラベルの作成</span><span class="sxs-lookup"><span data-stu-id="b9584-136">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="b9584-137">Azure Information Protection (AIP) クライアントを使用して、さまざまなレベルのセキュリティでドキュメントを分類する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9584-137">Demonstrate how the Azure Information Protection (AIP) client can be used to classify documents with various levels of security.</span></span>
    
- [<span data-ttu-id="b9584-138">Office 365 開発/テスト環境での分離した SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="b9584-138">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    <span data-ttu-id="b9584-139">重要なリソースや機密性の高いリソース用に、組織の他の部分から分離されている SharePoint Online チーム サイトを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9584-139">Demonstrate how to create a SharePoint Online team site that is isolated from the rest of the organization for sensitive or highly confidential resources.</span></span>
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="b9584-140">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-140">The Microsoft 365 Enterprise dev/test environment</span></span>

<span data-ttu-id="b9584-141">これらの記事を利用して [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) シナリオ向けの開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="b9584-141">Create a dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) scenarios with these articles:</span></span>
  
- [<span data-ttu-id="b9584-142">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-142">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="b9584-143">Office 365 E5、EMS E5、Windows 10 Enterprise を実行しているコンピューターが含まれる初期環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="b9584-143">Create the initial environment that includes Office 365 E5, EMS E5, and a computer running Windows 10 Enterprise.</span></span>
    
- [<span data-ttu-id="b9584-144">Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー</span><span class="sxs-lookup"><span data-stu-id="b9584-144">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="b9584-145">iOS および Android デバイスのユーザー グループとモバイル アプリケーション管理 (MAM) のポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9584-145">Create user groups and mobile application management (MAM) policies for ioS and Android devices.</span></span>
    
- [<span data-ttu-id="b9584-146">Microsoft 365 Enterprise 開発/テスト環境に iOS および Android デバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="b9584-146">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    <span data-ttu-id="b9584-147">iOS または Android デバイスを登録し、それらをリモートで管理します。</span><span class="sxs-lookup"><span data-stu-id="b9584-147">Enroll iOS or Android devices and manage them remotely.</span></span>
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="b9584-148">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-148">Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="b9584-149">以下の記事で、Dynamics 365 試用版サブスクリプションを追加し、Office 365 と Dynamics 365 の統合された機能とシナリオをテストします。</span><span class="sxs-lookup"><span data-stu-id="b9584-149">Add a Dynamics 365 trial subscription and test Office 365 and Dynamics 365 integrated features and scenarios with these articles:</span></span>
  
- [<span data-ttu-id="b9584-150">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-150">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
    <span data-ttu-id="b9584-151">Dynamics 365 試用版サブスクリプションと Dynamics 365 ライセンス、およびアクセス許可をユーザー アカウントに追加します。</span><span class="sxs-lookup"><span data-stu-id="b9584-151">Add a Dynamics 365 trial subscription and Dynamics 365 licences and permissions to your user accounts.</span></span>
    
- [<span data-ttu-id="b9584-152">Office 365 と Dynamics 365 の開発/テスト環境の Exchange Online 統合</span><span class="sxs-lookup"><span data-stu-id="b9584-152">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    <span data-ttu-id="b9584-153">Exchange Online のメールボックスで Office 365 と Dynamics 365 を併用するための構成と方法ついて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9584-153">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes.</span></span>
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="b9584-154">One Microsoft Cloud 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-154">The One Microsoft Cloud dev/test environment</span></span>

<span data-ttu-id="b9584-p104">次の Microsoft のクラウド サービスすべてを含む開発/テスト環境を作成します:Office 365、Azure、EMS、Dynamics 365。詳しい手順については、「[One Microsoft Cloud 開発/テスト環境](the-one-microsoft-cloud-dev-test-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9584-p104">Create a dev/test environment that includes all of Microsoft's cloud offerings: Office 365, Azure, EMS, and Dynamics 365. See [The One Microsoft Cloud dev/test environment](the-one-microsoft-cloud-dev-test-environment.md) for the step-by-step instructions.</span></span>
  
## <a name="simulated-cross-premises-devtest-environments"></a><span data-ttu-id="b9584-157">シミュレートされたクロスプレミスの開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-157">Simulated cross-premises dev/test environments</span></span>

<span data-ttu-id="b9584-158">以下の記事で、Azure 仮想ネットワークやシミュレートされたオンプレミス ネットワークが含まれている、クロスプレミスの開発/テスト環境を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b9584-158">You can create a cross-premises dev/test environment, which includes an Azure virtual network and a simulated on-premises network, with these articles:</span></span>
  
- [<span data-ttu-id="b9584-159">Azure でのシミュレートされたクロスプレミスの仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="b9584-159">Simulated cross-premises virtual network in Azure</span></span>](simulated-cross-premises-virtual-network-in-azure.md)
    
    <span data-ttu-id="b9584-160">シミュレートされたイントラネットを作成し、ハイブリッド クラウド構成で Azure Virtual Network に接続します。</span><span class="sxs-lookup"><span data-stu-id="b9584-160">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
- [<span data-ttu-id="b9584-161">Azure 開発/テスト環境でのイントラネット SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="b9584-161">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    <span data-ttu-id="b9584-162">Azure 仮想ネットワークに単一のサーバー SharePoint Server 2016 ファームを作成して、シミュレートされたオンプレミス ネットワークからの接続と管理をテストします。</span><span class="sxs-lookup"><span data-stu-id="b9584-162">Create a single-server SharePoint Server 2016 farm in the Azure virtual network and test connectivity and administration from the simulated on-premises network.</span></span>
    
## <a name="additional-cloud-based-devtest-environments"></a><span data-ttu-id="b9584-163">クラウド ベースの他の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-163">Additional cloud-based dev/test environments</span></span>

<span data-ttu-id="b9584-164">Azure インフラストラクチャ サービス内に作成できる、クラウド ベースのその他の開発/テスト環境は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b9584-164">Here are additional cloud-based dev/test environments that you can create in Azure infrastructure services:</span></span>
  
- [<span data-ttu-id="b9584-165">Azure における SharePoint Server 2016 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-165">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt723354.aspx)
    
    <span data-ttu-id="b9584-166">Azure インフラストラクチャ サービスに単一サーバーの SharePoint Server 2016 ファームを構築します。</span><span class="sxs-lookup"><span data-stu-id="b9584-166">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="b9584-167">Azure における Exchange 2016 開発およびテスト環境</span><span class="sxs-lookup"><span data-stu-id="b9584-167">Exchange 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    <span data-ttu-id="b9584-168">単一の Exchange 2016 サーバーを Azure インフラストラクチャ サービスに構築します。</span><span class="sxs-lookup"><span data-stu-id="b9584-168">Build a single Exchange 2016 server in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="b9584-169">SharePoint Server 2013 dev/test environments in Azure</span><span class="sxs-lookup"><span data-stu-id="b9584-169">SharePoint Server 2013 dev/test environments in Azure</span></span>](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    <span data-ttu-id="b9584-170">基本および高可用性の SharePoint Server 2013 ファームを Azure インフラストラクチャ サービスに構築します。</span><span class="sxs-lookup"><span data-stu-id="b9584-170">Build basic and high-availability SharePoint Server 2013 farms in Azure infrastructure services.</span></span>
    
<span data-ttu-id="b9584-171">**ディスカッションへの参加**</span><span class="sxs-lookup"><span data-stu-id="b9584-171">**Join the discussion**</span></span>

|<span data-ttu-id="b9584-172">**お問い合わせ**</span><span class="sxs-lookup"><span data-stu-id="b9584-172">**Contact us**</span></span>|<span data-ttu-id="b9584-173">**説明**</span><span class="sxs-lookup"><span data-stu-id="b9584-173">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b9584-174">**必要なソリューション**</span><span class="sxs-lookup"><span data-stu-id="b9584-174">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="b9584-p105">複数の Microsoft 製品やサービスにまたがるソリューションに関するコンテンツを作成しています。[MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) に電子メールを送信して、サーバー間のソリューションに関するご意見や、特定のソリューションに関するご質問をお寄せください。</span><span class="sxs-lookup"><span data-stu-id="b9584-p105">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="b9584-177">**ソリューションのディスカッションへの参加**</span><span class="sxs-lookup"><span data-stu-id="b9584-177">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="b9584-p106">クラウドベースのソリューションに関して強い関心がある場合は、Cloud Adoption Advisory Board (CAAB) に参加して、大規模で活発な Microsoft コンテンツ開発者、業界プロフェッショナル、および世界中のお客様の大規模で活発なコミュニティとつながることを検討してください。参加するには、Microsoft Tech Community の [CAAB (Cloud Adoption Advisory Board) スペース](https://aka.ms/caab)のメンバーとしてご自分を追加し、[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!) 宛に電子メールを送信してください。[CAAB ブログ](https://blogs.technet.com/b/solutions_advisory_board/)でコミュニティ関連のコンテンツをだれでも読むことができます。ただし、CAAB のメンバーになると、新しいクラウド導入のリソースやソリューションについての非公開 Web セミナーへの招待が送られます。</span><span class="sxs-lookup"><span data-stu-id="b9584-p106">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="b9584-182">**記載されているアートの取得方法**</span><span class="sxs-lookup"><span data-stu-id="b9584-182">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="b9584-p107">この記事にあるアートの編集可能なコピーが必要な方には、喜んでお送りします。アートの URL とタイトルを記述した電子メールを [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20) に送信してください。</span><span class="sxs-lookup"><span data-stu-id="b9584-p107">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="b9584-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9584-185">See Also</span></span>

<span data-ttu-id="b9584-186"><a name="ADD_TLGs"> </a></span><span class="sxs-lookup"><span data-stu-id="b9584-186"></span></span>

[<span data-ttu-id="b9584-187">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="b9584-187">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="b9584-188">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="b9584-188">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="b9584-189">SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル</span><span class="sxs-lookup"><span data-stu-id="b9584-189">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="b9584-190">ハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="b9584-190">Hybrid solutions</span></span>](hybrid-solutions.md)


