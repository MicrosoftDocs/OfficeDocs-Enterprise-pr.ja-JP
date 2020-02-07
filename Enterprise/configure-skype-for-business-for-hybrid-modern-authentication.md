---
title: Skype for Business をオンプレミスで構成して、ハイブリッド先進認証を使用するには
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: 先進認証は、ユーザーの認証と承認をさらに強力に提供する id 管理の方法であり、オンプレミスの Skype for Business server とオンプレミスの Exchange server、およびスプリットドメイン Skype for Business ハイブリッドで利用できます。
ms.openlocfilehash: de5063da9eed03e2cd455b79b3a2d1c2f671ad1e
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840724"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="13e5b-103">Skype for Business をオンプレミスで構成して、ハイブリッド先進認証を使用するには</span><span class="sxs-lookup"><span data-stu-id="13e5b-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="13e5b-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="13e5b-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="13e5b-105">先進認証は、ユーザーの認証と承認をさらに強力に提供する id 管理の方法であり、オンプレミスの Skype for Business server とオンプレミスの Exchange server、およびスプリットドメイン Skype for Business ハイブリッドで利用できます。</span><span class="sxs-lookup"><span data-stu-id="13e5b-105">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="13e5b-106">**重要**モダン認証 (MA) の詳細と、会社や組織での使用を希望する理由は何ですか。</span><span class="sxs-lookup"><span data-stu-id="13e5b-106">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="13e5b-107">概要については、[このドキュメント](hybrid-modern-auth-overview.md)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="13e5b-107">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="13e5b-108">MA でサポートされている Skype for Business のトポロジについて知る必要がある場合は、ここで説明します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-108">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span>
  
 <span data-ttu-id="13e5b-109">**開始する前に**、次のように呼び出します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-109">**Before we begin**, I call:</span></span>
  
- <span data-ttu-id="13e5b-110">モダン認証\> MA</span><span class="sxs-lookup"><span data-stu-id="13e5b-110">Modern Authentication \> MA</span></span>

- <span data-ttu-id="13e5b-111">ハイブリッド先進認証\>の HMA</span><span class="sxs-lookup"><span data-stu-id="13e5b-111">Hybrid Modern Authentication \> HMA</span></span>

- <span data-ttu-id="13e5b-112">Exchange オンプレミス\>の EXCH</span><span class="sxs-lookup"><span data-stu-id="13e5b-112">Exchange on-premises \> EXCH</span></span>

- <span data-ttu-id="13e5b-113">Exchange Online \> exo</span><span class="sxs-lookup"><span data-stu-id="13e5b-113">Exchange Online \> EXO</span></span>

- <span data-ttu-id="13e5b-114">Skype for Business オンプレミス\>の sfb</span><span class="sxs-lookup"><span data-stu-id="13e5b-114">Skype for Business on-premises \> SFB</span></span>

- <span data-ttu-id="13e5b-115">と Skype for Business Online \> sfbo</span><span class="sxs-lookup"><span data-stu-id="13e5b-115">and Skype for Business Online \> SFBO</span></span>

<span data-ttu-id="13e5b-116">また、この記事のグラフィックに淡色表示されるオブジェクトが含まれている場合は、グレーの要素が MA 固有の構成に含まれて**いない**ことを意味します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-116">Also, if a graphic in this article has an object that's greyed-out or dimmed that means the element shown in gray **is not** included in MA-specific configuration.</span></span>
  
## <a name="read-the-summary"></a><span data-ttu-id="13e5b-117">概要の読み取り</span><span class="sxs-lookup"><span data-stu-id="13e5b-117">Read the summary</span></span>

<span data-ttu-id="13e5b-118">この概要では、実行中に失われる可能性のある手順にプロセスを分解します。また、プロセスのどこで作業しているかを全体的なチェックリストに記録することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13e5b-118">This summary breaks down the process into steps that might otherwise get lost during the execution, and is good for an overall checklist to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="13e5b-119">最初に、すべての前提条件を満たしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="13e5b-119">First, make sure you meet all the prerequisites.</span></span>

1. <span data-ttu-id="13e5b-120">Skype for Business と Exchange の両方に共通の**前提条件**が多数存在するため、[事前要件チェックリストの概要記事を参照してください](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="13e5b-120">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="13e5b-121">この手順を実行する*前*に、この記事の手順を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13e5b-121">Do this  *before*  you begin any of the steps in this article.</span></span>

1. <span data-ttu-id="13e5b-122">ファイルまたは OneNote で必要な HMA 固有の情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-122">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>

1. <span data-ttu-id="13e5b-123">EXO のモダン認証を有効にします (まだ有効になっていない場合)。</span><span class="sxs-lookup"><span data-stu-id="13e5b-123">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>

1. <span data-ttu-id="13e5b-124">SFBO の先進認証を有効にします (まだ有効になっていない場合)。</span><span class="sxs-lookup"><span data-stu-id="13e5b-124">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>

1. <span data-ttu-id="13e5b-125">Exchange on-premises のハイブリッド先進認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="13e5b-125">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>

1. <span data-ttu-id="13e5b-126">オンプレミスの Skype for Business のハイブリッドモダン認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="13e5b-126">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>

<span data-ttu-id="13e5b-127">次の手順では、SFB、SFBO、EXCH、EXO に対して MA を有効にします。これは、SFB および SFBO (EXCH/EXO への依存関係を含む) の HMA 構成に参加可能なすべての製品です。</span><span class="sxs-lookup"><span data-stu-id="13e5b-127">These steps turn on MA for SFB, SFBO, EXCH, and EXO - that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="13e5b-128">言い換えると、ユーザーがハイブリッドの一部 (EXO + SFBO、EXO + SFB、EXCH + SFBO、または EXCH + SFB) で作成したメールボックスを持つ場合、完成した製品は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="13e5b-128">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![混在した6つの Skype for business HMA トポロジは、可能なすべての場所で MA になります。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="13e5b-130">MA を有効にするには、4つの異なる場所が存在します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-130">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="13e5b-131">最適なユーザー環境を実現するには、これらのすべての場所で MA をオンにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13e5b-131">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="13e5b-132">これらのすべての場所で MA をオンにできない場合は、環境に必要な場所で MA のみを有効にするように手順を調整します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-132">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="13e5b-133">サポートされているトポロジについては、「 [Skype for business での Skype For business のサポート」を](https://technet.microsoft.com/library/mt803262.aspx)参照してください。</span><span class="sxs-lookup"><span data-stu-id="13e5b-133">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/library/mt803262.aspx) for supported topologies.</span></span>
  
 <span data-ttu-id="13e5b-134">**重要**開始する前に、すべての前提条件を満たしていることをもう一度確認してください。</span><span class="sxs-lookup"><span data-stu-id="13e5b-134">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="13e5b-135">この情報について[は、こちら](hybrid-modern-auth-overview.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13e5b-135">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="13e5b-136">必要なすべての HMA 固有の情報を収集する</span><span class="sxs-lookup"><span data-stu-id="13e5b-136">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="13e5b-137">先進認証を使用するための[前提条件](hybrid-modern-auth-overview.md)を満たしていることを再度確認した後、前の手順で HMA を構成するために必要な情報を保持するためのファイルを作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="13e5b-137">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="13e5b-138">この記事で使用されている例:</span><span class="sxs-lookup"><span data-stu-id="13e5b-138">Examples used in this article:</span></span>
  
- <span data-ttu-id="13e5b-139">**SIP/SMTP ドメイン**</span><span class="sxs-lookup"><span data-stu-id="13e5b-139">**SIP/SMTP domain**</span></span>

  - <span data-ttu-id="13e5b-140">渡し.</span><span class="sxs-lookup"><span data-stu-id="13e5b-140">Ex.</span></span> <span data-ttu-id="13e5b-141">contoso.com (Office 365 と連携している)</span><span class="sxs-lookup"><span data-stu-id="13e5b-141">contoso.com (is federated with Office 365)</span></span>

- <span data-ttu-id="13e5b-142">**テナント ID**</span><span class="sxs-lookup"><span data-stu-id="13e5b-142">**Tenant ID**</span></span>

  - <span data-ttu-id="13e5b-143">Office 365 テナント (contoso.onmicrosoft.com のログイン時) を表す GUID。</span><span class="sxs-lookup"><span data-stu-id="13e5b-143">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>

- <span data-ttu-id="13e5b-144">**SFB 2015 CU5 Web サービスの Url**</span><span class="sxs-lookup"><span data-stu-id="13e5b-144">**SFB 2015 CU5 Web Service URLs**</span></span>

<span data-ttu-id="13e5b-145">展開されているすべての SfB 2015 プールについて、内部および外部 web サービスの URL が必要になります。</span><span class="sxs-lookup"><span data-stu-id="13e5b-145">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="13e5b-146">これらを取得するには、Skype for Business 管理シェルから次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-146">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="13e5b-147">渡し.</span><span class="sxs-lookup"><span data-stu-id="13e5b-147">Ex.</span></span> <span data-ttu-id="13e5b-148">社外https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="13e5b-148">Internal: https://lyncwebint01.contoso.com</span></span>

- <span data-ttu-id="13e5b-149">渡し.</span><span class="sxs-lookup"><span data-stu-id="13e5b-149">Ex.</span></span> <span data-ttu-id="13e5b-150">社外https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="13e5b-150">External: https://lyncwebext01.contoso.com</span></span>

<span data-ttu-id="13e5b-151">Standard Edition サーバーを使用している場合、内部 URL は空白になります。</span><span class="sxs-lookup"><span data-stu-id="13e5b-151">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="13e5b-152">この場合は、内部 URL にプールの fqdn を使用します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-152">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="13e5b-153">EXO の先進認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="13e5b-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="13e5b-154">「 [Exchange Online: テナントの先進認証を有効にする方法](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="13e5b-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="13e5b-155">SFBO の先進認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="13e5b-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="13e5b-156">「 [Skype For Business Online: テナントで先進認証を有効にする](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)」の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="13e5b-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="13e5b-157">Exchange on-premises のハイブリッド先進認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="13e5b-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="13e5b-158">この記事の手順に従ってください:[ハイブリッド先進認証を使用するように Exchange Server をオンプレミスで構成する方法](configure-exchange-server-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="13e5b-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="13e5b-159">オンプレミスの Skype for Business のハイブリッドモダン認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="13e5b-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="13e5b-160">オンプレミスの web サービス Url を Spn として Azure AD に追加する</span><span class="sxs-lookup"><span data-stu-id="13e5b-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="13e5b-161">ここで、SFBO のサービスプリンシパルとして、前の手順で収集した Url を追加するコマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13e5b-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="13e5b-162">**メモ**サービスプリンシパル名 (Spn) は、web サービスを識別し、それをセキュリティプリンシパル (アカウント名やグループなど) に関連付けて、サービスが権限のあるユーザーの代理として機能できるようにします。</span><span class="sxs-lookup"><span data-stu-id="13e5b-162">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="13e5b-163">クライアントがサーバーに対して認証を行うと、Spn に含まれる情報が利用されます。</span><span class="sxs-lookup"><span data-stu-id="13e5b-163">Clients authenticating to a server make use of information that's contained in SPNs.</span></span>
  
1. <span data-ttu-id="13e5b-164">最初に、[次の手順に従っ](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0)て AAD に接続します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>

2. <span data-ttu-id="13e5b-165">このコマンドをオンプレミスで実行して、SFB web サービス Url の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="13e5b-166">AppPrincipalId はから始まることに`00000004`注意してください。</span><span class="sxs-lookup"><span data-stu-id="13e5b-166">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="13e5b-167">これは、Skype for Business Online に対応しています。</span><span class="sxs-lookup"><span data-stu-id="13e5b-167">This corresponds to Skype for Business Online.</span></span>

   <span data-ttu-id="13e5b-168">このコマンドの出力では、SE と WS の URL が含まれていますが、ほとんどは、で`00000004-0000-0ff1-ce00-000000000000/`始まる spn から構成されていますのでメモを取ります。</span><span class="sxs-lookup"><span data-stu-id="13e5b-168">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```

3. <span data-ttu-id="13e5b-169">オンプレミスの内部**または**外部の Sfb url が欠落してhttps://lyncwebint01.contoso.com https://lyncwebext01.contoso.com)いる場合 (たとえば、である場合)、それらのレコードをこのリストに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13e5b-169">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span>

    <span data-ttu-id="13e5b-170">次の Url の*例は*、Add コマンドで実際の url に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="13e5b-170">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span>
  
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="13e5b-171">手順2で**new-msolserviceprincipal**コマンドを再度実行し、出力を調べて、新しいレコードが追加されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-171">Verify your new records were added by running the **Get-MsolServicePrincipal** command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="13e5b-172">リスト/スクリーンショットを以前から新しい Spn のリストに比較します (レコードの新しいリストのスクリーンショットを表示することもできます)。</span><span class="sxs-lookup"><span data-stu-id="13e5b-172">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="13e5b-173">成功した場合は、2つの新しい Url が一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="13e5b-173">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="13e5b-174">この例では、Spn の一覧に特定の Url https://lyncwebint01.contoso.comとhttps://lyncwebext01.contoso.com/が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="13e5b-174">Going by our example, the list of SPNs will now include the specific URLs https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>

### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="13e5b-175">EvoSTS 認証サーバーオブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="13e5b-175">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="13e5b-176">Skype for Business 管理シェルで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-176">Run the following command in the Skype for Business Management Shell.</span></span>
  
```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="13e5b-177">ハイブリッド先進認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="13e5b-177">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="13e5b-178">これは、実際に MA を有効にする手順です。</span><span class="sxs-lookup"><span data-stu-id="13e5b-178">This is the step that actually turns MA on.</span></span> <span data-ttu-id="13e5b-179">以前のすべての手順は、クライアント認証フローを変更せずに、前もって実行することができます。</span><span class="sxs-lookup"><span data-stu-id="13e5b-179">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="13e5b-180">認証フローを変更する準備ができたら、Skype for Business 管理シェルで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-180">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a><span data-ttu-id="13e5b-181">ことを確認</span><span class="sxs-lookup"><span data-stu-id="13e5b-181">Verify</span></span>

<span data-ttu-id="13e5b-182">HMA を有効にすると、クライアントの次のログインは新しい認証フローを使用します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-182">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="13e5b-183">HMA を有効にしても、クライアントに対しては再認証はトリガーされませんので注意してください。</span><span class="sxs-lookup"><span data-stu-id="13e5b-183">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="13e5b-184">クライアントは、認証トークンまたは証明書の有効期間に基づいて再認証を行います。</span><span class="sxs-lookup"><span data-stu-id="13e5b-184">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="13e5b-185">HMA が機能していることを確認した後で、その機能が動作していることをテストするには、テスト用の SFB Windows クライアントからサインアウトし、[資格情報の削除] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e5b-185">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="13e5b-186">もう一度サインインします。</span><span class="sxs-lookup"><span data-stu-id="13e5b-186">Sign in again.</span></span> <span data-ttu-id="13e5b-187">クライアントは、最新の認証フローを使用するようになり、ログインに ' 職場または学校のアカウントに対する**Office 365**プロンプトが含まれるようになりました。これで、クライアントがサーバーに接続してログインする前に表示されます。</span><span class="sxs-lookup"><span data-stu-id="13e5b-187">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span>
  
<span data-ttu-id="13e5b-188">「OAuth Authority」については、「Skype for Business クライアント」の「構成情報」も確認してください。</span><span class="sxs-lookup"><span data-stu-id="13e5b-188">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="13e5b-189">クライアントコンピューターでこれを行うには、CTRL キーを押しながら、Windows 通知トレイの [Skype for Business] アイコンを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="13e5b-189">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="13e5b-190">表示されるメニューの [**構成情報**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e5b-190">Click **Configuration Information** in the menu that appears.</span></span> <span data-ttu-id="13e5b-191">デスクトップに表示される [Skype for Business の構成情報] ウィンドウで、次のものを探します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-191">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![モダン認証を使用した Skype for Business クライアントの構成情報は、のhttps://login.windows.net/common/oauth2/authorizeLYNC および EWS OAUTH AUTHORITY の URL を示しています。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="13e5b-193">また、CTRL キーを押しながら Outlook クライアントのアイコン (Windows 通知トレイにもあります) を右クリックし、[接続の状態] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e5b-193">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="13e5b-194">OAuth で使用されるベアラートークンを表す、認証の種類 '\*ベアラー ' に対してクライアントの SMTP アドレスを検索します。</span><span class="sxs-lookup"><span data-stu-id="13e5b-194">Look for the client's SMTP address against an AuthN type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="13e5b-195">関連記事</span><span class="sxs-lookup"><span data-stu-id="13e5b-195">Related articles</span></span>

<span data-ttu-id="13e5b-196">[モダン認証の概要に戻る](hybrid-modern-auth-overview.md)</span><span class="sxs-lookup"><span data-stu-id="13e5b-196">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md).</span></span>
  
<span data-ttu-id="13e5b-197">Skype for Business クライアントで先進認証 (ADAL) を使用する方法を知る必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="13e5b-197">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="13e5b-198">[ここでは](https://technet.microsoft.com/library/mt710548.aspx)、手順を示しました。</span><span class="sxs-lookup"><span data-stu-id="13e5b-198">We've got steps [here](https://technet.microsoft.com/library/mt710548.aspx).</span></span>
