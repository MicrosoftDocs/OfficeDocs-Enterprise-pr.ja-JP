---
title: 複数地域環境の管理
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: 複数地域環境での SharePoint サービスおよび OneDrive サービスの管理について説明します。
ms.openlocfilehash: 9d4d35505dc5b0d24dd5b2ada8ff1028b1d0d61b
ms.sourcegitcommit: 5fe1c9be652222d6956c7dad5949ddcf0bd27041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2019
ms.locfileid: "38076141"
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="e2941-103">複数地域環境の管理</span><span class="sxs-lookup"><span data-stu-id="e2941-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="e2941-104">ここでは、複数地域環境で Office 365 のサービスが動作するしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e2941-104">Here's a look at how Office 365 services work in a multi-geo environment.</span></span>

## <a name="audit-log-search"></a><span data-ttu-id="e2941-105">監査ログ検索</span><span class="sxs-lookup"><span data-stu-id="e2941-105">Audit log search</span></span>

<span data-ttu-id="e2941-106">すべてのサテライト地域に対して統合された[監査ログ](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)は、Office 365 監査ログの検索ページから利用できます。</span><span class="sxs-lookup"><span data-stu-id="e2941-106">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your satellite locations is available from the Office 365 audit log search page.</span></span> <span data-ttu-id="e2941-107">すべての地域からの監査ログのエントリを参照できます。たとえば、NAM ユーザーと EUR ユーザーのアクティビティが、1 つの組織ビューに表示され、既存のフィルターを適用することで特定のユーザーのアクティビティを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e2941-107">You can see all the audit log entries from across geo locations, for example, NAM & EUR users' activities will show up in one org view and then you can apply existing filters to see specific user's activities.</span></span>

## <a name="bcs-secure-store-apps"></a><span data-ttu-id="e2941-108">BCS、Secure Store、Apps</span><span class="sxs-lookup"><span data-stu-id="e2941-108">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="e2941-109">BCS、Secure Store、およびすべての App は、各サテライトの場所に個別のインスタンスがあります。そのため、SharePoint Online 管理者は、これらのサービスを各サテライトの場所とは別に管理および構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2941-109">BCS, Secure Store, and Apps all have separate instances in each satellite location, therefore the SharePoint Online administrator should manage and configure these services separately from each satellite location.</span></span>

## <a name="ediscovery"></a><span data-ttu-id="e2941-110">電子情報開示</span><span class="sxs-lookup"><span data-stu-id="e2941-110">eDiscovery</span></span> 

<span data-ttu-id="e2941-111">デフォルトでは、複数地域のテナントの eDiscovery Manager またはeDiscovery Administrator が、そのテナントの中心地でのみ電子情報の開示ができるようになります。</span><span class="sxs-lookup"><span data-stu-id="e2941-111">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant.</span></span> <span data-ttu-id="e2941-112">Office 365 全体管理者は、別のユーザーが電子情報開示を実行できるように電子情報開示マネージャーのアクセス許可を割り当てる必要があります。また、サテライトの場所として電子情報開示を実施する地域を指定するために該当するコンプライアンス セキュリティ フィルターで "Region" パラメーターを割り当てる必要があります。それ以外の場合は、サテライトの場所で電子情報開示は実施されません。</span><span class="sxs-lookup"><span data-stu-id="e2941-112">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span> <span data-ttu-id="e2941-113">地域のコンプライアンス セキュリティ フィルター を構成するには、[Office 365 Multi-Geo eDiscovery の構成](multi-geo-ediscovery-configuration.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2941-113">To configure the Compliance Security Filter for a Region, see [Configure Office 365 Multi-Geo eDiscovery](multi-geo-ediscovery-configuration.md).</span></span>

## <a name="exchange-mailboxes"></a><span data-ttu-id="e2941-114">Exchange メールボックス</span><span class="sxs-lookup"><span data-stu-id="e2941-114">Exchange mailboxes</span></span>

<span data-ttu-id="e2941-115">ユーザーの PDL が変更された場合、Exchange メールボックスが自動的に移動します。</span><span class="sxs-lookup"><span data-stu-id="e2941-115">Users' Exchange mailboxes are moved automatically if their PDL is changed.</span></span> <span data-ttu-id="e2941-116">新しいメールボックスが作成されたとき、ユーザーの PDL の値が設定されていない場合は、ユーザーの PDL または中心地にメールボックスがプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="e2941-116">When a new mailbox is created, it is provisioned to the user's PDL or to the central location if no value has been set for the user's PDL.</span></span>

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="e2941-117">Information Protection (IP) データ損失防止 (DLP) ポリシー</span><span class="sxs-lookup"><span data-stu-id="e2941-117">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="e2941-118">必要に応じて、テナント全体または該当するユーザーにポリシーの範囲を指定するセキュリティ & コンプライアンス センターで、OneDrive for Business、SharePoint、Exchange の IP DLP ポリシーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="e2941-118">You can set your IP DLP policies for OneDrive for Business, SharePoint, and Exchange in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users.</span></span> <span data-ttu-id="e2941-119">例: サテライト地域にいるユーザーのポリシーを選択する場合は、そのポリシーを特定の OneDrive に適用し、ユーザーの OneDrive URL を入力するように選択します。</span><span class="sxs-lookup"><span data-stu-id="e2941-119">For example: If you wish to select a policy for a user in a satellite location, select to apply the policy to a specific OneDrive and enter the user's OneDrive url.</span></span> <span data-ttu-id="e2941-120">DLP ポリシーを作成する際の一般的なガイダンスについては、[データ損失防止ポリシーの概要](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2941-120">See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="e2941-121">DLP ポリシーは、そのポリシーの適用性に基づいて各地域の場所に自動的に同期されます。</span><span class="sxs-lookup"><span data-stu-id="e2941-121">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="e2941-122">地域の場所のすべてのユーザーに対する Information Protection ポリシーとデータ損失防止ポリシーの実装は、UI で使用可能なオプションではありません。その代わりに、ポリシーの適用が可能なアカウントを選択するか、すべてのアカウントにグローバルにポリシーを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2941-122">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable accounts for the policy or apply the policy globally to all accounts.</span></span>

## <a name="microsoft-flow"></a><span data-ttu-id="e2941-123">Microsoft Flow</span><span class="sxs-lookup"><span data-stu-id="e2941-123">Microsoft Flow</span></span>

<span data-ttu-id="e2941-124">サテライト地域に作成された Flow は、テナントのデフォルトの地域にあるエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e2941-124">Flows created for the satellite location will use the end point located in the default geo location for the tenant.</span></span>  <span data-ttu-id="e2941-125">Microsoft Flow は、Multi-Geo サービスではありません。</span><span class="sxs-lookup"><span data-stu-id="e2941-125">Microsoft Flow is not a Multi-Geo service.</span></span> 

## <a name="microsoft-powerapps"></a><span data-ttu-id="e2941-126">Microsoft PowerApps</span><span class="sxs-lookup"><span data-stu-id="e2941-126">Microsoft PowerApps</span></span>

<span data-ttu-id="e2941-127">サテライト地域に作成された PowerApps は、テナントの中心地にあるエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e2941-127">PowerApps created for the satellite location will use the end point located in the central location for the tenant.</span></span> <span data-ttu-id="e2941-128">Microsoft PowerApps は、Multi-Geo サービスではありません。</span><span class="sxs-lookup"><span data-stu-id="e2941-128">Microsoft PowerApps is not a Multi-Geo service.</span></span> 

## <a name="onedrive-administrator-experience"></a><span data-ttu-id="e2941-129">OneDrive 管理者のエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="e2941-129">OneDrive Administrator Experience</span></span>

<span data-ttu-id="e2941-p107">[OneDrive 管理センター](https://admin.onedrive.com)の左側のナビゲーションには、**[地域の場所]** タブがあります。このタブには、地域の場所の地図があり、地域の場所を確認および管理できます。</span><span class="sxs-lookup"><span data-stu-id="e2941-p107">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

## <a name="security-and-compliance-admin-center"></a><span data-ttu-id="e2941-132">セキュリティ/コンプライアンス管理センター</span><span class="sxs-lookup"><span data-stu-id="e2941-132">Security and Compliance Admin Center</span></span>

<span data-ttu-id="e2941-133">複数地域テナントには、[Office 365 セキュリティ/コンプライアンス センター](https://protection.office.com/?rfr=AdminCenter\#/homepage)という 1 つの中心的なコンプライアンス センターがあります。</span><span class="sxs-lookup"><span data-stu-id="e2941-133">There is one central compliance center for a multi-geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

## <a name="sharepoint-storage-quota"></a><span data-ttu-id="e2941-134">SharePoint のストレージ クォータ</span><span class="sxs-lookup"><span data-stu-id="e2941-134">SharePoint storage quota</span></span>

<span data-ttu-id="e2941-135">デフォルトでは、複数地域環境のすべての地域では、使用できるテナントの ストレージ クォータを共有します。</span><span class="sxs-lookup"><span data-stu-id="e2941-135">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>  <span data-ttu-id="e2941-136">特定の地域に固有のクォータを割り当てることで、ストレージ クォータを管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="e2941-136">You can also manage the storage quota by allocating a specific quota for a particular geo location.</span></span> <span data-ttu-id="e2941-137">詳細については、[複数地域環境における SharePoint ストレージ クォータ](sharepoint-multi-geo-storage-quota.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2941-137">For more information, see [SharePoint storage quotas in multi-geo environments](sharepoint-multi-geo-storage-quota.md).</span></span>

## <a name="sharing"></a><span data-ttu-id="e2941-138">共有</span><span class="sxs-lookup"><span data-stu-id="e2941-138">Sharing</span></span>

<span data-ttu-id="e2941-139">管理者は、各地域のポリシーの共有を設定し管理できます。</span><span class="sxs-lookup"><span data-stu-id="e2941-139">Administrators can set and manage sharing policies for each of their locations.</span></span> <span data-ttu-id="e2941-140">各地域の OneDrive と SharePoint サイトは、対応する地域固有の共有設定のみを優先します。</span><span class="sxs-lookup"><span data-stu-id="e2941-140">The OneDrive and SharePoint sites in each geo location will honor only the corresponding geo specific sharing settings.</span></span> <span data-ttu-id="e2941-141">(たとえば、中心地への[外部共有](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)は許可できますが、サテライト地域またはその逆にはできません) 共有設定は地域間の共有制限を構成できませんので注意してください。</span><span class="sxs-lookup"><span data-stu-id="e2941-141">(For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo locations.</span></span>

## <a name="taxonomy"></a><span data-ttu-id="e2941-142">分類</span><span class="sxs-lookup"><span data-stu-id="e2941-142">Taxonomy</span></span>

<span data-ttu-id="e2941-143">マスターは会社の中心地にホストされているため、地域全体で会社の管理されたメタデータに統一された[分類](https://docs.microsoft.com/sharepoint/managed-metadata)をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e2941-143">We support a unified [taxonomy](https://docs.microsoft.com/sharepoint/managed-metadata) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company.</span></span> <span data-ttu-id="e2941-144">中心地からグローバル分類を管理し、サテライト地域の分類に地域固有の用語を追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e2941-144">We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite location's Taxonomy.</span></span> <span data-ttu-id="e2941-145">グローバル分類の用語は、サテライト地域に同期されます。</span><span class="sxs-lookup"><span data-stu-id="e2941-145">Global taxonomy terms will synchronize to the satellite locations.</span></span>

<span data-ttu-id="e2941-146">詳細と開発者向けガイダンスについては、[複数地域テナントにおけるメタデータの管理](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-managedmetadata)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2941-146">See [Manage metadata in a multi-geo tenant](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-managedmetadata) for additional details and for developer guidance.</span></span>

## <a name="user-profile-application"></a><span data-ttu-id="e2941-147">ユーザー プロファイル アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e2941-147">User Profile Application</span></span>

<span data-ttu-id="e2941-148">各地域に[ユーザー プロフィール アプリケーション](https://docs.microsoft.com/sharepoint/manage-user-profiles)があります。</span><span class="sxs-lookup"><span data-stu-id="e2941-148">There is a [user profile application](https://docs.microsoft.com/sharepoint/manage-user-profiles) in each geo location.</span></span> <span data-ttu-id="e2941-149">各ユーザーのプロフィール情報は、ユーザーの地域でホストされており、その地域の管理者が利用できます。</span><span class="sxs-lookup"><span data-stu-id="e2941-149">Each user's profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="e2941-150">カスタムのプロフィール プロパティがある場合は、すべての地域で同じプロフィール スキーマを使用して、すべての地域の場所または必要な場所のどちらかにカスタムのプロフィール プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="e2941-150">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span> <span data-ttu-id="e2941-151">プログラムを使用したユーザー プロフィール データの設定方法に関するガイダンスは、[ユーザー プロフィールの一括更新 API](https://docs.microsoft.com/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2941-151">For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).</span></span>

<span data-ttu-id="e2941-152">詳細と開発者向けガイダンスについては、[複数地域テナントのユーザー プロフィールの操作](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-userprofileexperience)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2941-152">See [Work with user profiles in a multi-geo tenant](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) for additional details and for developer guidance.</span></span>

## <a name="video-portal"></a><span data-ttu-id="e2941-153">ビデオ ポータル</span><span class="sxs-lookup"><span data-stu-id="e2941-153">Video Portal</span></span>

<span data-ttu-id="e2941-154">複数地域テナントでは、O365 ビデオ ポータルはデフォルト地域からのみ提供され、すべてのユーザーはその中央ポータル URL にリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="e2941-154">In a multi-geo tenant, the O365 Video Portal is served only from default geo and all users will be redirected to that central portal url.</span></span> <span data-ttu-id="e2941-155">そのため、その地域の Remote Media Service (RMS) が、中心地に基づいて次のように使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2941-155">Hence, the Remote Media Service (RMS) for that region will be used, as follows based on your central location.</span></span>

<span data-ttu-id="e2941-156">現在、Stream は以下の地域で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e2941-156">Stream is currently available in the following regions:</span></span>

- <span data-ttu-id="e2941-157">北米 (米国でホストされている)</span><span class="sxs-lookup"><span data-stu-id="e2941-157">North America, hosted in the United States</span></span> 
- <span data-ttu-id="e2941-158">ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="e2941-158">Europe</span></span>
- <span data-ttu-id="e2941-159">アジア太平洋</span><span class="sxs-lookup"><span data-stu-id="e2941-159">Asia Pacific</span></span>

<span data-ttu-id="e2941-160">ただし Stream は、現在 Office 365 ビデオ向けにサポートされている次の地域ではまだ使用できません。そのため、これらのローカル インスタンスには、サポートされている最も近い地域にある RMS を使用します。</span><span class="sxs-lookup"><span data-stu-id="e2941-160">However, Stream is not yet available in the following regions that are currently supported for Office 365 Video, therefore for these local instances, we will use the RMS that is in the closest supported region.</span></span>

- <span data-ttu-id="e2941-161">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="e2941-161">Australia</span></span>
- <span data-ttu-id="e2941-162">カナダ</span><span class="sxs-lookup"><span data-stu-id="e2941-162">Canada</span></span>
- <span data-ttu-id="e2941-163">インド</span><span class="sxs-lookup"><span data-stu-id="e2941-163">India</span></span>
- <span data-ttu-id="e2941-164">英国</span><span class="sxs-lookup"><span data-stu-id="e2941-164">United Kingdom</span></span>
