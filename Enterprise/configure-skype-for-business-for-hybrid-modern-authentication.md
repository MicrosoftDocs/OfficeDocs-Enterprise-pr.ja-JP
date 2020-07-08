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
description: 先進認証は、ユーザーの認証と承認をより安全に提供する id 管理の方法であり、オンプレミスの Skype for Business server とオンプレミスの Exchange server、およびスプリットドメイン Skype for Business ハイブリッドで利用できます。
ms.openlocfilehash: 6415fe374f63093b44ebacc125dc40c9ea70e898
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052510"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="68ba5-103">Skype for Business をオンプレミスで構成して、ハイブリッド先進認証を使用するには</span><span class="sxs-lookup"><span data-stu-id="68ba5-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="68ba5-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="68ba5-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="68ba5-105">先進認証は、ユーザーの認証と承認をより安全に提供する id 管理の方法であり、オンプレミスの Skype for Business server とオンプレミスの Exchange server、およびスプリットドメイン Skype for Business ハイブリッドで利用できます。</span><span class="sxs-lookup"><span data-stu-id="68ba5-105">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, and split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="68ba5-106">**重要**モダン認証 (MA) の詳細と、会社や組織での使用を希望する理由は何ですか。</span><span class="sxs-lookup"><span data-stu-id="68ba5-106">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="68ba5-107">概要については、[このドキュメント](hybrid-modern-auth-overview.md)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="68ba5-107">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="68ba5-108">MA でサポートされている Skype for Business のトポロジについて知る必要がある場合は、ここで説明します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-108">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span>
  
 <span data-ttu-id="68ba5-109">**開始する前に**、次の用語を使用します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-109">**Before we begin**, I use these terms:</span></span>
  
- <span data-ttu-id="68ba5-110">モダン認証 (MA)</span><span class="sxs-lookup"><span data-stu-id="68ba5-110">Modern Authentication (MA)</span></span>

- <span data-ttu-id="68ba5-111">ハイブリッド先進認証 (HMA)</span><span class="sxs-lookup"><span data-stu-id="68ba5-111">Hybrid Modern Authentication (HMA)</span></span>

- <span data-ttu-id="68ba5-112">Exchange オンプレミス (EXCH)</span><span class="sxs-lookup"><span data-stu-id="68ba5-112">Exchange on-premises (EXCH)</span></span>

- <span data-ttu-id="68ba5-113">Exchange Online (EXO)</span><span class="sxs-lookup"><span data-stu-id="68ba5-113">Exchange Online (EXO)</span></span>

- <span data-ttu-id="68ba5-114">Skype for Business オンプレミス (SFB)</span><span class="sxs-lookup"><span data-stu-id="68ba5-114">Skype for Business on-premises (SFB)</span></span>

- <span data-ttu-id="68ba5-115">Skype for Business Online (SFBO)</span><span class="sxs-lookup"><span data-stu-id="68ba5-115">Skype for Business Online (SFBO)</span></span>

<span data-ttu-id="68ba5-116">また、この記事の図に淡色表示されている、または淡色表示されているオブジェクトがある場合、グレーの要素は MA 固有の構成**に含まれてい**ないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-116">Also, if a graphic in this article has an object that's grayed-out or dimmed that means the element shown in gray **isn't** included in MA-specific configuration.</span></span>
  
## <a name="read-the-summary"></a><span data-ttu-id="68ba5-117">概要の読み取り</span><span class="sxs-lookup"><span data-stu-id="68ba5-117">Read the summary</span></span>

<span data-ttu-id="68ba5-118">この概要では、実行中に失われる可能性のある手順にプロセスを分解します。また、プロセスのどこで作業しているかを全体的なチェックリストに記録することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="68ba5-118">This summary breaks down the process into steps that might otherwise get lost during the execution, and is good for an overall checklist to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="68ba5-119">最初に、すべての前提条件を満たしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="68ba5-119">First, make sure you meet all the prerequisites.</span></span>

1. <span data-ttu-id="68ba5-120">Skype for Business と Exchange の両方に共通の**前提条件**が多数存在するため、[事前要件チェックリストの概要記事を参照してください](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="68ba5-120">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="68ba5-121">この手順を実行する*前*に、この記事の手順を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ba5-121">Do this  *before*  you begin any of the steps in this article.</span></span>

1. <span data-ttu-id="68ba5-122">ファイルまたは OneNote で必要な HMA 固有の情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-122">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>

1. <span data-ttu-id="68ba5-123">EXO のモダン認証を有効にします (まだ有効になっていない場合)。</span><span class="sxs-lookup"><span data-stu-id="68ba5-123">Turn ON Modern Authentication for EXO (if it isn't already turned on).</span></span>

1. <span data-ttu-id="68ba5-124">SFBO の先進認証を有効にします (まだ有効になっていない場合)。</span><span class="sxs-lookup"><span data-stu-id="68ba5-124">Turn ON Modern Authentication for SFBO (if it isn't already turned on).</span></span>

1. <span data-ttu-id="68ba5-125">Exchange on-premises のハイブリッド先進認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="68ba5-125">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>

1. <span data-ttu-id="68ba5-126">オンプレミスの Skype for Business のハイブリッドモダン認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="68ba5-126">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>

<span data-ttu-id="68ba5-127">次の手順では、SFB、SFBO、EXCH、EXO に対して MA を有効にします。これは、SFB および SFBO (EXCH/EXO への依存関係を含む) の HMA 構成に参加できるすべての製品です。</span><span class="sxs-lookup"><span data-stu-id="68ba5-127">These steps turn on MA for SFB, SFBO, EXCH, and EXO - that is, all the products that can participate in an HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="68ba5-128">言い換えると、ユーザーがハイブリッドの一部 (EXO + SFBO、EXO + SFB、EXCH + SFBO、または EXCH + SFB) で作成したメールボックスを持つ場合、完成した製品は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="68ba5-128">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![混在した6つの Skype for business HMA トポロジは、可能なすべての場所で MA になります。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="68ba5-130">MA を有効にするには、4つの異なる場所が存在します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-130">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="68ba5-131">最適なユーザー環境を実現するには、これらのすべての場所で MA をオンにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="68ba5-131">For the best user experience, we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="68ba5-132">これらのすべての場所で MA をオンにできない場合は、環境に必要な場所で MA のみを有効にするように手順を調整します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-132">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="68ba5-133">サポートされているトポロジについては、「 [Skype for business での Skype For business のサポート」を](https://technet.microsoft.com/library/mt803262.aspx)参照してください。</span><span class="sxs-lookup"><span data-stu-id="68ba5-133">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/library/mt803262.aspx) for supported topologies.</span></span>
  
 <span data-ttu-id="68ba5-134">**重要**開始する前に、すべての前提条件を満たしていることをもう一度確認してください。</span><span class="sxs-lookup"><span data-stu-id="68ba5-134">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="68ba5-135">この情報について[は、こちら](hybrid-modern-auth-overview.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68ba5-135">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="68ba5-136">必要なすべての HMA 固有の情報を収集する</span><span class="sxs-lookup"><span data-stu-id="68ba5-136">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="68ba5-137">先進認証を使用するための[前提条件](hybrid-modern-auth-overview.md)を満たしていることを再度確認した後、前の手順で HMA を構成するために必要な情報を保持するためのファイルを作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ba5-137">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="68ba5-138">この記事で使用されている例:</span><span class="sxs-lookup"><span data-stu-id="68ba5-138">Examples used in this article:</span></span>
  
- <span data-ttu-id="68ba5-139">**SIP/SMTP ドメイン**</span><span class="sxs-lookup"><span data-stu-id="68ba5-139">**SIP/SMTP domain**</span></span>

  - <span data-ttu-id="68ba5-140">渡し.</span><span class="sxs-lookup"><span data-stu-id="68ba5-140">Ex.</span></span> <span data-ttu-id="68ba5-141">contoso.com (Office 365 と連携している)</span><span class="sxs-lookup"><span data-stu-id="68ba5-141">contoso.com (is federated with Office 365)</span></span>

- <span data-ttu-id="68ba5-142">**テナント ID**</span><span class="sxs-lookup"><span data-stu-id="68ba5-142">**Tenant ID**</span></span>

  - <span data-ttu-id="68ba5-143">Office 365 テナント (contoso.onmicrosoft.com のログイン時) を表す GUID。</span><span class="sxs-lookup"><span data-stu-id="68ba5-143">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>

- <span data-ttu-id="68ba5-144">**SFB 2015 CU5 Web サービスの Url**</span><span class="sxs-lookup"><span data-stu-id="68ba5-144">**SFB 2015 CU5 Web Service URLs**</span></span>

<span data-ttu-id="68ba5-145">展開されたすべての SfB 2015 プールについて、内部および外部の web サービス Url が必要になります。</span><span class="sxs-lookup"><span data-stu-id="68ba5-145">you'll need internal and external web service URLs for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="68ba5-146">これらを取得するには、Skype for Business 管理シェルから次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-146">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="68ba5-147">渡し.</span><span class="sxs-lookup"><span data-stu-id="68ba5-147">Ex.</span></span> <span data-ttu-id="68ba5-148">社外https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="68ba5-148">Internal: https://lyncwebint01.contoso.com</span></span>

- <span data-ttu-id="68ba5-149">渡し.</span><span class="sxs-lookup"><span data-stu-id="68ba5-149">Ex.</span></span> <span data-ttu-id="68ba5-150">社外https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="68ba5-150">External: https://lyncwebext01.contoso.com</span></span>

<span data-ttu-id="68ba5-151">Standard Edition サーバーを使用している場合、内部 URL は空白になります。</span><span class="sxs-lookup"><span data-stu-id="68ba5-151">If you're using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="68ba5-152">この場合は、内部 URL にプールの fqdn を使用します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-152">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="68ba5-153">EXO の先進認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="68ba5-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="68ba5-154">「 [Exchange Online: テナントの先進認証を有効にする方法](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="68ba5-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="68ba5-155">SFBO の先進認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="68ba5-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="68ba5-156">「 [Skype For Business Online: テナントで先進認証を有効にする](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)」の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="68ba5-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="68ba5-157">Exchange on-premises のハイブリッド先進認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="68ba5-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="68ba5-158">この記事の手順に従ってください:[ハイブリッド先進認証を使用するように Exchange Server をオンプレミスで構成する方法](configure-exchange-server-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="68ba5-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="68ba5-159">オンプレミスの Skype for Business のハイブリッドモダン認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="68ba5-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a><span data-ttu-id="68ba5-160">Azure Active Directory の Spn としてオンプレミスの web サービス Url を追加する</span><span class="sxs-lookup"><span data-stu-id="68ba5-160">Add on-premises web service URLs as SPNs in Azure Active Directory</span></span>

<span data-ttu-id="68ba5-161">ここで、SFBO のサービスプリンシパルとして、前の手順で収集した Url を追加するコマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ba5-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="68ba5-162">**メモ**サービスプリンシパル名 (Spn) は、web サービスを識別し、それをセキュリティプリンシパル (アカウント名やグループなど) に関連付けて、サービスが権限のあるユーザーの代理として機能できるようにします。</span><span class="sxs-lookup"><span data-stu-id="68ba5-162">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="68ba5-163">クライアントがサーバーに対して認証を行うと、Spn に含まれる情報が利用されます。</span><span class="sxs-lookup"><span data-stu-id="68ba5-163">Clients authenticating to a server make use of information that's contained in SPNs.</span></span>
  
1. <span data-ttu-id="68ba5-164">最初に、[これらの手順](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0)を使用して Azure Active Directory (azure AD) に接続します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-164">First, connect to Azure Active Directory (Azure AD) with [these instructions](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>

2. <span data-ttu-id="68ba5-165">このコマンドをオンプレミスで実行して、SFB web サービス Url の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="68ba5-166">AppPrincipalId はから始まることに注意して `00000004` ください。</span><span class="sxs-lookup"><span data-stu-id="68ba5-166">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="68ba5-167">これは、Skype for Business Online に対応しています。</span><span class="sxs-lookup"><span data-stu-id="68ba5-167">This corresponds to Skype for Business Online.</span></span>

   <span data-ttu-id="68ba5-168">このコマンドの出力では、SE と WS の URL が含まれていますが、ほとんどは、で始まる Spn から構成されていますのでメモを取り `00000004-0000-0ff1-ce00-000000000000/` ます。</span><span class="sxs-lookup"><span data-stu-id="68ba5-168">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```

3. <span data-ttu-id="68ba5-169">オンプレミスの内部**または**外部の Sfb url が欠落している場合 (たとえば、である場合)、 https://lyncwebint01.contoso.com それらのレコードを https://lyncwebext01.contoso.com) このリストに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ba5-169">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span>

    <span data-ttu-id="68ba5-170">次の*url の例は*、Add コマンドで実際の url に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="68ba5-170">Be sure to replace  *the example URLs* below with your actual URLs in the Add commands!</span></span>
  
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="68ba5-171">手順2で**new-msolserviceprincipal**コマンドを再度実行し、出力を調べて、新しいレコードが追加されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-171">Verify your new records were added by running the **Get-MsolServicePrincipal** command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="68ba5-172">リストまたはスクリーンショットを、Spn の新しいリストの前に比較します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-172">Compare the list or screenshot from before to the new list of SPNs.</span></span> <span data-ttu-id="68ba5-173">また、レコードの新しいリストのスクリーンショットを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="68ba5-173">You might also screenshot the new list for your records.</span></span> <span data-ttu-id="68ba5-174">成功した場合は、2つの新しい Url が一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="68ba5-174">If you were successful, you'll see the two new URLs in the list.</span></span> <span data-ttu-id="68ba5-175">この例では、Spn の一覧に特定の Url とが含まれるようになりました https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com/ 。</span><span class="sxs-lookup"><span data-stu-id="68ba5-175">Going by our example, the list of SPNs will now include the specific URLs https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>

### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="68ba5-176">EvoSTS 認証サーバーオブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="68ba5-176">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="68ba5-177">Skype for Business 管理シェルで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-177">Run the following command in the Skype for Business Management Shell.</span></span>
  
```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="68ba5-178">ハイブリッド先進認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="68ba5-178">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="68ba5-179">これは、実際に MA を有効にする手順です。</span><span class="sxs-lookup"><span data-stu-id="68ba5-179">This is the step that actually turns on MA.</span></span> <span data-ttu-id="68ba5-180">以前のすべての手順は、クライアント認証フローを変更せずに、前もって実行することができます。</span><span class="sxs-lookup"><span data-stu-id="68ba5-180">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="68ba5-181">認証フローを変更する準備ができたら、Skype for Business 管理シェルで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-181">When you're ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a><span data-ttu-id="68ba5-182">ことを確認</span><span class="sxs-lookup"><span data-stu-id="68ba5-182">Verify</span></span>

<span data-ttu-id="68ba5-183">HMA を有効にすると、クライアントの次のログインは新しい認証フローを使用します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-183">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="68ba5-184">HMA を有効にするだけでは、クライアントの再認証はトリガーされないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="68ba5-184">Note that just turning on HMA won't trigger a reauthentication for any client.</span></span> <span data-ttu-id="68ba5-185">クライアントは、認証トークンまたは証明書の有効期間に基づいて再認証を行います。</span><span class="sxs-lookup"><span data-stu-id="68ba5-185">The clients reauthenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="68ba5-186">HMA が機能していることを確認した後で、その機能が動作していることをテストするには、テスト用の SFB Windows クライアントからサインアウトし、[資格情報の削除] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ba5-186">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="68ba5-187">もう一度サインインします。</span><span class="sxs-lookup"><span data-stu-id="68ba5-187">Sign in again.</span></span> <span data-ttu-id="68ba5-188">クライアントは、最新の認証フローを使用するようになり、ログインに ' 職場または学校のアカウントに対する**Office 365**プロンプトが含まれるようになりました。これで、クライアントがサーバーに接続してログインする前に表示されます。</span><span class="sxs-lookup"><span data-stu-id="68ba5-188">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span>
  
<span data-ttu-id="68ba5-189">「OAuth Authority」については、「Skype for Business クライアント」の「構成情報」も確認してください。</span><span class="sxs-lookup"><span data-stu-id="68ba5-189">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="68ba5-190">クライアントコンピューターでこれを行うには、CTRL キーを押しながら、Windows 通知トレイの [Skype for Business] アイコンを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="68ba5-190">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="68ba5-191">表示されるメニューの [**構成情報**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ba5-191">Click **Configuration Information** in the menu that appears.</span></span> <span data-ttu-id="68ba5-192">デスクトップに表示される [Skype for Business の構成情報] ウィンドウで、次のものを探します。</span><span class="sxs-lookup"><span data-stu-id="68ba5-192">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![モダン認証を使用した Skype for Business クライアントの構成情報は、の Lync および EWS OAUTH Authority の URL を示して https://login.windows.net/common/oauth2/authorize います。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="68ba5-194">また、CTRL キーを押しながら Outlook クライアントのアイコンを右クリックし、[接続の状態] をクリックしても同じことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ba5-194">You should also hold down the CTRL key at the same time you right-click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="68ba5-195">OAuth で使用されるベアラートークンを表す、認証の種類 ' ベアラー ' に対してクライアントの SMTP アドレスを検索し \* ます。</span><span class="sxs-lookup"><span data-stu-id="68ba5-195">Look for the client's SMTP address against an AuthN type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="68ba5-196">関連記事</span><span class="sxs-lookup"><span data-stu-id="68ba5-196">Related articles</span></span>

<span data-ttu-id="68ba5-197">[モダン認証の概要に戻る](hybrid-modern-auth-overview.md)</span><span class="sxs-lookup"><span data-stu-id="68ba5-197">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md).</span></span>
  
<span data-ttu-id="68ba5-198">Skype for Business クライアントで先進認証 (ADAL) を使用する方法を知る必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="68ba5-198">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="68ba5-199">[ここでは](https://technet.microsoft.com/library/mt710548.aspx)、手順を示しました。</span><span class="sxs-lookup"><span data-stu-id="68ba5-199">We've got steps [here](https://technet.microsoft.com/library/mt710548.aspx).</span></span>
