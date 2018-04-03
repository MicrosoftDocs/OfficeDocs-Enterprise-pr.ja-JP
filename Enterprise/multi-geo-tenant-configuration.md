---
title: ビジネスの複数の地域のテナント構成の OneDrive
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: OneDrive に複数の地域のビジネスを構成する方法について説明します。
ms.openlocfilehash: 4ef31df802eeaedf2eecbdd295d2e359816e4909
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="627a8-103">ビジネスの複数の地域のテナント構成の OneDrive</span><span class="sxs-lookup"><span data-stu-id="627a8-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="627a8-p101">OneDrive は、テナントの複数の地域のビジネスを構成する前に、 [OneDrive 複数の地域のビジネスの計画](plan-for-multi-geo.md)を読んだことを確認します。この資料の手順を実行するを有効にする場所、およびそれらの場所を提供するテスト ユーザーの一覧を必要があります。</span><span class="sxs-lookup"><span data-stu-id="627a8-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="627a8-106">Office 365 のプランで、テナントに複数地域の機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="627a8-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="627a8-p102">複数の地域のビジネスの OneDrive を使用して、 _Office 365 の機能を複数の地域_の計画が必要です。この計画をテナントに追加するのには、アカウント ・ チームと協力します。アカウント ・ チームは適切なライセンスのスペシャ リストに接続して、構成、テナントを取得します。</span><span class="sxs-lookup"><span data-stu-id="627a8-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="627a8-p103">_Office 365 の機能を複数の地域_計画がユーザー レベルのサービス プランであることに注意します。Setellite の場所でホストするユーザーごとにライセンスが必要です。サテライト オフィスのユーザーを追加すると、時間の経過と共にライセンスを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="627a8-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a setellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="627a8-113">テナントは、 _Office 365 の機能を複数の地域_の計画と準備されていると[OneDrive の管理センター](https://admin.onedrive.com)で利用可能な**地域の場所**] タブになります。</span><span class="sxs-lookup"><span data-stu-id="627a8-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="627a8-114">許可されるデータの場所 (ADL) をテナントに設定します。</span><span class="sxs-lookup"><span data-stu-id="627a8-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="627a8-p104">必要がありますを設定する許可されるデータの場所、SharePoint の各地理的な場所のビジネスの OneDrive を使用します。利用可能な地域の場所は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="627a8-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="627a8-117"><strong>場所</strong></span><span class="sxs-lookup"><span data-stu-id="627a8-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="627a8-118"><strong>コード</strong></span><span class="sxs-lookup"><span data-stu-id="627a8-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="627a8-119">北アメリカ</span><span class="sxs-lookup"><span data-stu-id="627a8-119">North America</span></span></td>
<td align="left"><span data-ttu-id="627a8-120">名</span><span class="sxs-lookup"><span data-stu-id="627a8-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="627a8-121">ヨーロッパ東中央//アフリカ</span><span class="sxs-lookup"><span data-stu-id="627a8-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="627a8-122">EUR</span><span class="sxs-lookup"><span data-stu-id="627a8-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="627a8-123">アジア太平洋</span><span class="sxs-lookup"><span data-stu-id="627a8-123">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="627a8-124">APC</span><span class="sxs-lookup"><span data-stu-id="627a8-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="627a8-125">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="627a8-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="627a8-126">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="627a8-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="627a8-127">日本</span><span class="sxs-lookup"><span data-stu-id="627a8-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="627a8-128">日本語版</span><span class="sxs-lookup"><span data-stu-id="627a8-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="627a8-129">カナダ</span><span class="sxs-lookup"><span data-stu-id="627a8-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="627a8-130">できます。</span><span class="sxs-lookup"><span data-stu-id="627a8-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="627a8-131">英国</span><span class="sxs-lookup"><span data-stu-id="627a8-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="627a8-132">GBR</span><span class="sxs-lookup"><span data-stu-id="627a8-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="627a8-133">韓国</span><span class="sxs-lookup"><span data-stu-id="627a8-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="627a8-134">KOR</span><span class="sxs-lookup"><span data-stu-id="627a8-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="627a8-135">サテライト地域の場所を追加するには</span><span class="sxs-lookup"><span data-stu-id="627a8-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="627a8-136">[OneDrive 管理センター](https://admin.onedrive.com)を開きます。</span><span class="sxs-lookup"><span data-stu-id="627a8-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="627a8-137">**Geo [場所**] タブに移動します。</span><span class="sxs-lookup"><span data-stu-id="627a8-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="627a8-138">[**場所の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="627a8-138">Click **Add location**.</span></span>

4. <span data-ttu-id="627a8-139">を追加する場所を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="627a8-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="627a8-140">Geo の場所で使用するドメインを入力し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="627a8-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="627a8-141">[ **閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="627a8-141">Click **Close**.</span></span>

<span data-ttu-id="627a8-p105">サテライトの場所の準備が完了すると、確認の電子メールが表示されます。OneDrive 管理センターの**地域の場所**] タブ上のマップの青い地域の別の場所が表示されたら、ユーザーの希望するデータの場所をその地理的な場所に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="627a8-p105">Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="627a8-p106">新しいサテライト地域地域は、既定の設定で設定されます。これは、オプションを選択する、コンプライアンスのニーズに応じてその地域の場所を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="627a8-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="627a8-146">ユーザーの希望するデータの場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="627a8-146">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="627a8-p107">必要なデータの場所を有効にすると、適切なデータの場所を使用するユーザー アカウントを更新できます。場合でも、既定のデータの場所でそのユーザーが常にすべてのユーザーに対して推奨されるデータの場所を設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="627a8-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="627a8-149">広範な組織に複数の地域の機能を展開する前にテストのユーザーまたはユーザーの小さなグループでの検証を開始することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="627a8-149">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="627a8-p108">AAD ではユーザー オブジェクトの 2 つの種類があります: クラウド ユーザーと同期されたユーザーのみです。ユーザーの種類に適切な手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="627a8-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="627a8-152">ユーザーの優先データを使用して場所 AD の接続を同期します。</span><span class="sxs-lookup"><span data-stu-id="627a8-152">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="627a8-p109">ユーザーの会社の同期している場合、オンプレミスの Active Directory (AD) システムから Azure Active Directory (AAD) に、PreferredDataLocation を AD に設定され、AAD に同期する必要があります。次の処理では、 [Azure AD 接続の同期: 既定の構成に変更を加える](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)優先を構成するのにはデータの場所の同期のオンプレミス AD AAD にします。</span><span class="sxs-lookup"><span data-stu-id="627a8-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="627a8-155">ユーザーの優先データの場所を設定、標準のユーザー作成のワークフローの一部として含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="627a8-155">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="627a8-p110">準備なしの OneDrive を持つ新しいユーザーは、ユーザーの PDL は、ユーザーがビジネスのための OneDrive にログインする前に反映する変更の AAD を同期した後、少なくとも 24 時間待機します。(優先データを設定する場所がビジネスのための OneDrive を提供する、ユーザーがログインする前に確実にユーザーの新しい OneDrive が正しい位置に準備すること。)</span><span class="sxs-lookup"><span data-stu-id="627a8-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="627a8-158">クラウドの優先データの場所を設定するユーザーのみ</span><span class="sxs-lookup"><span data-stu-id="627a8-158">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="627a8-159">会社のユーザーが同期していない場合、オンプレミスの Active Directory (AD) システムから Azure Active Directory (AAD) に、Office 365 または AAD で作成されることを意味し、PDL 設定してください AAD PowerShell を使用します。</span><span class="sxs-lookup"><span data-stu-id="627a8-159">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="627a8-p111">このセクションの手順では、 [Microsoft Azure Active ディレクトリの Windows PowerShell モジュール](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)が必要です。既に AAD PowerShell をインストールする場合は、最新バージョンに更新するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="627a8-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="627a8-162">Windows PowerShell は、Microsoft Azure Active Directory のモジュールを開きます。</span><span class="sxs-lookup"><span data-stu-id="627a8-162">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="627a8-163">実行`Connect-MsolService`し、テナントのグローバル管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="627a8-163">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="627a8-p112">[セット MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser)コマンドレットを使用すると、個々 のユーザーの希望するデータの場所を設定できます。例えば：</span><span class="sxs-lookup"><span data-stu-id="627a8-p112">Use the [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="627a8-p113">Get MsolUser コマンドレットを使用して希望するデータの場所が正しく更新されたことを確認するのにはチェックすることができます。例えば：</span><span class="sxs-lookup"><span data-stu-id="627a8-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="627a8-168">ユーザーの優先データの場所を設定、標準のユーザー作成のワークフローの一部として含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="627a8-168">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="627a8-p114">準備なしの OneDrive を持つ新しいユーザーは、ユーザーの PDL は、ユーザーが SharePoint の OneDrive にログインする前に反映する変更の設定後 24 時間以上待ちます。(優先データを設定する場所がビジネスのための OneDrive を提供する、ユーザーがログインする前に確実にユーザーの新しい OneDrive が正しい位置に準備すること。)</span><span class="sxs-lookup"><span data-stu-id="627a8-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="627a8-171">OneDrive のプロビジョニングと PDL の効果</span><span class="sxs-lookup"><span data-stu-id="627a8-171">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="627a8-p115">ユーザーは、テナントで作成した OneDrive サイトを既に持っている場合、PDL の設定は自動的に移動されません、既存の OneDrive。ユーザーの OneDrive を移動するには、geo の場所の間で OneDrive の移動の指示に従ってください[OneDrive](move-onedrive-between-geo-locations.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="627a8-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="627a8-174">ユーザーは、テナント内の OneDrive サイトを持っていない場合 OneDrive が準備されますに、PDL の値に従って、ユーザーは PDL では、会社のデータが許可されている場所 (ADLs) のいずれかと一致すると仮定した場合します。</span><span class="sxs-lookup"><span data-stu-id="627a8-174">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="627a8-175">マルチ地域検索の構成</span><span class="sxs-lookup"><span data-stu-id="627a8-175">Configuring Multi-Geo search</span></span>

<span data-ttu-id="627a8-176">複数地域のテナントが任意の場所から結果を返す検索クエリを許可する集計の検索機能は、テナント内です。</span><span class="sxs-lookup"><span data-stu-id="627a8-176">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="627a8-177">既定では、これらのエントリ ポイントからの検索は各検索のインデックスは、関連する地域場所内にある場合でもに、集計結果を返します。</span><span class="sxs-lookup"><span data-stu-id="627a8-177">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="627a8-178">ビジネスの OneDrive</span><span class="sxs-lookup"><span data-stu-id="627a8-178">OneDrive for business</span></span>

- <span data-ttu-id="627a8-179">Delve</span><span class="sxs-lookup"><span data-stu-id="627a8-179">Delve</span></span>

- <span data-ttu-id="627a8-180">SharePoint ホーム</span><span class="sxs-lookup"><span data-stu-id="627a8-180">SharePoint Home</span></span>

- <span data-ttu-id="627a8-181">検索センター</span><span class="sxs-lookup"><span data-stu-id="627a8-181">Search Center</span></span>

<span data-ttu-id="627a8-182">さらに、SharePoint 検索 API を使用するカスタムの検索アプリケーションの複数の地域の検索機能を構成できます。</span><span class="sxs-lookup"><span data-stu-id="627a8-182">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="627a8-183">手順については、制限や相違点を含む、 [OneDrive 複数の地域のビジネスを検索する構成](configure-search-for-multi-geo.md)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="627a8-183">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="627a8-184">ビジネスの複数の地域の構成の OneDrive を検証しています。</span><span class="sxs-lookup"><span data-stu-id="627a8-184">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="627a8-p116">ロールバックする前に広く OneDrive を複数の地域のビジネス、会社に、検証の計画に含めることができます基本的な使用例を次に示します。これらのテストとは、会社に関連するすべての他の使用ケースを完了すると、初期のパイロットのグループにユーザーを追加するのに移動することができます。</span><span class="sxs-lookup"><span data-stu-id="627a8-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="627a8-187">**ビジネスの OneDrive**</span><span class="sxs-lookup"><span data-stu-id="627a8-187">**OneDrive for Business**</span></span>

<span data-ttu-id="627a8-p117">Office 365 アプリケーション起動プログラムから OneDrive を選択し、ユーザーの PDL に基づいて、ユーザーの適切な地理的な場所に自動的に送信されることを確認します。ビジネスの OneDrive の場所にプロビジョニングを開始する必要があります。アップロードといくつかのドキュメントをダウンロード、一度準備されたが、不正解です。</span><span class="sxs-lookup"><span data-stu-id="627a8-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="627a8-191">**OneDrive モバイル アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="627a8-191">**OneDrive Mobile App**</span></span>

<span data-ttu-id="627a8-p118">テスト アカウントの資格情報を使用して OneDrive のモバイル アプリケーションにログインします。ビジネス ファイルを OneDrive を参照してくださいことができ、モバイル デバイスから、それらと対話できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="627a8-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="627a8-194">**同期クライアントの OneDrive**</span><span class="sxs-lookup"><span data-stu-id="627a8-194">**OneDrive sync client**</span></span>

<span data-ttu-id="627a8-p119">OneDrive 同期クライアントがログインしたときにビジネスの地理的な場所に、OneDrive を自動的に検出することを確認します。同期クライアントをダウンロードする場合は、OneDrive ライブラリの**同期**をクリックできます。</span><span class="sxs-lookup"><span data-stu-id="627a8-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="627a8-197">**Office アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="627a8-197">**Office applications**</span></span>

<span data-ttu-id="627a8-p120">Word などの Office アプリケーションからログインすることによりビジネスの OneDrive にアクセスできることを確認します。開くには、Office アプリケーションで ["OneDrive- <TenantName>」です。Office は、OneDrive の場所を検出し、開くことができるファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="627a8-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="627a8-201">**Sharing**</span><span class="sxs-lookup"><span data-stu-id="627a8-201">**Sharing**</span></span>

<span data-ttu-id="627a8-p121">OneDrive ファイルを共有してみてください。ユーザー選択ウィンドウを表示するすべての SharePoint のオンライン ユーザーの地理的な場所に関係なくことを確認します。</span><span class="sxs-lookup"><span data-stu-id="627a8-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
