---
title: ディレクトリ同期のために非ルーティング ドメインの準備を整える
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_SetupDirSyncLocalDir
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Microsoft 365 と同期する前に、オンプレミスのユーザーに関連付けられた非ルーティングドメインがある場合の対処方法について説明します。
ms.openlocfilehash: 148d7e1abdeeeea11c838697bbc957e2937ea7f8
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736015"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="3c9bd-103">ディレクトリ同期のために非ルーティング ドメインの準備を整える</span><span class="sxs-lookup"><span data-stu-id="3c9bd-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="3c9bd-104">オンプレミスのディレクトリを Microsoft 365 と同期する場合は、Azure Active Directory (Azure AD) で確認済みのドメインを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-104">When you synchronize your on-premises directory with Microsoft 365 you have to have a verified domain in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="3c9bd-105">オンプレミスのドメインに関連付けられているユーザープリンシパル名 (UPN) のみが同期されます。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-105">Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized.</span></span> <span data-ttu-id="3c9bd-106">ただし、ルーティング可能ではないドメイン (たとえば billa@contoso ローカル) を含む任意の UPN は、onmicrosoft.com ドメイン (billa@contoso.onmicrosoft.com など) に同期されます。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-106">However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="3c9bd-107">現在、Active Directory ドメインサービス (AD DS) のユーザーアカウントにローカルドメインを使用している場合は、Microsoft 365 ドメインと適切に同期するために、確認済みのドメイン (billa@contoso.com など) を使用するように変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-107">If you currently use a .local domain for your user accounts in Active Directory Domain Services (AD DS) it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Microsoft 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="3c9bd-108">オンプレミス ドメインが .local のみの場合について</span><span class="sxs-lookup"><span data-stu-id="3c9bd-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="3c9bd-109">AD DS を Azure AD に同期するために使用できる最新のツールは、Azure AD Connect という名前です。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-109">The most recent tool you can use for synchronizing your AD DS to Azure AD is named Azure AD Connect.</span></span> <span data-ttu-id="3c9bd-110">詳細については、「[オンプレミス id と AZURE AD を統合する](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-110">For more information, see [Integrating your on-premises identities with Azure AD](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="3c9bd-111">Azure AD Connect は、ユーザーの UPN とパスワードを同期して、ユーザーがオンプレミスで使用したものと同じ資格情報でサインインできるようにします。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-111">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises.</span></span> <span data-ttu-id="3c9bd-112">ただし、Azure AD Connect は、Microsoft 365 によって検証されるドメインに対してのみユーザーを同期します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-112">However, Azure AD Connect only synchronizes users to domains that are verified by Microsoft 365.</span></span> <span data-ttu-id="3c9bd-113">これは、Microsoft 365 の id が Azure AD によって管理されているため、ドメインも Azure AD によって検証されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-113">This means that the domain also is verified by Azure AD because Microsoft 365 identities are managed by Azure AD.</span></span> <span data-ttu-id="3c9bd-114">言い換えると、ドメインは有効なインターネットドメインである必要があります (例: .com、.org、.net、. us など)。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-114">In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.).</span></span> <span data-ttu-id="3c9bd-115">内部 AD DS がルーティング可能ではないドメイン (たとえば、...) のみを使用している場合、これは Microsoft 365 の確認済みドメインと一致しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-115">If your internal AD DS only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Microsoft 365.</span></span> <span data-ttu-id="3c9bd-116">この問題を解決するには、オンプレミスの AD DS でプライマリドメインを変更するか、1つ以上の UPN サフィックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-116">You can fix this issue by either changing your primary domain in your on premises AD DS, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="3c9bd-117">**プライマリ ドメインを変更する**</span><span class="sxs-lookup"><span data-stu-id="3c9bd-117">**Change your primary domain**</span></span>

<span data-ttu-id="3c9bd-118">プライマリドメインを Microsoft 365 で確認したドメインに変更します。たとえば、contoso.com のようにします。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-118">Change your primary domain to a domain you have verified in Microsoft 365, for example, contoso.com.</span></span> <span data-ttu-id="3c9bd-119">ドメイン contoso. local を持つすべてのユーザーが contoso.com に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-119">Every user that has the domain contoso.local is then updated to contoso.com.</span></span> <span data-ttu-id="3c9bd-120">手順については、「[ドメイン名の変更のしくみ](https://go.microsoft.com/fwlink/p/?LinkId=624174)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-120">For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span></span> <span data-ttu-id="3c9bd-121">ただし、これは非常に複雑なプロセスであり、次のセクションではより簡単な解決方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-121">This is a very involved process, however, and an easier solution is described in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="3c9bd-122">**UPN サフィックスを追加してユーザーを更新する**</span><span class="sxs-lookup"><span data-stu-id="3c9bd-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="3c9bd-123">ローカルの問題を解決するには、Microsoft 365 で検証したドメイン (またはドメイン) に一致するように、AD DS に新しい UPN サフィックスまたはサフィックスを登録します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-123">You can solve the .local problem by registering new UPN suffix or suffixes in AD DS to match the domain (or domains) you verified in Microsoft 365.</span></span> <span data-ttu-id="3c9bd-124">新しいサフィックスを登録した後、ユーザーの Upn を更新して、を新しいドメイン名に置き換えます。たとえば、ユーザーアカウントが billa@contoso.com のように見えるようにします。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-124">After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="3c9bd-125">認証済みドメインを使用するように Upn を更新すると、オンプレミスの AD DS を Microsoft 365 と同期することができます。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises AD DS with Microsoft 365.</span></span>
  
 <span data-ttu-id="3c9bd-126">**手順 1: 新しい UPN サフィックスを追加する**</span><span class="sxs-lookup"><span data-stu-id="3c9bd-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="3c9bd-127">AD DS ドメインコントローラーのサーバーマネージャーで、[**ツール**] [ \> **Active Directory ドメインと信頼関係**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-127">On the AD DS domain controller, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="3c9bd-128">**または (Windows Server 2012 を所有していない場合)**</span><span class="sxs-lookup"><span data-stu-id="3c9bd-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="3c9bd-129">**Windows キー + R** を押して **[実行]** ダイアログ開き、「Domain.msc」と入力してから **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![[Active Directory ドメインと信頼関係] を選択します。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="3c9bd-131">**[Active Directory ドメインと信頼関係]** ウィンドウで、**[Active Directory ドメインと信頼関係]** を右クリックして **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![[Active Directory ドメインと信頼関係] を右クリックし、[プロパティ] を選択します。](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="3c9bd-133">**[UPN サフィックス]** タブの **[代替の UPN サフィックス]** ボックスに、新しいサフィックスを入力して **[追加]** \> **[適用]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![新しい UPN サフィックスを追加します](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="3c9bd-135">サフィックスの追加が完了したら、**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="3c9bd-136">**手順 2: 既存のユーザーの UPN サフィックスを変更する**</span><span class="sxs-lookup"><span data-stu-id="3c9bd-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="3c9bd-137">AD DS ドメインコントローラーで、サーバーマネージャーの [**ツール**] [ \> **Active Directory ユーザーとコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-137">On the AD DS domain controller, in the Server Manager choose **Tools** \> **Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="3c9bd-138">**または (Windows Server 2012 を所有していない場合)**</span><span class="sxs-lookup"><span data-stu-id="3c9bd-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="3c9bd-139">**Windows キー + R** を押して **[実行]** ダイアログ開き、「Dsa.msc」と入力してから **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="3c9bd-140">ユーザーを選択し、右クリックして **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="3c9bd-141">**[アカウント]** タブの UPN サフィックス ドロップダウン リストで、新しい UPN サフィックスを選択してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![ユーザーの新しい UPN サフィックスを追加する](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="3c9bd-143">すべてのユーザに対して、ここまでの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-143">Complete these steps for every user.</span></span>
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="3c9bd-144">**すべてのユーザーの UPN サフィックスを変更するために Windows PowerShell を使用する**</span><span class="sxs-lookup"><span data-stu-id="3c9bd-144">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="3c9bd-p106">更新するユーザー数が大量になる場合は、Windows PowerShell を使用すると作業が簡単になります。次の例では、コマンドレット [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) と [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) を使用して、すべての contoso.local サフィックスを contoso.com に変更します。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="3c9bd-147">用の例では、次の Windows PowerShell コマンドを実行して、すべての contoso. ローカルサフィックスを contoso.com に更新することができます。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-147">Foe example, you could run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

<span data-ttu-id="3c9bd-148">AD DS での Windows PowerShell の使用の詳細については、「 [Active Directory Windows powershell モジュール](https://go.microsoft.com/fwlink/p/?LinkId=624314)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c9bd-148">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in AD DS.</span></span> 

