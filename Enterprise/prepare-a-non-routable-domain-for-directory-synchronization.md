---
title: ディレクトリ同期のためのルーティング不可能なドメインを準備します。
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Office 365 と同期する前に、オンプレミスのユーザーと関連付けられている routale ではないドメインがある場合の対処方法を説明します。
ms.openlocfilehash: 62779ba879522177ba15a491644ab42f5961ece0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541783"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="fa63b-103">ディレクトリ同期のためのルーティング不可能なドメインを準備します。</span><span class="sxs-lookup"><span data-stu-id="fa63b-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="fa63b-p101">Azure Active Directory で検証済みのドメインに存在する必要が Office 365 で、設置ディレクトリを同期するとします。のみ、ユーザー プリンシパル名 (UPN)、オンプレミス ドメインに関連付けられているが同期されます。ルーティング不可能なドメイン (billa@contoso.local) のようなローカルな例が含まれているすべての UPN を同期するただし、です。 (billa@contoso.onmicrosoft.com) のような onmicrosoft.com ドメインです。</span><span class="sxs-lookup"><span data-stu-id="fa63b-p101">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory. Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized. However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="fa63b-107">現在 Active Directory でユーザー アカウントにローカルなドメインを使用する場合、Office 365 ドメインに正しく同期するために (billa@contoso.com) のようなことを確認したドメインを使用するように変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fa63b-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="fa63b-108">場合のみ .local オンプレミス ドメインがあるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="fa63b-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="fa63b-p102">Azure Active Directory、Active Directory を同期するために使用できる最新のツールを Azure AD 接続と呼びます。詳細については[、オンプレミス ユーザーは、Azure Active Directory との統合](https://go.microsoft.com/fwlink/p/?LinkId=624168)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa63b-p102">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=624168).</span></span>
  
<span data-ttu-id="fa63b-p103">Azure AD 接続と同期化、ユーザーの UPN パスワード ユーザーが署名できるように、設置型を使用する同じ資格情報を使用しています。ただし、Azure AD 接続は、ユーザーが Office 365 によって検証されているドメインのみを同期します。つまり、ドメインも検証 Azure Active Directory で Office 365 の id は、Azure Active Directory によって管理されるためです。つまり、ドメインを有効なインターネット ドメイン (たとえば、.com、.org、.net、.us など) をある必要があります。内部の Active Directory は、ルーティング不可能なドメイン (たとえば、ローカルな) のみを使用する場合は、Office 365 にあることを確認したドメイン可能性があると一致ことはできません。Active Directory で、設置型には、プライマリ ドメインを変更するか、または 1 つまたは複数の UPN サフィックスを追加することによってこの問題を解決できます。</span><span class="sxs-lookup"><span data-stu-id="fa63b-p103">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises. However, Azure AD Connect only synchronizes users to domains that are verified by Office 365. This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory. In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.). If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365. You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="fa63b-117">**プライマリ ドメインを変更します。**</span><span class="sxs-lookup"><span data-stu-id="fa63b-117">**Change your primary domain**</span></span>

<span data-ttu-id="fa63b-p104">プライマリ ドメインを Office 365 では、たとえば、contoso.com で確認したドメインに変更します。Contoso.com ドメイン contoso.local を持つすべてのユーザーが更新されます。手順については、[どのドメイン名変更のしくみ](https://go.microsoft.com/fwlink/p/?LinkId=624174)を参照してください。これは、非常に関連するプロセスでは、ただしと、簡単な解決法、[追加の UPN のサフィックスしユーザーがそれらを更新](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register)、次のセクションに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="fa63b-p104">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com. Every user that has the domain contoso.local is then updated to contoso.com. For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). This is a very involved process, however, and an easier solution is to [Add UPN suffixes and update your users to them](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), as shown in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="fa63b-122">**UPN サフィックスを追加し、ユーザーを更新すること**</span><span class="sxs-lookup"><span data-stu-id="fa63b-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="fa63b-p105">ローカルな問題を解決するドメイン (またはドメイン) に一致するように Active Directory に新しいユーザー プリンシパル名サフィックスやサフィックスを登録することでは、Office 365 のことを確認します。新しいサフィックスを登録した後は、ユーザーに置き換える、.local などの新しいドメイン名 billa@contoso.com のように、次のユーザー アカウントの Upn を更新します。</span><span class="sxs-lookup"><span data-stu-id="fa63b-p105">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365. After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="fa63b-125">検証済みのドメインを使用する Upn を更新した後、Office 365 で、オンプレミスの Active Directory を同期する準備が完了しています。</span><span class="sxs-lookup"><span data-stu-id="fa63b-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="fa63b-126">**手順 1: 新しい UPN サフィックスを追加します。**</span><span class="sxs-lookup"><span data-stu-id="fa63b-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="fa63b-127">[Active Directory ドメイン サービス (AD DS) を実行するサーバー、サーバー マネージャーで選択**ツール** \> **Active Directory ドメインと信頼関係**です。</span><span class="sxs-lookup"><span data-stu-id="fa63b-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="fa63b-128">**または、Windows Server 2012 を持っていない場合**</span><span class="sxs-lookup"><span data-stu-id="fa63b-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="fa63b-129">**実行**] ダイアログ ボックスを開き、表示、入力し、 **Windows キー + R**を押すし、[ **ok]** します。</span><span class="sxs-lookup"><span data-stu-id="fa63b-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Active Directory ドメインと信頼関係を選択します。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="fa63b-131">**Active Directory ドメインと信頼関係**] ウィンドウで、[ **Active Directory ドメインと信頼関係**を右クリックし、[**プロパティ**。</span><span class="sxs-lookup"><span data-stu-id="fa63b-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![ActiveDirectory ドメインと信頼関係を右クリックし、[プロパティ] を選択](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="fa63b-133">[ **UPN サフィックス**] タブ、[**代わりの UPN サフィックス**] ボックスに入力、新しい UPN サフィックスやサフィックス、および**追加**」を選択し、 \> **適用**します。</span><span class="sxs-lookup"><span data-stu-id="fa63b-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![新規のユーザー プリンシパル名サフィックスを追加します。](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="fa63b-135">サフィックスを追加する操作が完了したら、 **[ok]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fa63b-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="fa63b-136">**手順 2: 既存のユーザーの UPN サフィックスを変更します。**</span><span class="sxs-lookup"><span data-stu-id="fa63b-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="fa63b-137">[Active Directory ドメイン サービス (AD DS) を実行するサーバー、サーバー マネージャーで選択**ツール** \> **Active Directory Active Directory ユーザーとコンピューター**。</span><span class="sxs-lookup"><span data-stu-id="fa63b-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="fa63b-138">**または、Windows Server 2012 を持っていない場合**</span><span class="sxs-lookup"><span data-stu-id="fa63b-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="fa63b-139">**実行**] ダイアログ ボックスを開き、ファイルに入力するのには**Windows キー + R**を押すし、[ **OK** ] をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="fa63b-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="fa63b-140">ユーザーを選択し、右クリック**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa63b-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="fa63b-141">[**アカウント**] タブの [UPN サフィックスのボックスの一覧で、新しい UPN サフィックスを選択し、[ **ok]** します。</span><span class="sxs-lookup"><span data-stu-id="fa63b-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![ユーザー用の新しい UPN サフィックスを追加します。](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="fa63b-143">すべてのユーザーに対してこれらの手順を完了します。</span><span class="sxs-lookup"><span data-stu-id="fa63b-143">Complete these steps for every user.</span></span>
    
    <span data-ttu-id="fa63b-144">更新プログラムを一括してまたは UPN サフィックスの[すべてのユーザーの UPN サフィックスを変更するのには Windows PowerShell を使用することもできます](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh)。</span><span class="sxs-lookup"><span data-stu-id="fa63b-144">Alternately you can bulk update the UPN suffixes [You can also use Windows PowerShell to change the UPN suffix for all users](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span></span>
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="fa63b-145">**すべてのユーザーの UPN サフィックスを変更するのには、Windows PowerShell を使用することもできます。**</span><span class="sxs-lookup"><span data-stu-id="fa63b-145">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="fa63b-p106">多くのユーザを更新する場合は、Windows PowerShell を使用すると簡単です。次の使用例は、contoso.com にすべての contoso.local のサフィックスを変更するのには、 [Get ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312)と[セット ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313)コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="fa63b-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="fa63b-148">Contoso.com にすべての contoso.local のサフィックスを更新するのには、次の Windows PowerShell コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa63b-148">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="fa63b-149">Windows PowerShell を使用して Active Directory 内の詳細については、[作業中のディレクトリの Windows PowerShell モジュール](https://go.microsoft.com/fwlink/p/?LinkId=624314)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa63b-149">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

