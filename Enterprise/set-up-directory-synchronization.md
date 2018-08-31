---
title: Office 365 のディレクトリ同期のセットアップ
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365 と、オンプレミスの Active Directory のディレクトリ同期をセットアップする方法について説明します。
ms.openlocfilehash: e406eec08b34a694602c756235533f8b1ff6651e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541545"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="78eeb-103">Office 365 のディレクトリ同期のセットアップ</span><span class="sxs-lookup"><span data-stu-id="78eeb-103">Set up directory synchronization for Office 365</span></span>
<span data-ttu-id="78eeb-p101">Office 365 は、ユーザーを管理するのにクラウド ベースのユーザー id の管理の Azure Active Directory サービスを使用します。Azure AD を Office 365 で、オンプレミス環境を同期することにより、オンプレミスの Active Directory を統合することも。同期を設定すると、Azure AD 内で、または、設置ディレクトリ内のユーザー認証を決定できます。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="78eeb-107">Office 365 ディレクトリ同期</span><span class="sxs-lookup"><span data-stu-id="78eeb-107">Office 365 directory synchronization</span></span>
<span data-ttu-id="78eeb-p102">同期の id や、設置型の組織と Office 365 の間でフェデレーション id を使用することができます。同期の id で、ユーザー設置を管理すると、同じパスワードを使用、クラウドでオンプレミスと Azure の AD によって認証します。これは、最も一般的なディレクトリ同期シナリオです。パススルー認証] または [フェデレーション id は、ユーザーの設置型を管理することをでき、オンプレミス ディレクトリで認証します。フェデレートされた識別情報は、追加の構成を必要とし、のみ 1 回サインインすることができます。詳細については、 [Office 365 の Id を理解して Azure Active Directory](about-office-365-identity.md)を読み取る。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="78eeb-114">Azure Active Directory に接続するのには、Windows Azure Active Directory 同期 (DirSync) からアップグレードする場合は、</span><span class="sxs-lookup"><span data-stu-id="78eeb-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>
<span data-ttu-id="78eeb-115">ディレクトリ同期を現在使用してアップグレードする場合、ヘッドを[azure.com](https://azure.com)に[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)の。</span><span class="sxs-lookup"><span data-stu-id="78eeb-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="78eeb-116">Azure AD の前提条件を接続します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-116">Prerequisites for Azure AD Connect</span></span>
<span data-ttu-id="78eeb-p103">Azure AD に Office 365 サブスクリプションと無料サブスクリプションを取得します。、ディレクトリ同期をセットアップすると、Azure Active Directory の接続をインストール、オンプレミスのサーバーのいずれかにされます。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="78eeb-119">Office 365 用に必要になります。</span><span class="sxs-lookup"><span data-stu-id="78eeb-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="78eeb-120">(手順に従って、この)、オンプレミス ドメインを確認します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="78eeb-121">[ビジネス向けの Office 365 の管理者の役割を割り当てる](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)アクセス許可を持つ、Office 365 テナントとオンプレミスの Active Directory です。</span><span class="sxs-lookup"><span data-stu-id="78eeb-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span> 
    
<span data-ttu-id="78eeb-122">Azure AD 接続をインストールする、設置型サーバーの次のソフトウェアが必要になります。</span><span class="sxs-lookup"><span data-stu-id="78eeb-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="78eeb-123">**サーバ OS**</span><span class="sxs-lookup"><span data-stu-id="78eeb-123">**Server OS**</span></span>|<span data-ttu-id="78eeb-124">**その他のソフトウェア**</span><span class="sxs-lookup"><span data-stu-id="78eeb-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="78eeb-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="78eeb-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="78eeb-126">で PowerShell は、既定でインストール、操作する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="78eeb-126">- PowerShell is installed by default, no action is required.</span></span>  <br/> <span data-ttu-id="78eeb-p104">Net 4.5.1 以降のリリースが Windows Update で提供されているとします。コントロール パネルの Windows サーバーに最新の更新プログラムがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="78eeb-129">**パック 1 (SP1) のサービスを Windows Server 2008 R2**または**Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="78eeb-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="78eeb-p105">-PowerShell の最新バージョンは、Windows Management Framework 4.0 で使用できます。[Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で検索します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br/> <span data-ttu-id="78eeb-132">-.Net 4.5.1 およびそれ以降のリリースでは、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能です。</span><span class="sxs-lookup"><span data-stu-id="78eeb-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="78eeb-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="78eeb-133">**Windows Server 2008**</span></span> | <span data-ttu-id="78eeb-134">-サポートされる最新バージョンの PowerShell は、Windows Management Framework 3.0 では、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能な時間があります。</span><span class="sxs-lookup"><span data-stu-id="78eeb-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br/> <span data-ttu-id="78eeb-135">-.Net 4.5.1 およびそれ以降のリリースでは、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能です。</span><span class="sxs-lookup"><span data-stu-id="78eeb-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
   
> [!NOTE]
> <span data-ttu-id="78eeb-p106">Azure Active Directory のディレクトリ同期を使用している場合は、Azure Active Directory に、オンプレミスの Active Directory から同期することができる配布グループのメンバーの最大数が 15,000 です。Azure AD 接続では、その番号は 50,000 です。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="78eeb-138">Azure AD 接続のハードウェア、ソフトウェア、アカウントとアクセス許可の要件、SSL 証明書の要件、およびオブジェクトの制限をより慎重に確認、 [Azure Active Directory に接続するための前提条件](https://go.microsoft.com/fwlink/p/?LinkId=716896)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78eeb-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="78eeb-139">Azure AD 接続[リリースのバージョン履歴](https://go.microsoft.com/fwlink/p/?LinkId=733238)に含まれており、各リリースでの修正内容を参照してくださいかを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="78eeb-139">You can also review the Azure AD Connect [version release history](https://go.microsoft.com/fwlink/p/?LinkId=733238) to see what is included and fixed in each release.</span></span> 

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="78eeb-140">ディレクトリ同期を設定するには</span><span class="sxs-lookup"><span data-stu-id="78eeb-140">To set up directory synchronization</span></span>
1. <span data-ttu-id="78eeb-141">Office 365 の管理センターにサインインし、**ユーザー**の選択\>左のナビゲーションには、**アクティブなユーザー**です。</span><span class="sxs-lookup"><span data-stu-id="78eeb-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span> 
2. <span data-ttu-id="78eeb-142">Office 365 管理センターで、[**アクティブ ユーザ**] ページで選択 * * より * * \> **ディレクトリ同期**します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-142">In the Office 365 admin center, on the **Active users** page, choose ** More ** \> **Directory synchronization**.</span></span>
    
    ![[詳細] メニューの [ディレクトリ同期を選択します](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="78eeb-p107">* * は、ディレクトリ同期に最適ですか?* * ページの 2 つの最初の選択肢の**1 ~ 10** **11-50**で「組織の規模に基づいてことをお勧めを作成しクラウドでユーザーを管理します。ディレクトリ同期を使用すると、あなたの設定をより複雑ななります。クリックして、ユーザーを追加するのにはアクティブなユーザーをください。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p107">On the ** Is directory sync right for you? ** page, the two first choices of **1-10**, and **11-50** result in "Based on the size of your organization, we recommend that you create and manage users in the cloud. Using directory synchronization will make your setup more complex. Go to Active users to add your users."</span></span> 
    
    - <span data-ttu-id="78eeb-148">ただし、続行できますディレクトリ同期の設定によって、ページの一番下の**続行には、ここ**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78eeb-148">You can still, however, continue setting up directory synchronization by choosing **Continue here** on the bottom of the page.</span></span> 
    
    - <span data-ttu-id="78eeb-p108">**51 250** ] または [ **251 またはそれ以上**の 2 つの後者選択肢を選択した場合、同期の設定はディレクトリ同期処理をお勧めします。**次**へを選択します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p108">If you select the two latter choices, **51-250** or **251 or greater**, the synchronization setup will recommend directory synchronization. Choose **Next** to continue.</span></span> 
    
    ![次へを選択すると、ディレクトリ同期の設定を続行するのには](media/359a1eb9-99ae-4b5b-a413-4de53037cceb.png)
  
4. <span data-ttu-id="78eeb-152">**クラウドとローカルのディレクトリの同期**では、情報を読みし、詳細情報を表示する場合、学習に移動する複数のリンク: [Office 365 ディレクトリ同期によってユーザーを提供する準備](prepare-for-directory-synchronization.md)をし、次の**を選択**.</span><span class="sxs-lookup"><span data-stu-id="78eeb-152">On the **Sync your local directory with the cloud**, read the information, and if you want more information, choose the learn more link that goes to: [Prepare to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md), and then choose **Next**.</span></span> 
    
5. <span data-ttu-id="78eeb-p109">**では、ディレクトリを確認**] ページで、ディレクトリを自動的にチェックするための要件を確認します。要件に合致する場合は**次へ**を選択\>**スキャンを開始**します。要件を満たさない場合にも**手動で続行**を選択して続行できます。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p109">On the **Let's check your directory** page, review the requirements for automatically checking your directory. If you meet the requirements, choose **Next** \> **Start scan**. If you can't meet the requirements you can still continue by choosing **continue manually**.</span></span>
    
    ![[次へ] または [手動で続行します、[ディレクトリ] ページを確認しましょう](media/af4a6bd5-13aa-4bfa-9751-4464a32ca8db.png)
  
6. <span data-ttu-id="78eeb-157">ディレクトリをスキャンすることを選択した場合は、[**ディレクトリ同期の設定を評価する**] ページでは、**スキャンの開始**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78eeb-157">If you select to scan your directories, choose **Start scan** on the **Evaluating directory synchronization setup** page.</span></span> 
    
    <span data-ttu-id="78eeb-158">ダウンロードしてスキャンを実行する指示に従います。</span><span class="sxs-lookup"><span data-stu-id="78eeb-158">Follow the instructions to download and run the scan.</span></span>
    
7. <span data-ttu-id="78eeb-159">スキャンが完了した後、セットアップ ウィザードに戻ります、**次**のスキャン結果を表示する」を選択します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-159">Once the scan is complete, return to the setup wizard, and choose **Next** to see your scan results.</span></span> 
    
8. <span data-ttu-id="78eeb-p110">[**ドメインの所有権を確認**] ページの指示に従って、ドメインを確認します。詳細については、 [Office 365 の DNS レコードを管理するときに作成する DNS レコード](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p110">Verify your domains as instructed on the **Verify Ownership of your domains** page. For detailed instructions, see [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23).</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="78eeb-p111">自分のドメインを所有していることを確認するのには、TXT レコードを追加した後は、ドメイン ウィザードでユーザーを追加する次の手順に説明しないでください。ディレクトリ同期では、ユーザーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p111">After you have added a TXT record to verify you own your domain, do not go to the next step of adding users in the domains wizard. The directory synchronization will add users for you.</span></span> 
  
    <span data-ttu-id="78eeb-164">**Office 365 のセットアップ**・ ページに戻るし、**更新**を選択します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-164">Return to the **Office 365 Setup** page and choose **Refresh**</span></span>
    
    ![確認後、ドメイン、更新] を選択します。](media/9b5fb593-5ff7-49f0-80d0-18e36d39d669.png)
  
9. <span data-ttu-id="78eeb-166">**自分のドメインが準備完了**] ページで、[**次**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-166">On the **Your domains are ready** page, choose **Next**.</span></span>
    
10. <span data-ttu-id="78eeb-p112">**お客様の環境をクリーンアップする**] ページで、必要に応じて指示に従って、Active Directory をチェックするのには IDFix をダウンロードするします。**次**へを選択します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p112">On the **Clean up your environment** page, optionally follow the instructions to download IDFix to check your Active Directory. Choose **Next** to continue.</span></span> 
    
11. <span data-ttu-id="78eeb-169">* * Azure Active Directory 接続を実行 * * ページで、Azure AD 接続ウィザードをインストールするのには**ダウンロード**を選択します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-169">On the ** Run Azure Active Directory Connect ** page, choose **Download** to install Azure AD Connect wizard.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="78eeb-p113">この時点で、Azure AD 接続ウィザードができます。ディレクトリ同期ウィザードのページが最後にお使いのブラウザーで Azure AD 接続手順が完了した後に戻れるようにしておくことを確認します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p113">At this point you will be in the Azure AD Connect wizard. Make sure you leave the directory synchronization wizard page you were last on open in your browser, so you can return to it after the Azure AD Connect steps are done.</span></span> 
  
    <span data-ttu-id="78eeb-p114">Azure AD 接続ウィザードがインストール後に自動的に開きます。デスクトップのデフォルトのインストール ・ サイト、それを開くことができます。シナリオに応じて、ウィザードの指示に従います。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p114">After Azure AD Connect wizard has installed it will automatically open. You can also open it from your desktop, the default install site. Follow the wizard instructions depending on your scenario:</span></span>
    
  - <span data-ttu-id="78eeb-175">パスワード ハッシュの同期とのディレクトリ同期、[高速の設定を使用して、Azure の AD 接続](https://go.microsoft.com/fwlink/p/?LinkID=698537)を使用します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-175">For directory synchronization with password hash synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>
    
  - <span data-ttu-id="78eeb-176">複数のフォレスト、パススルー認証、フェデレートされた識別情報および SSO オプション、[カスタム インストールの Azure AD 接続](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-176">For multiple forests, pass-through authentication, federated identity and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
    
    <span data-ttu-id="78eeb-177">これらのオプションを使用する**高速の設定**] ページで **[ユーザー設定**を選択します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-177">Select **Customize** on the **Express Settings** page to use these options.</span></span> 
    
12. <span data-ttu-id="78eeb-p115">Azure AD 接続ウィザードが完了したら、 **Office 365 のセットアップ**ウィザードに戻るし、**予期されたページとして勤務していることを確認の同期を行う**] の指示に従って。**次**へを選択します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p115">After the Azure AD Connect wizard is done, return to the **Office 365 Setup** wizard, and follow the instructions on the **Make sure sync worked as expected page**. Choose **Next** to continue.</span></span> 
    
13. <span data-ttu-id="78eeb-180">上の指示を読み、* * ユーザーをアクティブにする * * ページし、し、[**次**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-180">Read the instructions on the ** Activate users ** page and then choose **Next**.</span></span>
    
14. <span data-ttu-id="78eeb-181">**あなたはすべてのセットアップ**] ページの [**完了**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-181">Choose **Finish** on the **You're all setup** page.</span></span> 
    
## <a name="assign-licences-to-synchronized-users"></a><span data-ttu-id="78eeb-182">同期のユーザーにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="78eeb-182">Assign licences to synchronized users</span></span>
<span data-ttu-id="78eeb-p116">同期したら、ユーザーが Office 365 は、作成されるが、メールなど、Office 365 の機能を使用するためにライセンスを割り当てる必要があります。手順については、[ビジネス向けの Office 365 のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78eeb-p116">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
    
## <a name="finish-setting-up-domains"></a><span data-ttu-id="78eeb-185">ドメインのセットアップを完了します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-185">Finish setting up domains</span></span>
<span data-ttu-id="78eeb-186">自分のドメインの設定を完了するのには[Office 365 の DNS レコードを管理するときに作成する DNS レコード](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="78eeb-186">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>