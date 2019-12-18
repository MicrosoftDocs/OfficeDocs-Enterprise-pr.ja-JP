---
title: 管理対象ゲストを使用して B2B エクストラネットを作成する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: パートナー組織から管理されたゲストユーザーを使用して、B2B エクストラネットのサイトまたはチームを作成する方法について説明します。
ms.openlocfilehash: b314949e97789141bc510554da40409e8bf3b6df
ms.sourcegitcommit: f18f75dba4cbec557fa094bd1cebd8c5cc4752c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "40085420"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a><span data-ttu-id="20658-103">管理対象ゲストを使用して B2B エクストラネットを作成する</span><span class="sxs-lookup"><span data-stu-id="20658-103">Create a B2B extranet with managed guests</span></span>

<span data-ttu-id="20658-104">Azure active [Directory 受給管理](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview)を使用して、Azure active directory を使用するパートナー組織と共同作業する B2B エクストラネットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="20658-104">You can use [Azure Active Directory Entitlement Management](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) to create a B2B extranet to collaborate with a partner organization that uses Azure Active Directory.</span></span> <span data-ttu-id="20658-105">これにより、ユーザーは、エクストラネットサイトまたはチームで自分を登録し、承認ワークフローを使用してアクセスを受信することができます。</span><span class="sxs-lookup"><span data-stu-id="20658-105">This allows users to self-enroll in the extranet site or team and receive access via an approval workflow.</span></span>

<span data-ttu-id="20658-106">グループ作業のためにリソースを共有するためのこの方法を使用すると、パートナー組織は、エンドユーザーに対するゲストユーザーの管理と承認を支援し、IT 部門の負担を軽減して、ユーザーを管理するためのコラボレーション契約に精通しているユーザーを許可することができます。接続.</span><span class="sxs-lookup"><span data-stu-id="20658-106">With this method of sharing resources for collaboration, the partner organization can help maintain and approve the guest users on their end, reducing the burden on your IT department and allowing those most familiar with the collaboration agreement to manage user access.</span></span>

<span data-ttu-id="20658-107">この記事では、セルフサービスアクセス登録モデルを使用してパートナー組織と共有できるリソース (この場合は、サイトまたはチーム) のパッケージを作成するための手順を順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="20658-107">This article walks through the steps to create a package of resources (in this case, a site or team) that you can share with a partner organization through a self-service access registration model.</span></span> 

<span data-ttu-id="20658-108">開始する前に、パートナー組織と共有するサイトまたはチームを作成し、ゲスト共有に対して有効にします。</span><span class="sxs-lookup"><span data-stu-id="20658-108">Before you begin, create the site or team that you want to share with the partner organization and enable it for guest sharing.</span></span> <span data-ttu-id="20658-109">詳細については[、「サイト内のゲストを使用した共同作業](collaborate-in-a-site.md)」または「[チーム内のゲストによる共同作業](collaborate-as-a-team.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20658-109">See [Collaborate with guests in a site](collaborate-in-a-site.md) or [Collaborate with guests in a team](collaborate-as-a-team.md) for more information.</span></span> <span data-ttu-id="20658-110">また、ゲストを使用して共同作業を行う場合に、ガバナンスポリシーを維持するために使用できるセキュリティとコンプライアンスの機能については、「セキュリティ[保護されたゲスト共有環境を作成](create-a-secure-guest-sharing-environment.md)する」を参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="20658-110">We also recommend that you review [Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md) for information about security and compliance features that you can use to help maintain your governance policies when collaborating with guests.</span></span>

## <a name="connect-the-partner-organization"></a><span data-ttu-id="20658-111">パートナー組織を接続する</span><span class="sxs-lookup"><span data-stu-id="20658-111">Connect the partner organization</span></span>

<span data-ttu-id="20658-112">パートナー組織からゲストを招待するには、パートナーのドメインを、接続された組織として Azure Active Directory に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20658-112">In order to invite guests from a partner organization, you need to add the the partner's domain as a connected organization in Azure Active Directory.</span></span>

<span data-ttu-id="20658-113">接続された組織を追加するには</span><span class="sxs-lookup"><span data-stu-id="20658-113">To add a connected organization</span></span>
1. <span data-ttu-id="20658-114">[Azure Active Directory](https://aad.portal.azure.com)で、[ **id ガバナンス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-114">In [Azure Active Directory](https://aad.portal.azure.com), click **Identity Governance**.</span></span>
2. <span data-ttu-id="20658-115">[**接続組織**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-115">Click **Connected organizations**.</span></span>
4. <span data-ttu-id="20658-116">[**接続組織の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-116">Click **Add connected organization**.</span></span>
5. <span data-ttu-id="20658-117">組織の名前と説明を入力し、[**次へ: ディレクトリ + ドメイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-117">Type a name and description for the organization, and then click **Next: Directory + domain**.</span></span>
6. <span data-ttu-id="20658-118">[**ディレクトリ + ドメインの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-118">Click **Add directory + domain**.</span></span>
7. <span data-ttu-id="20658-119">接続する組織のドメインを入力し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-119">Type the domain for the organization that you want to connect, and then click **Add**.</span></span>
8. <span data-ttu-id="20658-120">[**接続**] をクリックし、[**次へ: スポンサー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-120">Click **Connect**, and then click **Next: Sponsors**.</span></span>
9. <span data-ttu-id="20658-121">組織内のユーザー、またはゲストユーザーのアクセスを承認するユーザーを追加する組織からユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="20658-121">Add people from your organization or the organization that you're connecting to who you want to approve access for guest users.</span></span>
10. <span data-ttu-id="20658-122">[ **Next: Review + Create**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-122">Click **Next: Review + Create**.</span></span>
11. <span data-ttu-id="20658-123">選択した設定を確認し、[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-123">Review the settings that you've chosen and then click **Create**.</span></span>

    ![Azure Active Directory の [接続されている組織] ページのスクリーンショット](media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a><span data-ttu-id="20658-125">共有するリソースを選択する</span><span class="sxs-lookup"><span data-stu-id="20658-125">Choose the resources to share</span></span>

<span data-ttu-id="20658-126">パートナー組織と共有するリソースを選択する最初の手順は、それらを含めるためのカタログを作成することです。</span><span class="sxs-lookup"><span data-stu-id="20658-126">The first step in selecting resources to share with a partner organization is to create a catalog to contain them.</span></span>

<span data-ttu-id="20658-127">カタログを作成するには</span><span class="sxs-lookup"><span data-stu-id="20658-127">To create a catalog</span></span>
1. <span data-ttu-id="20658-128">[Azure Active Directory](https://aad.portal.azure.com)で、[ **id ガバナンス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-128">In [Azure Active Directory](https://aad.portal.azure.com), click **Identity Governance**.</span></span>
2. <span data-ttu-id="20658-129">[**カタログ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-129">Click **Catalogs**.</span></span>
3. <span data-ttu-id="20658-130">[**新しいカタログ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-130">Click **New catalog**.</span></span>
4. <span data-ttu-id="20658-131">カタログの名前と説明を入力し、[**有効**] と [**外部ユーザーが有効**] と [有効] の両方が **[はい]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="20658-131">Type a name and description for the catalog and ensure that **Enabled** and **Enabled for external users** are both set to **Yes**.</span></span>
5. <span data-ttu-id="20658-132">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-132">Click **Create**.</span></span>

   ![Azure Active Directory Id ガバナンスの [カタログ] ページのスクリーンショット](media/identity-governance-catalogs.png)

<span data-ttu-id="20658-134">カタログを作成したら、パートナー組織と共有する SharePoint サイトまたはチームを追加します。</span><span class="sxs-lookup"><span data-stu-id="20658-134">Once the catalog has been created, you add the SharePoint site or team that you want to share with the partner organization.</span></span>

<span data-ttu-id="20658-135">リソースをカタログに追加するには</span><span class="sxs-lookup"><span data-stu-id="20658-135">To add resources to a catalog</span></span>
1. <span data-ttu-id="20658-136">Azure AD Identity ガバナンスで、[**カタログ**] をクリックし、リソースを追加するカタログをクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-136">In Azure AD Identity Governance, click **Catalogs**, and then click the catalog where you want to add resources.</span></span>
2. <span data-ttu-id="20658-137">[**リソース**] をクリックし、[**リソースの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-137">Click **Resources** and then click **Add resources**.</span></span>
3. <span data-ttu-id="20658-138">エクストラネットに含める teams または SharePoint サイトを選択し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-138">Select the teams or SharePoint sites that you want to include in your extranet, and then click **Add**.</span></span>

   ![Azure Active Directory Id ガバナンスの [カタログリソース] ページのスクリーンショット](media/identity-governance-catalog-resource.png)

<span data-ttu-id="20658-140">共有するリソースを定義したら、次の手順として、アクセスパッケージを作成します。これにより、パートナーユーザーに付与されるアクセスの種類、およびアクセスを要求する新しいパートナーユーザーの承認プロセスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="20658-140">Once you've defined the resources that you want to share, the next step is to create an access package, which defines the type of access that partner users are granted and the approval process for new partner users requesting access.</span></span>

<span data-ttu-id="20658-141">アクセスパッケージを作成するには</span><span class="sxs-lookup"><span data-stu-id="20658-141">To create an access package</span></span>
1. <span data-ttu-id="20658-142">Azure AD Identity ガバナンスで、[**カタログ**] をクリックし、アクセスパッケージを作成するカタログをクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-142">In Azure AD Identity Governance, click **Catalogs**, and then click the catalog where you want to create an access package.</span></span>
2. <span data-ttu-id="20658-143">[ **Access パッケージ**] をクリックし、[**新しいアクセスパッケージ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-143">Click **Access packages**, and then click **New access package**.</span></span>
3. <span data-ttu-id="20658-144">アクセスパッケージの名前と説明を入力し、[**次へ: リソースロール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-144">Type a name and description for the access package, and then click **Next: Resource roles**.</span></span>
4. <span data-ttu-id="20658-145">エクストラネットに使用するリソースをカタログから選択します。</span><span class="sxs-lookup"><span data-stu-id="20658-145">Choose the resources from the catalog that you want to use for your extranet.</span></span>
5. <span data-ttu-id="20658-146">各リソースの [**役割**] 列で、エクストラネットを使用するゲストユーザーに付与するユーザーロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="20658-146">For each resource, in the **Role** column, choose the user role you want to grant to the guest users who use the extranet.</span></span>
6. <span data-ttu-id="20658-147">[**次へ: 要求**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-147">Click **Next: Requests**.</span></span>
7. <span data-ttu-id="20658-148">[**アクセスを要求できるユーザー**] で、**ディレクトリ以外のユーザーに対して**[] を選択します。</span><span class="sxs-lookup"><span data-stu-id="20658-148">Under **Users who can request access**, choose **For users not in your directory**.</span></span>
8. <span data-ttu-id="20658-149">[特定の**接続組織**] オプションが選択されていることを確認し、[**ディレクトリの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-149">Ensure that the **Specific connected organizations** option is selected, and then click **Add directories**.</span></span>
9. <span data-ttu-id="20658-150">以前に追加した接続済み組織を選択し、[**選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-150">Choose the connected organization that you add earlier, and then click **Select**</span></span>
10. <span data-ttu-id="20658-151">[**承認**] で、[**承認を必須**にする] で [**はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="20658-151">Under **Approval**, choose **Yes** for **Require approval**.</span></span>
11. <span data-ttu-id="20658-152">[**最初の承認者**] で、前に追加したスポンサのいずれかを選択するか、特定のユーザーを選択します。</span><span class="sxs-lookup"><span data-stu-id="20658-152">Under **First approver**, choose one of the sponsors that you added earlier or choose a specific user.</span></span>
12. <span data-ttu-id="20658-153">[**フォールバックの追加**] をクリックし、フォールバック承認者を選択します。</span><span class="sxs-lookup"><span data-stu-id="20658-153">Click **Add fallback** and select a fallback approver.</span></span>
13. <span data-ttu-id="20658-154">[**有効にする**] で、[**はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="20658-154">Under **Enable**, choose **Yes**.</span></span>
14. <span data-ttu-id="20658-155">[**次へ: ライフサイクル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-155">Click **Next: Lifecycle**.</span></span>
15. <span data-ttu-id="20658-156">使用する有効期限とアクセスレビューの設定を選択し、[次へ] をクリックします。 [**確認 + 作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-156">Choose the expiration and access review settings that you want to use, and then click **Next: Review + Create**.</span></span>
16. <span data-ttu-id="20658-157">設定内容を確認し、[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-157">Review your settings, and then click **Create**.</span></span>

    ![Azure Active Directory Id ガバナンスの [access パッケージ] 画面のスクリーンショット](media/identity-governance-access-packages.png)

<span data-ttu-id="20658-159">大規模な組織と提携している場合は、アクセスパッケージを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="20658-159">If you're partnering with a large organization, you may want to hide the access package.</span></span> <span data-ttu-id="20658-160">パッケージが非表示の場合、パートナー組織のユーザーには、*自分のアクセス*ポータルにパッケージが表示されません。</span><span class="sxs-lookup"><span data-stu-id="20658-160">If the package is hidden, then users in the partner organization will not see the package on their *My Access* portal.</span></span> <span data-ttu-id="20658-161">代わりに、そのパッケージにサインアップするための直接リンクを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20658-161">Instead, they must be sent a direct link to sign up for the package.</span></span> <span data-ttu-id="20658-162">アクセスパッケージを非表示にすると、不適切なアクセス要求の数を減らすことができます。また、パートナー組織のポータルで利用できるアクセスパッケージを保持するのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="20658-162">Hiding the access package can reduce the number of inappropriate access requests and can also help keep available access packages organized in the partner organization's portal.</span></span>

<span data-ttu-id="20658-163">アクセスパッケージを非表示に設定するには</span><span class="sxs-lookup"><span data-stu-id="20658-163">To set an access package to hidden</span></span>
1. <span data-ttu-id="20658-164">[Azure AD Identity ガバナンス] で、[**アクセスパッケージ**] をクリックし、アクセスパッケージをクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-164">In Azure AD Identity Governance, click **Access packages**, and then click your access package.</span></span>
2. <span data-ttu-id="20658-165">[**概要**] ページで、[**編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-165">On the **Overview** page, click **Edit**.</span></span>
3. <span data-ttu-id="20658-166">[**プロパティ**] で [**非表示**の場合は**はい]** を選択し、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-166">Under **Properties**, choose **Yes** for **Hidden**, and then click **Save**.</span></span>

   ![[Access パッケージの編集のプロパティ] 画面のスクリーンショット](media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a><span data-ttu-id="20658-168">パートナーユーザーの招待</span><span class="sxs-lookup"><span data-stu-id="20658-168">Invite partner users</span></span>

<span data-ttu-id="20658-169">アクセスパッケージを非表示に設定した場合は、パートナー組織への直接リンクを送信して、サイトまたはチームへのアクセスを要求できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="20658-169">If you set the access package to hidden, you need to send a direct link to the partner organization so that they can request access to your site or team.</span></span>

<span data-ttu-id="20658-170">アクセスポータルのリンクを見つけるには</span><span class="sxs-lookup"><span data-stu-id="20658-170">To find the access portal link</span></span>
1. <span data-ttu-id="20658-171">[Azure AD Identity ガバナンス] で、[**アクセスパッケージ**] をクリックし、アクセスパッケージをクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-171">In Azure AD Identity Governance, click **Access packages**, and then click your access package.</span></span>
2. <span data-ttu-id="20658-172">[**概要**] ページで、[ **My Access ポータル] リンク**の [**クリップボードにコピー** ] リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="20658-172">On the **Overview** page, click **Copy to clipboard** link for the **My Access portal link**.</span></span>

   ![Access ポータルリンクを使用した access パッケージプロパティのスクリーンショット](media/identity-governance-access-portal-link.png)

<span data-ttu-id="20658-174">リンクをコピーしたら、パートナー組織の連絡先と共有することができます。また、そのリンクをコラボレーションチームのユーザーに送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="20658-174">Once you have copied the link, you can share it with your contact at the partner organization and they can send it to the users on their collaboration team.</span></span>

## <a name="see-also"></a><span data-ttu-id="20658-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="20658-175">See Also</span></span>

[<span data-ttu-id="20658-176">セキュリティで保護されたゲスト共有の環境を作成する</span><span class="sxs-lookup"><span data-stu-id="20658-176">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

