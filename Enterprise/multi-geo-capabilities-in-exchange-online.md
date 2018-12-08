---
title: Exchange オンラインで複数の地域の機能
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Exchange Online の機能を複数地域での複数の地理的な領域に、Office 365 のプレゼンスを展開します。
ms.openlocfilehash: 6acd2ffab1f35b74d06d6ab5f7bfcbf70f88f8b4
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200740"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="da773-103">Exchange オンラインで複数の地域の機能</span><span class="sxs-lookup"><span data-stu-id="da773-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="da773-p101">Office 365 に複数の地域の機能は、複数の地域にまたがる 1 つのテナントを有効にします。複数地域を有効にすると、お客様は、ユーザーごとに Exchange Online のメールボックスの内容 (データ) の場所を選択できます。</span><span class="sxs-lookup"><span data-stu-id="da773-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations. When multi-geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="da773-p102">(中央の場所と呼ばれる)、初期のテナントの場所は、住所に基づいて決まります。複数地域を有効にすると、によって、他のサテライト オフィスでのメールボックスを配置できます。</span><span class="sxs-lookup"><span data-stu-id="da773-p102">Your initial tenant location (referred to as the central location) is determined based on your billing address. When multi-geo is enabled, you can place mailboxes in additional satellite locations by:</span></span>

- <span data-ttu-id="da773-108">サテライトの場所に直接新しいオンラインの Exchange メールボックスを作成しています。</span><span class="sxs-lookup"><span data-stu-id="da773-108">Creating a new Exchange Online mailbox directly in a satellite location.</span></span>

- <span data-ttu-id="da773-109">サテライトの場所に既存の Exchange Online メールボックスを移動します。</span><span class="sxs-lookup"><span data-stu-id="da773-109">Moving an existing Exchange Online mailbox into a satellite location.</span></span>

- <span data-ttu-id="da773-110">サテライトの場所に直接、オンプレミスの Exchange 組織からメールボックスを契約時。</span><span class="sxs-lookup"><span data-stu-id="da773-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location.</span></span>

<span data-ttu-id="da773-111">複数地域の構成で使用するため、以下の地域があります。</span><span class="sxs-lookup"><span data-stu-id="da773-111">The following geo locations are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="da773-112">アジア太平洋地域</span><span class="sxs-lookup"><span data-stu-id="da773-112">Asia Pacific</span></span>

- <span data-ttu-id="da773-113">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="da773-113">Australia</span></span>

- <span data-ttu-id="da773-114">カナダ</span><span class="sxs-lookup"><span data-stu-id="da773-114">Canada</span></span>

- <span data-ttu-id="da773-115">欧州連合</span><span class="sxs-lookup"><span data-stu-id="da773-115">European Union</span></span>

- <span data-ttu-id="da773-116">フランス</span><span class="sxs-lookup"><span data-stu-id="da773-116">France</span></span>

- <span data-ttu-id="da773-117">インド</span><span class="sxs-lookup"><span data-stu-id="da773-117">India</span></span>

- <span data-ttu-id="da773-118">日本</span><span class="sxs-lookup"><span data-stu-id="da773-118">Japan</span></span>

- <span data-ttu-id="da773-119">韓国</span><span class="sxs-lookup"><span data-stu-id="da773-119">Korea</span></span>

- <span data-ttu-id="da773-120">イギリス</span><span class="sxs-lookup"><span data-stu-id="da773-120">United Kingdom</span></span>

- <span data-ttu-id="da773-121">米国</span><span class="sxs-lookup"><span data-stu-id="da773-121">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="da773-122">前提条件の構成</span><span class="sxs-lookup"><span data-stu-id="da773-122">Prerequisite configuration</span></span>
<span data-ttu-id="da773-p103">機能を使用して複数の地域では、Exchange オンラインを開始する前にマイクロソフトは複数地域のサポートのため、Exchange Online のテナントを構成する必要があります。Office 365 の複数の地域のライセンス表示して、テナント内の順序を後に、この 1 回限りの構成プロセスがトリガーされます。1 回のみ構成する必要があります通常かかる 30 日未満で完了します。Office 365 の複数の地域を注文するのには、マイクロソフトの担当者に問い合わせてください。詳細についてを参照してくださいhttps://aka.ms/Multi-Geo。</span><span class="sxs-lookup"><span data-stu-id="da773-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for multi-geo support. This one-time configuration process is triggered after you order Office 365 Multi-Geo and the licenses show up in your tenant. This one-time configuration process should typically take less than 30 days to complete. To order Office 365 Multi-Geo, contact your Microsoft representative. For more information, see https://aka.ms/Multi-Geo.</span></span>

<span data-ttu-id="da773-p104">構成が完了したときは、 [Office 365 のメッセージ センター](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093)に通知が届きます。テナントに、複数地域のライセンスが表示されたら、構成が自動的にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="da773-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has completed. Configuration is automatically triggered once your multi-geo licenses show up in your tenant.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="da773-130">メールボックスの配置と移動</span><span class="sxs-lookup"><span data-stu-id="da773-130">Mailbox placement and moves</span></span>
<span data-ttu-id="da773-131">マイクロソフトでは、前提条件の複数の地域の設定手順が完了すると、Exchange Online を優先、ユーザー オブジェクトの**PreferredDataLocation**属性が Azure AD にします。</span><span class="sxs-lookup"><span data-stu-id="da773-131">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="da773-p105">Exchange Online は、オンラインの Exchange のディレクトリ サービス内の**MailboxRegion**プロパティに Azure AD から**PreferredDataLocation**のプロパティを同期します。**MailboxRegion**の値は、地域のユーザーのメールボックスと関連付けられているアーカイブ メールボックスの配置場所を決定します。ユーザーのプライマリ メールボックス、アーカイブ メールボックスを別の地域の場所に存在するを構成することはできません。ユーザー オブジェクトごと、地域の 1 つだけの場所を構成できます。</span><span class="sxs-lookup"><span data-stu-id="da773-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations. Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="da773-136">**PreferredDataLocation**が既存のメールボックスを持つユーザーで構成されると、メールボックスの再配置のキューに入れ、地域を指定した場所に自動的に移動します。</span><span class="sxs-lookup"><span data-stu-id="da773-136">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="da773-137">**PreferredDataLocation**が構成すると、既存のメールボックスにユーザーのメールボックスが地域を指定した場所に準備されます。</span><span class="sxs-lookup"><span data-stu-id="da773-137">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="da773-138">ユーザーに**PreferredDataLocation**を指定しない場合は、中央の場所で、メールボックスが配置されます。</span><span class="sxs-lookup"><span data-stu-id="da773-138">When **PreferredDataLocation** is not specified on a user, the mailbox will be placed in the central location.</span></span>

- <span data-ttu-id="da773-139">**PreferredDataLocation**コードが正しくない場合 (たとえば、型名ではなく NAN の)、メールボックスは、中央の場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="da773-139">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be placed in the central location.</span></span>

<span data-ttu-id="da773-p106">**注**: 複数地域の機能と Skype を地域ごとにホストされているビジネス オンラインの会議のプロパティを使用して**PreferredDataLocation**ユーザー オブジェクトのサービスを検索します。地域ごとにホストされている会議のためのユーザー オブジェクトの**PreferredDataLocation**の値を構成する場合は、それらのユーザーのメールボックスに自動的に移動されます地域を指定した場所に複数地域を有効にした後 Office 365 テナントに。</span><span class="sxs-lookup"><span data-stu-id="da773-p106">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="da773-142">Exchange オンラインで複数の地域の機能の制限</span><span class="sxs-lookup"><span data-stu-id="da773-142">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="da773-p107">ユーザーのメールボックス、リソース メールボックス (部屋・備品のメールボックス)、および共有メールボックスは、複数地域の機能をサポートします。パブリック フォルダーのメールボックスと Office 365 のグループは、中央の場所に残ります。</span><span class="sxs-lookup"><span data-stu-id="da773-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support multi-geo features. Public Folder Mailboxes and Office 365 Groups remain in the central location.</span></span>
 
2. <span data-ttu-id="da773-p108">セキュリティとコンプライアンスの機能 (たとえば、監査および電子的証拠開示) は、Exchange 管理センター (EAC) で使用されるは、複数地域の組織では使用できません。代わりに、セキュリティとコンプライアンスの機能を構成するのには、 [Office 365 のセキュリティとコンプライアンスのセンター](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da773-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="da773-p109">Mac ユーザーは、outlook は、地域の新しい場所に自分のメールボックスを移動するときに、そのオンライン ・ アーカイブのフォルダーへのアクセスの一時的な損失にすることがあります。この条件では、ユーザーのプライマリとアーカイブ メールボックスが別の地域の場所ではメールボックスの移動の間の地域は、さまざまな時点で完了可能性がありますのでに発生します。</span><span class="sxs-lookup"><span data-stu-id="da773-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location. This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="da773-p110">ユーザーは、Outlook (Outlook Web App または OWA と呼ばれていました)、web 上の場所を地域全体で*メールボックス フォルダー*を共有できません。たとえば、欧州連合内のユーザーは、米国内にあるメールボックス内の共有フォルダーを開くに web 上で Outlook を使用できません。ただし、Web ユーザーに Outlook は、 [Outlook Web App で別のブラウザー ウィンドウ内の他のユーザーのメールボックスを開く](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)で説明したように別のブラウザー ウィンドウを使用して、別の地域で*その他のメールボックス*を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="da773-p110">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="da773-152">**注**: Windows 上の Outlook ではサポートされて間 geo メールボックス フォルダーを共有します。</span><span class="sxs-lookup"><span data-stu-id="da773-152">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="da773-153">管理</span><span class="sxs-lookup"><span data-stu-id="da773-153">Administration</span></span> 
<span data-ttu-id="da773-p111">リモート PowerShell は、表示し、Office 365 環境内の複数の地域のプロパティを構成する必要があります。Office 365 の管理に使用される各種の PowerShell モジュールについては、 [Office 365 の管理、および Windows PowerShell で Exchange のオンライン](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da773-p111">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="da773-p112">[Microsoft Azure Active Directory の PowerShell モジュール](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx)の v1.1.166.0 または後での v1.x ユーザー オブジェクトの**PreferredDataLocation**プロパティを表示する必要があります。AAD に AAD の接続経由で同期するユーザー オブジェクトには、AAD PowerShell を使用して直接変更を加える、 **PreferredDataLocation**の値を持つことはできません。AAD PowerShell を使用してクラウド専用のユーザー オブジェクトを変更できます。Azure AD PowerShell に接続するには、 [Office 365 の PowerShell への接続](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da773-p112">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="da773-160">オンライン PowerShell を Exchange に接続するには、 [Exchange オンライン PowerShell への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da773-160">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="da773-161">Exchange オンライン PowerShell を使用して特定の地域に直接接続します。</span><span class="sxs-lookup"><span data-stu-id="da773-161">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="da773-p113">通常、Exchange のオンライン PowerShell は、geo の既定の場所に接続されます。既定以外の地域の場所に直接接続することもできます。パフォーマンスの向上のためだけにその地域の場所のユーザーを管理するときに、既定以外の地域の場所への直接接続をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="da773-p113">Typically, Exchange Online PowerShell will connect to the default geo location. But, you can also connect directly to non-default geo locations. Because of performance improvements, we recommend connecting directly to the non-default geo location when you only manage users in that geo location.</span></span>

<span data-ttu-id="da773-p114">特定の地域に接続するには*ConnectionUri*パラメーターは通常の接続手順とは異なるです。コマンドと値の残りの部分は、同じです。手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="da773-p114">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="da773-168">ローカル コンピューターに Windows PowerShell を開き次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="da773-168">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="da773-169">**Windows PowerShell の資格情報の要求**] ダイアログ ボックスで、作業時間や学校のアカウントとパスワードを入力し、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da773-169">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="da773-p115">交換`<emailaddress>`のターゲット地域の場所と実行次のコマンドでメールボックス**の**電子メール アドレスがあります。メールボックスとの関連性のステップ 1 で資格情報のアクセス許可は、ファクターではありません。電子メール アドレスだけで位置を通知 Exchange オンライン接続します。</span><span class="sxs-lookup"><span data-stu-id="da773-p115">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="da773-172">などの olga@contoso.onmicrosoft.com に接続する地域で有効なメールボックスの電子メール アドレスがある場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="da773-172">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="da773-173">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="da773-173">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="da773-174">Azure AD 接続バージョン要件</span><span class="sxs-lookup"><span data-stu-id="da773-174">Azure AD Connect version requirements</span></span>
<span data-ttu-id="da773-p116">AAD の接続のバージョン 1.1.524.0 または後でのみサポートされているメソッド、オンプレミスの Active Directory から同期されるユーザー オブジェクトの**PreferredDataLocation**プロパティを設定するためです。AAD に AAD の接続経由で同期するユーザー オブジェクトには、AAD PowerShell を使用して直接変更を加える、 **PreferredDataLocation**の値を持つことはできません。AAD PowerShell を使用してクラウド専用のユーザー オブジェクトを変更できます。詳細についてを参照してください[Azure Active Directory 接続の同期: Office 365 のリソースの優先データのパスを構成する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)です。</span><span class="sxs-lookup"><span data-stu-id="da773-p116">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="da773-179">地域コード</span><span class="sxs-lookup"><span data-stu-id="da773-179">Geo Codes</span></span>
<span data-ttu-id="da773-p117">**PreferredDataLocation**プロパティで、地域を指定するのにには、3 文字のコードを使用します。次の表は、使用可能な地域のコードを一覧します。</span><span class="sxs-lookup"><span data-stu-id="da773-p117">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="da773-182">geo</span><span class="sxs-lookup"><span data-stu-id="da773-182">Geo</span></span> |<span data-ttu-id="da773-183">コード</span><span class="sxs-lookup"><span data-stu-id="da773-183">Code</span></span> |
|---------|---------|
|<span data-ttu-id="da773-184">アジア/太平洋地域</span><span class="sxs-lookup"><span data-stu-id="da773-184">Asia/Pacific</span></span> |<span data-ttu-id="da773-185">APC</span><span class="sxs-lookup"><span data-stu-id="da773-185">APC</span></span> |
|<span data-ttu-id="da773-186">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="da773-186">Australia</span></span> |<span data-ttu-id="da773-187">AUS</span><span class="sxs-lookup"><span data-stu-id="da773-187">AUS</span></span> |
|<span data-ttu-id="da773-188">カナダ</span><span class="sxs-lookup"><span data-stu-id="da773-188">Canada</span></span> |<span data-ttu-id="da773-189">CAN</span><span class="sxs-lookup"><span data-stu-id="da773-189">CAN</span></span> |
|<span data-ttu-id="da773-190">欧州連合</span><span class="sxs-lookup"><span data-stu-id="da773-190">European Union</span></span> |<span data-ttu-id="da773-191">EUR</span><span class="sxs-lookup"><span data-stu-id="da773-191">EUR</span></span> |
|<span data-ttu-id="da773-192">フランス</span><span class="sxs-lookup"><span data-stu-id="da773-192">France</span></span> |<span data-ttu-id="da773-193">FRA</span><span class="sxs-lookup"><span data-stu-id="da773-193">FRA</span></span>|
|<span data-ttu-id="da773-194">インド</span><span class="sxs-lookup"><span data-stu-id="da773-194">India</span></span> |<span data-ttu-id="da773-195">IND</span><span class="sxs-lookup"><span data-stu-id="da773-195">IND</span></span> |
|<span data-ttu-id="da773-196">日本</span><span class="sxs-lookup"><span data-stu-id="da773-196">Japan</span></span> |<span data-ttu-id="da773-197">JPN</span><span class="sxs-lookup"><span data-stu-id="da773-197">JPN</span></span> |
|<span data-ttu-id="da773-198">韓国</span><span class="sxs-lookup"><span data-stu-id="da773-198">Korea</span></span> |<span data-ttu-id="da773-199">KOR</span><span class="sxs-lookup"><span data-stu-id="da773-199">KOR</span></span> |
|<span data-ttu-id="da773-200">イギリス</span><span class="sxs-lookup"><span data-stu-id="da773-200">United Kingdom</span></span> |<span data-ttu-id="da773-201">GBR</span><span class="sxs-lookup"><span data-stu-id="da773-201">GBR</span></span> |
|<span data-ttu-id="da773-202">米国</span><span class="sxs-lookup"><span data-stu-id="da773-202">United States</span></span> |<span data-ttu-id="da773-203">NAM</span><span class="sxs-lookup"><span data-stu-id="da773-203">NAM</span></span> |

<span data-ttu-id="da773-p118">**注**: **PreferredDataLocation**および**MailboxRegion**プロパティは、エラーのチェックなしで文字列です。無効な値 (たとえば、NAN) を入力する場合は、既定の地域で、メールボックスが配置されます。</span><span class="sxs-lookup"><span data-stu-id="da773-p118">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="da773-206">オンラインの Exchange 組織で構成されている使用可能な地域を表示します。</span><span class="sxs-lookup"><span data-stu-id="da773-206">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="da773-207">オンラインの Exchange 組織で構成されている地域の一覧を表示するには、次のコマンドを実行 Exchange オンライン PowerShell:</span><span class="sxs-lookup"><span data-stu-id="da773-207">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

<span data-ttu-id="da773-208">コマンドの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="da773-208">The output of the command looks like this:</span></span>

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a><span data-ttu-id="da773-209">Geo オンラインの Exchange 組織の既定の設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="da773-209">View the default Geo for your Exchange Online organization</span></span>
<span data-ttu-id="da773-210">オンラインの Exchange 組織の既定の地域を表示するには、次のコマンドを実行 Exchange オンライン PowerShell:</span><span class="sxs-lookup"><span data-stu-id="da773-210">To view the default geo of your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

<span data-ttu-id="da773-211">コマンドの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="da773-211">The output of the command looks like this:</span></span>

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="da773-212">メールボックスの地域の場所を検索します。</span><span class="sxs-lookup"><span data-stu-id="da773-212">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="da773-213">メールボックスのプロパティを Exchange オンライン PowerShell 表示次の複数の地域で**取得メールボックス**コマンドレットに関連します。</span><span class="sxs-lookup"><span data-stu-id="da773-213">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="da773-p119">**データベース**: データベース名の最初の 3 つの文字が、メールボックスが置かれている場所を表示する地域コードに対応します。オンライン アーカイブ メールボックスの**ArchiveDatabase**プロパティを使用してください。</span><span class="sxs-lookup"><span data-stu-id="da773-p119">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located. For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="da773-216">**MailboxRegion**: (Azure AD では、 **PreferredDataLocation**の同期) の管理者によって設定された地域場所コードを指定します。</span><span class="sxs-lookup"><span data-stu-id="da773-216">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="da773-217">**MailboxRegionLastUpdateTime**: MailboxRegion が最終更新日時 (自動または手動のいずれか) を示します。</span><span class="sxs-lookup"><span data-stu-id="da773-217">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="da773-218">メールボックスのこれらのプロパティを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="da773-218">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="da773-219">などのメールボックスの chris@contoso.onmicrosoft.com の地域情報を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="da773-219">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="da773-220">コマンドの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="da773-220">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="da773-221">**注:** 地域場所コード、データベース名には、 **MailboxRegion**の値と一致しない、メールボックスの再配置のキューに自動的にするなり、 **MailboxRegion**の値で指定された地域の場所に移動 (Exchange のオンライン検索は一致しないこれらのプロパティ値の間)。</span><span class="sxs-lookup"><span data-stu-id="da773-221">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a><span data-ttu-id="da773-222">既存クラウド専用のメールボックスを特定の地域に移動します。</span><span class="sxs-lookup"><span data-stu-id="da773-222">Move an existing cloud-only mailbox to a specific Geo</span></span>
<span data-ttu-id="da773-p120">クラウド専用のユーザーは、AAD の接続を使用してテナントのときではないユーザーです。Azure AD で直接、このユーザーが作成されました。Windows PowerShell の Azure AD モジュールで**Get MsolUser**と**セット MsolUser**コマンドレットを使用して、表示またはクラウドのみユーザーのメールボックスを格納する地域を指定します。</span><span class="sxs-lookup"><span data-stu-id="da773-p120">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect. This user was created directly in Azure AD. Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="da773-226">ユーザーの**PreferredDataLocation**の値を表示するには、Azure AD PowerShell でこの構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="da773-226">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="da773-227">たとえば、ユーザーの michelle@contoso.onmicrosoft.com の**PreferredDataLocation**の値を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="da773-227">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="da773-228">コマンドの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="da773-228">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="da773-229">クラウド専用のユーザー オブジェクトの**PreferredDataLocation**の値を変更するには、Azure AD PowerShell で次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="da773-229">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="da773-230">たとえば、ユーザー michelle@contoso.onmicrosoft.com の欧州連合 (EUR) の地域には、 **PreferredDataLocation**値を設定するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="da773-230">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="da773-231">**注**:</span><span class="sxs-lookup"><span data-stu-id="da773-231">**Notes**:</span></span>

- <span data-ttu-id="da773-p121">説明したように以前は使用できませんこの手順、オンプレミスの Active Directory から同期されたユーザー オブジェクトの。AAD の接続を使用して**PreferredDataLocation**の値を変更する必要があります。詳細についてを参照してください[Azure Active Directory 接続の同期: Office 365 のリソースの優先データのパスを構成する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)です。</span><span class="sxs-lookup"><span data-stu-id="da773-p121">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="da773-235">かかる目的の地域の別の場所に、現在の地域は、いくつかの要因によって異なります、mailboxfrom を再配置します。</span><span class="sxs-lookup"><span data-stu-id="da773-235">How long it takes to relocate a mailboxfrom its current geo to the new desired geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="da773-236">サイズとメールボックスの種類。</span><span class="sxs-lookup"><span data-stu-id="da773-236">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="da773-237">移動中のメールボックスの数です。</span><span class="sxs-lookup"><span data-stu-id="da773-237">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="da773-238">リソースの可用性の移動します。</span><span class="sxs-lookup"><span data-stu-id="da773-238">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="da773-239">移動には、証拠保全上にあるメールボックスが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="da773-239">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="da773-p122">電子証拠開示の目的が無効になっている状態で、 **PreferredDataLocation**の値を変更することで移動できないのは、証拠保全上のメールボックスを無効にします。保留中の訴訟で無効になっているメールボックスを移動するのには</span><span class="sxs-lookup"><span data-stu-id="da773-p122">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="da773-242">一時的にメールボックスにライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="da773-242">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="da773-243">**PreferredDataLocation**を変更します。</span><span class="sxs-lookup"><span data-stu-id="da773-243">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="da773-244">無効の状態に戻すことを選択した地域の場所に、移動した後、メールボックスからライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="da773-244">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="da773-245">特定の地域で新しいクラウドのメールボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="da773-245">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="da773-246">地域の特定の場所に新しいメールボックスを作成するには次の手順のいずれかを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da773-246">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="da773-p123">前のセクション*の前に*メールボックスの作成は、オンライン Exchange で説明したように、 **PreferredDataLocation**の値を構成します。ユーザーにライセンスを割り当てる前に、たとえば、 **PreferredDataLocation**の値を構成します。</span><span class="sxs-lookup"><span data-stu-id="da773-p123">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online. For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="da773-249">**PreferredDataLocation**値を設定すると同時にライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="da773-249">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="da773-250">特定の地域で、新しいクラウド専用ライセンスを受けたユーザー (AAD 接続の同期) を作成するには、Azure AD PowerShell で次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="da773-250">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="da773-251">次の使用例は、次の値を持つエリザベス Brunner の新しいユーザー アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="da773-251">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="da773-252">ユーザー プリンシパル名: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="da773-252">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="da773-253">名: エリザベス</span><span class="sxs-lookup"><span data-stu-id="da773-253">First name: Elizabeth</span></span>

- <span data-ttu-id="da773-254">姓、名: Brunner</span><span class="sxs-lookup"><span data-stu-id="da773-254">Last name: Brunner</span></span>

- <span data-ttu-id="da773-255">エリザベス Brunner の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="da773-255">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="da773-256">パスワード: は、ランダムに生成され、(*パスワード*パラメーターは使用しない) ために、コマンドの結果に示すように</span><span class="sxs-lookup"><span data-stu-id="da773-256">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="da773-257">ライセンス: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="da773-257">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="da773-258">場所: オーストラリア (オーストラリア)</span><span class="sxs-lookup"><span data-stu-id="da773-258">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="da773-259">新しいユーザー アカウントを作成して、Azure AD PowerShell で LicenseAssignment の値を検索する方法の詳細については、 [Office 365 の PowerShell でユーザー アカウントを作成](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)し、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da773-259">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="da773-p124">**注:** メールボックスを有効にし、 **PreferredDataLocation**で指定されている地域で直接作成するメールボックスが必要な Exchange のオンライン PowerShell を使用する場合は、**有効にするメールボックス**や新規メールボックスの**などのオンラインの Exchange のコマンドレットを使用する必要があります。** クラウド サービスを直接します。**有効にする RemoteMailbox**オンプレミスの Exchange コマンドレットを使用する場合は、既定の地域で、メールボックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="da773-p124">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="da773-262">既存のオンボード設置特定地域内のメールボックス</span><span class="sxs-lookup"><span data-stu-id="da773-262">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="da773-263">など[、EAC での移行のダッシュ ボード](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)の[新規 MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch)コマンドレットでは、Exchange オンライン Exchange オンライン、オンプレミスの Exchange 組織からメールボックスを移行するのには、契約時の標準的なツールとプロセスを使用することができます。PowerShell。</span><span class="sxs-lookup"><span data-stu-id="da773-263">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="da773-p125">最初のステップでは、onboarded では、Azure AD では、適切な**PreferredDataLocation**値を設定することを確認するには、各メールボックスのユーザー オブジェクトが存在することを確認します。契約時のツールは、 **PreferredDataLocation**の値が反映され、指定の地域に直接メールボックスが移行されます。</span><span class="sxs-lookup"><span data-stu-id="da773-p125">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="da773-266">または、Exchange オンライン PowerShell の[新規 MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest)コマンドレットを使用して特定の地域の場所に直接オンボードのメールボックスに次の手順を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="da773-266">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="da773-p126">Onboarded と**PreferredDataLocation**は、Azure AD で目的の値に設定されている各メールボックスのユーザー オブジェクトが存在することを確認します。**PreferredDataLocation**の値が同期されます、対応するメール ユーザー オブジェクトの**MailboxRegion**属性に Exchange オンライン。</span><span class="sxs-lookup"><span data-stu-id="da773-p126">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="da773-269">特定の衛星からの接続方法を使用して、このトピックで前述した地域に直接接続します。</span><span class="sxs-lookup"><span data-stu-id="da773-269">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="da773-270">Exchange オンラインの PowerShell で次のコマンドを実行して、変数にメールボックスの移行を実行するために使用される設置管理者の資格情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="da773-270">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="da773-271">Exchange オンラインの PowerShell で次の例のような新しい**新しい MoveRequest**を作成します。</span><span class="sxs-lookup"><span data-stu-id="da773-271">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="da773-272">メールボックスが現在接続しているサテライトの場所に、オンプレミスの Exchange から移行する必要がありますごとに手順 4 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="da773-272">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="da773-273">さまざまなサテライトの場所に追加のメールボックスを移行する場合は、特定の衛星場所ごとに手順 2 ~ 4 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="da773-273">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="da773-274">複数地域のレポート</span><span class="sxs-lookup"><span data-stu-id="da773-274">Multi-Geo Reporting</span></span>
<span data-ttu-id="da773-p127">Office 365 管理センターの**利用状況レポートの複数の地域**では、地域の場所でユーザー数が表示されます。レポートでは、当月のユーザーの分散を表示し、過去 6 か月の履歴データを提供します。</span><span class="sxs-lookup"><span data-stu-id="da773-p127">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by geo location. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
