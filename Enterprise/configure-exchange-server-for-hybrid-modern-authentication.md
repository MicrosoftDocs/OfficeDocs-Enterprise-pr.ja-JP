---
title: Exchange Server をオンプレミスで構成して、ハイブリッド先進認証を使用するには
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 3/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: ハイブリッド現代認証 (HMA) より安全なユーザー認証と承認を提供し、Exchange サーバー設置型のハイブリッド展開を利用する id 管理の方法です。
ms.openlocfilehash: cfacb5661ddf4a2ac61054582f0c2043d8fe7a5a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975195"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="5d6f7-103">Exchange Server をオンプレミスで構成して、ハイブリッド先進認証を使用するには</span><span class="sxs-lookup"><span data-stu-id="5d6f7-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="5d6f7-104">ハイブリッド現代認証 (HMA) より安全なユーザー認証と承認を提供し、Exchange サーバー設置型のハイブリッド展開を利用する id 管理の方法です。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="5d6f7-105">ヒント</span><span class="sxs-lookup"><span data-stu-id="5d6f7-105">FYI</span></span>

<span data-ttu-id="5d6f7-106">始める前に私を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="5d6f7-107">ハイブリッド現代認証\>HMA</span><span class="sxs-lookup"><span data-stu-id="5d6f7-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="5d6f7-108">オンプレミスの exchange \> EXCH</span><span class="sxs-lookup"><span data-stu-id="5d6f7-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="5d6f7-109">オンライン交換\>EXO</span><span class="sxs-lookup"><span data-stu-id="5d6f7-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="5d6f7-110">また、*図形ではこの資料はするには '灰色' または '淡色表示されている' つまり、HMA に固有の構成では灰色で表示する要素が含まれていないオブジェクト*にします。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="5d6f7-111">ハイブリッド現代の認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="5d6f7-112">手段には、HMA を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="5d6f7-113">開始する前に、前提を満たしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="5d6f7-p101">以降、多く**の前提条件**は、両方の Skype ビジネスと Exchange では、[ハイブリッドの最新の認証の概要とでそれを使用するための前提条件、オンプレミス Skype ビジネスおよび Exchange サーバーの](hybrid-modern-auth-overview.md)ための一般的なのです。この資料の手順のいずれかを開始する前にこれを行います。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p101">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="5d6f7-116">追加設置 web サービスの Url のサービス プリンシパル名 (Spn) として Azure AD で。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="5d6f7-117">HMA のすべての仮想ディレクトリのことを確認が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="5d6f7-118">EvoSTS 認証サーバー オブジェクトのチェック</span><span class="sxs-lookup"><span data-stu-id="5d6f7-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="5d6f7-119">為替で HMA を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="5d6f7-p102">**メモ**Office のバージョンは MA をサポートしますか。[Office 2013 および Office 2016 のクライアント アプリケーションの現在の認証のしくみ](modern-auth-for-office-2013-and-2016.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p102">**Note** Does your version of Office support MA? See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="5d6f7-122">すべての前提条件を満たしているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="5d6f7-p103">ビジネスと Exchange の両方の Skype の一般的な多くの前提条件であるために、[ハイブリッド現代の認証の概要とビジネスと Exchange サーバーの設置型の Skype でそれを使用するための前提条件](hybrid-modern-auth-overview.md)を確認します。この*前に*この資料の手順のいずれかを開始します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p103">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="5d6f7-125">設置型は、Azure AD で Spn としてサービスの Url を web に追加します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="5d6f7-p104">Azure AD Spn。 Spn が使っているクライアント コンピューターとデバイスの認証と承認の際に、設置型の web サービスの Url を割り当てるコマンドを実行します。AAD を (内部および外部の名前空間を含む) では、Azure Active Directory (AAD) に設置からの接続に使用されるすべての Url を登録してください。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p104">Run the commands that assign your on-premises web service URLs as Azure AD SPNs. SPNs are used by client machines and devices during authentication and authorization. All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="5d6f7-p105">まず、AAD に追加する必要があるすべての Url を収集します。これらのコマンドで設置型を実行します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p105">First, gather all the URLs that you need to add in AAD. Run these commands on-premises:</span></span>
  
- <span data-ttu-id="5d6f7-131">Get MapiVirtualDirectory |FL サーバー、\*の url\*</span><span class="sxs-lookup"><span data-stu-id="5d6f7-131">Get-MapiVirtualDirectory | FL server,\*url\*</span></span>
    
- <span data-ttu-id="5d6f7-132">Get WebServicesVirtualDirectory |FL サーバー、\*の url\*</span><span class="sxs-lookup"><span data-stu-id="5d6f7-132">Get-WebServicesVirtualDirectory | FL server,\*url\*</span></span>
    
- <span data-ttu-id="5d6f7-133">**Get ActiveSyncVirtualDirectory |FL サーバー、\*の url\***</span><span class="sxs-lookup"><span data-stu-id="5d6f7-133">**Get-ActiveSyncVirtualDirectory | FL server,\*url\***</span></span>
    
- <span data-ttu-id="5d6f7-134">Get OABVirtualDirectory |FL サーバー、\*の url\*</span><span class="sxs-lookup"><span data-stu-id="5d6f7-134">Get-OABVirtualDirectory | FL server,\*url\*</span></span>
    
<span data-ttu-id="5d6f7-135">AAD での HTTPS サービス プリンシパル名として登録されている可能性がありますクライアント接続の Url を確認します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-135">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="5d6f7-136">最初に、[次の手順](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell)で AAD に接続します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-136">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span>
    
2. <span data-ttu-id="5d6f7-137">Exchange 関連の Url は次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-137">For your Exchange related URLs, type the following command:</span></span>
    
- <span data-ttu-id="5d6f7-138">Get-MsolServicePrincipal-AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 |-ExpandProperty ServicePrincipalNames を選択します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-138">Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames</span></span>
    
<span data-ttu-id="5d6f7-p106">メモ (および後で比較のスクリーン ショット)、https:// を含める必要があります、このコマンドの出力を行う \* 自動検出します。*宛先*\* と*mail.yourdomain.com*の URL を https://、00000002-0000-0ff1-ce00-000000000000 で始まる Spn のほとんどで構成されますと。オンプレミスで不足しているから https:// の Url がある場合はこの一覧にある特定のレコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p106">Take note of (and screenshot for later comparison) the output of this command, which should include an https:// \*autodiscover. *yourdomain*  .com \*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/. If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="5d6f7-142">このリストの内部および外部 MAPI 要求、EWS、ActiveSync、OAB、および自動検出レコードが表示されない場合、次のコマンドを使用して、追加する必要があります (この例の Url は、'`mail.corp.contoso.com`'と'`owa.contoso.com`'、**独自の Url の例を置換**する必要があるが、):</span><span class="sxs-lookup"><span data-stu-id="5d6f7-142">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```
- $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
- $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
- $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
- $x.ServicePrincipalnames.Add("https://eas.contoso.com/")
- Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="5d6f7-p107">手順 2 から Get MsolServicePrincipal コマンドを再度実行して、出力を確認して、新しいレコードが追加されたことを確認します。一覧を比較/スクリーン ショットの前に新しい (必要な場合も、新しいリストのスクリーン ショットを記録用) の Spn の一覧にします。成功した場合は、リスト内の 2 つの新しい Url が表示されます。この例では、移動、Spn の一覧表示されます特定の Url`https://mail.corp.contoso.com`と`https://owa.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p107">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="5d6f7-147">仮想ディレクトリは、適切に構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-147">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="5d6f7-148">か確認して OAuth が適切に有効になっている次のコマンドを実行して、すべての仮想ディレクトリの Outlook で Exchange を使用します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-148">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```
Get-MapiVirtualDirectory | FL server,\*url\*,\*auth\* 
Get-WebServicesVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-OABVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-AutoDiscoverVirtualDirectory | FL server,\*oauth\*
```

<span data-ttu-id="5d6f7-149">これらの VDirs のそれぞれにチェックすることを確認して**OAuth**が有効になっている、次のようになります (およびを見ることは、'OAuth') です。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-149">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 
  
 <span data-ttu-id="5d6f7-150">**[PS]C:\Windows\system32\>Get MapiVirtualDirectory |fl サーバー、\*url\*、\*認証\***</span><span class="sxs-lookup"><span data-stu-id="5d6f7-150">**[PS] C:\Windows\system32\>Get-MapiVirtualDirectory | fl server,\*url\*,\*auth\***</span></span>
  
 <span data-ttu-id="5d6f7-151">**サーバー: EX1**</span><span class="sxs-lookup"><span data-stu-id="5d6f7-151">**Server : EX1**</span></span>
  
 <span data-ttu-id="5d6f7-152">**InternalUrl。`https://mail.contoso.com/mapi`**</span><span class="sxs-lookup"><span data-stu-id="5d6f7-152">**InternalUrl : `https://mail.contoso.com/mapi`**</span></span>
  
 <span data-ttu-id="5d6f7-153">**ExternalUrl。`https://mail.contoso.com/mapi`**</span><span class="sxs-lookup"><span data-stu-id="5d6f7-153">**ExternalUrl : `https://mail.contoso.com/mapi`**</span></span>
  
 <span data-ttu-id="5d6f7-154">**IISAuthenticationMethods: {Ntlm、OAuth の交渉}**</span><span class="sxs-lookup"><span data-stu-id="5d6f7-154">**IISAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
 <span data-ttu-id="5d6f7-155">**InternalAuthenticationMethods: {Ntlm、OAuth の交渉}**</span><span class="sxs-lookup"><span data-stu-id="5d6f7-155">**InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
 <span data-ttu-id="5d6f7-156">**ExternalAuthenticationMethods: {Ntlm、OAuth の交渉}**</span><span class="sxs-lookup"><span data-stu-id="5d6f7-156">**ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
<span data-ttu-id="5d6f7-157">OAuth では、任意のサーバーと 4 つの仮想ディレクトリのいずれかに表示されない場合は、続行する前に関連するコマンドを使用して追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-157">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="5d6f7-158">EvoSTS 認証サーバー オブジェクトが存在であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-158">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="5d6f7-p108">この最後のコマンドに、オンプレミスの Exchange 管理シェルに戻ります。これで、設置型では、evoSTS の認証プロバイダーのエントリがあるかを検証できます。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p108">Return to the on-premises Exchange Management Shell for this last command. Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
`Get-AuthServer | where {$_.Name -eq "EvoSts"}`
    
<span data-ttu-id="5d6f7-p109">出力の名前 EvoSts、AuthServer を表示する必要があり、'有効' の状態が True にする必要があります。このメッセージが表示されない場合は、ダウンロードして、ハイブリッド構成ウィザードの最新バージョンを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p109">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True. If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="5d6f7-163">**重要です**環境内で Exchange 2010 を実行している場合は、EvoSTS の認証プロバイダーが作成されません。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-163">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="5d6f7-164">HMA を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-164">Enable HMA</span></span>

<span data-ttu-id="5d6f7-165">設置、Exchange 管理シェルで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-165">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="5d6f7-166">[確認]</span><span class="sxs-lookup"><span data-stu-id="5d6f7-166">Verify</span></span>

<span data-ttu-id="5d6f7-p110">HMA を有効にすると、クライアントの次回のログインは、新しい認証フローを使用します。HMA を入れただけではありませんをトリガーする再認証のすべてのクライアントに注意してください。クライアントを再認証に基づく認証トークンや証明書の有効期間があります。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p110">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="5d6f7-p111">また、(Windows の通知トレイ) にも Outlook クライアントのアイコンを右クリックすると同時に、CTRL キーを押し、[接続ステータス] をクリックしてください。に対して、'認証' 型のクライアントの SMTP アドレスを検索 ' ベアラー\*'、OAuth でベアラー トークンを表します。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p111">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="5d6f7-p112">**メモ**HMA にビジネス用の Skype を構成する必要がありますか。2 つの記事をする必要があります:[サポートされるトポロジ](https://technet.microsoft.com/en-us/library/mt803262.aspx)はの一覧が表示されると[、構成を行う方法](configure-skype-for-business-for-hybrid-modern-authentication.md)を示しています。</span><span class="sxs-lookup"><span data-stu-id="5d6f7-p112">**Note** Need to configure Skype for Business with HMA? You'll need two articles: One that lists [supported topologies](https://technet.microsoft.com/en-us/library/mt803262.aspx), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="5d6f7-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d6f7-174">Related topics</span></span>

[<span data-ttu-id="5d6f7-175">ハイブリッド現代の認証の概要とビジネスと Exchange サーバーの設置型の Skype で使用するための前提条件</span><span class="sxs-lookup"><span data-stu-id="5d6f7-175">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

