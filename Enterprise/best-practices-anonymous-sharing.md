---
title: 認証されていない共有のベスト プラクティス
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
f1.keywords: NOCSH
description: 認証されていないユーザーとファイルおよびフォルダーを共有するためのベスト プラクティスを説明します。
ms.openlocfilehash: 38afdcb2d59547144e57656971395c48506bcbbf
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549126"
---
# <a name="best-practices-for-sharing-files-and-folders-with-unauthenticated-users"></a><span data-ttu-id="f6b51-103">認証されていないユーザーとファイルおよびフォルダーを共有するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="f6b51-103">Best practices for sharing files and folders with unauthenticated users</span></span>

<span data-ttu-id="f6b51-104">認証されていない共有 ([*すべてのユーザー*] リンク) は便利で、さまざまなシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-104">Unauthenticated sharing (*Anyone* links) can be convenient and is useful in various scenarios.</span></span> <span data-ttu-id="f6b51-105">[*すべてのユーザー*] リンクは、最も簡単な共有方法です。ユーザーは認証なしでリンクを開くことができ、そのリンクを他のユーザーに自由に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-105">*Anyone* links are the easiest way to share: people can open the link without authentication and are free to pass it on to others.</span></span>

<span data-ttu-id="f6b51-106">通常、組織内のすべてのコンテンツが認証されていない共有に適しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f6b51-106">Usually, not all content in an organization is appropriate for unauthenticated sharing.</span></span> <span data-ttu-id="f6b51-107">この記事では、ユーザーがファイルやフォルダーの認証されていない共有を使用できるものの、組織のコンテンツを保護するのに役立つセーフガードが設定されている環境を作成するのに利用できるオプションを説明します。</span><span class="sxs-lookup"><span data-stu-id="f6b51-107">This article covers the options available to help you create an environment where your users can use unauthenticated sharing of files and folders, but where there are safeguards in place to help protect your organization's content.</span></span>

> [!NOTE]
> <span data-ttu-id="f6b51-108">認証されていない共有を機能させるには、お客様の組織、および使用する予定の個々のサイトやチームに対して認証されていない共有を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6b51-108">For unauthenticated sharing to work, you must enable it for your organization and for the individual site or team that you'll be using.</span></span> <span data-ttu-id="f6b51-109">有効にするシナリオについては、「[組織外のユーザーとの共同作業](collaborating-with-people-outside-your-organization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6b51-109">See [Collaborating with people outside your organization](collaborating-with-people-outside-your-organization.md) for the scenario that you want to enable.</span></span>

## <a name="set-an-expiration-date-for-anyone-links"></a><span data-ttu-id="f6b51-110">[すべてのユーザー] リンクの有効期限を設定する</span><span class="sxs-lookup"><span data-stu-id="f6b51-110">Set an expiration date for Anyone links</span></span>

<span data-ttu-id="f6b51-111">ファイルは、サイト、グループ、チーム内に長期間保存されることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="f6b51-111">Files are often stored in sites, groups, and teams for long periods of time.</span></span> <span data-ttu-id="f6b51-112">データ保持ポリシーによってファイルを数年間保持するように要求されている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f6b51-112">Occasionally there are data retention policies that require files to be retained for years.</span></span> <span data-ttu-id="f6b51-113">そのようなファイルが認証されていない人と共有されている場合、ファイルへの予期しないアクセスや変更の原因となる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6b51-113">If such files are shared with unauthenticated people, this could lead to unexpected access and changes to files in the future.</span></span> <span data-ttu-id="f6b51-114">このような可能性を軽減するため、*[すべてのユーザー]* リンクの有効期限を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-114">To mitigate this possibility, you can configure an expiration time for *Anyone* links.</span></span>

<span data-ttu-id="f6b51-115">*[すべてのユーザー]* リンクの期限が切れると、そのリンクを使用してコンテンツにアクセスすることはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="f6b51-115">Once an *Anyone* link expires, it can no longer be used to access content.</span></span>

<span data-ttu-id="f6b51-116">[すべてのユーザー] リンクの有効期限を設定するには</span><span class="sxs-lookup"><span data-stu-id="f6b51-116">To set an expiration date for Anyone links</span></span>
1. <span data-ttu-id="f6b51-117">SharePoint Online 管理センターを開きます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-117">Open the SharePoint Online admin center.</span></span>
2. <span data-ttu-id="f6b51-118">左側のナビゲーションで **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-118">In the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="f6b51-119">**[[すべてのユーザー] リンクの詳細設定]** で、**[これらのリンクは、次の日数以内に期限切れにする必要があります]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-119">Under **Advanced settings for "Anyone" links**, select the **These links must expire within this many days** check box.</span></span></br>
   <span data-ttu-id="f6b51-120">![SharePoint における組織レベルの [すべてのユーザー] リンクの有効期限設定のスクリーンショット](media/sharepoint-organization-anyone-link-expiration.png)</span><span class="sxs-lookup"><span data-stu-id="f6b51-120">![Screenshot of SharePoint organization-level Anyone link expiration settings](media/sharepoint-organization-anyone-link-expiration.png)</span></span>
4. <span data-ttu-id="f6b51-121">このボックスに日数を入力し、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-121">Type a number of days in the box, and then click **Save**.</span></span>

<span data-ttu-id="f6b51-122">*[すべてのユーザー]* リンクの有効期限が切れても、新しい *[すべてのユーザー]* リンクを使ってファイルやフォルダーを再共有できることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="f6b51-122">Note that once an *Anyone* link expires, the file or folder can be re-shared with a new *Anyone* link.</span></span>

## <a name="set-link-permissions"></a><span data-ttu-id="f6b51-123">リンクのアクセス許可を設定する</span><span class="sxs-lookup"><span data-stu-id="f6b51-123">Set link permissions</span></span>

<span data-ttu-id="f6b51-124">既定では、ファイルに対して *[すべてのユーザー]* リンクを使用すると、ユーザーはそのファイルを編集することができます。また、フォルダーに対して *[すべてのユーザー]* リンクを使用すると、ユーザーはファイルの編集と表示に加えて、そのフォルダーに新しいファイルをアップロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-124">By default, *Anyone* links for a file allow people to edit the file, and *Anyone* links for a folder allow people to edit and view files, and upload new files to the folder.</span></span> <span data-ttu-id="f6b51-125">ファイルやフォルダーに対するこれらのアクセス許可は、表示のみに個別に変更できます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-125">You can change these permissions for files and for folders independently to view-only.</span></span>

<span data-ttu-id="f6b51-126">認証されていない共有を許可したい一方で、認証されていない人によって組織のコンテンツが変更されることへの懸念がある場合は、ファイルとフォルダーのアクセス許可を [**表示**] に設定することをご検討ください。</span><span class="sxs-lookup"><span data-stu-id="f6b51-126">If you want to allow unauthenticated sharing, but are concerned about unauthenticated people modifying your organization's content, consider setting the file and folder permissions to **View**.</span></span>

<span data-ttu-id="f6b51-127">[すべてのユーザー] リンクにアクセス許可を設定するには</span><span class="sxs-lookup"><span data-stu-id="f6b51-127">To set permissions for Anyone links</span></span>
1. <span data-ttu-id="f6b51-128">SharePoint Online 管理センターを開きます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-128">Open the SharePoint Online admin center.</span></span>
2. <span data-ttu-id="f6b51-129">左側のナビゲーションで **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-129">In the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="f6b51-130">**[[すべてのユーザー] リンクの詳細設定]** で、使用するファイルとフォルダーのアクセス許可を選択します。</span><span class="sxs-lookup"><span data-stu-id="f6b51-130">Under **Advanced settings for "Anyone" links**, select the file and folder permissions that you want to use.</span></span></br>
   <span data-ttu-id="f6b51-131">![SharePoint における組織レベルの [すべてのユーザー] リンクのアクセス許可設定のスクリーンショット](media/sharepoint-organization-anyone-link-permissions.png)</span><span class="sxs-lookup"><span data-stu-id="f6b51-131">![Screenshot of SharePoint organization-level Anyone link permissions settings](media/sharepoint-organization-anyone-link-permissions.png)</span></span>

<span data-ttu-id="f6b51-132">*[すべてのユーザー]* リンクが **[表示]** に設定されていても、*[特定のユーザー]* リンクを使用することにより、ユーザーはファイルやフォルダーをゲストと共有して、ゲストに編集するアクセス許可を付与できます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-132">With *Anyone* links set to **View**, users can still share files and folders with guests and give them edit permissions by using *Specific people* links.</span></span> <span data-ttu-id="f6b51-133">[特定のユーザー] リンクでは組織外のユーザーにゲストとしての認証が要求されるため、これらのリンクを使用して共有されているファイルやフォルダーに対するゲストのアクティビティを追跡および監査できます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-133">These links require people outside your organization to authenticate as guests, and you can track and audit guest activity on files and folders shared with these links.</span></span>

## <a name="set-default-link-type-to-only-work-for-people-in-your-organization"></a><span data-ttu-id="f6b51-134">既定のリンクの種類が組織内のユーザーに対してのみ有効になるように設定する</span><span class="sxs-lookup"><span data-stu-id="f6b51-134">Set default link type to only work for people in your organization</span></span>

<span data-ttu-id="f6b51-135">組織で *[すべてのユーザー]* 共有が有効になっている場合、既定の共有リンクは通常 **[すべてのユーザー]** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="f6b51-135">When *Anyone* sharing is enabled for your organization, the default sharing link is normally set to **Anyone**.</span></span> <span data-ttu-id="f6b51-136">これはユーザーにとって便利である反面、意図せずに認証されていない共有のリスクを高める可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6b51-136">While this can be convenient for users, it can increase the risk of unintentional unauthenticated sharing.</span></span> <span data-ttu-id="f6b51-137">機密性の高いドキュメントを共有する際にユーザーがリンクの種類を変更し忘れると、認証を必要としない共有リンクが誤って作成される恐れがあります。</span><span class="sxs-lookup"><span data-stu-id="f6b51-137">If a user forgets to change the link type while sharing a sensitive document, they might accidentally create a sharing link that doesn't require authentication.</span></span>

<span data-ttu-id="f6b51-138">既定のリンク設定を組織内のユーザーに対してのみ有効なリンクに変更することにより、このようなリスクを軽減できます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-138">You can mitigate this risk by changing the default link setting to a link that only works for people inside your organization.</span></span> <span data-ttu-id="f6b51-139">認証されていない人と共有したいユーザーは、そのオプションを意図的に選択することが必要になります。</span><span class="sxs-lookup"><span data-stu-id="f6b51-139">Users who want to share with unauthenticated people would then have to specifically select that option.</span></span>

<span data-ttu-id="f6b51-140">既定のファイルおよびフォルダーの共有リンクを設定するには</span><span class="sxs-lookup"><span data-stu-id="f6b51-140">To set the default file and folder sharing link</span></span>
1. <span data-ttu-id="f6b51-141">SharePoint 管理センターの左側のナビゲーションで、**[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="f6b51-142">**[ファイルとフォルダーのリンク]** で、**[自分の組織内のユーザーのみ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f6b51-142">Under **File and folder links**, select **Only people in your organization**.</span></span></br>
   <span data-ttu-id="f6b51-143">![SharePoint の既定のリンクの種類設定のスクリーンショット](media/sharepoint-default-sharing-link-company-link.png)</span><span class="sxs-lookup"><span data-stu-id="f6b51-143">![Screenshot of SharePoint default link type setting](media/sharepoint-default-sharing-link-company-link.png)</span></span>
3. <span data-ttu-id="f6b51-144">**[保存]** をクリックします</span><span class="sxs-lookup"><span data-stu-id="f6b51-144">Click **Save**</span></span>

## <a name="protect-against-malicious-files"></a><span data-ttu-id="f6b51-145">悪意のあるファイルから保護する</span><span class="sxs-lookup"><span data-stu-id="f6b51-145">Protect against malicious files</span></span>

<span data-ttu-id="f6b51-146">匿名ユーザーにファイルのアップロードを許可する場合、悪意のあるファイルをアップロードされるリスクが高くなります。</span><span class="sxs-lookup"><span data-stu-id="f6b51-146">When you allow anonymous users to upload files, you're at an increased risk of someone uploading a malicious file.</span></span> <span data-ttu-id="f6b51-147">Microsoft 365 では、Advanced Threat Protection の*安全な添付ファイル*機能を使用することにより、アップロードされたファイルを自動的にスキャンし、安全でないことが判明したファイルを検疫できます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-147">In Microsoft 365, you can use the *safe attachments* feature in Advanced Threat Protection to automatically scan uploaded files and quarantine files that are found to be unsafe.</span></span>

<span data-ttu-id="f6b51-148">安全な添付ファイル機能をオンにするには</span><span class="sxs-lookup"><span data-stu-id="f6b51-148">To turn on safe attachments</span></span>
1. <span data-ttu-id="f6b51-149">[Microsoft 365 セキュリティ](https://security.microsoft.com)管理センターを開きます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-149">Open the [Microsoft 365 security](https://security.microsoft.com) admin center.</span></span>
2. <span data-ttu-id="f6b51-150">左側のナビゲーションで **[ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-150">In the left navigation, click **Policies**.</span></span>
3. <span data-ttu-id="f6b51-151">**[脅威の防止]** で、**[ATP の安全な添付ファイル (Office 365)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-151">Under **Threat protection**, click **ATP safe attachments (Office 365)**.</span></span>
4. <span data-ttu-id="f6b51-152">**[SharePoint、OneDrive、Microsoft Teams に対して ATP を有効にする]** チェック ボックスをオンにし、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-152">Select the **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams** check box, and then click **Save**.</span></span></br>
   <span data-ttu-id="f6b51-153">![セキュリティ/コンプライアンス センターの安全な添付ファイル設定のスクリーンショット](media/safe-attachments-setting.png)</span><span class="sxs-lookup"><span data-stu-id="f6b51-153">![Screenshot of the safe attachments setting in the Security and Compliance center](media/safe-attachments-setting.png)</span></span>

## <a name="add-copyright-information-to-your-files"></a><span data-ttu-id="f6b51-154">ファイルに著作権情報を追加する</span><span class="sxs-lookup"><span data-stu-id="f6b51-154">Add copyright information to your files</span></span>

<span data-ttu-id="f6b51-155">Microsoft 365 コンプライアンス管理センターで秘密度ラベルを使用する場合、組織の Office ドキュメントに透かしやヘッダーかフッターが自動的に追加されるようにラベルを設定できます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-155">If you use sensitivity labels in the Microsoft 365 Compliance admin center, you can configure your labels to add a watermark or a header or footer automatically to your organization's Office documents.</span></span> <span data-ttu-id="f6b51-156">このようにすることで、共有ファイルに著作権などの所有者情報が確実に含められるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-156">In this way, you can make sure that shared files contain copyright or other ownership information.</span></span>

<span data-ttu-id="f6b51-157">ラベルが付けられたファイルにフッターを追加するには</span><span class="sxs-lookup"><span data-stu-id="f6b51-157">To add a footer to a labeled file</span></span>
1. <span data-ttu-id="f6b51-158">[Microsoft 365 コンプライアンス管理センター](https://compliance.microsoft.com)を開きます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-158">Open the [Microsoft 365 compliance admin center](https://compliance.microsoft.com).</span></span>
2. <span data-ttu-id="f6b51-159">左側のナビゲーションの **[分類]** で、**[秘密度ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-159">In the left navigation, under **Classification**, click **Sensitivity labels**.</span></span>
3. <span data-ttu-id="f6b51-160">フッターを追加するラベルをクリックし、**[ラベルの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-160">Click the label that you want to have add a footer, and then click **Edit label**.</span></span>
4. <span data-ttu-id="f6b51-161">**[コンテンツのマーキング]** タブをクリックし、[コンテンツのマーキング] を **[オン]** にします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-161">Click the **Content marking** tab, and then turn **On** content marking.</span></span>
5. <span data-ttu-id="f6b51-162">追加するテキストの種類のチェック ボックスをオンにして、**[テキストをカスタマイズする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-162">Select the check box for the type of text you want to add, and then click **Customize text**.</span></span>
6. <span data-ttu-id="f6b51-163">ドキュメントに追加するテキストを入力し、目的のテキスト オプションを選択して、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-163">Type the text that you want added to your documents, select the text options that you want, and then click **Save**.</span></span></br>
   <span data-ttu-id="f6b51-164">![秘密度ラベルのコンテンツのマーキング設定のスクリーンショット](media/content-marking-for-anonymous-sharing.png)</span><span class="sxs-lookup"><span data-stu-id="f6b51-164">![Screenshot of the content marking settings for a sensitivity label](media/content-marking-for-anonymous-sharing.png)</span></span>
7. <span data-ttu-id="f6b51-165">**[保存]** をクリックし、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6b51-165">Click **Save**, and then click **Close**.</span></span>

<span data-ttu-id="f6b51-166">コンテンツのマーキングがラベルに対して有効になっている状態で、そのラベルをユーザーが適用すると、Office ドキュメントに指定したテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="f6b51-166">With content marking enabled for the label, the text you specified will be added to Office documents when a user applies that label.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6b51-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6b51-167">See Also</span></span>


[<span data-ttu-id="f6b51-168">秘密度ラベルの概要</span><span class="sxs-lookup"><span data-stu-id="f6b51-168">Overview of sensitivity labels</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)

[<span data-ttu-id="f6b51-169">ゲストと共有するときにファイルの偶発的な公開を制限する</span><span class="sxs-lookup"><span data-stu-id="f6b51-169">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

[<span data-ttu-id="f6b51-170">セキュリティで保護されたゲスト共有環境を作成する</span><span class="sxs-lookup"><span data-stu-id="f6b51-170">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)