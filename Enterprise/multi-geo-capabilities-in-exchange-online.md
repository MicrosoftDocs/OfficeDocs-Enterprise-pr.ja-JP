---
title: Exchange オンラインで複数の地域の機能
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Exchange Online の機能を複数地域での複数の地理的な領域に、Office 365 のプレゼンスを展開します。
ms.openlocfilehash: ea00ab52142e92e122273ab4ba718e98bd94b572
ms.sourcegitcommit: 12d3223cc2d6bf39a8960409a923254e1790fd2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="dbac6-103">Exchange オンラインで複数の地域の機能</span><span class="sxs-lookup"><span data-stu-id="dbac6-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="dbac6-p101">Office 365 に複数の地域の機能は、複数の地理的な場所 (地域) にまたがる 1 つのテナントを有効にします。複数地域を有効にすると、お客様は、ユーザーごとに Exchange Online のメールボックスの内容 (データ) の場所を選択できます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="dbac6-p102">(、「既定値」または「場所」と呼ばれる)、初期のテナントの場所は、住所に基づいて決まります。複数地域を有効にすると、「サテライト」の他の場所でのメールボックスを格納することができます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="dbac6-108">サテライトに直接新しいオンラインの Exchange メールボックスを作成しています。</span><span class="sxs-lookup"><span data-stu-id="dbac6-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="dbac6-109">サテライトに既存の Exchange Online メールボックスを移動します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="dbac6-110">サテライトに直接、オンプレミスの Exchange 組織からメールボックスを契約時。</span><span class="sxs-lookup"><span data-stu-id="dbac6-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="dbac6-111">複数地域の構成で使用する以下の地域があります。</span><span class="sxs-lookup"><span data-stu-id="dbac6-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="dbac6-112">アジア太平洋地域</span><span class="sxs-lookup"><span data-stu-id="dbac6-112">Asia Pacific</span></span>

- <span data-ttu-id="dbac6-113">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="dbac6-113">Australia</span></span>

- <span data-ttu-id="dbac6-114">カナダ</span><span class="sxs-lookup"><span data-stu-id="dbac6-114">Canada</span></span>

- <span data-ttu-id="dbac6-115">欧州連合</span><span class="sxs-lookup"><span data-stu-id="dbac6-115">European Union</span></span>

- <span data-ttu-id="dbac6-116">インド (現在インドでの請求先住所を持つ顧客にのみ使用可能)</span><span class="sxs-lookup"><span data-stu-id="dbac6-116">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="dbac6-117">日本</span><span class="sxs-lookup"><span data-stu-id="dbac6-117">Japan</span></span>

- <span data-ttu-id="dbac6-118">韓国</span><span class="sxs-lookup"><span data-stu-id="dbac6-118">Korea</span></span>

- <span data-ttu-id="dbac6-119">英国</span><span class="sxs-lookup"><span data-stu-id="dbac6-119">United Kingdom</span></span>

- <span data-ttu-id="dbac6-120">米国</span><span class="sxs-lookup"><span data-stu-id="dbac6-120">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="dbac6-121">前提条件の構成</span><span class="sxs-lookup"><span data-stu-id="dbac6-121">Prerequisite configuration</span></span>
<span data-ttu-id="dbac6-p103">機能を使用して複数の地域では、Exchange オンラインを開始する前にマイクロソフトは複数地域のサポートのため、Exchange Online のテナントを構成する必要があります。複数地域のライセンスを注文すると 30 日未満で完了を実行する必要があります通常は、この 1 回限りの構成プロセスがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered when you order Multi-Geo licenses and should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="dbac6-p104">構成が開始して完了したときに[Office 365 のメッセージ センター](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093)に通知が表示されます。構成は、複数地域のライセンスを購入するときに自動的にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has started and completed. Configuration is automatically triggered when you buy Multi-Geo licenses.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="dbac6-126">メールボックスの配置と移動</span><span class="sxs-lookup"><span data-stu-id="dbac6-126">Mailbox placement and moves</span></span>
<span data-ttu-id="dbac6-127">マイクロソフトでは、複数地域の必須の構成手順が完了すると、Exchange Online を優先、ユーザー オブジェクトの**PreferredDataLocation**属性が Azure AD にします。</span><span class="sxs-lookup"><span data-stu-id="dbac6-127">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="dbac6-p105">Exchange Online は、オンラインの Exchange のディレクトリ サービス内の**MailboxRegion**プロパティに Azure AD から**PreferredDataLocation**のプロパティを同期します。**MailboxRegion**の値は、地域のユーザーのメールボックスと関連付けられているアーカイブ メールボックスの配置場所を決定します。ユーザーのプライマリ メールボックスとアーカイブ メールボックスを別の地域に存在するを構成することはできません。ユーザー オブジェクト 1 つにつき 1 つだけの地域に設定できます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It isn't possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="dbac6-132">**PreferredDataLocation**が既存のメールボックスを持つユーザーで構成されると、指定した地域に、メールボックスを自動的に移動されます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-132">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="dbac6-133">**PreferredDataLocation**が構成すると、既存のメールボックスにユーザーのメールボックスが指定した地域に準備されます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-133">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="dbac6-134">地域が指定されていない場合は、既定の地域で、メールボックスが配置されます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-134">If no Geo is specified, the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="dbac6-p106">**注**: 複数地域の機能と Skype を地域ごとにホストされているビジネス オンラインの会議のプロパティを使用して**PreferredDataLocation**ユーザー オブジェクトのサービスを検索します。地域ごとにホストされている会議のためのユーザー オブジェクトの**PreferredDataLocation**の値を構成する場合は、それらのユーザーのメールボックスに自動的に移動されます指定した地域に複数地域を有効にした後 Office 365 テナントに。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="dbac6-137">Exchange オンラインで複数の地域の機能の制限</span><span class="sxs-lookup"><span data-stu-id="dbac6-137">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="dbac6-p107">ユーザーのメールボックス、リソース メールボックス (部屋・備品のメールボックス)、および共有メールボックスは、複数地域の機能をサポートします。パブリック フォルダーのメールボックスと Office 365 のグループは、お客様の自宅の地域にのみ配置できます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. You can only place public folder mailboxes and Office 365 Groups in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="dbac6-p108">セキュリティとコンプライアンスの機能 (たとえば、監査および電子的証拠開示) は、Exchange 管理センター (EAC) で使用されるは、複数地域の組織では使用できません。代わりに、セキュリティとコンプライアンスの機能を構成するのには、 [Office 365 のセキュリティとコンプライアンスのセンター](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="dbac6-p109">Mac ユーザーは、outlook は、自分のメールボックスを新しい地域に移動するときに、そのオンライン ・ アーカイブのフォルダーへのアクセスの一時的な損失にすることがあります。この条件では、ユーザーのプライマリとアーカイブ メールボックスが別の地域では地域間のメールボックスの移動は、異なる時間に完了可能性がありますのでに発生します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="dbac6-p110">ユーザーは、Outlook (Outlook Web App または OWA と呼ばれていました)、web 上での地域間で*メールボックス フォルダー*を共有できません。たとえば、欧州連合内のユーザーは、米国内にあるメールボックス内の共有フォルダーを開くに web 上で Outlook を使用できません。ただし、web ユーザーに Outlook は、 [Outlook Web App で別のブラウザー ウィンドウ内の他のユーザーのメールボックスを開く](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)で説明したように別のブラウザー ウィンドウを使用して、別の地域で*その他のメールボックス*を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="dbac6-147">**注**: Windows 上の Outlook ではサポートされて間 Geo メールボックス フォルダーを共有します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-147">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

5. <span data-ttu-id="dbac6-p111">現在、web 上の Outlook でクロス地域カレンダーの委任がサポートされていません。クロス地域カレンダーの委任は、Windows 上の Outlook でサポートされてです。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p111">Currently, cross-Geo calendar delegation isn't supported in Outlook on the web. Cross-Geo calendar delegation is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="dbac6-150">管理</span><span class="sxs-lookup"><span data-stu-id="dbac6-150">Administration</span></span> 
<span data-ttu-id="dbac6-p112">リモート PowerShell は、表示して、Office 365 環境内の地域に関連するプロパティを構成する必要があります。Office 365 の管理に使用される各種の PowerShell モジュールについては、 [Office 365 の管理、および Windows PowerShell で Exchange のオンライン](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p112">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="dbac6-p113">[Microsoft Azure Active Directory の PowerShell モジュール](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx)の v1.1.166.0 または後での v1.x ユーザー オブジェクトの**PreferredDataLocation**プロパティを表示する必要があります。Azure AD PowerShell に接続するには、 [Office 365 の PowerShell への接続](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p113">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="dbac6-155">オンライン PowerShell を Exchange に接続するには、 [Exchange オンライン PowerShell への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbac6-155">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="dbac6-156">Exchange オンライン PowerShell を使用して特定の地域に直接接続します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-156">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="dbac6-p114">通常、Exchange オンライン PowerShell では、既定の地域に接続されます。既定以外の地域に直接接続することもできます。パフォーマンスの向上のためだけにその地域のユーザーを管理するときに、既定以外の地域への直接接続をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p114">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="dbac6-p115">特定の地域に接続するには*ConnectionUri*パラメーターは通常の接続手順とは異なるです。コマンドと値の残りの部分は、同じです。手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p115">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="dbac6-163">ローカル コンピューターに Windows PowerShell を開き次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-163">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="dbac6-164">**Windows PowerShell の資格情報の要求**] ダイアログ ボックスで、作業時間や学校のアカウントとパスワードを入力し、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbac6-164">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="dbac6-p116">交換`<emailaddress>`、電子メールのアドレスでターゲット地域内のメールボックス**、**および次のコマンドを実行します。メールボックスとの関連性のステップ 1 で資格情報のアクセス許可は、ファクターではありません。電子メール アドレスだけで位置を通知 Exchange オンライン接続します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p116">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="dbac6-167">などの olga@contoso.onmicrosoft.com に接続する地域で有効なメールボックスの電子メール アドレスがある場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-167">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="dbac6-168">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-168">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="dbac6-169">Azure AD 接続バージョン要件</span><span class="sxs-lookup"><span data-stu-id="dbac6-169">Azure AD Connect version requirements</span></span>
<span data-ttu-id="dbac6-p117">AAD の接続のバージョン 1.1.524.0 または後でのみサポートされているメソッド、オンプレミスの Active Directory から同期されるユーザー オブジェクトの**PreferredDataLocation**プロパティを設定するためです。詳細についてを参照してください[Azure Active Directory 接続の同期: Office 365 のリソースの優先データのパスを構成する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)です。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p117">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="dbac6-172">地域コード</span><span class="sxs-lookup"><span data-stu-id="dbac6-172">Geo Codes</span></span>
<span data-ttu-id="dbac6-p118">**PreferredDataLocation**プロパティで、地域を指定するのにには、3 文字のコードを使用します。次の表は、使用可能な地域のコードを一覧します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p118">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="dbac6-175">geo</span><span class="sxs-lookup"><span data-stu-id="dbac6-175">Geo</span></span> |<span data-ttu-id="dbac6-176">コード</span><span class="sxs-lookup"><span data-stu-id="dbac6-176">Code</span></span> |
|---------|---------|
|<span data-ttu-id="dbac6-177">アジア/太平洋地域</span><span class="sxs-lookup"><span data-stu-id="dbac6-177">Asia/Pacific</span></span> |<span data-ttu-id="dbac6-178">APC</span><span class="sxs-lookup"><span data-stu-id="dbac6-178">APC</span></span> |
|<span data-ttu-id="dbac6-179">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="dbac6-179">Australia</span></span> |<span data-ttu-id="dbac6-180">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="dbac6-180">AUS</span></span> |
|<span data-ttu-id="dbac6-181">カナダ</span><span class="sxs-lookup"><span data-stu-id="dbac6-181">Canada</span></span> |<span data-ttu-id="dbac6-182">できます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-182">CAN</span></span> |
|<span data-ttu-id="dbac6-183">欧州連合</span><span class="sxs-lookup"><span data-stu-id="dbac6-183">European Union</span></span> |<span data-ttu-id="dbac6-184">EUR</span><span class="sxs-lookup"><span data-stu-id="dbac6-184">EUR</span></span> |
|<span data-ttu-id="dbac6-185">インド</span><span class="sxs-lookup"><span data-stu-id="dbac6-185">India</span></span> |<span data-ttu-id="dbac6-186">IND</span><span class="sxs-lookup"><span data-stu-id="dbac6-186">IND</span></span> |
|<span data-ttu-id="dbac6-187">日本</span><span class="sxs-lookup"><span data-stu-id="dbac6-187">Japan</span></span> |<span data-ttu-id="dbac6-188">日本語版</span><span class="sxs-lookup"><span data-stu-id="dbac6-188">JPN</span></span> |
|<span data-ttu-id="dbac6-189">韓国</span><span class="sxs-lookup"><span data-stu-id="dbac6-189">Korea</span></span> |<span data-ttu-id="dbac6-190">KOR</span><span class="sxs-lookup"><span data-stu-id="dbac6-190">KOR</span></span> |
|<span data-ttu-id="dbac6-191">英国</span><span class="sxs-lookup"><span data-stu-id="dbac6-191">United Kingdom</span></span> |<span data-ttu-id="dbac6-192">GBR</span><span class="sxs-lookup"><span data-stu-id="dbac6-192">GBR</span></span> |
|<span data-ttu-id="dbac6-193">米国</span><span class="sxs-lookup"><span data-stu-id="dbac6-193">United States</span></span> |<span data-ttu-id="dbac6-194">名</span><span class="sxs-lookup"><span data-stu-id="dbac6-194">NAM</span></span> |

<span data-ttu-id="dbac6-p119">**注**: **PreferredDataLocation**および**MailboxRegion**プロパティは、エラーのチェックなしで文字列です。無効な値 (たとえば、NAN) を入力する場合は、既定の地域で、メールボックスが配置されます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p119">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="dbac6-197">オンラインの Exchange 組織で構成されている使用可能な地域を表示します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-197">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="dbac6-198">オンラインの Exchange 組織で構成されている地域の一覧を表示するには、次のコマンドを実行 Exchange オンライン PowerShell:</span><span class="sxs-lookup"><span data-stu-id="dbac6-198">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

<span data-ttu-id="dbac6-199">コマンドの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dbac6-199">The output of the command looks like this:</span></span>

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="dbac6-200">メールボックスの地域の場所を検索します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-200">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="dbac6-201">Exchange オンライン PowerShell で**Get メールボックス**コマンドレットでは、メールボックスには次の地域に関連するプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-201">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="dbac6-202">**データベース**: データベース名の最初の 3 つの文字が、メールボックスが置かれている場所を表示する地域コードに対応します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-202">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located.</span></span>

- <span data-ttu-id="dbac6-203">**MailboxRegion**: (Azure AD では、 **PreferredDataLocation**の同期) の管理者によって設定された地域コードを指定します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-203">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="dbac6-204">**MailboxRegionLastUpdateTime**: MailboxRegion が最終更新日時 (自動または手動のいずれか) を示します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-204">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="dbac6-205">メールボックスのこれらのプロパティを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-205">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="dbac6-206">などのメールボックスの chris@contoso.onmicrosoft.com の地域情報を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-206">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="dbac6-207">コマンドの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dbac6-207">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> <span data-ttu-id="dbac6-208">地域コードは、データベース名が**MailboxRegion**の値に一致しない場合 (これらのプロパティ値の間の不一致の Exchange Online の検索) **MailboxRegion**の値で指定された地域に、メールボックスを自動的に移動されます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-208">If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a><span data-ttu-id="dbac6-209">既存のクラウドのメールボックスを特定の地域に移動します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-209">Move an existing cloud mailbox to a specific Geo</span></span>
<span data-ttu-id="dbac6-210">Windows PowerShell の Azure AD モジュールで**Get MsolUser**と**セット MsolUser**コマンドレットを使用して、表示、またはユーザーのメールボックスを格納する地域を指定します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-210">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a user's mailbox will be stored.</span></span>

<span data-ttu-id="dbac6-211">ユーザーの**PreferredDataLocation**の値を表示するには、Azure AD PowerShell でこの構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-211">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="dbac6-212">たとえば、ユーザーの michelle@contoso.onmicrosoft.com の**PreferredDataLocation**の値を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-212">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="dbac6-213">コマンドの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dbac6-213">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="dbac6-214">クラウド専用のユーザー オブジェクトの**PreferredDataLocation**の値を変更するには、Azure AD PowerShell で次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-214">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="dbac6-215">などに、欧州連合 (EUR) ユーザーの michelle@contoso.onmicrosoft.com の**PreferredDataLocation**値を設定するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-215">For example, to set the **PreferredDataLocation** value to the European Union (EUR) for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="dbac6-216">**注**:</span><span class="sxs-lookup"><span data-stu-id="dbac6-216">**Notes**:</span></span>

- <span data-ttu-id="dbac6-p120">説明したように、オンプレミスの Active Directory からユーザーの同期オブジェクトには、この手順を使用できません。AAD の接続を使用して**PreferredDataLocation**の値を変更する必要があります。詳細についてを参照してください[Azure Active Directory 接続の同期: Office 365 のリソースの優先データのパスを構成する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)です。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p120">As mentioned previously for synchronized user objects from on-premises Active Directory, you can't use this procedure. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="dbac6-220">メールボックスの移動にかかる時間は、いくつかの要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="dbac6-220">How long it takes to move a mailbox depends on several factors:</span></span>
 
  - <span data-ttu-id="dbac6-221">サイズとメールボックスの種類。</span><span class="sxs-lookup"><span data-stu-id="dbac6-221">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="dbac6-222">移動中のメールボックスの数です。</span><span class="sxs-lookup"><span data-stu-id="dbac6-222">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="dbac6-223">リソースの可用性の移動します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-223">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="dbac6-224">移動には、証拠保全上にあるメールボックスが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="dbac6-224">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="dbac6-p121">電子証拠開示の目的が無効になっている状態で、 **PreferredDataLocation**の値を変更することで移動できないのは、証拠保全上のメールボックスを無効にします。保留中の訴訟で無効になっているメールボックスを移動するのには</span><span class="sxs-lookup"><span data-stu-id="dbac6-p121">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes can't be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="dbac6-227">一時的にメールボックスにライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-227">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="dbac6-228">**PreferredDataLocation**を変更します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-228">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="dbac6-229">無効の状態に戻すことを選択した地域に移動した後、メールボックスからライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-229">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="dbac6-230">特定の地域で新しいクラウドのメールボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-230">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="dbac6-231">特定地域での新しいメールボックスを作成するには次の手順のいずれかを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbac6-231">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="dbac6-232">前で説明したように**PreferredDataLocation**の値を構成するセクションの*前に*(たとえば、ユーザーにライセンスを割り当てる前に**PreferredDataLocation**値を設定) によって、Exchange Online のメールボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-232">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online (for example, by configuring the **PreferredDataLocation** value on a user before assigning a license).</span></span> 

- <span data-ttu-id="dbac6-233">**PreferredDataLocation**値を設定すると同時にライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-233">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="dbac6-234">特定の地域で、新しいクラウド専用ライセンスを受けたユーザー (AAD 接続の同期) を作成するには、Azure AD PowerShell で次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-234">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="dbac6-235">次の使用例は、次の値を持つエリザベス Brunner の新しいユーザー アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-235">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="dbac6-236">ユーザー プリンシパル名: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="dbac6-236">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="dbac6-237">名: エリザベス</span><span class="sxs-lookup"><span data-stu-id="dbac6-237">First name: Elizabeth</span></span>

- <span data-ttu-id="dbac6-238">姓、名: Brunner</span><span class="sxs-lookup"><span data-stu-id="dbac6-238">Last name: Brunner</span></span>

- <span data-ttu-id="dbac6-239">エリザベス Brunner の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-239">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="dbac6-240">パスワード: は、ランダムに生成され、(*パスワード*パラメーターは使用しない) ために、コマンドの結果に示すように</span><span class="sxs-lookup"><span data-stu-id="dbac6-240">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="dbac6-241">ライセンス: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="dbac6-241">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

<span data-ttu-id="dbac6-242">3 場所: オーストラリア (オーストラリア)</span><span class="sxs-lookup"><span data-stu-id="dbac6-242">3- Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="dbac6-243">新しいユーザー アカウントを作成して、Azure AD PowerShell で LicenseAssignment の値を検索する方法の詳細については、 [Office 365 の PowerShell でユーザー アカウントを作成](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)し、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbac6-243">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="dbac6-p122">メールボックスを有効にし、 **PreferredDataLocation**で指定されている地域で直接作成するメールボックスが必要な Exchange の PowerShell を使用する場合は、**有効にするメールボックス**や**新規メールボックス**などの Exchange Online のコマンドレットを使用する必要があります。直接、クラウド サービスに対して。**有効にする RemoteMailbox**オンプレミスの Exchange コマンドレットを使用する場合は、既定の地域で、メールボックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p122">If you are using Exchange PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="dbac6-246">既存のオンボード設置特定地域内のメールボックス</span><span class="sxs-lookup"><span data-stu-id="dbac6-246">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="dbac6-247">など[、EAC での移行のダッシュ ボード](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)の[新規 MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch)コマンドレットでは、Exchange オンライン Exchange オンライン、オンプレミスの Exchange 組織からメールボックスを移行するのには、契約時の標準的なツールとプロセスを使用することができます。PowerShell。</span><span class="sxs-lookup"><span data-stu-id="dbac6-247">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="dbac6-p123">最初のステップでは、onboarded では、Azure AD では、適切な**PreferredDataLocation**値を設定することを確認するには、各メールボックスのユーザー オブジェクトが存在することを確認します。契約時のツールは、 **PreferredDataLocation**の値が反映され、指定の地域に直接メールボックスが移行されます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p123">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="dbac6-250">または、Exchange オンライン PowerShell の[新規 MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest)コマンドレットを使用して特定の地域で直接オンボードのメールボックスに次の手順を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="dbac6-250">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="dbac6-p124">Onboarded と**PreferredDataLocation**は、Azure AD で目的の値に設定されている各メールボックスのユーザー オブジェクトが存在することを確認します。**PreferredDataLocation**の値が同期されます、対応するメール ユーザー オブジェクトの**MailboxRegion**属性に Exchange オンライン。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p124">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="dbac6-253">特定の衛星からの接続方法を使用して、このトピックで前述した地域に直接接続します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-253">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="dbac6-254">Exchange オンラインの PowerShell で次のコマンドを実行して、変数にメールボックスの移行を実行するために使用される設置管理者の資格情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-254">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="dbac6-255">Exchange オンラインの PowerShell で次の例のような新しい**新しい MoveRequest**を作成します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-255">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="dbac6-256">サテライトに現在接続している地域に、オンプレミスの Exchange から移行する必要がありますすべてのメールボックスに対して、手順 4 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-256">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="dbac6-257">異なるサテライト地域を追加のメールボックスを移行する場合は、それぞれ固有のサテライト Geo の手順 2 4 からを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-257">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="dbac6-258">複数地域のレポート</span><span class="sxs-lookup"><span data-stu-id="dbac6-258">Multi-Geo Reporting</span></span>
<span data-ttu-id="dbac6-p125">Office 365 管理センターの**利用状況レポートの複数の地域**では、Geo でユーザー数が表示されます。レポートでは、当月のユーザーの分散を表示し、過去 6 か月の履歴データを提供します。</span><span class="sxs-lookup"><span data-stu-id="dbac6-p125">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
 
