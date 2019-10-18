---
title: Office 365 Multi-Geo テナントの構成
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Office 365 Multi-Geo の構成方法の詳細。
ms.openlocfilehash: e1e76482e6b775a2bb1b6ea4428112af738d6a5a
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070013"
---
# <a name="office-365-multi-geo-tenant-configuration"></a><span data-ttu-id="ceefd-103">Office 365 Multi-Geo テナントの構成</span><span class="sxs-lookup"><span data-stu-id="ceefd-103">Office 365 Multi-Geo tenant configuration</span></span>

<span data-ttu-id="ceefd-104">Office 365 Multi-Geo 用にテナントを構成する前に、必ず「[Office 365 Multi-Geo のプラン](plan-for-multi-geo.md)」を読んでください。</span><span class="sxs-lookup"><span data-stu-id="ceefd-104">Before you configure your tenant for Office 365 Multi-Geo, be sure you have read [Plan for Office 365 Multi-Geo](plan-for-multi-geo.md).</span></span> <span data-ttu-id="ceefd-105">この記事の手順を実行するには、サテライトの場所として有効にする地理的位置のリストと、それらの場所用にプロビジョニングするテスト ユーザーが必要です。</span><span class="sxs-lookup"><span data-stu-id="ceefd-105">To follow the steps in this article, you'll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="ceefd-106">Office 365 プランの複数地域機能をテナントに追加する</span><span class="sxs-lookup"><span data-stu-id="ceefd-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="ceefd-107">Office 365 Multi-Geo を使用するには、_Office 365 の複数地域機能_ のプランが必要です。</span><span class="sxs-lookup"><span data-stu-id="ceefd-107">To use Office 365 Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan.</span></span> <span data-ttu-id="ceefd-108">アカウント チームと連携して、このプランをテナントに追加してください。</span><span class="sxs-lookup"><span data-stu-id="ceefd-108">Work with your account team to add this plan to your tenant.</span></span> <span data-ttu-id="ceefd-109">アカウント チームが適切なライセンス スペシャリストと連絡を取り、テナントを構成します。</span><span class="sxs-lookup"><span data-stu-id="ceefd-109">Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="ceefd-p103">_Office 365 の複数地域機能_プランは、ユーザー レベルのサービス プランである点に注意してください。サテライトの場所でホストするユーザーごとにライセンスが必要です。サテライトの場所にユーザーを追加するたびに、さらにライセンスを追加できます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="ceefd-113">テナントが _Office 365 の複数地域機能_プランでプロビジョニングされると、OneDrive および SharePoint 管理センターで [**地理的位置**] タブが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ceefd-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the OneDrive and SharePoint admin centers.</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="ceefd-114">サテライトの場所をテナントに追加する</span><span class="sxs-lookup"><span data-stu-id="ceefd-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="ceefd-115">データを保存する地理的位置ごとにサテライトの場所を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ceefd-115">You must add a satellite location for each geo location where you want to store data.</span></span> <span data-ttu-id="ceefd-116">以下の表に、使用可能な地理的位置を示します。</span><span class="sxs-lookup"><span data-stu-id="ceefd-116">Available geo locations are shown in the following table:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![SharePoint 管理センターの [地域の場所] ページのスクリーン ショット](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="ceefd-118">サテライトの場所を追加する方法</span><span class="sxs-lookup"><span data-stu-id="ceefd-118">To add a satellite location</span></span>

1. <span data-ttu-id="ceefd-119">SharePoint 管理センターを開きます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-119">Open the SharePoint admin center.</span></span>

2. <span data-ttu-id="ceefd-120">**[地理的位置]** タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-120">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="ceefd-121">**[場所を追加します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ceefd-121">Click **Add location**.</span></span>

4. <span data-ttu-id="ceefd-122">追加する場所を選択して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ceefd-122">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="ceefd-123">地域の場所で使用するドメインを入力して、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ceefd-123">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="ceefd-124">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ceefd-124">Click **Close**.</span></span>

<span data-ttu-id="ceefd-p105">テナントのサイズに応じて、プロビジョニングには最大 72 時間かかることがあります。サテライトの場所のプロビジョニングが完了すると、電子メールの確認通知が送信されます。OneDrive 管理センターの **[地理的位置]** タブにある地図上に、新しい地域の場所が青色で表示されているときには、その地域の場所にユーザーの優先されるデータの場所を設定する作業に進めます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ceefd-p106">新しいサテライトの場所は、既定の設定でセットアップされます。そのサテライトの場所は、この設定を使用して、ローカルのコンプライアンス ニーズに適合するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p106">Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="ceefd-130">ユーザーの優先されるデータの場所の設定</span><span class="sxs-lookup"><span data-stu-id="ceefd-130">Setting users' preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="ceefd-p107">必要なサテライトの場所を使用可能にすると、適切な優先されるデータの場所を使用するように、ユーザー アカウントを更新できます。ユーザーが中央の場所から移動しない場合でも、すべてのユーザーに対して優先されるデータの場所を設定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p107">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ceefd-133">ユーザーの優先されるデータの場所がサテライトの場所または中央の場所として構成されていない場所に設定されている場合、OneDrive および SharePoint サイトとグループ メールボックスをプロビジョニングするときに、システムは既定で中央の場所に設定します。</span><span class="sxs-lookup"><span data-stu-id="ceefd-133">If a user's preferred data location is set to a location that has not been configured as a satellite location or the central location, the system will default to the central location when provisioning OneDrive and SharePoint sites and Group mailboxes.</span></span>

> [!TIP]
> <span data-ttu-id="ceefd-134">組織の広範囲に Multi-Geo をロール アウトする前に、テスト ユーザーまたは少数のユーザーのグループでのテストを開始するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ceefd-134">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="ceefd-135">Azure Active Directory には、クラウドのみのユーザーと同期ユーザーの 2 種類のユーザー オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="ceefd-135">In Azure Active Directory there are two types of user objects: cloud only users and synchronized users.</span></span> <span data-ttu-id="ceefd-136">ユーザーの種類に適した指示に従ってください。</span><span class="sxs-lookup"><span data-stu-id="ceefd-136">Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a><span data-ttu-id="ceefd-137">Azure Active Directory Connect を使用してユーザーの優先されるデータの場所を同期する</span><span class="sxs-lookup"><span data-stu-id="ceefd-137">Synchronize user's Preferred Data Location using Azure Active Directory Connect</span></span> 

<span data-ttu-id="ceefd-p109">社内のユーザーがオンプレミスの Active Directory システムから Azure Active Directory に同期される場合は、そうしたユーザーの PreferredDataLocation は AD に移入する必要があり、AAD に同期される必要があります。「[Azure Active Directory Connect 同期: Office 365 リソースの優先されるデータの場所を構成する](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation)」の手順に従って、オンプレミスの Active Directory から Azure Active Directory への優先されるデータの場所の同期を構成します。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p109">If your company’s users are synchronized from an on-premises Active Directory system to Azure Active Directory, their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from on-premises Active Directory to Azure Active Directory.</span></span>

<span data-ttu-id="ceefd-140">標準のユーザー作成フローの一部として、ユーザーの優先されるデータの場所の設定を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ceefd-140">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ceefd-141">OneDrive がプロビジョニングされていない新規ユーザーの場合、ユーザーが OneDrive for Business にログインする前に、ユーザーの PDL が Azure Active Directory に同期されてから少なくとも 24 時間待ち、変更が反映されるようにします。</span><span class="sxs-lookup"><span data-stu-id="ceefd-141">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure Active Directory for the changes to propagate before the user logs in to OneDrive for Business.</span></span> <span data-ttu-id="ceefd-142">(ユーザーが OneDrive for Business をプロビジョニングするために、ログインする前に優先されるデータの場所を設定しておくと、ユーザーの新しい OneDrive が正しい場所にプロビジョニングされるようになります。)</span><span class="sxs-lookup"><span data-stu-id="ceefd-142">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="ceefd-143">クラウド専用ユーザーの優先されるデータの場所を設定する</span><span class="sxs-lookup"><span data-stu-id="ceefd-143">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="ceefd-144">社内のユーザーがオンプレミスの Active Directory システムから Azure Active Directory に同期されていない場合、つまり、ユーザーが Office 365 または Azure Active Directory で作成されている場合は、Azure Active Directory PowerShell を使用して PDL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ceefd-144">If your company's users are not synchronized from an on-premises Active Directory system to Azure Active Directory, meaning they are created in Office 365 or Azure Active Directory, then the PDL must be set using Azure Active Directory PowerShell.</span></span>

<span data-ttu-id="ceefd-p111">ここに示す手順には、[Windows PowerShell 用 Microsoft Azure Active Directory モジュール](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)が必要です。Azure Active Directory PowerShell のインストールが済んでいる場合は、最新バージョンに更新してください。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have Azure Active Directory PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="ceefd-147">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを開きます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-147">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="ceefd-148">`Connect-MsolService` を実行して、テナントの全体管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="ceefd-148">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="ceefd-p112">[Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) コマンドレットを使用して、ユーザーごとに優先されるデータの場所を設定します。次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="ceefd-p113">Get-MsolUser コマンドレットを使用すると、優先されるデータの場所が適切に更新されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![set-msoluser を示す PowerShell ウィンドウのスクリーン ショット](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="ceefd-154">標準のユーザー作成フローの一部として、ユーザーの優先されるデータの場所の設定を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ceefd-154">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ceefd-155">OneDrive がプロビジョニングされていない新規ユーザーの場合、ユーザーが OneDrive にログインする前に、ユーザーの PDL が 設定されてから少なくとも 24 時間待ち、変更が反映されるようにします。</span><span class="sxs-lookup"><span data-stu-id="ceefd-155">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive.</span></span> <span data-ttu-id="ceefd-156">(ユーザーが OneDrive for Business をプロビジョニングするために、ログインする前に優先されるデータの場所を設定すると、新しい OneDrive が正しい場所にプロビジョニングされるようになります。)</span><span class="sxs-lookup"><span data-stu-id="ceefd-156">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="ceefd-157">OneDrive のプロビジョニングと PDL の効果</span><span class="sxs-lookup"><span data-stu-id="ceefd-157">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="ceefd-158">テナントに ユーザーの OneDrive サイトが既に作成されている場合は、そのユーザーの PDL を設定しても既存の OneDrive は自動的に移動されません。</span><span class="sxs-lookup"><span data-stu-id="ceefd-158">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive.</span></span> <span data-ttu-id="ceefd-159">ユーザーの OneDrive を移動するには、「[OneDrive for Business の地域移動](move-onedrive-between-geo-locations.md)」を参照し、地域間での OneDrive の移動手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="ceefd-159">To move a user's OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span> <span data-ttu-id="ceefd-160">(ユーザーの PDL を設定すると、Exchange メールボックスは自動的に移動します。)</span><span class="sxs-lookup"><span data-stu-id="ceefd-160">(Note that the user's Exchange mailbox does move automatically when you set the user's PDL.)</span></span>

<span data-ttu-id="ceefd-161">テナント内に OneDrive サイトを持っていないユーザーの場合、ユーザーの PDL が会社のサテライトの場所のいずれかと一致すれば、ユーザーの OneDrive は PDL 値に基づいてプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-161">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company's satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="ceefd-162">複数地域検索の構成</span><span class="sxs-lookup"><span data-stu-id="ceefd-162">Configuring Multi-Geo search</span></span>

<span data-ttu-id="ceefd-163">複数地域テナントには、検索クエリでテナント内のあらゆる場所からの結果が得られるようになる、集約検索機能が備わります。</span><span class="sxs-lookup"><span data-stu-id="ceefd-163">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="ceefd-164">既定では、それらのエントリ ポイントからの検索は、それぞれの検索インデックスが関連する地域の場所に配置されていたとしても、集約された結果を返します。</span><span class="sxs-lookup"><span data-stu-id="ceefd-164">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="ceefd-165">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="ceefd-165">OneDrive for business</span></span>

- <span data-ttu-id="ceefd-166">Delve</span><span class="sxs-lookup"><span data-stu-id="ceefd-166">Delve</span></span>

- <span data-ttu-id="ceefd-167">SharePoint Home</span><span class="sxs-lookup"><span data-stu-id="ceefd-167">SharePoint Home</span></span>

- <span data-ttu-id="ceefd-168">検索センター</span><span class="sxs-lookup"><span data-stu-id="ceefd-168">Search Center</span></span>

<span data-ttu-id="ceefd-169">さらに、Multi-Geo 検索機能は、SharePoint 検索 API を使用するカスタムの検索アプリケーション用に構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-169">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="ceefd-170">手順と制限事項や相違点などについては、「[OneDrive for Business 複数地域の検索の構成](configure-search-for-multi-geo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ceefd-170">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-office-365-multi-geo-configuration"></a><span data-ttu-id="ceefd-171">Office 365 Multi-Geo の構成を検証する</span><span class="sxs-lookup"><span data-stu-id="ceefd-171">Validating the Office 365 Multi-Geo configuration</span></span>

<span data-ttu-id="ceefd-172">以下は、Office 365 Multi-Geo を会社で広く展開する前に、検証のプランに含めることができる基本的なユース ケースです。</span><span class="sxs-lookup"><span data-stu-id="ceefd-172">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out Office 365 Multi-Geo to your company.</span></span> <span data-ttu-id="ceefd-173">これらのテストと会社に関連するその他のユース ケースを完了すると、最初のパイロット グループへのユーザーの追加を開始できます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-173">Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="ceefd-174">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="ceefd-174">**OneDrive for Business**</span></span>

<span data-ttu-id="ceefd-175">Office 365 アプリ起動ツールから OneDrive を選択し、ユーザーの PDLに基づいて、適切な地理的位置に自動的に誘導されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ceefd-175">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user's PDL.</span></span> <span data-ttu-id="ceefd-176">OneDrive for Business により、その場所でプロビジョニングが開始されるはずです。</span><span class="sxs-lookup"><span data-stu-id="ceefd-176">OneDrive for Business should now begin provisioning at that location.</span></span> <span data-ttu-id="ceefd-177">プロビジョニングが完了したら、ドキュメントのアップロードやダウンロードを試してください。</span><span class="sxs-lookup"><span data-stu-id="ceefd-177">Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="ceefd-178">**OneDrive モバイル アプリ**</span><span class="sxs-lookup"><span data-stu-id="ceefd-178">**OneDrive Mobile App**</span></span>

<span data-ttu-id="ceefd-p118">OneDrive モバイル アプリにテスト用アカウントの資格情報でログインします。OneDrive for Business のファイルを表示できることと、それらのファイルをモバイル デバイスから操作できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="ceefd-181">**OneDrive 同期クライアント**</span><span class="sxs-lookup"><span data-stu-id="ceefd-181">**OneDrive sync client**</span></span>

<span data-ttu-id="ceefd-p119">ログイン時に、OneDrive 同期クライアントが OneDrive for Business 地域の場所を自動的に検出することを確認します。同期クライアントのダウンロードが必要な場合は、OneDrive ライブラリで **[同期]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="ceefd-184">**Office アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="ceefd-184">**Office applications**</span></span>

<span data-ttu-id="ceefd-p120">Word などの Office アプリケーションからのログインで OneDrive for Business にアクセスできることを確認します。Office アプリケーションを開いて、[OneDrive – <TenantName>] を選択します。Office によって、OneDrive の場所が検出され、開くことができるファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="ceefd-188">**共有**</span><span class="sxs-lookup"><span data-stu-id="ceefd-188">**Sharing**</span></span>

<span data-ttu-id="ceefd-p121">OneDrive ファイルを共有してみます。地域の場所に関係なく、ユーザー選択にすべての SharePoint Online ユーザーが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ceefd-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
