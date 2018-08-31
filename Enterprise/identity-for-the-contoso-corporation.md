---
title: Contoso Corporation の ID
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: Contoso 社の IDaaS を利用して地理的に分散、冗長化されたユーザーと認証の概要を理解します。
ms.openlocfilehash: 25e708147bda51fa8f8b4d0ea5e83eb4a9cd10b0
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915442"
---
# <a name="identity-for-the-contoso-corporation"></a><span data-ttu-id="68c60-103">Contoso Corporation の ID</span><span class="sxs-lookup"><span data-stu-id="68c60-103">Identity for the Contoso Corporation</span></span>

 <span data-ttu-id="68c60-104">**の概要:** Contoso 社の IDaaS を利用して地理的に分散、冗長化されたユーザーと認証を理解します。</span><span class="sxs-lookup"><span data-stu-id="68c60-104">**Summary:** Understand how Contoso takes advantage of IDaaS and provides geographically distributed and redundant authentication for its users.</span></span>
  
<span data-ttu-id="68c60-p101">マイクロソフトは、サービス (IDaaS) として、クラウド サービスの間で Id を提供します。クラウドの包括的なインフラストラクチャを導入するには、contoso 社の IDaaS ソリューション必要があります、設置型の id プロバイダーを活用を既存の信頼できる、サードパーティの id プロバイダーとのフェデレーションの認証が含まれてできます。</span><span class="sxs-lookup"><span data-stu-id="68c60-p101">Microsoft provides an Identity as a Service (IDaaS) across its cloud offerings. To adopt a cloud-inclusive infrastructure, Contoso's IDaaS solution must leverage their on-premises identity provider and include federated authentication with their existing trusted, third-party identity providers.</span></span>
  
## <a name="contosos-windows-server-ad-forest"></a><span data-ttu-id="68c60-107">Contoso 社の Windows サーバーの AD フォレスト</span><span class="sxs-lookup"><span data-stu-id="68c60-107">Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="68c60-p102">Contoso 社では、contoso.com に対して 7 つのドメインを持つ単一の Windows Server Active Directory (AD) フォレストを使用しており、世界の地域ごとに 1 つのドメインを使用します。本社、地域ハブ オフィス、サテライト オフィスには、ローカルの認証と承認のためのドメイン コントローラーが含まれています。
</span><span class="sxs-lookup"><span data-stu-id="68c60-p102">Contoso uses a single Windows Server Active Directory (AD) forest for contoso.com with seven domains, one for each region of the world. The headquarters, regional hub offices, and satellite offices contain domain controllers for local authentication and authorization.</span></span>
  
<span data-ttu-id="68c60-110">**図 1:Contoso 社の世界的なフォレストとドメイン**</span><span class="sxs-lookup"><span data-stu-id="68c60-110">**Figure 1: Contoso's forest and domains worldwide**</span></span>

![世界各地の Contoso 社の Windows サーバーの AD フォレストとドメイン](media/Contoso-Poster/Contoso-WW-ID.png)
  
<span data-ttu-id="68c60-112">図 1 では、地域ハブを含む世界各地の地域ドメインを持つ Contoso 社のフォレストを示しています。</span><span class="sxs-lookup"><span data-stu-id="68c60-112">Figure 1 shows the Contoso forest with regional domains for the different parts of the world that contain regional hubs.</span></span>
  
<span data-ttu-id="68c60-113">Contoso 社では、クラウドベースのアプリおよびワークロードの認証と承認のために、contoso.com フォレストのアカウントとグループを使用することを望んでいます。</span><span class="sxs-lookup"><span data-stu-id="68c60-113">Contoso wants to use the accounts and groups in the contoso.com forest for authentication and authorization for its cloud-based apps and workloads.</span></span>
  
## <a name="contosos-federated-authentication-infrastructure"></a><span data-ttu-id="68c60-114">Contoso 社のフェデレーション認証インフラストラクチャ</span><span class="sxs-lookup"><span data-stu-id="68c60-114">Contoso's federated authentication infrastructure</span></span>

<span data-ttu-id="68c60-115">Contoso 社では次のことが可能です。
 


</span><span class="sxs-lookup"><span data-stu-id="68c60-115">Contoso allows:</span></span>
  
- <span data-ttu-id="68c60-116">顧客は Microsoft、Facebook、または Google のメール アカウントを使用してパブリック Web サイトにサインインできます。</span><span class="sxs-lookup"><span data-stu-id="68c60-116">Customers to use their Microsoft, Facebook, or Google Mail accounts to sign in to their public web site.</span></span>
    
- <span data-ttu-id="68c60-117">ベンダーおよびパートナーは、LinkedIn、Salesforce、または Google のメール アカウントを使用してパートナー エクストラネットにサインインできます。</span><span class="sxs-lookup"><span data-stu-id="68c60-117">Vendors and partners to use their LinkedIn, Salesforce, or Google Mail accounts to sign in to the partner extranet.</span></span>
    
<span data-ttu-id="68c60-118">**図 2:Contoso 社の顧客とパートナーのフェデレーション認証のサポート**</span><span class="sxs-lookup"><span data-stu-id="68c60-118">**Figure 2: Contoso's support for federated authentication for customers and partners**</span></span>

![顧客とパートナーのフェデレーション認証をサポートする Contoso 社の既存のインフラストラクチャ](media/Contoso-Poster/Federated-ID.png)
  
<span data-ttu-id="68c60-p103">図 2 は、公開 Web サイト、パートナーのエクストラネット、および AD FS サーバーのセットを含む Contoso 社の DMZ を示しています。DMZ は、顧客、パートナー、およびインターネット サービスを含むインターネットに接続されています。</span><span class="sxs-lookup"><span data-stu-id="68c60-p103">Figure 2 shows the Contoso DMZ containing a public web site, a partner extranet, and a set of AD FS servers. The DMZ is connected to the Internet that contains customers and partners and Internet services.</span></span>
  
<span data-ttu-id="68c60-122">DMZ の Active Directory フェデレーション サービス (AD FS) サーバーは、パブリック Web サイトにアクセスするための顧客資格情報、およびパートナー エクストラネットにアクセスするためのパートナー資格情報を認証します。</span><span class="sxs-lookup"><span data-stu-id="68c60-122">Active Directory Federation Services (AD FS) servers in the DMZ authenticate customer credentials for access to the public web site and partner credentials for access to the partner extranet.</span></span>
  
<span data-ttu-id="68c60-p104">Contoso 社では、Azure の Web アプリケーションやビジネス パートナーのエクストラネットに Dynamics 365 にパブリック web サイトを移行と、の顧客やパートナーのこれらのサードパーティの id プロバイダーを使用して続行します。Contoso Azure AD テナントとこれらのサードパーティの id プロバイダーとの間のフェデレーションを構成することによってこれを達成します。</span><span class="sxs-lookup"><span data-stu-id="68c60-p104">When Contoso transitions its public web site to an Azure Web App and partner extranet to Dynamics 365, they want to continue to use these third-party identity providers for their customers and partners. This will be accomplished by configuring federation between Contoso Azure AD tenants and these third-party identity providers.</span></span>
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a><span data-ttu-id="68c60-125">Contoso 社の Windows サーバーの AD フォレストのディレクトリの同期</span><span class="sxs-lookup"><span data-stu-id="68c60-125">Directory synchronization for Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="68c60-p105">Contoso 社は、パリのデータ センター内のサーバーのクラスターに AD の Azure 接続ツールを導入しました。Azure AD 接続では、contoso 社の Office 365、EMS、Dynamics 365 で、Azure サブスクリプションで共有する Azure AD テナント contoso.com フォレストの Windows サーバーの AD への変更を同期します。サブスクリプション、ライセンス、ユーザー アカウント、およびテナントの詳細については、[サブスクリプション、ライセンス、および Contoso 社のユーザー アカウント](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68c60-p105">Contoso has deployed the Azure AD Connect tool on a cluster of servers in its Paris datacenter. Azure AD Connect synchronizes changes to the contoso.com Windows Server AD forest with the Azure AD tenant shared by Contoso's Office 365, EMS, Dynamics 365, and Azure subscriptions. For more information about subscriptions, licenses, user accounts, and tenants, see [Subscriptions, licenses, and user accounts for the Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span></span>
  
<span data-ttu-id="68c60-129">**図 3:Contoso 社のディレクトリ同期インフラストラクチャ**</span><span class="sxs-lookup"><span data-stu-id="68c60-129">**Figure 3: Contoso's directory synchronization infrastructure**</span></span>

![Contoso 社のディレクトリ同期インフラストラクチャ](media/Contoso-Poster/DirSync.png)
  
<span data-ttu-id="68c60-131">図 3 は、Azure AD テナントで Contoso 社の Windows Server AD フォレストを同期する Azure AD Connect を実行するサーバーのクラスターを示しています。</span><span class="sxs-lookup"><span data-stu-id="68c60-131">Figure 3 shows a cluster of servers running Azure AD Connect synchronizing the Contoso Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="68c60-p106">Contoso 社では、contoso 社の作業者のシングル サインオンを提供する、共通の認証を構成しました。Contoso.com フォレストの Windows サーバーの AD に既にサインインしているユーザーは、マイクロソフトの SaaS や PaaS クラウド リソースをアクセスする場合、いない求められますパスワードの。</span><span class="sxs-lookup"><span data-stu-id="68c60-p106">Contoso has configured federated authentication, which provides single sign-on for Contoso's workers. When a user that has already signed in to the contoso.com Windows Server AD forest accesses a Microsoft SaaS or PaaS cloud resource, they will not be prompted for a password.</span></span>
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a><span data-ttu-id="68c60-134">Contoso 社の認証トラフィックの地理的分布</span><span class="sxs-lookup"><span data-stu-id="68c60-134">Geographical distribution of Contoso authentication traffic</span></span>

<span data-ttu-id="68c60-p107">モバイルおよびリモートの要員をより良くサポートするために、Contoso 社は地域のオフィスにて認証サーバーのセットを展開しました。このインフラストラクチャでは、共通の Azure AD テナントを使用する Microsoft クラウド製品にアクセスするためのユーザー資格情報を認証するときに、負荷が分散され、冗長性と高パフォーマンスが実現されます。
</span><span class="sxs-lookup"><span data-stu-id="68c60-p107">To better support its mobile and remote workforce, Contoso has deployed sets of authentication servers in its regional offices. This infrastructure distributes the load and provides redundancy and higher performance when authenticating user credentials for access to Microsoft cloud offerings that use the common Azure AD tenant.</span></span>
  
<span data-ttu-id="68c60-137">認証要求の負荷を分散するために、Contoso 社は、パフォーマンス ルーティング方法を使用するプロファイルを使用して Azure Traffic Manager を構成しました。この方法では、認証クライアントを地域の最も近い認証サーバーのセットにルーティングします。 </span><span class="sxs-lookup"><span data-stu-id="68c60-137">To distribute the load of authentication requests, Contoso has configured Azure Traffic Manager with a profile that uses the performance routing method, which refers authenticating clients to the regionally closest set of authentication servers.</span></span> 
  
<span data-ttu-id="68c60-138">**図 4:地域のオフィスのための認証トラフィックの地理的分布**</span><span class="sxs-lookup"><span data-stu-id="68c60-138">**Figure 4: Geographical distribution of authentication traffic for regional offices**</span></span>

![Contoso 社の支社のための認証トラフィックの地理的分布](media/Contoso-Poster/Auth-GeoDist.png)
  
<span data-ttu-id="68c60-p108">図 4 では、地域のオフィスでのクライアント コンピューター、Azure Traffic Manager、および認証サーバーのレイヤーを示します。それぞれの地域のオフィスは Web プロキシおよび AD FS サーバーを使用して、Windows Server AD ドメイン コントローラーとユーザーの資格情報を認証します。</span><span class="sxs-lookup"><span data-stu-id="68c60-p108">Figure 4 shows the layers of client computers, Azure Traffic Manager, and authentication servers in regional offices. Each regional office uses web proxies and AD FS servers to authenticate user credentials with Windows Server AD domain controllers.</span></span>
  
<span data-ttu-id="68c60-142">認証プロセスの例:</span><span class="sxs-lookup"><span data-stu-id="68c60-142">Authentication process example:</span></span>
  
1. <span data-ttu-id="68c60-143">クライアント コンピューターは、ヨーロッパの Office 365 テナント内の Web ページ (sharepoint.contoso.com など) と通信を開始します。


</span><span class="sxs-lookup"><span data-stu-id="68c60-143">The client computer initiates communication with a web page in the Office 365 tenancy in Europe (such as sharepoint.contoso.com).</span></span>
    
2. <span data-ttu-id="68c60-p109">Office 365 は、認証の証明を送信する要求を送り返します。要求には、認証のために連絡する URL が含まれています。</span><span class="sxs-lookup"><span data-stu-id="68c60-p109">Office 365 sends back a request to send proof of authentication. The request contains the URL to contact for authentication.</span></span>
    
3. <span data-ttu-id="68c60-146">クライアント コンピューターは、URL 内の DNS 名を IP アドレスに解決しようとします。</span><span class="sxs-lookup"><span data-stu-id="68c60-146">The client computer attempts to resolve the DNS name in the URL to an IP address.</span></span>
    
4. <span data-ttu-id="68c60-147">Azure Traffic Manager は DNS クエリを受信し、クライアント コンピューターに最も近い地域オフィスの Web アプリケーション プロキシ サーバーの IP アドレスを持つクライアント コンピューターに応答します。</span><span class="sxs-lookup"><span data-stu-id="68c60-147">Azure Traffic Manager receives the DNS query and responds to the client computer with the IP address of a web application proxy server in the regional office that is closest to the client computer.</span></span>
    
5.  <span data-ttu-id="68c60-148"> クライアント コンピューターは、認証要求を Web アプリケーション プロキシ サーバーに送信し、このサーバーは要求を AD FS サーバーに転送します。



</span><span class="sxs-lookup"><span data-stu-id="68c60-148">The client computer sends an authentication request to a web application proxy server, which forwards the request to an AD FS server.</span></span>
    
6. <span data-ttu-id="68c60-149">AD FS サーバーは、クライアント コンピューターからユーザー資格情報を要求します。</span><span class="sxs-lookup"><span data-stu-id="68c60-149">The AD FS server requests the user credentials from the client computer.</span></span>
    
7. <span data-ttu-id="68c60-150">クライアント コンピューターは、ユーザーに確認せずにユーザー資格情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="68c60-150">The client computer sends the user credentials without prompting the user.</span></span>
    
8. <span data-ttu-id="68c60-151">AD FS サーバーは、地域オフィスの Windows Server AD ドメイン コントローラーによって資格情報を検証し、クライアント コンピューターにセキュリティ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="68c60-151">The AD FS server validates the credentials with a Windows Server AD domain controller in the regional office and returns a security token to the client computer.</span></span>
    
9. <span data-ttu-id="68c60-152">クライアント コンピューターは、セキュリティ トークンを Office 365 に送信します。</span><span class="sxs-lookup"><span data-stu-id="68c60-152">The client computer sends the security token to Office 365.</span></span>
    
10. <span data-ttu-id="68c60-153">検証に成功したら、Office 365 はセキュリティ トークンをキャッシュし、手順 1 で要求された Web ページをクライアント コンピューターに送信します。</span><span class="sxs-lookup"><span data-stu-id="68c60-153">After successful validation, Office 365 caches the security token and sends the web page requested in step 1 to the client computer.</span></span>
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a><span data-ttu-id="68c60-154">Azure IaaS における本社の認証インフラストラクチャの冗長性</span><span class="sxs-lookup"><span data-stu-id="68c60-154">Redundancy for the headquarters authentication infrastructure in Azure IaaS</span></span>

<span data-ttu-id="68c60-155">15,000 人のワーカーを抱えるパリ本社のリモート ワーカーおよびモバイル ワーカーに冗長性をもたらすために、Contoso 社は、Azure IaaS にアプリケーション プロキシと AD FS サーバーの 2 つ目のセットを展開しました。
</span><span class="sxs-lookup"><span data-stu-id="68c60-155">To provide redundancy for the remote and mobile workers of the Paris headquarters that contains 15,000 workers, Contoso has deployed a second set of application proxies and AD FS servers in Azure IaaS.</span></span>
  
<span data-ttu-id="68c60-156">**図 5:Azure IaaS における冗長認証インフラストラクチャ**</span><span class="sxs-lookup"><span data-stu-id="68c60-156">**Figure 5: Redundant authentication infrastructure in Azure IaaS**</span></span>

![パリ本社の Azure IaaS における冗長認証インフラストラクチャ](media/Contoso-Poster/Paris-Auth-Redun.png)
  
<span data-ttu-id="68c60-158">図 5 は、DMZ にある Web プロキシと AD FS サーバー、およびクロスプレミスの Azure 仮想ネットワークごとの追加のセットを示しています。</span><span class="sxs-lookup"><span data-stu-id="68c60-158">Figure 5 shows web proxies and AD FS servers in the DMZ and an additional set of each in a cross-premises Azure virtual network.</span></span>
  
<span data-ttu-id="68c60-p110">本社 DMZ 内の主要な認証サーバーが利用できなくなると、IT スタッフは Azure IaaS で展開されている冗長セットに切り替えます。パリのオフィスのコンピューターからの後続の認証要求は、可用性の問題が修正されるまで Azure IaaS のセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="68c60-p110">When the primary authentication servers in the headquarters DMZ become unavailable, IT staff switch over to the redundant set deployed in Azure IaaS. Subsequent authentication requests from Paris office computers use the set in Azure IaaS until the availability problem is corrected.</span></span>
  
<span data-ttu-id="68c60-161">切り替えを行うために、Contoso 社はパリ地域の Azure Traffic Manager プロファイルを更新して、Web アプリケーション プロキシに次の異なる IP アドレスのセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="68c60-161">To switch over and switch back, Contoso updates the Azure Traffic Manager profile for the Paris region to use a different set of IP addresses for the web application proxies:</span></span>
  
- <span data-ttu-id="68c60-162">DMZ 認証サーバーが使用できる場合は、DMZ のサーバーの IP アドレスを使用します。
</span><span class="sxs-lookup"><span data-stu-id="68c60-162">When the DMZ authentication servers are available, use the IP addresses of the servers in the DMZ.</span></span>
    
- <span data-ttu-id="68c60-163">DMZ 認証サーバーを使用できない場合は、Azure IaaS のサーバーの IP アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="68c60-163">When the DMZ authentication servers are not available, use the IP addresses of the servers in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="68c60-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="68c60-164">See Also</span></span>

[<span data-ttu-id="68c60-165">Microsoft Cloud の Contoso</span><span class="sxs-lookup"><span data-stu-id="68c60-165">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="68c60-166">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="68c60-166">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="68c60-167">エンタープライズ アーキテクトのための Microsoft クラウド ID</span><span class="sxs-lookup"><span data-stu-id="68c60-167">Microsoft Cloud Identity for Enterprise Architects</span></span>](http://aka.ms/cloudarchidentity)
  
[<span data-ttu-id="68c60-168">Office 365 の ID とデバイス保護</span><span class="sxs-lookup"><span data-stu-id="68c60-168">Identity and Device Protection for Office 365</span></span>](http://aka.ms/o365protect_device)
  
[<span data-ttu-id="68c60-169">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="68c60-169">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



