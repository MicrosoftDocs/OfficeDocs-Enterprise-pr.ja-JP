---
title: ディレクトリ同期のために非ルーティング ドメインの準備を整える
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: オンプレミス ユーザーに非ルーティング ドメインが関連付けられている場合、Office 365 との同期前に実行する手順について説明します。
ms.openlocfilehash: cf7b901c3aaf6f49e4ecd92d27b9a6d9b8951d40
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203636"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="183db-103">ディレクトリ同期のために非ルーティング ドメインの準備を整える</span><span class="sxs-lookup"><span data-stu-id="183db-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="183db-p101">Office 365 とオンプレミス ディレクトリとの同期時には、Azure Active Directory 内に確認済みのドメインを用意する必要があります。オンプレミス ドメインに関連付けられたユーザー プリンシパル名 (UPN) のみが同期されます。ただし、.local などの非ルーティング ドメインが含まれている UPN (例: billa@contoso.local) は、.onmicrosoft.com ドメイン (例: billa@contoso.onmicrosoft.com) と同期されるようになります。</span><span class="sxs-lookup"><span data-stu-id="183db-p101">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory. Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized. However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="183db-107">現在、Active Directory 内のユーザー アカウントに .local ドメインを使用している場合は、Office 365 ドメインとの正しい同期のために、確認済みのドメイン (例: billa@contoso.com) を使用するようにユーザー アカウントを変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="183db-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="183db-108">オンプレミス ドメインが .local のみの場合について</span><span class="sxs-lookup"><span data-stu-id="183db-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="183db-p102">Active Directory と Azure Active Directory の同期には、Azure AD Connect という最新のツールを使用できます。詳細については、「[オンプレミスの ID と Azure Active Directory を統合する](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="183db-p102">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="183db-p103">Azure AD Connect では、ユーザーがオンプレミスで使用している資格情報と同じものを使用してサインイン可能になるように、ユーザーの UPN とパスワードを同期します。ただし、Azure AD Connect によるユーザーの同期は、Office 365 で確認済みのドメインのみを対象としています。Office 365 の ID は Azure Active Directory によって管理されるため、ドメインも Azure Active Directory によって確認されていることになります。つまり、ドメインは有効なインターネット ドメイン (com、.org、.net、.us など) であることが必要になります。内部の Active Directory が非ルーティング ドメイン (例: .local) のみを使用している場合は、そのドメインが Office 365 の確認済みドメインと一致する可能性はありません。この問題は、オンプレミスの Active Directory のプライマリ ドメインを変更するか、1 つ以上の UPN サフィックスを追加することで解決できます。</span><span class="sxs-lookup"><span data-stu-id="183db-p103">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises. However, Azure AD Connect only synchronizes users to domains that are verified by Office 365. This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory. In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.). If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365. You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="183db-117">**プライマリ ドメインを変更する**</span><span class="sxs-lookup"><span data-stu-id="183db-117">**Change your primary domain**</span></span>

<span data-ttu-id="183db-118">プライマリドメインを Office 365 で確認したドメイン (contoso.com など) に変更します。</span><span class="sxs-lookup"><span data-stu-id="183db-118">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com.</span></span> <span data-ttu-id="183db-119">ドメイン contoso. local を持つすべてのユーザーが contoso.com に更新されます。</span><span class="sxs-lookup"><span data-stu-id="183db-119">Every user that has the domain contoso.local is then updated to contoso.com.</span></span> <span data-ttu-id="183db-120">手順については、「[ドメイン名の変更のしくみ](https://go.microsoft.com/fwlink/p/?LinkId=624174)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="183db-120">For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span></span> <span data-ttu-id="183db-121">ただし、これは非常に複雑なプロセスであり、次のセクションではより簡単な解決方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="183db-121">This is a very involved process, however, and an easier solution is described in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="183db-122">**UPN サフィックスを追加してユーザーを更新する**</span><span class="sxs-lookup"><span data-stu-id="183db-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="183db-p105">.local の問題は、Office 365 で確認したドメインと一致する新しい UPN サフィックスを Active Directory に登録することで解決できます。新しいサフィックスの登録後に、ユーザー アカウントが billa@contoso.com のようになるように、.local を置換することでユーザー UPN を更新します。</span><span class="sxs-lookup"><span data-stu-id="183db-p105">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365. After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="183db-125">確認済みのドメインを使用するように UPN を更新すると、オンプレミスの Active Directory を Office 365 と同期するための準備が整います。</span><span class="sxs-lookup"><span data-stu-id="183db-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="183db-126">**手順 1: 新しい UPN サフィックスを追加する**</span><span class="sxs-lookup"><span data-stu-id="183db-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="183db-127">Active Directory ドメイン サービス (AD DS) を実行しているサーバーで、サーバー マネージャの **[ツール]** \> **[Active Directory ドメインと信頼関係]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="183db-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="183db-128">**または (Windows Server 2012 を所有していない場合)**</span><span class="sxs-lookup"><span data-stu-id="183db-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="183db-129">**Windows キー + R** を押して **[実行]** ダイアログ開き、「Domain.msc」と入力してから **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="183db-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![[Active Directory ドメインと信頼関係] を選択します。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="183db-131">**[Active Directory ドメインと信頼関係]** ウィンドウで、**[Active Directory ドメインと信頼関係]** を右クリックして **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="183db-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![[Active Directory ドメインと信頼関係] を右クリックして [プロパティ] を選択します](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="183db-133">**[UPN サフィックス]** タブの **[代替の UPN サフィックス]** ボックスに、新しいサフィックスを入力して **[追加]** \> **[適用]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="183db-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![新しい UPN サフィックスを追加します](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="183db-135">サフィックスの追加が完了したら、**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="183db-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="183db-136">**手順 2: 既存のユーザーの UPN サフィックスを変更する**</span><span class="sxs-lookup"><span data-stu-id="183db-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="183db-137">Active Directory ドメイン サービス (AD DS) を実行しているサーバーで、サーバー マネージャの **[ツール]** \> **[Active Directory ユーザーとコンピューター]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="183db-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="183db-138">**または (Windows Server 2012 を所有していない場合)**</span><span class="sxs-lookup"><span data-stu-id="183db-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="183db-139">**Windows キー + R** を押して **[実行]** ダイアログ開き、「Dsa.msc」と入力してから **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="183db-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="183db-140">ユーザーを選択し、右クリックして **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="183db-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="183db-141">**[アカウント]** タブの UPN サフィックス ドロップダウン リストで、新しい UPN サフィックスを選択してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="183db-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![ユーザーの新しい UPN サフィックスを追加する](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="183db-143">すべてのユーザに対して、ここまでの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="183db-143">Complete these steps for every user.</span></span>
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="183db-144">**すべてのユーザーの UPN サフィックスを変更するために Windows PowerShell を使用する**</span><span class="sxs-lookup"><span data-stu-id="183db-144">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="183db-p106">更新するユーザー数が大量になる場合は、Windows PowerShell を使用すると作業が簡単になります。次の例では、コマンドレット [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) と [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) を使用して、すべての contoso.local サフィックスを contoso.com に変更します。</span><span class="sxs-lookup"><span data-stu-id="183db-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="183db-147">次の Windows PowerShell コマンドを実行すると、すべての contoso.local サフィックスが contoso.com に更新されます。</span><span class="sxs-lookup"><span data-stu-id="183db-147">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="183db-148">Active Directory の Windows PowerShell を使用する方法の詳細については、「[Active Directory Windows PowerShell モジュール](https://go.microsoft.com/fwlink/p/?LinkId=624314)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="183db-148">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

