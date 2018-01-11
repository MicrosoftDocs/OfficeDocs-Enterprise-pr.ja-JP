---
title: "エンタープライズ アーキテクトのための Microsoft クラウド ID"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "概要: Microsoft クラウド サービスとプラットフォームの ID ソリューションを設計します。"
ms.openlocfilehash: 601d449937d0b21299f4653aa872e0a3d4bc5337
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="microsoft-cloud-identity-for-enterprise-architects"></a><span data-ttu-id="d8755-103">エンタープライズ アーキテクトのための Microsoft クラウド ID</span><span class="sxs-lookup"><span data-stu-id="d8755-103">Microsoft Cloud Identity for Enterprise Architects</span></span>

 <span data-ttu-id="d8755-104">**概要:** Microsoft クラウド サービスとプラットフォームの ID ソリューションを設計します。</span><span class="sxs-lookup"><span data-stu-id="d8755-104">**Summary:** Design your identity solution for Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="d8755-p101">この記事では、Microsoft クラウド サービスとプラットフォームを使用して、組織の ID を設計する上で IT アーキテクトが知る必要のある事柄を説明します。この記事を 5 ページのポスターとして表示し、タブロイド形式 (レジャー、11 x 17、または A3 とも表される) で印刷することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8755-p101">This article describes what IT architects need to know about designing identity for organizations using Microsoft cloud services and platforms. You can also view this article as a 5-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="d8755-107">[![Microsoft クラウド ID モデルのサムネイル画像](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="d8755-107">[![Thumb image for Microsoft cloud identity model](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="d8755-108">![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio ファイル](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![他の言語のバージョンのページを参照してください](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[その他の言語](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="d8755-108">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![See a page with versions in additional languages](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="d8755-109">すべてのモデルを [Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)で見ることも、「[Microsoft の Enterprise Cloud ロードマップ: IT の意思決定者向けのリソース](https://aka.ms/cloudarchitecture)」でスワイプして見ることもできます。</span><span class="sxs-lookup"><span data-stu-id="d8755-109">You can also see all of the models in the [Microsoft Cloud IT architecture resources](microsoft-cloud-it-architecture-resources.md) and swipe through [Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture).</span></span>
  
> [!NOTE]
> <span data-ttu-id="d8755-p102">この記事は「**エンタープライズ アーキテクトのための Microsoft クラウド ID**」ポスター (2016 年 1 月版) を反映しています。ポスターの 2016 年 4 月以降の版の変更点は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="d8755-p102">This article reflects the January 2016 version of the **Microsoft cloud identity for enterprise architects** poster. It does not contain the changes for the April 2016 or later versions of the poster.</span></span>
  
## <a name="designing-identity-for-the-microsoft-cloud"></a><span data-ttu-id="d8755-112">Microsoft クラウドの ID を設計する</span><span class="sxs-lookup"><span data-stu-id="d8755-112">Designing identity for the Microsoft cloud</span></span>

<span data-ttu-id="d8755-p103">ID を Microsoft クラウドと統合すると、広範なサービスとクラウド プラットフォームのオプションにアクセスできるようになります。主に 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="d8755-p103">Integrating your identities with the Microsoft cloud provides access to a broad range of services and cloud platform options. There are two main options:</span></span>
  
- <span data-ttu-id="d8755-p104">Microsoft Azure Active Directory (AD) と統合できます。これには、オンプレミスのアカウントを、Microsoft クラウドの ID プロバイダーである Azure AD に同期することが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d8755-p104">You can integrate with Microsoft Azure Active Directory (AD). This involves synchronizing your on-premises accounts to Azure AD, the identity provider for the Microsoft cloud.</span></span>
    
- <span data-ttu-id="d8755-117">オンプレミスの Active Directory ドメイン サービス (AD DS) 環境を、Microsoft Azure インフラストラクチャ サービスで実行されている仮想マシンに拡張できます。</span><span class="sxs-lookup"><span data-stu-id="d8755-117">You can extend your on-premises Active Directory Domain Services (AD DS) environment to virtual machines running in Microsoft Azure infrastructure services.</span></span>
    
![クラウドで ID を設計するためのオプション](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 <span data-ttu-id="d8755-119">**図 1:クラウドの ID の設計のオプション**</span><span class="sxs-lookup"><span data-stu-id="d8755-119">**Figure 1: Options for designing your identities in the cloud**</span></span>
  
<span data-ttu-id="d8755-120">図 1 は、Azure AD が Microsoft のサービスとしてのソフトウェア (SaaS) サービスと Azure のサービスとしてのプラットフォーム (PaaS) アプリケーションの ID プロバイダーであることと、どのようにして基幹業務アプリケーションがオンプレミスの AD DS を使用するのかを示しています。</span><span class="sxs-lookup"><span data-stu-id="d8755-120">Figure 1 shows how Azure AD is the identity provider for Microsoft Software as a Service (SaaS) services and Azure Platform as a Service (PaaS) applications and how line-of-business applications can use on-premises AD DS.</span></span> 
  
### <a name="azure-active-directory"></a><span data-ttu-id="d8755-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="d8755-121">Azure Active Directory</span></span>

<span data-ttu-id="d8755-p105">Microsoft Azure AD は、Microsoft クラウドでホストされる、ID およびアクセス管理サービスです。これは、Microsoft クラウド サービスとプラットフォームの中心にあります。Azure AD と統合すると、現在のアカウントとパスワードのセットを使用して、すべての Microsoft SaaS サービスにアクセスできるようになります。その統合により、Azure PaaS アプリケーションのクラウドベースの ID も提供されます。</span><span class="sxs-lookup"><span data-stu-id="d8755-p105">Microsoft Azure AD is the Microsoft cloud-hosted identity and access management service. It's at the center of Microsoft cloud services and platforms. Integrating with Azure AD provides access to all of the Microsoft SaaS services using your current set of accounts and passwords. That integration also provides cloud-based identity for Azure PaaS applications.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="d8755-126">Azure AD を統合するからといって、大企業や、Azure のサービスとしてのインフラストラクチャ (IaaS) で実行されている Windows ベースの仮想マシンのためのオンプレミスの AD DS が必要なくなるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d8755-126">Azure AD does not replace the need for AD DS on-premises for enterprise organizations or for Windows -based virtual machines running in Azure Infrastructure as a Service (IaaS).</span></span> 
  
<span data-ttu-id="d8755-127">Azure AD には 3 つのエディションがあります。それは、無料、基本、プレミアムです。</span><span class="sxs-lookup"><span data-stu-id="d8755-127">There are three editions of Azure AD: Free, Basic, and Premium.</span></span> 
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="d8755-128">**無料**</span><span class="sxs-lookup"><span data-stu-id="d8755-128">**Free**</span></span> <br/> |<span data-ttu-id="d8755-129">**基本**</span><span class="sxs-lookup"><span data-stu-id="d8755-129">**Basic**</span></span> <br/> |<span data-ttu-id="d8755-130">**プレミアム**</span><span class="sxs-lookup"><span data-stu-id="d8755-130">**Premium**</span></span> <br/> |
| <span data-ttu-id="d8755-131">	ユーザー アカウントの管理</span><span class="sxs-lookup"><span data-stu-id="d8755-131">Manage user accounts</span></span> <br/>  <span data-ttu-id="d8755-132">オンプレミスのディレクトリと同期する</span><span class="sxs-lookup"><span data-stu-id="d8755-132">Synchronize with on-premises directories</span></span> <br/>  <span data-ttu-id="d8755-133">Azure、Office 365、何千もの他の人気のある SaaS アプリケーション (Salesforce、Workday、Concur、DocuSign、Google アプリ、Box、ServiceNow、Dropbox など) 間でのシングル サインオン</span><span class="sxs-lookup"><span data-stu-id="d8755-133">Single sign-on across Azure, Office 365, and thousands of other popular SaaS applications, such as Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more</span></span> <br/> | <span data-ttu-id="d8755-134">無料エディションのすべての機能に加え、以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d8755-134">Includes all of the abilities in the Free edition, plus:</span></span> <br/>  <span data-ttu-id="d8755-135">会社のブランド化</span><span class="sxs-lookup"><span data-stu-id="d8755-135">Company branding</span></span> <br/>  <span data-ttu-id="d8755-136">グループベースのアプリケーションへのアクセス</span><span class="sxs-lookup"><span data-stu-id="d8755-136">Group-based application access</span></span> <br/>  <span data-ttu-id="d8755-137">セルフサービスによるパスワードのリセット</span><span class="sxs-lookup"><span data-stu-id="d8755-137">Self-service password reset</span></span> <br/>  <span data-ttu-id="d8755-138">99.9% のエンタープライズ SLA </span><span class="sxs-lookup"><span data-stu-id="d8755-138">Enterprise SLA of 99.9%</span></span> <br/> | <span data-ttu-id="d8755-139">無料と基本エディションのすべての機能に加え、以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d8755-139">Includes all of the features of the Free and Basic editions, plus:</span></span> <br/>  <span data-ttu-id="d8755-140">セルフサービスによるグループの管理</span><span class="sxs-lookup"><span data-stu-id="d8755-140">Self-service group management</span></span> <br/>  <span data-ttu-id="d8755-141">	高度なセキュリティ レポートと警告</span><span class="sxs-lookup"><span data-stu-id="d8755-141">Advanced security reports and alerts</span></span> <br/>  <span data-ttu-id="d8755-142">	多要素認証</span><span class="sxs-lookup"><span data-stu-id="d8755-142">Multi-factor authentication</span></span> <br/>  <span data-ttu-id="d8755-143">オンプレミス AD DS へのライトバックによるパスワードのリセット</span><span class="sxs-lookup"><span data-stu-id="d8755-143">Password reset with write-back to on-premises AD DS</span></span> <br/>  <span data-ttu-id="d8755-144">Azure AD Connect ツールの双方向同期</span><span class="sxs-lookup"><span data-stu-id="d8755-144">Azure AD Connect tool bidirectional synchronization</span></span> <br/>  <span data-ttu-id="d8755-145">Azure AD アプリケーション プロキシ</span><span class="sxs-lookup"><span data-stu-id="d8755-145">Azure AD Application Proxy</span></span> <br/>  <span data-ttu-id="d8755-146">	Microsoft Forefront Identity Manager (MIM)</span><span class="sxs-lookup"><span data-stu-id="d8755-146">Microsoft Forefront Identity Manager (MIM)</span></span> <br/> |
   
<span data-ttu-id="d8755-147">バージョンについて詳しくは、「[Azure Active Directory のエディション](https://go.microsoft.com/fwlink/p/?LinkId=524280)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d8755-147">For more information about versions, see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
### <a name="option-1-integrate-with-azure-active-directory"></a><span data-ttu-id="d8755-148">オプション 1:Azure Active Directory と統合する</span><span class="sxs-lookup"><span data-stu-id="d8755-148">Option 1: Integrate with Azure Active Directory</span></span>

<span data-ttu-id="d8755-p106">ほとんどの組織では、標準的なオブジェクトのセットと Azure AD テナントの属性を同期します。Azure AD Connect ツールは、オンプレミス AD DS と Azure AD テナント間でアカウントを同期します。</span><span class="sxs-lookup"><span data-stu-id="d8755-p106">Most organizations synchronize a standard set of objects and attributes to their Azure AD tenant. The Azure AD Connect tool synchronizes your accounts between on-premises AD DS and an Azure AD tenant.</span></span>
  
![Azure AD と統合する](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 <span data-ttu-id="d8755-152">**図 2:Azure AD と統合する**</span><span class="sxs-lookup"><span data-stu-id="d8755-152">**Figure 2: Integrating with Azure AD**</span></span>
  
<span data-ttu-id="d8755-p107">図 2 は、Azure AD Connect ツールが AD DS の変更を取得し、Azure AD テナントに送信する方法を示します。この場合、Azure AD テナントは、重要なオンプレミス ディレクトリ コンテンツの、クラウドでホストされたコピーです。</span><span class="sxs-lookup"><span data-stu-id="d8755-p107">Figure 2 shows how the Azure AD Connect tool obtains AD DS changes and sends them to your Azure AD tenant. In this case, your Azure AD tenant is a cloud-hosted duplicate of essential on-premises directory content.</span></span>
  
<span data-ttu-id="d8755-p108">多くの組織は、オンプレミスの ID プロバイダーとして AD DS を使用しています。異なる種類のオンプレミスの ID プロバイダー (LDAP を使用する ID プロバイダーなど) を使用し、それらを Azure AD に同期できます。</span><span class="sxs-lookup"><span data-stu-id="d8755-p108">Many organizations use AD DS as their on-premises identity provider. You can use a different type of identity provider on-premises (such as one that uses LDAP), and synchronize these to Azure AD.</span></span>
  
### <a name="option-2-extend-ad-ds-to-azure"></a><span data-ttu-id="d8755-157">オプション 2:Azure に AD DS を拡張する</span><span class="sxs-lookup"><span data-stu-id="d8755-157">Option 2: Extend AD DS to Azure</span></span>

<span data-ttu-id="d8755-p109">Azure インフラストラクチャ サービスで実行されている仮想マシンに AD DS を拡張すると、Azure AD との同期とは異なるソリューションとアプケーションのセットがサポートされます。2 つを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d8755-p109">Extending AD DS to virtual machines running in Azure infrastructure services supports a different set of solutions and applications compared to synchronization with Azure AD. Here are two:</span></span>
  
- <span data-ttu-id="d8755-160">NTLM や Kerberos 認証を必要とするクラウドベースのソリューションや、AD DS ドメインに参加している仮想マシンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d8755-160">Supports cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="d8755-161">Microsoft クラウド サービスとプラットフォーム間でのクラウド サービスとアプリケーションの他の統合の可能性を追加します。</span><span class="sxs-lookup"><span data-stu-id="d8755-161">Adds additional integration potential for cloud services and applications across Microsoft cloud services and platforms.</span></span>
    
![Azure に AD DS を拡張する](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 <span data-ttu-id="d8755-163">**図 3:Azure に AD DS を拡張する**</span><span class="sxs-lookup"><span data-stu-id="d8755-163">**Figure 3: Extending AD DS to Azure**</span></span>
  
<span data-ttu-id="d8755-p110">図 3 は、オンプレミスの VPN デバイスや Azure VPN ゲートウェイを通じて Azure 仮想ネットワークに接続している AD DS ドメイン コントローラーを示しています。Azure 仮想ネットワークには、基幹業務アプリケーションと その独自の AD DS ドメイン コントローラー セットのサーバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d8755-p110">Figure 3 shows an AD DS domain controller connected to an Azure virtual network through an on-premises VPN device and an Azure VPN gateway. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers.</span></span>
  
### <a name="more-information"></a><span data-ttu-id="d8755-166">詳細</span><span class="sxs-lookup"><span data-stu-id="d8755-166">More Information</span></span>

- [<span data-ttu-id="d8755-167">簡単にディレクトリを Office 365 と同期できます</span><span class="sxs-lookup"><span data-stu-id="d8755-167">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="d8755-168">インフォグラフィック:クラウド ID およびアクセス管理</span><span class="sxs-lookup"><span data-stu-id="d8755-168">Infographic: Cloud identity and access management</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [<span data-ttu-id="d8755-169">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="d8755-169">Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## <a name="integrate-your-on-premises-ad-ds-accounts-with-microsoft-azure-ad"></a><span data-ttu-id="d8755-170">オンプレミスの AD DS アカウントを Microsoft Azure AD と統合する</span><span class="sxs-lookup"><span data-stu-id="d8755-170">Integrate your on-premises AD DS accounts with Microsoft Azure AD</span></span>

<span data-ttu-id="d8755-171">オンプレミスの AD DS アカウントを Azure AD と統合すると、ユーザーは、オンプレミスの AD DS アカウントを使用して以下にアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d8755-171">By synchronizing your on-premises AD DS accounts with Azure AD, your users can use their on-premises AD DS accounts to access:</span></span>
  
- <span data-ttu-id="d8755-172">すべてのMicrosoft SaaS サービス (Office 365、Microsoft Intune、Dynamics CRM Online)</span><span class="sxs-lookup"><span data-stu-id="d8755-172">All of the Microsoft SaaS services (Office 365, Microsoft Intune, and Dynamics CRM Online)</span></span>
    
- <span data-ttu-id="d8755-173">Azure PaaS で実行されているアプリケーション</span><span class="sxs-lookup"><span data-stu-id="d8755-173">Your applications running in Azure PaaS</span></span>
    
<span data-ttu-id="d8755-174">この統合を構成する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="d8755-174">There are two ways to configure this integration:</span></span>
  
- <span data-ttu-id="d8755-175">ディレクトリ同期とパスワード同期</span><span class="sxs-lookup"><span data-stu-id="d8755-175">Directory and password synchronization</span></span>
    
- <span data-ttu-id="d8755-176">フェデレーションとシングル サインオン</span><span class="sxs-lookup"><span data-stu-id="d8755-176">Federation and single sign-on</span></span>
    
<span data-ttu-id="d8755-p111">まずは、お客様のニーズを満たす最も簡単なオプションを使用します。必要に応じて、これらのオプション間を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="d8755-p111">Start with the simplest option that meets your needs. You can switch between these options, if needed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d8755-179">クラウド専用のアカウントを使用する (オンプレミスの AD DS と統合しない) ことは、エンタープライズ規模の組織にはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="d8755-179">Using cloud-only accounts (not integrating with your on-premises AD DS) is not recommended for enterprise-scale organizations.</span></span> 
  
### <a name="directory-and-password-synchronization"></a><span data-ttu-id="d8755-180">ディレクトリ同期とパスワード同期</span><span class="sxs-lookup"><span data-stu-id="d8755-180">Directory and password synchronization</span></span>

<span data-ttu-id="d8755-181">これは最も簡単なオプションであり、Azure AD Connect ツールを実行するサーバーのみが必要です。</span><span class="sxs-lookup"><span data-stu-id="d8755-181">This is the simplest option and requires only a server running the Azure AD Connect tool.</span></span> 
  
![ディレクトリおよびパスワード同期の構成](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 <span data-ttu-id="d8755-183">**図 4:ディレクトリ同期とパスワード同期を構成する**</span><span class="sxs-lookup"><span data-stu-id="d8755-183">**Figure 4: Directory and password synchronization configuration**</span></span>
  
<span data-ttu-id="d8755-p112">図 4 は、オンプレミスやプライベート クラウドのデータ センターと AD DS ドメイン コントローラーを示しています。Azure AD Connect ツールを実行するサーバーは、アカウント名のリストを Azure AD と同期します。</span><span class="sxs-lookup"><span data-stu-id="d8755-p112">Figure 4 shows an on-premises or private cloud datacenter with an AD DS domain controller. A server running the Azure AD Connect tool synchronizes the list of account names with Azure AD.</span></span>
  
<span data-ttu-id="d8755-186">このオプションを使用する場合:</span><span class="sxs-lookup"><span data-stu-id="d8755-186">With this option:</span></span>
  
- <span data-ttu-id="d8755-p113">ユーザー アカウントは、オンプレミスの AD DS (または他の ID プロバイダー) から Azure AD テナントに同期されます。オンプレミスのディレクトリは、アカウントに対して権限のあるソースのままで、そこからすべてのアカウントの変更を管理します。</span><span class="sxs-lookup"><span data-stu-id="d8755-p113">User accounts are synchronized from your on-premises AD DS (or other identity provider) to your Azure AD tenant. The on-premises directory remains the authoritative source for accounts and you manage all account changes from there.</span></span>
    
- <span data-ttu-id="d8755-189">Azure AD は、Microsoft SaaS ベースのサービスと Azure PaaS アプリケーションのすべての認証を実行します。</span><span class="sxs-lookup"><span data-stu-id="d8755-189">Azure AD performs all authentication for Microsoft SaaS-based services and Azure PaaS applications.</span></span>
    
- <span data-ttu-id="d8755-190">複数の AD DS フォレストの同期を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8755-190">You can also configure synchronization for multiple AD DS forests.</span></span>
    
<span data-ttu-id="d8755-191">パスワード同期を使用する場合:</span><span class="sxs-lookup"><span data-stu-id="d8755-191">With password synchronization:</span></span>
  
- <span data-ttu-id="d8755-192">ユーザーは、クラウド サービスにアクセスするときにパスワードを入力するように求められます。このパスワードは、オンプレミスのリソースで使用するパスワードと同じです。</span><span class="sxs-lookup"><span data-stu-id="d8755-192">Users are prompted to enter a password when accessing cloud services, which is the same password that they use for on-premises resources.</span></span>
    
- <span data-ttu-id="d8755-p114">ユーザーのパスワードは、Azure AD にクリア テキストとして送信されることは決してありません。その代わり、パスワードのハッシュが使用されます。暗号により、パスワード ハッシュの暗号化やリバース エンジニアリングを行い、クリア テキストのパスワードを取得することは不可能です。</span><span class="sxs-lookup"><span data-stu-id="d8755-p114">User passwords are never sent as cleartext to Azure AD. Instead, a hash of the password is used. It is cryptographically impossible to decrypt or reverse-engineer the password hash and obtain the cleartext password.</span></span> 
    
<span data-ttu-id="d8755-196">多要素認証 (MFA) を使用する場合:</span><span class="sxs-lookup"><span data-stu-id="d8755-196">With multi-factor authentication (MFA):</span></span>
  
- <span data-ttu-id="d8755-197">Office 365 により提供される基本的な MFA の機能を活用できます。</span><span class="sxs-lookup"><span data-stu-id="d8755-197">You can take advantage of basic MFA features offered with Office 365.</span></span>
    
- <span data-ttu-id="d8755-198">Azure PaaS アプリケーションの開発者は、Azure 多要素認証サービスを活用できます。</span><span class="sxs-lookup"><span data-stu-id="d8755-198">Azure PaaS application developers can take advantage of the Azure Multi-Factor Authentication service.</span></span>
    
<span data-ttu-id="d8755-199">ディレクトリ同期では、オンプレミスの MFA ソリューションとの統合は提供されません。</span><span class="sxs-lookup"><span data-stu-id="d8755-199">Directory synchronization does not provide integration with on-premises MFA solutions.</span></span>
  
### <a name="federation-and-single-sign-on"></a><span data-ttu-id="d8755-200">フェデレーションとシングル サインオン</span><span class="sxs-lookup"><span data-stu-id="d8755-200">Federation and single sign-on</span></span>

<span data-ttu-id="d8755-201">このオプションには、追加のサーバーとインフラストラクチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="d8755-201">This option requires additional servers and infrastructure.</span></span> 
  
![フェデレーション認証に必要なサーバー](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 <span data-ttu-id="d8755-203">**図 5: フェデレーション認証に必要なサーバー**</span><span class="sxs-lookup"><span data-stu-id="d8755-203">**Figure 5: Servers needed for federated authentication**</span></span>
  
<span data-ttu-id="d8755-p115">図 5 は、フェデレーション認証用のコンポーネントのセットを示しています。Azure AD は、Active Directory フェデレーション サービス (AD FS) サーバーに認証要求を転送する Web アプリケーション プロキシに接続します。AD FS サーバーは、評価と応答のために AD DS ドメイン コント ローラーに要求を転送します。Azure AD Connect ツールを実行するサーバーは、AD DS から Azure AD にアカウント名のリストを同期します。</span><span class="sxs-lookup"><span data-stu-id="d8755-p115">Figure 5 shows the set of components for federated authentication. Azure AD contacts a web application proxy, which forwards the authentication request to an Active Directory Federation Services (AD FS) server, which forwards the request to an AD DS domain controller for evaluation and response. A server running the Azure AD Connect tool synchronizes the list of account names from AD DS to Azure AD.</span></span>
  
<span data-ttu-id="d8755-207">フェデレーションは、以下の追加のエンタープライズ機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="d8755-207">Federation provides these additional enterprise capabilities:</span></span>
  
- <span data-ttu-id="d8755-208">Azure AD に送信されるすべての認証要求は、AD FS を通じてオンプレミスの ID プロバイダーに転送され実行されます。</span><span class="sxs-lookup"><span data-stu-id="d8755-208">All authentication requests sent to Azure AD are forwarded to and performed against the on-premises identity provider through AD FS.</span></span>
    
- <span data-ttu-id="d8755-209">Microsoft 以外の ID プロバイダーと共に機能します。</span><span class="sxs-lookup"><span data-stu-id="d8755-209">Works with non-Microsoft identity providers.</span></span>
    
- <span data-ttu-id="d8755-210">パスワード ハッシュ同期は、フェデレーション サインインのサインイン バックアップとして使用できます (たとえば、フェデレーション認証に失敗した場合)。</span><span class="sxs-lookup"><span data-stu-id="d8755-210">Password hash synchronization can act as a sign-in backup for federated sign-in (for example, if the federated authentication fails).</span></span>
    
<span data-ttu-id="d8755-211">以下の場合は、フェデレーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="d8755-211">Use federation if:</span></span>
  
- <span data-ttu-id="d8755-p116">シングル サインオンが必要です。シングル サインオンでは、クラウド サービスにアクセスする際、ユーザーは資格情報 (ユーザー名やパスワード) の入力を求められません。</span><span class="sxs-lookup"><span data-stu-id="d8755-p116">Single sign-on is required. With single sign-on, users are not prompted to enter any credentials (user name or password), when accessing a cloud service.</span></span>
    
- <span data-ttu-id="d8755-214">AD FS は既に展開されています。</span><span class="sxs-lookup"><span data-stu-id="d8755-214">AD FS is already deployed.</span></span>
    
- <span data-ttu-id="d8755-215">サードパーティの ID プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="d8755-215">You use a third-party identity provider.</span></span>
    
- <span data-ttu-id="d8755-216">Forefront Identity Manager 2010 R2 を使用します (パスワード ハッシュ同期をサポートしません)。</span><span class="sxs-lookup"><span data-stu-id="d8755-216">You use Forefront Identity Manager 2010 R2 (does not support password hash synchronization).</span></span>
    
- <span data-ttu-id="d8755-217">オンプレミスの統合されたスマート カードやその他の MFA ソリューションがあります。</span><span class="sxs-lookup"><span data-stu-id="d8755-217">You have an on-premises integrated smart card or other MFA solution.</span></span>
    
- <span data-ttu-id="d8755-218">サインイン監査またはアカウントの無効化あるいはその両方が必要です。</span><span class="sxs-lookup"><span data-stu-id="d8755-218">You require sign-in audit and/or disablement of accounts.</span></span>
    
- <span data-ttu-id="d8755-219">組織では、ネットワークの場所や作業時間による、クライアントのサインインの制限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d8755-219">Your organization requires client sign-in restrictions by network location or work hours.</span></span>
    
- <span data-ttu-id="d8755-220">連邦情報処理規格 (FIPS) に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8755-220">You must comply with Federal Information Processing Standards (FIPS).</span></span>
    
<span data-ttu-id="d8755-221">フェデレーション認証には、インフラストラクチャ オンプレミスへの多額の投資が必要です。</span><span class="sxs-lookup"><span data-stu-id="d8755-221">Federated authentication requires a greater investment in infrastructure on-premises.</span></span>
  
- <span data-ttu-id="d8755-p117">オンプレミスのサーバーは、会社のファイアウォールを介してインターネットにアクセスできる必要があります。Microsoft は、境界ネットワークに展開された Web アプリケーション プロキシ サーバーの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d8755-p117">The on-premises servers must be Internet-accessible through a corporate firewall. Microsoft recommends the use of Web Application Proxy servers deployed in your perimeter network.</span></span>
    
- <span data-ttu-id="d8755-224">ハードウェア、ライセンス、AD FS サーバー、AD FS プロキシ、Web アプリケーション プロキシ サーバーの操作、ファイアウォール、ロード バランサーが必要です。</span><span class="sxs-lookup"><span data-stu-id="d8755-224">Requires hardware, licenses, and operations for AD FS servers, AD FS proxy or Web Application Proxy servers, firewalls, and load balancers.</span></span> 
    
- <span data-ttu-id="d8755-225">ユーザーが Office 365 とその他のクラウド アプリケーションへのアクセスを確保するために、可用性とパフォーマンスは重要です。</span><span class="sxs-lookup"><span data-stu-id="d8755-225">Availability and performance are important to ensure users can access Office 365 and other cloud applications.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="d8755-226">詳細</span><span class="sxs-lookup"><span data-stu-id="d8755-226">More Information</span></span>

- [<span data-ttu-id="d8755-227">簡単にディレクトリを Office 365 と同期できます</span><span class="sxs-lookup"><span data-stu-id="d8755-227">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="d8755-228">Office 365 へのディレクトリ同期を通してユーザーをプロビジョニングするための準備</span><span class="sxs-lookup"><span data-stu-id="d8755-228">Prepare to provision users through directory synchronization to Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [<span data-ttu-id="d8755-229">Office 365 の多要素認証</span><span class="sxs-lookup"><span data-stu-id="d8755-229">Multi-Factor Authentication for Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [<span data-ttu-id="d8755-230">Azure 多要素認証</span><span class="sxs-lookup"><span data-stu-id="d8755-230">Azure Multi-Factor Authentication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [<span data-ttu-id="d8755-231">TechEd 2014:ディレクトリ統合:Active Directory と Azure Active Directory を使用して 1 つのディレクトリを作成する</span><span class="sxs-lookup"><span data-stu-id="d8755-231">TechEd 2014: Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## <a name="extend-ad-ds-to-azure"></a><span data-ttu-id="d8755-232">Azure に AD DS を拡張する</span><span class="sxs-lookup"><span data-stu-id="d8755-232">Extend AD DS to Azure</span></span>

<span data-ttu-id="d8755-233">Azure インフラストラクチャ サービスの仮想マシンで実行されている基幹業務アプリケーションをサポートするためには、まず Azure に AD DS を拡張します。この拡張により、以下が行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="d8755-233">Extending AD DS to Azure is the first step to support line-of-business applications running on virtual machines in Azure infrastructure services, which provides:</span></span>
  
- <span data-ttu-id="d8755-234">NTLM や Kerberos 認証を必要とするクラウドベースのソリューションや、AD DS ドメインに参加している仮想マシンに対するサポート。</span><span class="sxs-lookup"><span data-stu-id="d8755-234">Support for cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="d8755-235">クラウド サービスとアプリケーションの他の統合をいつでも追加できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d8755-235">Additional integration potential for cloud services and applications and can be added at any time.</span></span>
    
![Azure 仮想ネットワークに AD DS を拡張する](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 <span data-ttu-id="d8755-237">**図 6: Azure 仮想ネットワークに AD DS を拡張する**</span><span class="sxs-lookup"><span data-stu-id="d8755-237">**Figure 6: Extending AD DS to an Azure virtual network**</span></span>
  
<span data-ttu-id="d8755-p118">図 6 は、オンプレミスやプライベート クラウドのデータ センター、Azure 仮想マシンに接続している AD DS、サイト間 VPN や ExpressRoute 接続を示しています。Azure 仮想ネットワークには、基幹業務アプリケーションと その独自の AD DS ドメイン コントローラー セットのサーバーが含まれています。この構成は、オンプレミスの AD DS と Azure インフラストラクチャ サービスのハイブリッド展開です。以下が必要です。</span><span class="sxs-lookup"><span data-stu-id="d8755-p118">Figure 6 shows an on-premises or private cloud datacenter with AD DS connected to an Azure virtual network with a site-to-site VPN or ExpressRoute connection. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers. This configuration is a hybrid deployment of AD DS on-premises and in Azure infrastructure services. It requires:</span></span>
  
- <span data-ttu-id="d8755-242">Azure 仮想ネットワーク。</span><span class="sxs-lookup"><span data-stu-id="d8755-242">An Azure virtual network.</span></span>
    
- <span data-ttu-id="d8755-243">オンプレミスの仮想プライベート ネットワーク (VPN) デバイスやルーターと、Azure の VPN ゲートウェイ間の接続。</span><span class="sxs-lookup"><span data-stu-id="d8755-243">A connection between an on-premises virtual private network (VPN) device or router and an Azure VPN gateway.</span></span>
    
- <span data-ttu-id="d8755-244">オンプレミスの IP アドレス空間の一部を仮想ネットワーク内の仮想マシンに使用すること。</span><span class="sxs-lookup"><span data-stu-id="d8755-244">Using a portion of your on-premises IP address space for the virtual machines in the virtual network.</span></span>
    
- <span data-ttu-id="d8755-245">仮想ネットワーク内の 1 つ以上のドメイン コントローラーを、グローバル カタログ サーバーとして展開すること (VPN 接続経由の出力トラフィックが減少します)。</span><span class="sxs-lookup"><span data-stu-id="d8755-245">Deploying one or more domain controllers in the virtual network designated as global catalog servers (reduces egress traffic across the VPN connection).</span></span>
    
<span data-ttu-id="d8755-246">この ID アーキテクチャは、Azure AD との同期とは異なるソリューションとアプリケーションのセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d8755-246">This identity architecture supports a different set of solutions and applications compared to synchronization with Azure AD.</span></span>
  
### <a name="on-premises-to-azure-connection-options"></a><span data-ttu-id="d8755-247">オンプレミスから Azure への接続のオプション</span><span class="sxs-lookup"><span data-stu-id="d8755-247">On-premises to Azure connection options</span></span>

<span data-ttu-id="d8755-248">オンプレミス ネットワークを Azure 仮想ネットワークに接続するには、以下を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8755-248">To connect your on-premises network to an Azure virtual network, you can use:</span></span>
  
- <span data-ttu-id="d8755-249">サイト間 VPN 接続。単一の Azure 仮想ネットワーク に 1 ～ 10 個のサイト (他の Azure 仮想ネットワークを含む) を接続できます。</span><span class="sxs-lookup"><span data-stu-id="d8755-249">A site-to-site VPN connection, which can connect 1-10 sites (including other Azure virtual networks) to a single Azure virtual network.</span></span>
    
- <span data-ttu-id="d8755-p119">ExpressRoute。これは、パートナーのネットワークとデータセンター サービスのプロバイダーを経由する Azure へのセキュリティ保護されたプライベート WAN リンクです。ExpressRoute 接続では、高い信頼性、広い帯域幅、低レイテンシが実現できます。</span><span class="sxs-lookup"><span data-stu-id="d8755-p119">ExpressRoute, a private, secure WAN link to Azure through a partner network and datacenter services provider. ExpressRoute connections can offer increased reliability, higher bandwidth, and lower latencies.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="d8755-252">詳細</span><span class="sxs-lookup"><span data-stu-id="d8755-252">More Information</span></span>

- [<span data-ttu-id="d8755-253">仮想ネットワークのクロスプレミス接続</span><span class="sxs-lookup"><span data-stu-id="d8755-253">Cross-premises connectivity for virtual networks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [<span data-ttu-id="d8755-254">ExpressRoute の技術概要</span><span class="sxs-lookup"><span data-stu-id="d8755-254">ExpressRoute Technical Overview</span></span>](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [<span data-ttu-id="d8755-255">Azure 仮想マシン上で Windows Server Active Directory を展開するためのガイドライン</span><span class="sxs-lookup"><span data-stu-id="d8755-255">Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## <a name="integrate-your-applications-with-cloud-identities"></a><span data-ttu-id="d8755-256">アプリケーションをクラウド ID と統合する</span><span class="sxs-lookup"><span data-stu-id="d8755-256">Integrate your applications with cloud identities</span></span>

<span data-ttu-id="d8755-p120">クラウドで実行するアプリケーションを設計および開発する際は、必要な資格情報のセットなど、認証プロセスのユーザー エクスペリエンスが一貫したものになるようにする必要があります。たとえば、Windows の資格情報を使用する場合、Azure AD や拡張 AD DS のどちらであろうと、ユーザーがすばやく認証を行い、タスクに集中できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d8755-p120">When designing and developing applications that run in the cloud, you should aim for consistency of the user experience for the authentication process, including the set of required credentials. For example, when using Windows credentials, whether against Azure AD or an extended AD DS, ensure that users can quickly authenticate and focus on their tasks.</span></span>
  
![アプリケーションをクラウド ID と統合する](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 <span data-ttu-id="d8755-260">**図 7:アプリケーションをクラウド ID と統合する**</span><span class="sxs-lookup"><span data-stu-id="d8755-260">**Figure 7: Integrate your applications with cloud identities**</span></span>
  
<span data-ttu-id="d8755-261">図 7 は、アプリケーションをクラウド ID と統合するための 3 つのオプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="d8755-261">Figure 7 shows three options for integrating your application with cloud identities.</span></span>
  
1. <span data-ttu-id="d8755-262">クラウドでホストされているアプリケーションを Azure AD に登録します。</span><span class="sxs-lookup"><span data-stu-id="d8755-262">Register your cloud-hosted applications with Azure AD.</span></span>
    
    <span data-ttu-id="d8755-p121">MSDN 記事「[アプリケーションを Azure Active Directory と統合する](https://go.microsoft.com/fwlink/p/?LinkId=524303)」をご覧ください。これにより、Azure AD を使用して PaaS アプリケーションへのアクセスを認証することが可能になり、また、アプリケーションが Office 365 などの他のクラウド サービスのコンテンツにユーザーや管理者に代わってアクセスするための権限を、ユーザーや管理者がアプリケーションに対して付与できるようになります。詳細とコード サンプルについては、MSDN 記事「[Azure Active Directory の認証シナリオ](https://go.microsoft.com/fwlink/p/?LinkId=524304)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d8755-p121">See the MSDN article [Integrating Applications with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). This lets you use Azure AD to authenticate access to your PaaS application, as well as allowing users or administrators to grant rights to your application to access content on their behalf from other cloud services, such as Office 365. More details and code samples can be found in the MSDN article [Authentication Scenarios for Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span></span> 
    
2. <span data-ttu-id="d8755-266">AD SD、Windows Server 2012 R2 上の AD FS、Azure AD を使用してセキュリティ保護されているアプリケーションにアクセスするためにプログラムによる認証を必要とするアプリケーションでは、以下を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8755-266">Applications that require programmatic authentication to gain access to an application secured by AD SD, AD FS on Windows Server 2012 R2, or Azure AD can use:</span></span>
    
  - <span data-ttu-id="d8755-267">[Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span><span class="sxs-lookup"><span data-stu-id="d8755-267">The [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span></span>
    
  - [<span data-ttu-id="d8755-268">Active Directory 認証ライブラリ (ADAL)</span><span class="sxs-lookup"><span data-stu-id="d8755-268">Active Directory Authentication Library (ADAL)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=524297)
    
    <span data-ttu-id="d8755-p122">Azure AD Graph API は、OAuth と OpenID Connect をサポートします。PaaS アプリケーションでも動作します。</span><span class="sxs-lookup"><span data-stu-id="d8755-p122">The Azure AD Graph API supports OAuth and OpenID Connect. It also works with PaaS applications.</span></span>
    
3. <span data-ttu-id="d8755-p123">Windows 認証 (NTLM や Kerberos) を直接使用するように、オンプレミスのアプリケーションや Azure 仮想ネットワークの仮想マシンで実行されている基幹業務アプリケーションを構成します。これは、ユーザーにとって最適なエクスペリエンスであり、この場合、サーバー アプリケーションの開発者は最小限の構成を行うだけでよいことになります。</span><span class="sxs-lookup"><span data-stu-id="d8755-p123">Configure on-premises applications or line-of-business applications running on virtual machines in an Azure virtual network to use Windows authentication (NTLM or Kerberos) directly. This is the best experience for users and requires the least configuration for server application developers.</span></span>
    
### <a name="application-integration-example"></a><span data-ttu-id="d8755-273">アプリケーション統合の例</span><span class="sxs-lookup"><span data-stu-id="d8755-273">Application integration example</span></span>

<span data-ttu-id="d8755-p124">組織は、他のアプリケーションが最新の売上データを取得できる REST エンドポイントを公開する ASP.NET アプリケーションを作成します。その REST エンドポイントへのアクセスは、Azure AD でセキュリティ保護されます。アプリケーションは、ASP.NET アプリケーションが要求されたデータを送信する前に、Azure AD で認証できる資格情報を指定する必要があります。組織内の他の開発者は、REST エンドポイントからの売上データを使用して独自のアプリケーションを記述できます。</span><span class="sxs-lookup"><span data-stu-id="d8755-p124">An organization builds an ASP.NET application that exposes a REST endpoint where other applications can obtain the latest sales data. Access to that REST endpoint is secured with Azure AD. Applications must provide credentials that can be authenticated by Azure AD before the ASP.NET application sends the requested data. Other developers in the organization can then write their own applications that use the sales data from the REST endpoint.</span></span>
  
<span data-ttu-id="d8755-p125">Azure AD への認証を行いデータを取得するため、ADAL はユーザー認証プロセスを管理して、売上データへのアクセスに使用できるように、アプリケーションにアクセス トークンを渡します。ADAL によって、トークン、OAuth フロー、その他の要素の取得と解析はだいぶ簡略化されます。ADAL も、急速に変化するテクノロジ ソリューションであるため、開発者は NuGet で最新バージョンを探すようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d8755-p125">To authenticate to Azure AD and retrieve data, ADAL manages the user authentication process and hands the access token off to the application so it can be used to gain access to the sales data. ADAL abstracts out much of the complexity of obtaining and parsing tokens, OAuth flows, and other elements. ADAL is another technology solution that is rapidly changing so developers should look for the latest version on NuGet.</span></span>
  
## <a name="deploying-directory-components-in-azure"></a><span data-ttu-id="d8755-281">ディレクトリ コンポーネントを Azure に展開する</span><span class="sxs-lookup"><span data-stu-id="d8755-281">Deploying directory components in Azure</span></span>

<span data-ttu-id="d8755-p126">パスワード同期やフェデレーション認証用のサーバーなどのディレクトリ コンポーネントは、オンプレミスのデータ センターではなく、Azure 仮想ネットワークに展開できます。Azure に AD DS を拡張する場合は特に、その利点をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="d8755-p126">You can deploy directory components, such as servers for password synchronization or federated authentication, in an Azure virtual network rather than an on-premises datacenter. Consider its benefits, especially if you plan to extend AD DS into Azure.</span></span>
  
<span data-ttu-id="d8755-284">Azure 仮想ネットワークに格納できるディレクトリ コンポーネントを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d8755-284">Here are the directory components that can be put in an Azure virtual network:</span></span>
  
- <span data-ttu-id="d8755-285">Azure AD Connect ツール</span><span class="sxs-lookup"><span data-stu-id="d8755-285">Azure AD Connect tool</span></span>
    
- <span data-ttu-id="d8755-286">フェデレーション認証コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d8755-286">Federated authentication components</span></span>
    
- <span data-ttu-id="d8755-287">スタンドアロン AD DS 環境</span><span class="sxs-lookup"><span data-stu-id="d8755-287">A standalone AD DS environment</span></span>
    
### <a name="ad-connect-tool"></a><span data-ttu-id="d8755-288">AD Connect ツール</span><span class="sxs-lookup"><span data-stu-id="d8755-288">AD Connect tool</span></span>

<span data-ttu-id="d8755-p127">Azure AD Connect ツールは、Azure 仮想ネットワーク上のクラウドにホストできます。このワークロードを Azure に展開することには、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="d8755-p127">The Azure AD Connect tool can be hosted in the cloud on an Azure virtual network. Consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="d8755-291">プロビジョニングを高速化して運用コストを削減できる可能性がある</span><span class="sxs-lookup"><span data-stu-id="d8755-291">Potentially faster provisioning and lower cost of operations</span></span>
    
- <span data-ttu-id="d8755-292">可用性が向上する</span><span class="sxs-lookup"><span data-stu-id="d8755-292">Increased availability</span></span>
    
![Azure インフラストラクチャ サービスで実行されている AD Connect ツール](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 <span data-ttu-id="d8755-294">**図 8:Azure で実行されている AD Connect ツール**</span><span class="sxs-lookup"><span data-stu-id="d8755-294">**Figure 8: The AD Connect tool running in Azure**</span></span>
  
<span data-ttu-id="d8755-p128">図 8 は、Azure 仮想ネットワーク内の仮想マシンで実行されている AD Connect ツールを示しています。AD Connect ツールはオンプレミスの AD DS ドメイン コントローラーに対してアカウントの変更についてのクエリを実行し、Office 365 にそれらの変更を送信します。このソリューションは、以下と共に機能します。</span><span class="sxs-lookup"><span data-stu-id="d8755-p128">Figure 8 shows the AD Connect tool running on a virtual machine in an Azure virtual network, which queries an on-premises AD DS domain controller for account changes and then sends those changes to Office 365. This solution works with:</span></span>
  
- <span data-ttu-id="d8755-297">Office 365 サービス。</span><span class="sxs-lookup"><span data-stu-id="d8755-297">Office 365 services.</span></span>
    
- <span data-ttu-id="d8755-298">インターネット上で利用できる Azure PaaS アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="d8755-298">Azure PaaS applications that are available over the Internet.</span></span>
    
- <span data-ttu-id="d8755-299">サイト間 VPN や ExpressRoute 接続を介して、オンプレミス環境から利用できる Azure 内の基幹業務アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="d8755-299">Line-of-business applications in Azure that are available from on-premises environments through the site-to-site VPN or ExpressRoute connection.</span></span>
    
<span data-ttu-id="d8755-300">詳しくは「[オンプレミスの ID を Azure Active Directory と統合する](https://go.microsoft.com/fwlink/p/?LinkId=524307)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d8755-300">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="federated-authentication-infrastructure"></a><span data-ttu-id="d8755-301">フェデレーション認証インフラストラクチャ</span><span class="sxs-lookup"><span data-stu-id="d8755-301">Federated authentication infrastructure</span></span>

<span data-ttu-id="d8755-302">オンプレミスに AD FS をまだ展開していない場合は、このワークロードを Azure に展開することの利点についてご検討ください。それには次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="d8755-302">If you haven't already deployed AD FS on-premises, consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="d8755-303">クラウド サービスへの認証の独立性を提供します (オンプレミスには依存しない)</span><span class="sxs-lookup"><span data-stu-id="d8755-303">Provides autonomy for authentication to cloud services (no on-premises dependencies)</span></span>
    
- <span data-ttu-id="d8755-304">オンプレミスにホストされるサーバーとツールの数を減らします</span><span class="sxs-lookup"><span data-stu-id="d8755-304">Reduces servers and tools hosted on-premises</span></span>
    
- <span data-ttu-id="d8755-305">2 ノードのフェールオーバー クラスターのサイト間 VPN ゲートウェイを使用して Azure に接続します (新しい点)</span><span class="sxs-lookup"><span data-stu-id="d8755-305">Uses a site-to-site VPN gateway on a two-node failover cluster to connect to Azure (new)</span></span>
    
- <span data-ttu-id="d8755-306">ACL を使用することにより、Web アプリケーション プロキシ サーバーのみが AD FS と通信できるようにし、ドメイン コントローラーや他のサーバーが直接 AD FS と通信することのないようにします</span><span class="sxs-lookup"><span data-stu-id="d8755-306">Uses ACLs to ensure that Web Application Proxy servers can only communicate with AD FS, not domain controllers or other servers directly</span></span>
    
![Azure でフェデレーション認証インフラストラクチャを展開する](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 <span data-ttu-id="d8755-308">**図 9:Azure でフェデレーション認証インフラストラクチャを展開する**</span><span class="sxs-lookup"><span data-stu-id="d8755-308">**Figure 9: Deploying your federated authentication infrastructure in Azure**</span></span>
  
<span data-ttu-id="d8755-p129">図 9 は、Azure 仮想ネットワーク内のドメイン コントローラーのセットとの間で AD DS 情報をレプリケートするオンプレミスのドメイン コントローラーのセットを示しています。Azure 仮想ネットワーク内のサーバーで実行されている Azure AD Connect ツールは、ローカルのドメイン コントローラーに対して変更についてのクエリを実行し、Azure AD にそれらの変更を送信します。Microsoft SaaS サービス、Azure PaaS アプリケーション、その他のクラウド アプリケーションから受信した Azure AD への認証要求は、外部のロード バランサーに転送されます。その後、外部ロード バランサーは要求を Web アプリケーション プロキシ サーバーのセットに転送します。Web アプリケーション プロキシ サーバーは要求を内部ロード バランサーに転送し、内部ロード バランサーは AD FS サーバーのセットに転送します。その後、送信資格情報を検証するため、AD FS サーバーは要求をドメイン コントローラーに転送します。</span><span class="sxs-lookup"><span data-stu-id="d8755-p129">Figure 9 shows a set of on-premises domain controllers replicating AD DS information with a set of domain controllers in an Azure virtual network. The Azure AD Connect tool running on a server in the Azure virtual network queries the local domain controllers for changes and then sends those changes to Azure AD. Incoming authentication requests to Azure AD from Microsoft SaaS services, Azure PaaS applications, and other cloud applications are forwarded to an external load balancer, which forwards the request to a set of Web Application Proxy servers. The Web Application Proxy servers forward the request to an internal load balancer, which forwards the request to a set of AD FS servers. The AD FS servers then forward the request to a domain controller to validate the send credentials.</span></span>
  
 <span data-ttu-id="d8755-314">このソリューションは、以下と共に機能します。</span><span class="sxs-lookup"><span data-stu-id="d8755-314">This solution works with:</span></span>
  
- <span data-ttu-id="d8755-315">Kerberos を必要とするアプリケーション</span><span class="sxs-lookup"><span data-stu-id="d8755-315">Applications that require Kerberos</span></span>
    
- <span data-ttu-id="d8755-316">すべての Microsoft の SaaS サービス</span><span class="sxs-lookup"><span data-stu-id="d8755-316">All of Microsoft's SaaS services</span></span>
    
- <span data-ttu-id="d8755-317">インターネットに接続された Azure 内のアプリケーション</span><span class="sxs-lookup"><span data-stu-id="d8755-317">Applications in Azure that are Internet-facing</span></span>
    
- <span data-ttu-id="d8755-318">組織の AD DS のアカウントのセットでの認証を必要とする Azure IaaS や PaaS 内のアプリケーション</span><span class="sxs-lookup"><span data-stu-id="d8755-318">Applications in Azure IaaS or PaaS that require authentication with the set of accounts in your organization's AD DS</span></span>
    
<span data-ttu-id="d8755-319">詳しくは「[オンプレミスの ID を Azure Active Directory と統合する](https://go.microsoft.com/fwlink/p/?LinkId=524307)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d8755-319">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="standalone-ad-ds-environment-in-an-azure-virtual-network"></a><span data-ttu-id="d8755-320">Azure 仮想ネットワーク内のスタンドアロン AD DS 環境</span><span class="sxs-lookup"><span data-stu-id="d8755-320">Standalone AD DS environment in an Azure virtual network</span></span>

<span data-ttu-id="d8755-p130">必ずしも、クラウド アプリケーションをオンプレミス環境と統合する必要はありません。たとえば、Azure 仮想ネットワーク内のスタンドアロン AD DS ドメインは、インターネット サイトなど、一般向けのアプリケーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d8755-p130">You don't always need to integrate a cloud application with your on-premises environment. For example, a standalone AD DS domain in an Azure virtual network supports applications that are public-facing, such as Internet sites.</span></span>
  
![サーバー ベース アプリケーションのスタンドアロン AD DS 環境](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 <span data-ttu-id="d8755-324">**図 10:サーバーベース アプリケーションのスタンドアロン AD DS 環境**</span><span class="sxs-lookup"><span data-stu-id="d8755-324">**Figure 10: A standalone AD DS environment for a server-based application**</span></span>
  
<span data-ttu-id="d8755-p131">図 10 は、AD DS と DNS の両方のサービスを提供する AD DS サーバーのセットと、アプリケーションをホストするサーバーのセットをホストしている Azure の仮想ネットワークを示しています。このソリューションは、以下と共に機能します。</span><span class="sxs-lookup"><span data-stu-id="d8755-p131">Figure 10 shows an Azure virtual network hosting a set of AD DS servers, providing both AD DS and DNS services, with a set of servers that host an application. This solution works with:</span></span>
  
- <span data-ttu-id="d8755-327">インターネットに接続された Web サイトとアプリケーション</span><span class="sxs-lookup"><span data-stu-id="d8755-327">Internet-facing web sites and applications</span></span>
    
- <span data-ttu-id="d8755-328">NTLM や Kerberos 認証を必要とするアプリケーション</span><span class="sxs-lookup"><span data-stu-id="d8755-328">Applications that require NTLM or Kerberos authentication</span></span>
    
- <span data-ttu-id="d8755-329">AD DS を必要とする Windows ベースのサーバーで実行されているアプリケーション</span><span class="sxs-lookup"><span data-stu-id="d8755-329">Applications running on Windows-based servers that require AD DS</span></span>
    
<span data-ttu-id="d8755-330">詳しくは「[オンプレミスの ID を Azure Active Directory と統合する](https://go.microsoft.com/fwlink/p/?LinkId=524307)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d8755-330">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d8755-331">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8755-331">See Also</span></span>

[<span data-ttu-id="d8755-332">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="d8755-332">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="d8755-333">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span><span class="sxs-lookup"><span data-stu-id="d8755-333">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>



