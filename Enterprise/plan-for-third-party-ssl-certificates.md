---
title: Office 365 のサード パーティ SSL 証明書の計画
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 概要:Exchange の社内およびハイブリッドと、AD FS、Exchange Online サービス、Exchange Web サービスを使用した SSO に必要な SSL 証明書について説明します。
ms.openlocfilehash: 3c22daa2315e36c45b5b5dd6271842168c90726d
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085326"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a><span data-ttu-id="7557b-103">Office 365 のサード パーティ SSL 証明書の計画</span><span class="sxs-lookup"><span data-stu-id="7557b-103">Plan for third-party SSL certificates for Office 365</span></span>

 <span data-ttu-id="7557b-104">**概要:** exchange の社内およびハイブリッドに必要な SSL 証明書、AD FS を使用する SSO、exchange Online サービス、および exchange Web サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7557b-104">**Summary:** Describes the SSL certificates needed for Exchange on-premises and hybrid, SSO using AD FS, Exchange Online services, and Exchange Web Services.</span></span> 
  
<span data-ttu-id="7557b-105">クライアントと Office 365 環境の間の通信を暗号化するには、サードパーティの Secure sockets Layer (SSL) 証明書をインフラストラクチャサーバーにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7557b-105">To encrypt communications between your clients and the Office 365 environment, third-party Secure Socket Layer (SSL) certificates must be installed on your infrastructure servers.</span></span>

||
|:-----|
| <span data-ttu-id="7557b-106">この記事は[、Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="7557b-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|
   
<span data-ttu-id="7557b-107">証明書は、次の Office 365 コンポーネントに必要となります。</span><span class="sxs-lookup"><span data-stu-id="7557b-107">Certificates are required for the following Office 365 components:</span></span>
  
- <span data-ttu-id="7557b-108">Exchange on-premises</span><span class="sxs-lookup"><span data-stu-id="7557b-108">Exchange on-premises</span></span>
    
- <span data-ttu-id="7557b-109">シングル サインオン (SSO) (Active Directory Federation Services (AD FS) フェデレーション サーバーと AD FS フェデレーション サーバー プロキシの両方)</span><span class="sxs-lookup"><span data-stu-id="7557b-109">Single sign-on (SSO) (for both the Active Directory Federation Services (AD FS) federation servers and AD FS federation server proxies)</span></span>
    
- <span data-ttu-id="7557b-110">exchange Online サービス (自動検出、Outlook Anywhere、exchange Web サービスなど)</span><span class="sxs-lookup"><span data-stu-id="7557b-110">Exchange Online services, such as Autodiscover, Outlook Anywhere, and Exchange Web Services</span></span>
    
- <span data-ttu-id="7557b-111">Exchange ハイブリッド サーバー</span><span class="sxs-lookup"><span data-stu-id="7557b-111">Exchange hybrid server</span></span>
    
## <a name="certificates-for-exchange-on-premises"></a><span data-ttu-id="7557b-112">Exchange On-Premises のための証明書</span><span class="sxs-lookup"><span data-stu-id="7557b-112">Certificates for Exchange On-Premises</span></span>

<span data-ttu-id="7557b-113">デジタル証明書を使用してオンプレミスの exchange 組織と exchange Online の間の通信を確立する方法の概要については、TechNet の記事「[証明書の要件につい](https://go.microsoft.com/fwlink/p/?LinkID=243657)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7557b-113">For an overview about how to use digital certificates to make the communication between the on-premises Exchange organization and Exchange Online secure, see the TechNet article [Understanding Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).</span></span>
  
## <a name="certificates-for-single-sign-on"></a><span data-ttu-id="7557b-114">シングル サインオンの証明書</span><span class="sxs-lookup"><span data-stu-id="7557b-114">Certificates for Single Sign-On</span></span>

<span data-ttu-id="7557b-p101">堅牢なセキュリティを備えたシングルサインオンのシンプルな操作性をユーザーに提供するには、フェデレーションサーバーまたはフェデレーションサーバープロキシのどちらかに、次の表に示す証明書が必要です。下の表では、Active Directory フェデレーションサービス (AD FS) について重点的に説明します。また、[サードパーティの id プロバイダーを使用する方法](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)についても詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="7557b-p101">To provide your users with a simplified single sign-on experience that includes robust security, the certificates shown in the following table are required on either the federation servers or the federation server proxies. The table below focuses on Active Directory Federation Services (AD FS), we also have more information on [using third-party identity providers](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="7557b-117">**証明書の種類**</span><span class="sxs-lookup"><span data-stu-id="7557b-117">**Certificate Type**</span></span> <br/> |<span data-ttu-id="7557b-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="7557b-118">**Description**</span></span> <br/> |<span data-ttu-id="7557b-119">**展開する前に把握しておくべき情報**</span><span class="sxs-lookup"><span data-stu-id="7557b-119">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="7557b-120">**SSL 証明書 (別名、サーバー認証証明書)**</span><span class="sxs-lookup"><span data-stu-id="7557b-120">**SSL certificate (also called a server authentication certificate)**</span></span> <br/> |<span data-ttu-id="7557b-121">これは、フェデレーション サーバー コンピューター、クライアント コンピューター、フェデレーション サーバー プロキシ コンピューター間の通信を保護するために使用される標準の SSL 証明書です。</span><span class="sxs-lookup"><span data-stu-id="7557b-121">This is a standard SSL certificate that is used to make communications between federation servers, clients, and federation server proxy computers secure.</span></span>  <br/> |<span data-ttu-id="7557b-p102">AD FS には SSL 証明書が必要です。既定では、AD FS は、インターネットインフォメーションサービス (IIS) 内の既定の web サイトに対して構成された SSL 証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="7557b-p102">AD FS requires an SSL certificate. By default, AD FS uses the SSL certificate that is configured for the default website in Internet Information Services (IIS).  </span></span><br/> <span data-ttu-id="7557b-p103">この SSL 証明書のサブジェクト名は、展開する AD FS の各インスタンスのフェデレーションサービス (fs) 名を決定するために使用されます。Office 365 に対して会社または組織の名前を最もよく表す新しい証明機関 (CA) で発行された証明書のサブジェクト名を選択することを検討してください。この名前は、インターネット経由でルーティング可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7557b-p103">The subject name of this SSL certificate is used to determine the Federation Service (FS) name for each instance of AD FS that you deploy. Consider choosing a subject name for any new certification authority (CA)-issued certificates that best represents the name of your company or organization to Office 365. This name must be Internet-routable.  </span></span><br/><span data-ttu-id="7557b-127">**注意:** AD FS では、この SSL 証明書に、ドット形式 (省略形) のサブジェクト名が含まれていないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="7557b-127">**Caution:** AD FS requires that this SSL certificate have no dotless (short-name) subject name.</span></span>          <br/> <span data-ttu-id="7557b-128">**推奨事項:** この証明書は AD FS のクライアントによって信頼される必要があるため、パブリック (サードパーティ) ca または公的に信頼されたルートに従属する ca によって発行される SSL 証明書を使用することをお勧めします。たとえば、VeriSign または Thawte のようになります。</span><span class="sxs-lookup"><span data-stu-id="7557b-128">**Recommendation:** Because this certificate must be trusted by clients of AD FS, we recommend that you use an SSL certificate issued by a public (third-party) CA or by a CA that is subordinate to a publicly trusted root; for example, VeriSign or Thawte.</span></span>  <br/> |
|<span data-ttu-id="7557b-129">**トークン署名証明書**</span><span class="sxs-lookup"><span data-stu-id="7557b-129">**Token-signing certificate**</span></span> <br/> |<span data-ttu-id="7557b-130">これは、フェデレーションサーバーが発行するすべてのトークンに安全に署名するために使用される標準の x.509 証明書で、Office 365 が受け入れて検証します。</span><span class="sxs-lookup"><span data-stu-id="7557b-130">This is a standard X.509 certificate that's used for securely signing all tokens that the federation server issues and that Office 365 accepts and validates.</span></span>  <br/> |<span data-ttu-id="7557b-p104">トークン署名証明書には、FS の信頼されたルートにチェーンする秘密キーが含まれている必要があります。既定では、AD FS は自己署名証明書を作成します。ただし、組織のニーズによっては、AD FS 管理スナップインを使用して、この証明書を CA によって発行された証明書に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="7557b-p104">The token-signing certificate must contain a private key that chains to a trusted root in the FS. By default, AD FS creates a self-signed certificate. However, depending on the needs of your organization, you can change this certificate to a CA-issued certificate by using the AD FS management snap-in.  </span></span><br/><span data-ttu-id="7557b-p105">**注意:** トークン署名証明書は、FS の安定性にとって重要です。証明書が変更された場合、Office 365 に変更を通知する必要があります。通知が提供されていない場合、ユーザーは Office 365 サービスオファーリングにサインインできません。</span><span class="sxs-lookup"><span data-stu-id="7557b-p105">**Caution:** The token-signing certificate is critical to the stability of the FS. If the certificate is changed, Office 365 must be notified of the change. If notification is not provided, users can't sign in to their Office 365 service offerings.</span></span><br/><span data-ttu-id="7557b-p106">**推奨事項:** AD FS によって生成される自己署名入りのトークン署名証明書を使用することをお勧めします。これにより、既定でこの証明書が管理されます。たとえば、この証明書が期限切れになると、AD FS は新しい自己署名証明書を生成します。</span><span class="sxs-lookup"><span data-stu-id="7557b-p106">**Recommendation:** We recommend that you use the self-signed token-signing certificate that is generated by AD FS. By doing so, it manages this certificate for you by default. For example, when this certificate is about to expire, AD FS will generate a new self-signed certificate.  </span></span><br/> |
   
<span data-ttu-id="7557b-140">フェデレーション サーバー プロキシには、次の表に示された証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="7557b-140">Federation server proxies require the certificate that is described in the following table.</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="7557b-141">**証明書の種類**</span><span class="sxs-lookup"><span data-stu-id="7557b-141">**Certificate Type**</span></span> <br/> |<span data-ttu-id="7557b-142">**説明**</span><span class="sxs-lookup"><span data-stu-id="7557b-142">**Description**</span></span> <br/> |<span data-ttu-id="7557b-143">**展開する前に把握しておくべき情報**</span><span class="sxs-lookup"><span data-stu-id="7557b-143">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="7557b-144">SSL 証明書</span><span class="sxs-lookup"><span data-stu-id="7557b-144">SSL certificate</span></span>  <br/> |<span data-ttu-id="7557b-145">これは、フェデレーション サーバー コンピューター、フェデレーション サーバー プロキシ コンピューター、およびインターネット接続コンピューター間の通信を保護するために使用される標準の SSL 証明書です。</span><span class="sxs-lookup"><span data-stu-id="7557b-145">This is a standard SSL certificate that is used for securing communications between a federation server, a federation server proxy, and Internet client computers.</span></span>  <br/> |<span data-ttu-id="7557b-146">AD FS フェデレーションサーバープロキシ構成ウィザードを正常に実行するには、この SSL 証明書を IIS の既定の web サイトにバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7557b-146">This SSL certificate must be bound to the default website in IIS before you can successfully run the AD FS Federation Server Proxy Configuration wizard.</span></span>  <br/> <span data-ttu-id="7557b-147">この証明書には、企業ネットワーク内のフェデレーション サーバーに構成された SSL 証明書と同じ件名を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="7557b-147">This certificate must have the same subject name as the SSL certificate that was configured on the federation server in the corporate network.</span></span>  <br/> <span data-ttu-id="7557b-148">**推奨事項:** このフェデレーション サーバー プロキシが接続されているフェデレーション サーバーに構成されているのと同じサーバー認証証明書を使うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7557b-148">**Recommendation:** We recommend that you use the same server authentication certificate that is configured on the federation server that this federation server proxy connects to.</span></span>  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a><span data-ttu-id="7557b-149">自動検出、Outlook Anywhere、および Active Directory 同期の証明書</span><span class="sxs-lookup"><span data-stu-id="7557b-149">Certificates for Autodiscover, Outlook Anywhere, and Active Directory Synchronization</span></span>

<span data-ttu-id="7557b-p107">外部に接続された exchange 2013、exchange 2010、exchange 2007、および exchange 2003 クライアントアクセスサーバー (cass) には、自動検出、Outlook Anywhere、および Active Directory 同期サービスのために、サードパーティの SSL 証明書が必要です。この証明書は、オンプレミス環境に既にインストールされている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7557b-p107">Your external-facing Exchange 2013, Exchange 2010, Exchange 2007, and Exchange 2003 Client Access servers (CASs) require a third-party SSL certificate for secure connections for Autodiscover, Outlook Anywhere, and Active Directory synchronization services. You may already have this certificate installed in your on-premises environment.</span></span>
  
## <a name="certificate-for-an-exchange-hybrid-server"></a><span data-ttu-id="7557b-152">Exchange ハイブリッド サーバーの証明書</span><span class="sxs-lookup"><span data-stu-id="7557b-152">Certificate for an Exchange Hybrid Server</span></span>

<span data-ttu-id="7557b-p108">外部に接続された exchange ハイブリッドサーバーでは、exchange Online サービスとの接続をセキュリティで保護するために、サードパーティの SSL 証明書が必要です。この証明書は、サードパーティの SSL プロバイダーから入手する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7557b-p108">Your external-facing Exchange hybrid server or servers require a third-party SSL certificate for secure connectivity with the Exchange Online service. You need to get this certificate from your third-party SSL provider.</span></span>
  
## <a name="office-365-certificate-chains"></a><span data-ttu-id="7557b-155">Office 365 証明書チェーン</span><span class="sxs-lookup"><span data-stu-id="7557b-155">Office 365 Certificate Chains</span></span>

<span data-ttu-id="7557b-p109">この記事では、インフラストラクチャにインストールする必要がある証明書について説明します。office 365 サーバーにインストールされている証明書の詳細については、「 [office 365 証明書チェーン](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7557b-p109">This article describes the certificates you may need to install on your infrastructure. For more information on the certificates installed on our Office 365 servers, see [Office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).</span></span>
  

