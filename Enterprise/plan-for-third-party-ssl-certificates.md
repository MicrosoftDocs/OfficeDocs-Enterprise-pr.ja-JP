---
title: Office 365 のサード パーティ SSL 証明書の計画
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: '概要: Exchange の社内およびハイブリッドに必要な SSL 証明書、AD FS を使用する SSO、Exchange Online サービス、および Exchange Web サービスについて説明します。'
ms.openlocfilehash: a28acae142f97a52f7c6db8e5a7d93049b2876cc
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841733"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a><span data-ttu-id="fbb09-103">Office 365 のサード パーティ SSL 証明書の計画</span><span class="sxs-lookup"><span data-stu-id="fbb09-103">Plan for third-party SSL certificates for Office 365</span></span>

<span data-ttu-id="fbb09-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="fbb09-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="fbb09-105">クライアントと Office 365 環境の間の通信を暗号化するには、サードパーティの Secure Sockets Layer (SSL) 証明書をインフラストラクチャサーバーにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbb09-105">To encrypt communications between your clients and the Office 365 environment, third-party Secure Socket Layer (SSL) certificates must be installed on your infrastructure servers.</span></span>

||
|:-----|
| <span data-ttu-id="fbb09-106">この記事は[、Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="fbb09-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|
   
<span data-ttu-id="fbb09-107">次の Office 365 コンポーネントには、証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="fbb09-107">Certificates are required for the following Office 365 components:</span></span>
  
- <span data-ttu-id="fbb09-108">オンプレミスの Exchange</span><span class="sxs-lookup"><span data-stu-id="fbb09-108">Exchange on-premises</span></span>
    
- <span data-ttu-id="fbb09-109">シングルサインオン (SSO) (Active Directory フェデレーションサービス (AD FS) フェデレーションサーバーと AD FS フェデレーションサーバープロキシの両方)</span><span class="sxs-lookup"><span data-stu-id="fbb09-109">Single sign-on (SSO) (for both the Active Directory Federation Services (AD FS) federation servers and AD FS federation server proxies)</span></span>
    
- <span data-ttu-id="fbb09-110">Exchange Online サービス (自動検出、Outlook Anywhere、Exchange Web サービスなど)</span><span class="sxs-lookup"><span data-stu-id="fbb09-110">Exchange Online services, such as Autodiscover, Outlook Anywhere, and Exchange Web Services</span></span>
    
- <span data-ttu-id="fbb09-111">Exchange ハイブリッドサーバー</span><span class="sxs-lookup"><span data-stu-id="fbb09-111">Exchange hybrid server</span></span>
    
## <a name="certificates-for-exchange-on-premises"></a><span data-ttu-id="fbb09-112">オンプレミスの Exchange の証明書</span><span class="sxs-lookup"><span data-stu-id="fbb09-112">Certificates for Exchange On-Premises</span></span>

<span data-ttu-id="fbb09-113">デジタル証明書を使用してオンプレミスの Exchange 組織と Exchange Online の間の通信を確立する方法の概要については、TechNet の記事「[証明書の要件につい](https://go.microsoft.com/fwlink/p/?LinkID=243657)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbb09-113">For an overview about how to use digital certificates to make the communication between the on-premises Exchange organization and Exchange Online secure, see the TechNet article [Understanding Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).</span></span>
  
## <a name="certificates-for-single-sign-on"></a><span data-ttu-id="fbb09-114">シングルサインオンの証明書</span><span class="sxs-lookup"><span data-stu-id="fbb09-114">Certificates for Single Sign-On</span></span>

<span data-ttu-id="fbb09-115">堅牢なセキュリティを備えたシングルサインオンのシンプルな操作性をユーザーに提供するには、フェデレーションサーバーまたはフェデレーションサーバープロキシのどちらかに、次の表に示す証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="fbb09-115">To provide your users with a simplified single sign-on experience that includes robust security, the certificates shown in the following table are required on either the federation servers or the federation server proxies.</span></span> <span data-ttu-id="fbb09-116">下の表では、Active Directory フェデレーションサービス (AD FS) について重点的に説明します。また、[サードパーティの id プロバイダーを使用する方法](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)についても詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="fbb09-116">The table below focuses on Active Directory Federation Services (AD FS), we also have more information on [using third-party identity providers](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="fbb09-117">**証明書の種類**</span><span class="sxs-lookup"><span data-stu-id="fbb09-117">**Certificate Type**</span></span> <br/> |<span data-ttu-id="fbb09-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="fbb09-118">**Description**</span></span> <br/> |<span data-ttu-id="fbb09-119">**を展開する前に把握しておくべき情報**</span><span class="sxs-lookup"><span data-stu-id="fbb09-119">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="fbb09-120">**SSL 証明書 (サーバー認証証明書とも呼ばれる)**</span><span class="sxs-lookup"><span data-stu-id="fbb09-120">**SSL certificate (also called a server authentication certificate)**</span></span> <br/> |<span data-ttu-id="fbb09-121">これは、フェデレーションサーバー、クライアント、およびフェデレーションサーバープロキシコンピューター間の通信をセキュリティで保護するために使用される標準の SSL 証明書です。</span><span class="sxs-lookup"><span data-stu-id="fbb09-121">This is a standard SSL certificate that is used to make communications between federation servers, clients, and federation server proxy computers secure.</span></span>  <br/> |<span data-ttu-id="fbb09-122">AD FS には SSL 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="fbb09-122">AD FS requires an SSL certificate.</span></span> <span data-ttu-id="fbb09-123">既定では、AD FS は、インターネットインフォメーションサービス (IIS) 内の既定の web サイトに対して構成された SSL 証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="fbb09-123">By default, AD FS uses the SSL certificate that is configured for the default website in Internet Information Services (IIS).</span></span>  <br/> <span data-ttu-id="fbb09-124">この SSL 証明書のサブジェクト名は、展開する AD FS の各インスタンスのフェデレーションサービス (FS) 名を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb09-124">The subject name of this SSL certificate is used to determine the Federation Service (FS) name for each instance of AD FS that you deploy.</span></span> <span data-ttu-id="fbb09-125">Office 365 に対して会社または組織の名前を最もよく表す新しい証明機関 (CA) で発行された証明書のサブジェクト名を選択することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="fbb09-125">Consider choosing a subject name for any new certification authority (CA)-issued certificates that best represents the name of your company or organization to Office 365.</span></span> <span data-ttu-id="fbb09-126">この名前は、インターネット経由でルーティング可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbb09-126">This name must be Internet-routable.</span></span>  <br/><span data-ttu-id="fbb09-127">**注意:** AD FS では、この SSL 証明書に、ドット形式 (省略形) のサブジェクト名が含まれていないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="fbb09-127">**Caution:** AD FS requires that this SSL certificate have no dotless (short-name) subject name.</span></span>          <br/> <span data-ttu-id="fbb09-128">**推奨事項:** この証明書は AD FS のクライアントによって信頼される必要があるため、パブリック (サードパーティ) CA または公的に信頼されたルートに従属する CA によって発行される SSL 証明書を使用することをお勧めします。たとえば、VeriSign または Thawte のようになります。</span><span class="sxs-lookup"><span data-stu-id="fbb09-128">**Recommendation:** Because this certificate must be trusted by clients of AD FS, we recommend that you use an SSL certificate issued by a public (third-party) CA or by a CA that is subordinate to a publicly trusted root; for example, VeriSign or Thawte.</span></span>  <br/> |
|<span data-ttu-id="fbb09-129">**トークン署名証明書**</span><span class="sxs-lookup"><span data-stu-id="fbb09-129">**Token-signing certificate**</span></span> <br/> |<span data-ttu-id="fbb09-130">これは、フェデレーションサーバーが発行するすべてのトークンに安全に署名するために使用される標準の x.509 証明書で、Office 365 が受け入れて検証します。</span><span class="sxs-lookup"><span data-stu-id="fbb09-130">This is a standard X.509 certificate that's used for securely signing all tokens that the federation server issues and that Office 365 accepts and validates.</span></span>  <br/> |<span data-ttu-id="fbb09-131">トークン署名証明書には、FS の信頼されたルートにチェーンする秘密キーが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbb09-131">The token-signing certificate must contain a private key that chains to a trusted root in the FS.</span></span> <span data-ttu-id="fbb09-132">既定では、AD FS は自己署名証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="fbb09-132">By default, AD FS creates a self-signed certificate.</span></span> <span data-ttu-id="fbb09-133">ただし、組織のニーズによっては、AD FS 管理スナップインを使用して、この証明書を CA によって発行された証明書に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="fbb09-133">However, depending on the needs of your organization, you can change this certificate to a CA-issued certificate by using the AD FS management snap-in.</span></span>  <br/><span data-ttu-id="fbb09-134">**注意:** トークン署名証明書は、FS の安定性にとって重要です。</span><span class="sxs-lookup"><span data-stu-id="fbb09-134">**Caution:** The token-signing certificate is critical to the stability of the FS.</span></span> <span data-ttu-id="fbb09-135">証明書が変更された場合、Office 365 に変更を通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbb09-135">If the certificate is changed, Office 365 must be notified of the change.</span></span> <span data-ttu-id="fbb09-136">通知が提供されていない場合、ユーザーは Office 365 サービスオファーリングにサインインできません。</span><span class="sxs-lookup"><span data-stu-id="fbb09-136">If notification is not provided, users can't sign in to their Office 365 service offerings.</span></span><br/><span data-ttu-id="fbb09-137">**推奨事項:** AD FS によって生成される自己署名入りのトークン署名証明書を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fbb09-137">**Recommendation:** We recommend that you use the self-signed token-signing certificate that is generated by AD FS.</span></span> <span data-ttu-id="fbb09-138">これにより、既定でこの証明書が管理されます。</span><span class="sxs-lookup"><span data-stu-id="fbb09-138">By doing so, it manages this certificate for you by default.</span></span> <span data-ttu-id="fbb09-139">たとえば、この証明書が期限切れになると、AD FS は新しい自己署名証明書を生成します。</span><span class="sxs-lookup"><span data-stu-id="fbb09-139">For example, when this certificate is about to expire, AD FS will generate a new self-signed certificate.</span></span>  <br/> |
   
<span data-ttu-id="fbb09-140">フェデレーションサーバープロキシには、次の表に記載されている証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="fbb09-140">Federation server proxies require the certificate that is described in the following table.</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="fbb09-141">**証明書の種類**</span><span class="sxs-lookup"><span data-stu-id="fbb09-141">**Certificate Type**</span></span> <br/> |<span data-ttu-id="fbb09-142">**説明**</span><span class="sxs-lookup"><span data-stu-id="fbb09-142">**Description**</span></span> <br/> |<span data-ttu-id="fbb09-143">**を展開する前に把握しておくべき情報**</span><span class="sxs-lookup"><span data-stu-id="fbb09-143">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="fbb09-144">SSL 証明書</span><span class="sxs-lookup"><span data-stu-id="fbb09-144">SSL certificate</span></span>  <br/> |<span data-ttu-id="fbb09-145">これは、フェデレーションサーバー、フェデレーションサーバープロキシ、およびインターネットクライアントコンピューター間の通信をセキュリティで保護するために使用される標準の SSL 証明書です。</span><span class="sxs-lookup"><span data-stu-id="fbb09-145">This is a standard SSL certificate that is used for securing communications between a federation server, a federation server proxy, and Internet client computers.</span></span>  <br/> |<span data-ttu-id="fbb09-146">AD FS フェデレーションサーバープロキシ構成ウィザードを正常に実行するには、この SSL 証明書を IIS の既定の web サイトにバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbb09-146">This SSL certificate must be bound to the default website in IIS before you can successfully run the AD FS Federation Server Proxy Configuration wizard.</span></span>  <br/> <span data-ttu-id="fbb09-147">この証明書のサブジェクト名は、企業ネットワークのフェデレーションサーバーで構成された SSL 証明書と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbb09-147">This certificate must have the same subject name as the SSL certificate that was configured on the federation server in the corporate network.</span></span>  <br/> <span data-ttu-id="fbb09-148">**推奨事項:** このフェデレーションサーバープロキシが接続するフェデレーションサーバーで構成されているのと同じサーバー認証証明書を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fbb09-148">**Recommendation:** We recommend that you use the same server authentication certificate that is configured on the federation server that this federation server proxy connects to.</span></span>  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a><span data-ttu-id="fbb09-149">自動検出、Outlook Anywhere、および Active Directory 同期の証明書</span><span class="sxs-lookup"><span data-stu-id="fbb09-149">Certificates for Autodiscover, Outlook Anywhere, and Active Directory Synchronization</span></span>

<span data-ttu-id="fbb09-150">外部に接続された Exchange 2013、Exchange 2010、Exchange 2007、および Exchange 2003 クライアントアクセスサーバー (CASs) には、自動検出、Outlook Anywhere、および Active Directory 同期サービスのために、サードパーティの SSL 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="fbb09-150">Your external-facing Exchange 2013, Exchange 2010, Exchange 2007, and Exchange 2003 Client Access servers (CASs) require a third-party SSL certificate for secure connections for Autodiscover, Outlook Anywhere, and Active Directory synchronization services.</span></span> <span data-ttu-id="fbb09-151">この証明書は、オンプレミス環境に既にインストールされている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fbb09-151">You may already have this certificate installed in your on-premises environment.</span></span>
  
## <a name="certificate-for-an-exchange-hybrid-server"></a><span data-ttu-id="fbb09-152">Exchange ハイブリッドサーバーの証明書</span><span class="sxs-lookup"><span data-stu-id="fbb09-152">Certificate for an Exchange Hybrid Server</span></span>

<span data-ttu-id="fbb09-153">外部に接続された Exchange ハイブリッドサーバーでは、Exchange Online サービスとの接続をセキュリティで保護するために、サードパーティの SSL 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="fbb09-153">Your external-facing Exchange hybrid server or servers require a third-party SSL certificate for secure connectivity with the Exchange Online service.</span></span> <span data-ttu-id="fbb09-154">この証明書は、サードパーティの SSL プロバイダーから入手する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbb09-154">You need to get this certificate from your third-party SSL provider.</span></span>
  
## <a name="office-365-certificate-chains"></a><span data-ttu-id="fbb09-155">Office 365 証明書チェーン</span><span class="sxs-lookup"><span data-stu-id="fbb09-155">Office 365 Certificate Chains</span></span>

<span data-ttu-id="fbb09-156">この記事では、インフラストラクチャにインストールする必要がある証明書について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbb09-156">This article describes the certificates you may need to install on your infrastructure.</span></span> <span data-ttu-id="fbb09-157">Office 365 サーバーにインストールされている証明書の詳細については、「 [office 365 証明書チェーン](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbb09-157">For more information on the certificates installed on our Office 365 servers, see [Office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fbb09-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbb09-158">See also</span></span>

[<span data-ttu-id="fbb09-159">Microsoft 365 Enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="fbb09-159">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
