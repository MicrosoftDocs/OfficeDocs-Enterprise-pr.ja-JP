---
title: テスト ラボ ガイド (TLG) を使用して Office 365 をテストする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
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
description: '概要: 次に示すテスト ラボ ガイド (TLG) を使用して、Office 365 のデモンストレーション、概念実証、または開発/テスト環境をセットアップします。'
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302739"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a><span data-ttu-id="8e245-103">テスト ラボ ガイド (TLG) を使用して Office 365 をテストする</span><span class="sxs-lookup"><span data-stu-id="8e245-103">Test Office 365 with cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="8e245-104">**概要**: 次に示す記事を使用して、Office 365 のデモンストレーション、概念実証、または開発/テスト環境をセットアップします。</span><span class="sxs-lookup"><span data-stu-id="8e245-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365.</span></span>
  
<span data-ttu-id="8e245-p101">TLG では短時間で Microsoft 製品について学習できます。あるテクノロジや構成について、それが特定の状況に適しているかどうかを決定し、デザイン、プランニングを行いテクノロジをユーザーにロールアウトするさいに、事前に評価が必要な場合に最適です。この実地体験型ガイドにより、新しい製品やソリューションの展開要件を理解し、運用環境でホストする計画を立てやすくなります。</span><span class="sxs-lookup"><span data-stu-id="8e245-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you and before you begin the design, planning, and rollout to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="8e245-108">また、TLG は、アプリケーションの開発およびテスト用の典型的な環境を作成します。これは、開発/テスト環境とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8e245-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Microsoft Cloud のテスト ラボ ガイド](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a><span data-ttu-id="8e245-110">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="8e245-110">Office 365 dev/test environment</span></span>

<span data-ttu-id="8e245-111">Office 365 の開発/テスト環境を構築するのに、次の記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="8e245-111">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="8e245-112">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="8e245-112">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="8e245-p102">Microsoft Azure インフラストラクチャ サービスで実行される簡易型のイントラネットを作成します。シミュレートされたエンタープライズ構成を構築する場合、このステップは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="8e245-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="8e245-115">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="8e245-115">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="8e245-116">Office 365 Enterprise E5 試用版サブスクリプションを作成します。これは、使用中のコンピューターから、または Azure インフラストラクチャ サービスで実行される簡易型のイントラネットから実行できます。</span><span class="sxs-lookup"><span data-stu-id="8e245-116">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="8e245-117">ディレクトリ同期</span><span class="sxs-lookup"><span data-stu-id="8e245-117">Directory synchronization</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8e245-p103">Azure AD Connect をインストールして、ディレクトリ同期をパスワード同期と共に実行するように構成します。このステップは省略可能で、シミュレートされたエンタープライズ構成を構築する場合は行ってください。</span><span class="sxs-lookup"><span data-stu-id="8e245-p103">Install and configure Azure AD Connect for directory synchronization with password hash synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="8e245-120">Office 365 の開発/テスト環境では、Office 365 のエンタープライズ機能をデモンストレーションするために次の記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="8e245-120">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="8e245-121">多要素認証</span><span class="sxs-lookup"><span data-stu-id="8e245-121">Multi-factor authentication</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8e245-122">Office 365 サブスクリプションのアカウントに対応するスマートフォンに送信されたテキスト メッセージを使用して、セカンダリ認証を構成してテストします。</span><span class="sxs-lookup"><span data-stu-id="8e245-122">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="8e245-123">フェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="8e245-123">Federated identity</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8e245-124">Active Directory Domain Services (AD DS) ドメインのアカウントを使用して、フェデレーション認証の構成とデモンストレーションを行います。</span><span class="sxs-lookup"><span data-stu-id="8e245-124">Configure and demonstrate federated authentication with the accounts of an Active Directory Domain Services (AD DS) domain.</span></span>
    
- [<span data-ttu-id="8e245-125">Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="8e245-125">Advanced Threat Protection</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8e245-126">Advanced Threat Protection の構成とデモンストレーションを行います。これは Exchange Online Protection (EOP) の機能であり、マルウェアからメールを保護します。</span><span class="sxs-lookup"><span data-stu-id="8e245-126">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>

## <a name="simulated-cross-premises-devtest-environment"></a><span data-ttu-id="8e245-127">シミュレートされたクロスプレミスの開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="8e245-127">Simulated cross-premises dev/test environments</span></span>

<span data-ttu-id="8e245-128">[シミュレートされたイントラネット](simulated-cross-premises-virtual-network-in-azure.md)を作成し、ハイブリッド クラウド構成で Azure Virtual Network に接続します。</span><span class="sxs-lookup"><span data-stu-id="8e245-128">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
## <a name="sharepoint-server-2016-devtest-environment"></a><span data-ttu-id="8e245-129">SharePoint Server 2016 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="8e245-129">SharePoint Server 2016 dev/test environment in Azure</span></span>

<span data-ttu-id="8e245-130">Azure インフラストラクチャ サービスに[単一サーバーの SharePoint Server 2016 ファーム](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)を構築します。</span><span class="sxs-lookup"><span data-stu-id="8e245-130">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>

## <a name="microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="8e245-131">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="8e245-131">The Microsoft 365 Enterprise dev/test environment</span></span>

<span data-ttu-id="8e245-132">[Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides) の開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="8e245-132">Create a dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides) scenarios with these articles:</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="8e245-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e245-133">See Also</span></span>

[<span data-ttu-id="8e245-134">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="8e245-134">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="8e245-135">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="8e245-135">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="8e245-136">SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル</span><span class="sxs-lookup"><span data-stu-id="8e245-136">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="8e245-137">ハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="8e245-137">Hybrid solutions</span></span>](hybrid-solutions.md)
