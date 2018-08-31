---
title: Skype for Business をオンプレミスで構成して、ハイブリッド先進認証を使用するには
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: 現代の認証より安全なユーザー認証と承認を提供する、ビジネス サーバー設置型 Exchange サーバー設置とビジネスの混成のドメインを分割 Skype の Skype の利用は、id 管理の方法です。
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541863"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="1b361-103">Skype for Business をオンプレミスで構成して、ハイブリッド先進認証を使用するには</span><span class="sxs-lookup"><span data-stu-id="1b361-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="1b361-104">現代の認証より安全なユーザー認証と承認を提供する、ビジネス サーバー設置型 Exchange サーバー設置とビジネスの混成のドメインを分割 Skype の Skype の利用は、id 管理の方法です。</span><span class="sxs-lookup"><span data-stu-id="1b361-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="1b361-p101">**重要です**現代認証 (MA) と、会社または組織で使用する方がよい理由の詳細を把握してもよろしいですか。概要については[このドキュメント](hybrid-modern-auth-overview.md)を確認してください。場合はビジネス ・ トポロジーは、ここに記載されている MA でサポートされているにどのような Skype を把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b361-p101">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization? Check [this document](hybrid-modern-auth-overview.md) for an overview. If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="1b361-108">**始める前に**、私を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1b361-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="1b361-109">現代の認証\>MA</span><span class="sxs-lookup"><span data-stu-id="1b361-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="1b361-110">ハイブリッド現代認証\>HMA</span><span class="sxs-lookup"><span data-stu-id="1b361-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="1b361-111">オンプレミスの exchange \> EXCH</span><span class="sxs-lookup"><span data-stu-id="1b361-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="1b361-112">オンライン交換\>EXO</span><span class="sxs-lookup"><span data-stu-id="1b361-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="1b361-113">設置型のビジネスの Skype\>デバイス</span><span class="sxs-lookup"><span data-stu-id="1b361-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="1b361-114">オンライン ビジネスの Skype \> SFBO</span><span class="sxs-lookup"><span data-stu-id="1b361-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="1b361-115">また、\* この資料の画像が灰色で**は**MA に固有の構成に含まれて表示されている要素のことを意味する '灰色' または '淡色表示されている' オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="1b361-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="1b361-116">サマリーを読む</span><span class="sxs-lookup"><span data-stu-id="1b361-116">Read the summary</span></span>

<span data-ttu-id="1b361-117">この概要では、プロセスを要するに、実行中に失われた場合は取得可能性がありますし、プロセスであるかを追跡する全体的なチェック項目の手順にします。</span><span class="sxs-lookup"><span data-stu-id="1b361-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="1b361-118">まず、すべての前提条件を満たしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1b361-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="1b361-p102">以降、多く**の前提条件**は、ビジネスと[の前提条件チェックリストの概要記事を参照して](hybrid-modern-auth-overview.md)Exchange の両方の Skype の一般的なのです。この*前に*この資料の手順のいずれかを開始します。</span><span class="sxs-lookup"><span data-stu-id="1b361-p102">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="1b361-121">ファイル、または OneNote にする必要があるときなどに固有の情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="1b361-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="1b361-122">有効に現代の認証 EXO (それが入っていない場合既に)。</span><span class="sxs-lookup"><span data-stu-id="1b361-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="1b361-123">有効に現代の認証 SFBO (それが入っていない場合既に)。</span><span class="sxs-lookup"><span data-stu-id="1b361-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="1b361-124">設置型の Exchange ハイブリッド現代の認証をオンにします。</span><span class="sxs-lookup"><span data-stu-id="1b361-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="1b361-125">設置型のビジネスには、Skype のハイブリッド現代の認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1b361-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="1b361-p103">次の手順を有効にする MA デバイス、SFBO、EXCH、EXO--は、HMA 構成でのデバイスと SFBO の (EXCH EXO との依存関係を含む) をサポートしているすべての製品に注意してください。つまり、ユーザーが置かれている場合、ハイブリッド (EXO + SFBO、EXO + デバイス、EXCH + SFBO、または EXCH + デバイス) の一部としてメールボックスを作成、完成品のようになります。</span><span class="sxs-lookup"><span data-stu-id="1b361-p103">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO). In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![ビジネス HMA トポロジの混在の 6 Skype を持っている MA の 4 つのすべての可能な場所。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="1b361-p104">ご覧の MA を有効にするのには 4 つの異なる場所があります。最高のユーザー エクスペリエンスでは、これらの場所のすべての 4 つの MA を有効にするをお勧めします。MA は、これらすべての場所でにことはできません、する場合は、MA は、環境に必要な場所でのみを有効にするように手順を調整します。</span><span class="sxs-lookup"><span data-stu-id="1b361-p104">As you can see there are four different places to turn on MA! For the best user experience we recommend you turn on MA in all four of these locations. If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="1b361-132">サポートされているトポロジについては、 [MA とビジネス用の Skype のサポートのトピック](https://technet.microsoft.com/en-us/library/mt803262.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b361-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="1b361-p105">**重要です**開始する前に、すべての前提条件が満たされていることを再確認してください。その情報については[ここで](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1b361-p105">**Important** Double-check that you've met all the prerequisites before you begin. You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="1b361-135">必要がありますすべてのときなどに固有の情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="1b361-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="1b361-p106">現代の認証を使用する[前提条件](hybrid-modern-auth-overview.md)を満たすことをダブル チェックした後 (上記のメモ参照)、前の手順で、HMA を構成するための必要情報を保持するためにファイルを作成する必要があります。この資料で使用する例:</span><span class="sxs-lookup"><span data-stu-id="1b361-p106">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead. Examples used in this article:</span></span> 
  
- <span data-ttu-id="1b361-138">**SIP または SMTP ドメイン**</span><span class="sxs-lookup"><span data-stu-id="1b361-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="1b361-p107">例: contoso.com の (Office 365 とフェデレーションでは)</span><span class="sxs-lookup"><span data-stu-id="1b361-p107">Ex. contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="1b361-141">**Tenant ID**</span><span class="sxs-lookup"><span data-stu-id="1b361-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="1b361-142">(Contoso.onmicrosoft.com のログイン) で、Office 365 のテナントを表す GUID です。</span><span class="sxs-lookup"><span data-stu-id="1b361-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="1b361-143">**デバイス 2015 CU5 Web サービスの Url**</span><span class="sxs-lookup"><span data-stu-id="1b361-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="1b361-p108">内部および外部の web サービスの URL は、展開のすべてのデバイスの 2015年プールの必要があります。これらを入手するには、ビジネス管理シェルの Skype から次を実行します。</span><span class="sxs-lookup"><span data-stu-id="1b361-p108">You will need internal and external web service URL's for all SfB 2015 pools deployed. To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
<span data-ttu-id="1b361-146">Get CsService-web サーバー。選択オブジェクト PoolFqdn、InternalFqdn、ExternalFqdn。FL</span><span class="sxs-lookup"><span data-stu-id="1b361-146">Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL</span></span>
  
- <span data-ttu-id="1b361-p109">例: 内部。https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1b361-p109">Ex. Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="1b361-p110">例: 外部。https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1b361-p110">Ex. External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="1b361-p111">Standard Edition サーバーを使用している場合、内部 URL は空白になります。この例では、内部 URL のプールの fqdn を使用します。</span><span class="sxs-lookup"><span data-stu-id="1b361-p111">If you are using a Standard Edition server, the internal URL will be blank. In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="1b361-153">EXO の最新の認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1b361-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="1b361-154">ここに示す手順に従います: [Exchange オンライン: 最新の認証のため、テナントを有効にする方法です](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1b361-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="1b361-155">SFBO 用の最新の認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1b361-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="1b361-156">ここに示す手順に従います:[ビジネス オンラインの Skype: 最新の認証のため、テナントを有効にする](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1b361-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="1b361-157">設置型の Exchange ハイブリッド現代の認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1b361-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="1b361-158">ここに示す手順に従います:[ハイブリッド現代の認証を使用するオンプレミスの Exchange Server を構成する方法](configure-exchange-server-for-hybrid-modern-authentication.md)です。</span><span class="sxs-lookup"><span data-stu-id="1b361-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="1b361-159">設置型のビジネスに、Skype のハイブリッド現代の認証を有効に</span><span class="sxs-lookup"><span data-stu-id="1b361-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="1b361-160">設置型は、Azure AD で Spn としてサービスの Url を web に追加します。</span><span class="sxs-lookup"><span data-stu-id="1b361-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="1b361-161">ここで SFBO のサービス ・ プリンシパルとして (収集された以前のバージョン) の Url を追加するのにはコマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b361-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="1b361-p112">**メモ**サービス プリンシパル名 (Spn) web サービスを識別して関連付けること (アカウント名またはグループ) などのセキュリティ プリンシパル、権限を持つユーザーの代わりに、サービスが機能するようです。クライアントがサーバーに対して認証を行うを利用情報に格納されている Spn のです。</span><span class="sxs-lookup"><span data-stu-id="1b361-p112">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user. Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="1b361-164">最初に、[次の手順](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0)で AAD に接続します。</span><span class="sxs-lookup"><span data-stu-id="1b361-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span></span>
    
2. <span data-ttu-id="1b361-165">このコマンドを設置、デバイスの web サービスの Url の一覧を取得するを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b361-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>
    
  - <span data-ttu-id="1b361-166">Get-MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 |-ExpandProperty ServicePrincipalNames を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b361-166">Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames</span></span>
    
    <span data-ttu-id="1b361-p113">'00000004' で、AppPrincipalId が始まることに注意してください。これは、オンライン ビジネスの Skype に対応しています。</span><span class="sxs-lookup"><span data-stu-id="1b361-p113">Notice that the AppPrincipalId begins with '00000004'. This corresponds to Skype for Business Online.</span></span>
    
    <span data-ttu-id="1b361-169">メモ (および後で比較のスクリーン ショット)、SE と WS の URL が 00000004-0000-0ff1-ce00-000000000000 で始まる Spn のほとんどで構成されますが、このコマンドの出力を行うとします。</span><span class="sxs-lookup"><span data-stu-id="1b361-169">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with 00000004-0000-0ff1-ce00-000000000000/.</span></span>
    
3. <span data-ttu-id="1b361-170">内部**または**外部設置型からデバイスの Url が表示されない場合 (たとえば、https://lyncwebint01.contoso.comとhttps://lyncwebext01.contoso.com)がこの一覧にある特定のレコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b361-170">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="1b361-171">[追加] コマンドで、実際の Url を持つ、下の*Url の例*を交換することを確認するには!</span><span class="sxs-lookup"><span data-stu-id="1b361-171">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
    
  - <span data-ttu-id="1b361-172">$x = get MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span><span class="sxs-lookup"><span data-stu-id="1b361-172">$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span></span>
    
  - <span data-ttu-id="1b361-173">$x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="1b361-173">$x.ServicePrincipalnames.Add(" *https://lyncwebint01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="1b361-174">$x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="1b361-174">$x.ServicePrincipalnames.Add(" *https://lyncwebext01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="1b361-175">セット-MSOLServicePrincipal-AppPrincipalId の 00000004-0000-0ff1-ce00-000000000000 ・ ServicePrincipalNames $x.ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="1b361-175">Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames</span></span>
    
4. <span data-ttu-id="1b361-p114">手順 2 から Get MsolServicePrincipal コマンドを再度実行して、出力を確認して、新しいレコードが追加されたことを確認します。一覧を比較/スクリーン ショットの前に新しい (必要な場合も、新しいリストのスクリーン ショットを記録用) の Spn の一覧にします。成功した場合は、リスト内の 2 つの新しい Url が表示されます。この例では、移動、Spn の一覧表示されます特定の Urlhttps://lyncweb01.contoso.comとhttps://autodiscover.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="1b361-p114">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://autodiscover.contoso.com.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="1b361-180">EvoSTS 認証サーバー オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b361-180">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="1b361-181">ビジネス管理シェルには、Skype で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b361-181">Run the following command in the Skype for Business Management Shell.</span></span>
  
- <span data-ttu-id="1b361-182">新しい-CsOAuthServer-の Id evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml AcceptSecurityIdentifierInformation $true-タイプ AzureAD</span><span class="sxs-lookup"><span data-stu-id="1b361-182">New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD</span></span>
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="1b361-183">ハイブリッド現代の認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1b361-183">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="1b361-p115">これは、実際に MA を有効にする手順です。以前のすべての手順は、事前にクライアントの認証フローを変更することがなく実行できます。認証フローを変更する準備ができたらは、ビジネス管理シェルには、Skype でこのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b361-p115">This is the step that actually turns MA on. All the previous steps can be run ahead of time without changing the client authentication flow. When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
- <span data-ttu-id="1b361-187">セット-CsOAuthConfiguration-ClientAuthorizationOAuthServerIdentity evoSTS</span><span class="sxs-lookup"><span data-stu-id="1b361-187">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS</span></span>
    
## <a name="verify"></a><span data-ttu-id="1b361-188">[確認]</span><span class="sxs-lookup"><span data-stu-id="1b361-188">Verify</span></span>

<span data-ttu-id="1b361-p116">HMA を有効にすると、クライアントの次回のログインは、新しい認証フローを使用します。HMA を入れただけではありませんをトリガーする再認証のすべてのクライアントに注意してください。クライアントを再認証に基づく認証トークンや証明書の有効期間があります。</span><span class="sxs-lookup"><span data-stu-id="1b361-p116">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="1b361-p117">HMA に有効にした後に動作しているをテストするには、テスト デバイスの Windows クライアントからサインアウトし、[資格情報を削除] をクリックしてください。もう一度サインインします。現代の認証フローを使用してください、クライアントと '職場または学校' の**Office 365**のプロンプトと表示されます、ログイン アカウント、クライアントがサーバーに接続しログに記録する前に右に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b361-p117">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'. Sign in again. The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="1b361-p118">'OAuth 機関' の Skype のビジネスのクライアントの構成情報をチェックする必要がありますもします。クライアント コンピューターには、するを右クリックし、Skype ビジネスのアイコンを Windows のトレイで同時に CTRL キーを押しします。構成情報が表示されるメニューでクリックします。デスクトップ上に表示される 'の構成についてはビジネス Skype' ウィンドウに、次の表示します。</span><span class="sxs-lookup"><span data-stu-id="1b361-p118">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'. To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray. Click Configuration Information in the menu that appears. In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![Skype の最新の認証を使用してビジネス クライアント用の構成情報は、Lync との EWS OAUTH 機関の URL を示しています。 https://login.windows.net/common/oauth2/authorize。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="1b361-p119">また、(Windows の通知トレイ) にも Outlook クライアントのアイコンを右クリックすると同時に、CTRL キーを押し、[接続ステータス] をクリックしてください。に対して、各種の認証の種類のクライアントの SMTP アドレスを検索 ' ベアラー\*'、OAuth でベアラー トークンを表します。</span><span class="sxs-lookup"><span data-stu-id="1b361-p119">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="1b361-202">関連記事</span><span class="sxs-lookup"><span data-stu-id="1b361-202">Related articles</span></span>

<span data-ttu-id="1b361-203">[現代の認証の概要へのリンク](hybrid-modern-auth-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="1b361-203">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="1b361-p120">Skype のビジネス クライアントの最新の認証 (ADAL) を使用する方法を理解する必要がありますか。我々 の手順[は、ここ](https://technet.microsoft.com/en-us/library/mt710548.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="1b361-p120">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients? We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="1b361-p121">Exchange Server に表示される次の手順を参照するを選択して、設置、デバイスを使用せずに実行しますか。これらの手順は、ここで使用できます。</span><span class="sxs-lookup"><span data-stu-id="1b361-p121">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB? Those steps are available here.</span></span>
  

