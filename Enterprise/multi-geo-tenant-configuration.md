---
title: OneDrive for Business 複数地域テナントの構成
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: OneDrive for Business 複数地域の構成方法について説明します。
ms.openlocfilehash: 1817eee1bb2ceefa0e2e167e327af417dd0c517d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915252"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="cb8cd-103">OneDrive for Business 複数地域テナントの構成</span><span class="sxs-lookup"><span data-stu-id="cb8cd-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="cb8cd-p101">OneDrive for Business 複数地域のテナントを構成する前に、「[OneDrive for Business 複数地域の計画](plan-for-multi-geo.md)」を参照してください。この記事の手順を実行するには、有効にする場所とその場所にプロビジョニングするテスト ユーザーのリストが必要になります。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="cb8cd-106">Office 365 プランの複数地域機能をテナントに追加する</span><span class="sxs-lookup"><span data-stu-id="cb8cd-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="cb8cd-p102">OneDrive for Business 複数地域を使用するには、_Office 365 の複数地域機能_プランが必要になります。アカウント チームと協力して、このプランをテナントに追加してください。アカウント チームは、適切なライセンス スペシャリストを紹介してテナントを構成します。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="cb8cd-p103">_Office 365 の複数地域機能_プランは、ユーザー レベルのサービス プランである点に注意してください。サテライトの場所でホストするユーザーごとにライセンスが必要です。サテライトの場所にユーザーを追加するたびに、さらにライセンスを追加できます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="cb8cd-113">テナントが _Office 365 の複数地域機能_プランでプロビジョニングされると、[OneDrive 管理センター](https://admin.onedrive.com)で **[地理的位置]** タブが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="cb8cd-114">テナントに許可されたデータの場所 (ADL) を設定する</span><span class="sxs-lookup"><span data-stu-id="cb8cd-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="cb8cd-p104">OneDrive for Business を使用する地理的位置ごとに、SharePoint の許可されたデータの場所を設定する必要があります。次の表に、利用可能な地理的位置を示します。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="cb8cd-117"><strong>場所</strong></span><span class="sxs-lookup"><span data-stu-id="cb8cd-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="cb8cd-118"><strong>コード</strong></span><span class="sxs-lookup"><span data-stu-id="cb8cd-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="cb8cd-119">アジア太平洋</span><span class="sxs-lookup"><span data-stu-id="cb8cd-119">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="cb8cd-120">APC</span><span class="sxs-lookup"><span data-stu-id="cb8cd-120">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cb8cd-121">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="cb8cd-121">Australia</span></span></td>
<td align="left"><span data-ttu-id="cb8cd-122">AUS</span><span class="sxs-lookup"><span data-stu-id="cb8cd-122">AUS</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cb8cd-123">カナダ</span><span class="sxs-lookup"><span data-stu-id="cb8cd-123">Canada</span></span></td>
<td align="left"><span data-ttu-id="cb8cd-124">CAN</span><span class="sxs-lookup"><span data-stu-id="cb8cd-124">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cb8cd-125">ヨーロッパ/中東/アフリカ</span><span class="sxs-lookup"><span data-stu-id="cb8cd-125">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="cb8cd-126">EUR</span><span class="sxs-lookup"><span data-stu-id="cb8cd-126">EUR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cb8cd-127">フランス</span><span class="sxs-lookup"><span data-stu-id="cb8cd-127">France</span></span></td>
<td align="left"><span data-ttu-id="cb8cd-128">FRA</span><span class="sxs-lookup"><span data-stu-id="cb8cd-128">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cb8cd-129">日本</span><span class="sxs-lookup"><span data-stu-id="cb8cd-129">Japan</span></span></td>
<td align="left"><span data-ttu-id="cb8cd-130">JPN</span><span class="sxs-lookup"><span data-stu-id="cb8cd-130">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cb8cd-131">韓国</span><span class="sxs-lookup"><span data-stu-id="cb8cd-131">Korea</span></span></td>
<td align="left"><span data-ttu-id="cb8cd-132">KOR</span><span class="sxs-lookup"><span data-stu-id="cb8cd-132">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cb8cd-133">北アメリカ</span><span class="sxs-lookup"><span data-stu-id="cb8cd-133">North America</span></span></td>
<td align="left"><span data-ttu-id="cb8cd-134">NAM</span><span class="sxs-lookup"><span data-stu-id="cb8cd-134">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cb8cd-135">イギリス</span><span class="sxs-lookup"><span data-stu-id="cb8cd-135">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="cb8cd-136">GBR</span><span class="sxs-lookup"><span data-stu-id="cb8cd-136">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="cb8cd-137">サテライトの地域の場所を追加するには</span><span class="sxs-lookup"><span data-stu-id="cb8cd-137">To add a satellite geo location</span></span>

1. <span data-ttu-id="cb8cd-138">[OneDrive 管理センター](https://admin.onedrive.com)を開きます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-138">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="cb8cd-139">**[地理的位置]** タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-139">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="cb8cd-140">**[場所を追加します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-140">Click **Add location**.</span></span>

4. <span data-ttu-id="cb8cd-141">追加する場所を選択して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-141">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="cb8cd-142">地域の場所で使用するドメインを入力して、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-142">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="cb8cd-143">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-143">Click **Close**.</span></span>

<span data-ttu-id="cb8cd-p105">テナントのサイズに応じて、プロビジョニングには最大 72 時間かかることがあります。サテライトの場所のプロビジョニングが完了すると、電子メールの確認通知が送信されます。OneDrive 管理センターの **[地理的位置]** タブにある地図上に、新しい地域の場所が青色で表示されているときには、その地域の場所にユーザーの優先されるデータの場所を設定する作業に進めます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="cb8cd-p106">新しいサテライトの地域の場所は、既定の設定でセットアップされます。その地域の場所は、この設定を使用して、ローカルのコンプライアンス ニーズに適合するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="cb8cd-149">ユーザーの優先されるデータの場所の設定</span><span class="sxs-lookup"><span data-stu-id="cb8cd-149">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="cb8cd-p107">必要とされるデータの場所を使用可能にすると、適切なデータの場所を使用するように、ユーザー アカウントを更新できます。ユーザーが既定の場所から移動しない場合でも、すべてのユーザーに対して優先されるデータの場所を設定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="cb8cd-152">組織の広範囲に複数地域機能をロール アウトする前に、テスト ユーザーまたは少数のユーザーのグループでのテストを開始するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-152">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="cb8cd-p108">AAD には、クラウド専用ユーザーと同期ユーザーの 2 種類のユーザー オブジェクトがあります。目的のユーザーの種類に該当する指示に従ってください。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="cb8cd-155">AD Connect を使用してユーザーの優先されるデータの場所を同期する</span><span class="sxs-lookup"><span data-stu-id="cb8cd-155">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="cb8cd-p109">社内のユーザーがオンプレミスの Active Directory (AD) システムから Azure Active Directory (AAD) に同期される場合は、そうしたユーザーの PreferredDataLocation は AD に移入する必要があり、AAD に同期される必要があります。「[Azure AD Connect Sync: 既定の構成を変更する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)」の手順に従って、オンプレミスの AD から AAD への優先されるデータの場所の同期を構成します。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="cb8cd-158">標準のユーザー作成フローの一部として、ユーザーの優先されるデータの場所の設定を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-158">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb8cd-p110">OneDrive がプロビジョニングされていない新しいユーザーの場合は、変更内容の反映のためにユーザーの PDL が AAD に同期されてから少なくとも 24 時間待機して、OneDrive for Business にログインします (OneDrive for Business をプロビジョニングするためにユーザーがログインする前に優先されるデータの場所を設定することで、ユーザーの新しい OneDrive が正しい場所にプロビジョニングされるようになります)。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="cb8cd-161">クラウド専用ユーザーの優先されるデータの場所を設定する</span><span class="sxs-lookup"><span data-stu-id="cb8cd-161">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="cb8cd-162">社内のユーザーがオンプレミスの Active Directory (AD) システムから Azure Active Directory (AAD) に同期されていない場合、つまり、ユーザーが Office 365 または AAD で作成されている場合は、AAD PowerShell を使用して PDL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-162">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="cb8cd-p111">ここに示す手順には、[Windows PowerShell 用 Microsoft Azure Active Directory モジュール](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)が必要です。AAD PowerShell のインストールが済んでいる場合は、最新バージョンに更新してください。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="cb8cd-165">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを開きます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-165">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="cb8cd-166">`Connect-MsolService` を実行して、テナントの全体管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-166">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="cb8cd-p112">[Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) コマンドレットを使用して、ユーザーごとに優先されるデータの場所を設定します。次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="cb8cd-p113">Get-MsolUser コマンドレットを使用すると、優先されるデータの場所が適切に更新されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="cb8cd-171">標準のユーザー作成フローの一部として、ユーザーの優先されるデータの場所の設定を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-171">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb8cd-p114">OneDrive がプロビジョニングされていない新しいユーザーの場合は、変更内容の反映のためにユーザーの PDL が設定されてから少なくとも 24 時間待機して、SharePoint OneDrives にログインします (OneDrive for Business をプロビジョニングするためにユーザーがログインする前に優先されるデータの場所を設定することで、ユーザーの新しい OneDrive が正しい場所にプロビジョニングされるようになります)。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="cb8cd-174">OneDrive のプロビジョニングと PDL の効果</span><span class="sxs-lookup"><span data-stu-id="cb8cd-174">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="cb8cd-p115">既にユーザーがテナントで作成された OneDrive サイトを持っている場合は、そのユーザーの PDL を設定しても既存の OneDrive が自動的に移動されることはありません。ユーザーの OneDrive を移動する場合は、「[OneDrive for Business の地域の移動](move-onedrive-between-geo-locations.md)」を参照して、地域の場所間での OneDrive の移動についての手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="cb8cd-177">ユーザーがテナント内に OneDrive サイトを持っていないユーザーの場合、ユーザーの PDL が会社の許可されたデータの場所 (ADL) のいずれかと一致すれば、ユーザーの OneDrive は PDL 値に応じてプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-177">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="cb8cd-178">複数地域検索の構成</span><span class="sxs-lookup"><span data-stu-id="cb8cd-178">Configuring Multi-Geo search</span></span>

<span data-ttu-id="cb8cd-179">複数地域テナントには、検索クエリでテナント内のあらゆる場所からの結果が得られるようになる、集約検索機能が備わります。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-179">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="cb8cd-180">既定では、それらのエントリ ポイントからの検索は、それぞれの検索インデックスが関連する地域の場所に配置されていたとしても、集約された結果を返します。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-180">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="cb8cd-181">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="cb8cd-181">OneDrive for business</span></span>

- <span data-ttu-id="cb8cd-182">Delve</span><span class="sxs-lookup"><span data-stu-id="cb8cd-182">Delve</span></span>

- <span data-ttu-id="cb8cd-183">SharePoint Home</span><span class="sxs-lookup"><span data-stu-id="cb8cd-183">SharePoint Home</span></span>

- <span data-ttu-id="cb8cd-184">検索センター</span><span class="sxs-lookup"><span data-stu-id="cb8cd-184">Search Center</span></span>

<span data-ttu-id="cb8cd-185">さらに、複数地域検索機能は、SharePoint 検索 API を使用するカスタムの検索アプリケーション用に構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-185">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="cb8cd-186">手順と制限事項や相違点などについては、「[OneDrive for Business 複数地域の検索の構成](configure-search-for-multi-geo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-186">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="cb8cd-187">OneDrive for Business 複数地域の構成の検証</span><span class="sxs-lookup"><span data-stu-id="cb8cd-187">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="cb8cd-p116">次に示す、いくつかのユース ケースは、OneDrive for Business 複数地域を会社に広範囲にロール アウトする前の検証計画に含めるようにします。これらのテストと会社に関連する追加のユース ケースを完了してから、最初のパイロット グループにユーザーを追加するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="cb8cd-190">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="cb8cd-190">**OneDrive for Business**</span></span>

<span data-ttu-id="cb8cd-p117">Office 365 アプリ起動ツールから OneDrive を選択し、ユーザーの PDL に基づいて、そのユーザーにとって自動的に適切な地域の場所に自動的に移動されることを確認します。その場所で OneDrive for Business のプロビジョニングが開始されます。プロビジョニングが完了したら、ドキュメントのアップロードとダウンロードを試してください。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="cb8cd-194">**OneDrive モバイル アプリ**</span><span class="sxs-lookup"><span data-stu-id="cb8cd-194">**OneDrive Mobile App**</span></span>

<span data-ttu-id="cb8cd-p118">OneDrive モバイル アプリにテスト用アカウントの資格情報でログインします。OneDrive for Business のファイルを表示できることと、それらのファイルをモバイル デバイスから操作できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="cb8cd-197">**OneDrive 同期クライアント**</span><span class="sxs-lookup"><span data-stu-id="cb8cd-197">**OneDrive sync client**</span></span>

<span data-ttu-id="cb8cd-p119">ログイン時に、OneDrive 同期クライアントが OneDrive for Business 地域の場所を自動的に検出することを確認します。同期クライアントのダウンロードが必要な場合は、OneDrive ライブラリで **[同期]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="cb8cd-200">**Office アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="cb8cd-200">**Office applications**</span></span>

<span data-ttu-id="cb8cd-p120">Word などの Office アプリケーションからのログインで OneDrive for Business にアクセスできることを確認します。Office アプリケーションを開いて、[OneDrive – <TenantName>] を選択します。Office によって、OneDrive の場所が検出され、開くことができるファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="cb8cd-204">**共有**</span><span class="sxs-lookup"><span data-stu-id="cb8cd-204">**Sharing**</span></span>

<span data-ttu-id="cb8cd-p121">OneDrive ファイルを共有してみます。地域の場所に関係なく、ユーザー選択にすべての SharePoint Online ユーザーが表示されていることを確認します</span><span class="sxs-lookup"><span data-stu-id="cb8cd-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
