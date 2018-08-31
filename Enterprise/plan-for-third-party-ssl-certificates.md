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
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 概要:Exchange の社内およびハイブリッドと、AD FS、Exchange Online サービス、Exchange Web サービスを使用した SSO に必要な SSL 証明書について説明します。
ms.openlocfilehash: 5092734c66f39583d32d4cd9f926e76ed794668b
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223019"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a><span data-ttu-id="b522c-103">Office 365 のサード パーティ SSL 証明書の計画</span><span class="sxs-lookup"><span data-stu-id="b522c-103">Plan for third-party SSL certificates for Office 365</span></span>

 <span data-ttu-id="b522c-104">**の概要:** Exchange の設置型とハイブリッドに、AD FS を使用して SSO に必要な SSL 証明書を説明し、Exchange のオンライン サービスは、Exchange Web サービス。</span><span class="sxs-lookup"><span data-stu-id="b522c-104">**Summary:** Describes the SSL certificates needed for Exchange on-premises and hybrid, SSO using AD FS, Exchange Online services, and Exchange Web Services.</span></span> 
  
<span data-ttu-id="b522c-105">クライアントと前の 365Office 365 環境間の通信を暗号化するには、インフラストラクチャ サーバーのサード ・ パーティ製のセキュア ソケット レイヤー (SSL) 証明書をインストールしなければなりません。</span><span class="sxs-lookup"><span data-stu-id="b522c-105">To encrypt communications between your clients and theOffice 365Office 365 environment, third-party Secure Socket Layer (SSL) certificates must be installed on your infrastructure servers.</span></span>

||
|:-----|
| <span data-ttu-id="b522c-106">この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)の一部です。</span><span class="sxs-lookup"><span data-stu-id="b522c-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|
   
<span data-ttu-id="b522c-107">証明書は、次の Office 365 コンポーネントに必要となります。</span><span class="sxs-lookup"><span data-stu-id="b522c-107">Certificates are required for the following Office 365 components:</span></span>
  
- <span data-ttu-id="b522c-108">Exchange on-premises</span><span class="sxs-lookup"><span data-stu-id="b522c-108">Exchange on-premises</span></span>
    
- <span data-ttu-id="b522c-109">シングル サインオン (SSO) (Active Directory Federation Services (AD FS) フェデレーション サーバーと AD FS フェデレーション サーバー プロキシの両方)</span><span class="sxs-lookup"><span data-stu-id="b522c-109">Single sign-on (SSO) (for both the Active Directory Federation Services (AD FS) federation servers and AD FS federation server proxies)</span></span>
    
- <span data-ttu-id="b522c-110">自動検出、Outlook Anywhere では、Exchange Web サービスなどの Exchange のオンライン サービス</span><span class="sxs-lookup"><span data-stu-id="b522c-110">Exchange Online services, such as Autodiscover, Outlook Anywhere, and Exchange Web Services</span></span>
    
- <span data-ttu-id="b522c-111">Exchange ハイブリッド サーバー</span><span class="sxs-lookup"><span data-stu-id="b522c-111">Exchange hybrid server</span></span>
    
## <a name="certificates-for-exchange-on-premises"></a><span data-ttu-id="b522c-112">Exchange On-Premises のための証明書</span><span class="sxs-lookup"><span data-stu-id="b522c-112">Certificates for Exchange On-Premises</span></span>

<span data-ttu-id="b522c-113">TechNet の記事「[証明書要件について](https://go.microsoft.com/fwlink/p/?LinkID=243657)を参照してくださいくださいオンプレミスの Exchange 組織と Exchange Online との間の通信をセキュリティで保護されたデジタル証明書を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b522c-113">For an overview about how to use digital certificates to make the communication between the on-premises Exchange organization and Exchange Online secure, see the TechNet article [Understanding Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).</span></span>
  
## <a name="certificates-for-single-sign-on"></a><span data-ttu-id="b522c-114">シングル サインオンの証明書</span><span class="sxs-lookup"><span data-stu-id="b522c-114">Certificates for Single Sign-On</span></span>

<span data-ttu-id="b522c-p101">ユーザーに提供する、シンプルなシングル サインオン エクスペリエンスを堅牢なセキュリティが含まれていますが、次の表に示すように証明書が、フェデレーション サーバーまたはフェデレーション サーバー プロキシのいずれかの必要があります。次の表は、Active Directory フェデレーション サービス (AD FS) に焦点を当てています、[サードパーティの id プロバイダーを使用する方法](https://go.microsoft.com/fwlink/?LinkId=532869)についてもあります。</span><span class="sxs-lookup"><span data-stu-id="b522c-p101">To provide your users with a simplified single sign-on experience that includes robust security, the certificates shown in the following table are required on either the federation servers or the federation server proxies. The table below focuses on Active Directory Federation Services (AD FS), we also have more information on [using third-party identity providers](https://go.microsoft.com/fwlink/?LinkId=532869).</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="b522c-117">**証明書の種類**</span><span class="sxs-lookup"><span data-stu-id="b522c-117">**Certificate Type**</span></span> <br/> |<span data-ttu-id="b522c-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="b522c-118">**Description**</span></span> <br/> |<span data-ttu-id="b522c-119">**展開する前に把握しておくべき情報**</span><span class="sxs-lookup"><span data-stu-id="b522c-119">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="b522c-120">**SSL 証明書 (別名、サーバー認証証明書)**</span><span class="sxs-lookup"><span data-stu-id="b522c-120">**SSL certificate (also called a server authentication certificate)**</span></span> <br/> |<span data-ttu-id="b522c-121">これは、フェデレーション サーバー コンピューター、クライアント コンピューター、フェデレーション サーバー プロキシ コンピューター間の通信を保護するために使用される標準の SSL 証明書です。</span><span class="sxs-lookup"><span data-stu-id="b522c-121">This is a standard SSL certificate that is used to make communications between federation servers, clients, and federation server proxy computers secure.</span></span>  <br/> |<span data-ttu-id="b522c-p102">AD FS では、SSL 証明書が必要です。既定では、AD FS は、インターネット インフォメーション サービス (IIS) で既定の web サイトの構成されている SSL 証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="b522c-p102">AD FS requires an SSL certificate. By default, AD FS uses the SSL certificate that is configured for the default website in Internet Information Services (IIS).  </span></span><br/> <span data-ttu-id="b522c-p103">この SSL 証明書のサブジェクト名は、フェデレーション サービス (FS) の名前を展開する AD FS の各インスタンスを決定する使用されます。あらゆる新しい証明機関 (CA) のサブジェクト名を選択することを検討してください-ベストが、会社や組織が Office 365 の名前を表すことの証明書を発行します。この名前は、インターネット ルーティング可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b522c-p103">The subject name of this SSL certificate is used to determine the Federation Service (FS) name for each instance of AD FS that you deploy. Consider choosing a subject name for any new certification authority (CA)-issued certificates that best represents the name of your company or organization to Office 365. This name must be Internet-routable.  </span></span><br/><span data-ttu-id="b522c-127">**注意:** AD FS では、この SSL 証明書があるないドットなしの (短い名前) サブジェクト名が必要です。</span><span class="sxs-lookup"><span data-stu-id="b522c-127">**Caution:** AD FS requires that this SSL certificate have no dotless (short-name) subject name.</span></span>          </br> <span data-ttu-id="b522c-128">**推奨値:** パブリック (サード パーティの) CA またはを公的に信頼されたルートの下位の CA によって発行された SSL 証明書を使用することをお勧めため、この証明書は、AD FS のクライアントによって信頼されている必要があります、たとえば、VeriSign や Thawte などです。</span><span class="sxs-lookup"><span data-stu-id="b522c-128">**Recommendation:** Because this certificate must be trusted by clients of AD FS, we recommend that you use an SSL certificate issued by a public (third-party) CA or by a CA that is subordinate to a publicly trusted root; for example, VeriSign or Thawte.</span></span>  <br/> |
|<span data-ttu-id="b522c-129">**トークン署名証明書**</span><span class="sxs-lookup"><span data-stu-id="b522c-129">**Token-signing certificate**</span></span> <br/> |<span data-ttu-id="b522c-130">これは、フェデレーション サーバーの問題と、Office 365 を受け入れるし、検証するすべてのトークンに安全に署名するために使用される標準的な X.509 証明書です。</span><span class="sxs-lookup"><span data-stu-id="b522c-130">This is a standard X.509 certificate that's used for securely signing all tokens that the federation server issues and that Office 365 accepts and validates.</span></span>  <br/> |<span data-ttu-id="b522c-p104">トークン署名証明書には、FS 内の信頼されたルートにチェーンする秘密キーを含める必要があります。既定では、AD FS は、自己署名証明書を作成します。ただし、組織のニーズに応じて変更できますこの証明書 CA が発行した証明書を AD FS の管理スナップインを使用しています。</span><span class="sxs-lookup"><span data-stu-id="b522c-p104">The token-signing certificate must contain a private key that chains to a trusted root in the FS. By default, AD FS creates a self-signed certificate. However, depending on the needs of your organization, you can change this certificate to a CA-issued certificate by using the AD FS management snap-in.  </span></span><br/><span data-ttu-id="b522c-p105">**注意:** トークン署名証明書は、FS の安定性に不可欠です。証明書を変更すると、Office 365 が変更を通知する必要があります。通知が指定されていない場合、ユーザーは、Office 365 サービスにサインインできません。</span><span class="sxs-lookup"><span data-stu-id="b522c-p105">**Caution:** The token-signing certificate is critical to the stability of the FS. If the certificate is changed, Office 365 must be notified of the change. If notification is not provided, users can't sign in to their Office 365 service offerings.</span></span></br><span data-ttu-id="b522c-p106">**推奨値:** AD FS によって生成された自己署名のトークン署名証明を使用することをお勧めします。これによって、既定の証明書を管理します。たとえば、この証明書は有効期限が、AD FS は新しい自己署名証明書を生成します。</span><span class="sxs-lookup"><span data-stu-id="b522c-p106">**Recommendation:** We recommend that you use the self-signed token-signing certificate that is generated by AD FS. By doing so, it manages this certificate for you by default. For example, when this certificate is about to expire, AD FS will generate a new self-signed certificate.  </span></span><br/> |
   
<span data-ttu-id="b522c-140">フェデレーション サーバー プロキシには、次の表に示された証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="b522c-140">Federation server proxies require the certificate that is described in the following table.</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="b522c-141">**証明書の種類**</span><span class="sxs-lookup"><span data-stu-id="b522c-141">**Certificate Type**</span></span> <br/> |<span data-ttu-id="b522c-142">**説明**</span><span class="sxs-lookup"><span data-stu-id="b522c-142">**Description**</span></span> <br/> |<span data-ttu-id="b522c-143">**展開する前に把握しておくべき情報**</span><span class="sxs-lookup"><span data-stu-id="b522c-143">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="b522c-144">SSL 証明書</span><span class="sxs-lookup"><span data-stu-id="b522c-144">SSL certificate</span></span>  <br/> |<span data-ttu-id="b522c-145">これは、フェデレーション サーバー コンピューター、フェデレーション サーバー プロキシ コンピューター、およびインターネット接続コンピューター間の通信を保護するために使用される標準の SSL 証明書です。</span><span class="sxs-lookup"><span data-stu-id="b522c-145">This is a standard SSL certificate that is used for securing communications between a federation server, a federation server proxy, and Internet client computers.</span></span>  <br/> |<span data-ttu-id="b522c-146">AD FS フェデレーション サーバー プロキシの構成ウィザードを正常に実行する前に、この SSL 証明書を IIS で既定の web サイトにバインドしてください。</span><span class="sxs-lookup"><span data-stu-id="b522c-146">This SSL certificate must be bound to the default website in IIS before you can successfully run the AD FS Federation Server Proxy Configuration wizard.</span></span>  <br/> <span data-ttu-id="b522c-147">この証明書には、企業ネットワーク内のフェデレーション サーバーに構成された SSL 証明書と同じ件名を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="b522c-147">This certificate must have the same subject name as the SSL certificate that was configured on the federation server in the corporate network.</span></span>  <br/> <span data-ttu-id="b522c-148">**推奨事項:** このフェデレーション サーバー プロキシが接続されているフェデレーション サーバーに構成されているのと同じサーバー認証証明書を使うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b522c-148">**Recommendation:** We recommend that you use the same server authentication certificate that is configured on the federation server that this federation server proxy connects to.</span></span>  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a><span data-ttu-id="b522c-149">証明書を自動検出、Outlook の任意の場所、および Active Directory の同期</span><span class="sxs-lookup"><span data-stu-id="b522c-149">Certificates for Autodiscover, Outlook Anywhere, and Active Directory Synchronization</span></span>

<span data-ttu-id="b522c-p107">外部に接続する Exchange 2013、Exchange 2010、Exchange 2007 および Exchange 2003 クライアント アクセス サーバー (CASs) では、セキュリティで保護された接続の自動検出、Outlook Anywhere および Active Directory の同期サービスのサード パーティの SSL 証明書が必要です。オンプレミス環境にインストールされているこの証明書が既にあります。</span><span class="sxs-lookup"><span data-stu-id="b522c-p107">Your external-facing Exchange 2013, Exchange 2010, Exchange 2007, and Exchange 2003 Client Access servers (CASs) require a third-party SSL certificate for secure connections for Autodiscover, Outlook Anywhere, and Active Directory synchronization services. You may already have this certificate installed in your on-premises environment.</span></span>
  
## <a name="certificate-for-an-exchange-hybrid-server"></a><span data-ttu-id="b522c-152">Exchange ハイブリッド サーバーの証明書</span><span class="sxs-lookup"><span data-stu-id="b522c-152">Certificate for an Exchange Hybrid Server</span></span>

<span data-ttu-id="b522c-p108">外部に接続する Exchange ハイブリッド サーバーまたはサーバーは、Exchange のオンライン サービスとセキュリティで保護された接続のサードパーティの SSL 証明書を必要とします。サードパーティの SSL プロバイダーからこの証明書を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b522c-p108">Your external-facing Exchange hybrid server or servers require a third-party SSL certificate for secure connectivity with the Exchange Online service. You need to get this certificate from your third-party SSL provider.</span></span>
  
## <a name="office-365-certificate-chains"></a><span data-ttu-id="b522c-155">Office 365 の証明書チェーン</span><span class="sxs-lookup"><span data-stu-id="b522c-155">Office 365 Certificate Chains</span></span>

<span data-ttu-id="b522c-p109">この資料では、お客様のインフラストラクチャにインストールする必要があります証明書を説明します。Office 365 サーバーにインストールされている証明書の詳細については、 [Office 365 の証明書チェーン](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b522c-p109">This article describes the certificates you may need to install on your infrastructure. For more information on the certificates installed on our Office 365 servers, see [Office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).</span></span>
  

