---
title: SharePoint 2007 の移行オプションを考慮するには
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
description: SharePoint Server 2007 は、サポートの終わりに達しましたし、アップグレードする時間です。計画を作成するためには、この資料を使用します。
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169879"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a><span data-ttu-id="a6ed6-104">SharePoint 2007 の移行オプションを考慮するには</span><span class="sxs-lookup"><span data-stu-id="a6ed6-104">SharePoint 2007 migration options to consider</span></span>

<span data-ttu-id="a6ed6-p102">Microsoft SharePoint 2007 と SharePoint Server 2007 は、サポートの最後に到達しました。アップグレードする時間です。この資料では、移行オプションに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p102">Microsoft SharePoint 2007 and SharePoint Server 2007 have reached end of support. It's time to upgrade! This article provides information about your migration options.</span></span>
  
## <a name="common-upgrade-strategies-for-sharepoint"></a><span data-ttu-id="a6ed6-108">SharePoint の一般的なアップグレードの戦略</span><span class="sxs-lookup"><span data-stu-id="a6ed6-108">Common upgrade strategies for SharePoint</span></span>

<span data-ttu-id="a6ed6-p103">SharePoint のサーバー環境をアップグレードするのには複数のメソッドがあります。Microsoft Office SharePoint Server 2007 ファームがあれば、アップグレードの方法の例をいくつか挙げます。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p103">There are multiple methods to upgrade a SharePoint Server environment. If you have a Microsoft Office SharePoint Server 2007 farm, here are some examples of the upgrade methods:</span></span>
  
- <span data-ttu-id="a6ed6-111">データベース接続</span><span class="sxs-lookup"><span data-stu-id="a6ed6-111">Database attach</span></span>
    
- <span data-ttu-id="a6ed6-112">サイド バイ サイド アップグレード</span><span class="sxs-lookup"><span data-stu-id="a6ed6-112">Side-by-side upgrade</span></span>
    
- <span data-ttu-id="a6ed6-113">一括アップグレード</span><span class="sxs-lookup"><span data-stu-id="a6ed6-113">In-place upgrade</span></span>
    
- <span data-ttu-id="a6ed6-114">ハイブリッドのアップグレード (同じ場所では、デタッチされたデータベースまたは独立したデータベースを添付)</span><span class="sxs-lookup"><span data-stu-id="a6ed6-114">Hybrid upgrade (in-place with detached databases / separate database attach)</span></span>
    
- <span data-ttu-id="a6ed6-115">SharePoint の混成 (オンラインに接続、設置型の SharePoint)</span><span class="sxs-lookup"><span data-stu-id="a6ed6-115">SharePoint hybrids (connect online to on-premises SharePoint)</span></span>
    
- <span data-ttu-id="a6ed6-116">サイト コレクションまたはライブラリ間でデータを手動で移動します。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-116">Manually move data between site collections or libraries</span></span>
    
- <span data-ttu-id="a6ed6-117">Fasttrack というウィザードが Office 365 ([SharePoint Online 導入アドバイザー](https://aka.ms/spoguidance)) にアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-117">FastTrack Wizard upgrade to Office 365 ([SharePoint Online deployment advisor](https://aka.ms/spoguidance))</span></span>
    
- <span data-ttu-id="a6ed6-118">(SPO SharePoint オンライン) では、Office 365 に移行 API</span><span class="sxs-lookup"><span data-stu-id="a6ed6-118">Migration API to SharePoint Online (SPO) in Office 365</span></span>
    
<span data-ttu-id="a6ed6-119">どのような最適でしょうか。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-119">What works best for you?</span></span>
  
<span data-ttu-id="a6ed6-p104">ファームとものの使用に関する知識は、戦術的な力をアップグレードする際にユーザーは、SharePoint ファームを使用する方法では、オプションから選択できます。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p104">Your knowledge of what your farm does and is used for is a tactical strength when it comes to upgrade. The way people use the SharePoint Farm will help you choose from your options.</span></span>
  
> [!TIP]
> <span data-ttu-id="a6ed6-p105">Microsoft Office SharePoint Server 2007 では、ここで取り上げていない段階的アップグレードもあります。ステップに固有のアップグレードの一覧を参照してください記事は[SharePoint Server 2007 の最後のロードマップをサポート](sharepoint-2007-end-of-support.md)するを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p105">Microsoft Office SharePoint Server 2007 also has a gradual upgrade not covered here. To see a list of step-specific upgrade articles see the [SharePoint Server 2007 end of support Roadmap](sharepoint-2007-end-of-support.md).</span></span> 
  
<span data-ttu-id="a6ed6-p106">アップグレードする SharePoint のバージョンの[製品のライフ サイクル](https://support.microsoft.com/en-us/lifecycle/search)とシステム要件を確認してください。注意してください次のアップグレードになります (たとえば、複数のアップグレードを計画には、終了日のサポートを確認してください、SharePoint Server 2010 のような従来の製品を一時停止する場合)、必要なときは、この計画をサポートするハードウェアを設定されているとします。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p106">Remember to check the [Product Lifecycle](https://support.microsoft.com/en-us/lifecycle/search) and System Requirements for whatever version of SharePoint you're upgrading to. This is so you'll be aware when the next upgrade will be necessary (for example, if you pause at a legacy product like SharePoint Server 2010 to plan for more upgrades, be sure you know its end of support date), and to be certain you have hardware that supports your plan.</span></span> 
  
<span data-ttu-id="a6ed6-p107">一部またはすべての SharePoint サイト、クラウドでの Office 365 に移行する計画を立てる場合は[Office 365 のサービスの説明](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)へのリンクにブックマークを設定するときです。SharePoint Online の機能の詳細については、サービスの説明をする必要がありますとの違いがあります、設置型の SharePoint サーバー。機能の Microsoft Office SharePoint Server 2007 ファームをアップグレードします。インストールには、破損したサイトがある場合は、修正にアップグレードする前に。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p107">If you're planning to transition some, or all, of your SharePoint sites to Office 365 in the Cloud, this is a time to bookmark a link to the [Service Descriptions for Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). You'll need the Service Descriptions to learn about SharePoint Online features and how they might differ from on-premises SharePoint Server. Upgrade functional Microsoft Office SharePoint Server 2007 farms. If your installation has sites that are broken, fix them prior to upgrade.</span></span>
  
## <a name="a-note-about-managing-risk"></a><span data-ttu-id="a6ed6-130">リスクの管理に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="a6ed6-130">A note about managing risk</span></span>

<span data-ttu-id="a6ed6-p108">'サイド バイ サイド' のような方法は、アップグレードのロジックのパターンに重要です。サイド バイ サイドをアップグレードする場合、Microsoft Office SharePoint Server 2007 ファームを維持するが、ファーム次のバージョンを構築する (SharePoint Server 2010) から新しいハードウェア上で。これは、3 つの方法に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p108">Methods like 'side-by-side' are important in the scheme of upgrade logic. When you upgrade side-by-side, you maintain your Microsoft Office SharePoint Server 2007 farm, but build a farm the next version up from it (SharePoint Server 2010) on new hardware. This helps in three ways:</span></span>
  
1. <span data-ttu-id="a6ed6-134">個別にアップグレードして、データベースを使用して接続する Microsoft Office SharePoint Server 2007 データベースのバックアップを実行する場所があります。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-134">You have a place to take backups of your Microsoft Office SharePoint Server 2007 databases to upgrade them separately, by using database attach.</span></span>
    
2. <span data-ttu-id="a6ed6-135">理解のみ、少数の重要なドキュメント ライブラリとその他の情報が、Microsoft Office SharePoint Server 2007 ファームで使用されている場合、は、SharePoint Server 2010 に、Microsoft Office SharePoint Server 2007 からのデータを手動で移動することもできます。、または特定のサイトと web のみすることができます、ジョブを簡単に) 次のバージョンにします。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-135">If you figure out that only a small number of critical document libraries and other information are in use on your Microsoft Office SharePoint Server 2007 farm, you can choose to manually move data from Microsoft Office SharePoint Server 2007 to SharePoint Server 2010, or take only specific sites and webs to the next version (which can make your job easier).</span></span>
    
3. <span data-ttu-id="a6ed6-136">ほどするには、Microsoft Office SharePoint Server 2007 サーバー ファームを直接より安全なアップグレードとしてファームのデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-136">The less you do to the Microsoft Office SharePoint Server 2007 server farm, directly, the safer the data that farm contains as you upgrade.</span></span>
    
<span data-ttu-id="a6ed6-p109">メソッドでは、インプレース アップグレードと同様に機能、Microsoft Office SharePoint Server 2007 ファーム上で直接パスを破棄し、初期の環境からもう一度開始する簡単なオプションが少ない。いくつかの安全対策のようなことと、元の環境のバックアップのテスト) でビルドをできるだけ。などの場合は、Microsoft Office SharePoint Server 2007 ファームは、仮想、バックアップと復元のために重複していますが、し、バックアップとアップグレード、サービス ウィンドウの前に、最新のデータベースを復元します。バックアップ、データベースを復元するオプションがあることを知ることは、フェイル セーフを提供するのみ、という安心感を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p109">Methods like In-Place upgrade will act directly on your Microsoft Office SharePoint Server 2007 farm, giving you fewer easy options to abandon a path and begin again with your pristine environment. As much as possible, build in some safety measures (like taking and testing backups of the original environment). For example, if your Microsoft Office SharePoint Server 2007 farm is virtual, and is duplicated for the purposes of backup and restore, then back-up and restore the most current databases prior to your service window for the upgrade. Knowing that you have the option to restore database backups will not only give you a failsafe, it can give you peace of mind.</span></span>
  
> [!TIP]
> <span data-ttu-id="a6ed6-p110">アップグレードのためのベスト ・ プラクティス ・ ドキュメントは、 [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx)、 [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx)、 [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)では、 [SharePoint サーバーの 2016年](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx)の存在です。アップグレードや移行の Office 365 の経験を持つ[マイクロソフトのパートナー企業](https://partnercenter.microsoft.com/en-us/pcv/search)の検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p110">Best practices documents for upgrade exist for [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx), and [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx). You can also search for [Microsoft Partners](https://partnercenter.microsoft.com/en-us/pcv/search) who have experience with upgrades or Office 365 migrations.</span></span> 
  
## <a name="make-your-plan"></a><span data-ttu-id="a6ed6-143">プランします。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-143">Make your plan</span></span>

<span data-ttu-id="a6ed6-p111">アップグレードする場合を計画する必要があり、すべてこれらのケースで 1 つのサイズに収まらない。計画には、'SharePoint Online で、Office 365 サブスクリプションを作成、ドメインを登録およびファイルを保存するユーザーをリダイレクトする' ような単純な可能性があります。できない場合があります。その判断は、自分とにどのようなユーザーが本当に必要です。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p111">If you need to upgrade, you need a plan, and one-size doesn't fit all in these cases. Your plan may be as simple as 'Create an Office 365 subscription with SharePoint Online, register a domain, and redirect people to save their files there'. And it may not be. That decision is yours, and it's down to what you and your users really need.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a6ed6-p112">ことは危険でのライフ サイクルが終了したソフトウェアを実行します。問題が発見されたときにサポートが終了している製品が不要になったパッチです。新しいセキュリティの脅威が発生する場合があるなしのセキュリティ更新プログラムまたは修正プログラム ライフ サイクルでの最後の製品はサポートされていませんのでこれも意味します。そのような状況を回避してください。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p112">It's risky to run on software whose lifecycle has ended. Products that are out of support are no longer patched when issues are found. This also means that if new security threats arise, there will be no security patches or fixes because the end-of-lifecycle products are no longer supported. Please avoid that situation!</span></span> 
  
### <a name="first-know-your-farm"></a><span data-ttu-id="a6ed6-152">最初に、ファームを知る</span><span class="sxs-lookup"><span data-stu-id="a6ed6-152">First, know your farm</span></span>

<span data-ttu-id="a6ed6-p113">アップグレードする場合、意思決定が、ファームがどの程度、組織のベースする必要があります。どのような必要性を満たすことはでしょうか。その役割とは何ですか。社内の各ファームには、別のロールがあります。*重要な*いくつかの SharePoint ファームの場合があります、ファイル ・ アーカイブ--に対する保護があります。または場合は、ファームでは、一度に多くの役割がいっぱい、しする必要がありますどのようなサイト コレクション、web、またはドキュメント ライブラリも行うには、すべてのカスタマイズとはどの程度重要です。多くの作業となる可能性がこのレベルでデータの分析、アップグレード、または移行する前に、ドメインのマスターに時間と労力の節約にもしています。すべての可動部分と最も重要なビットがわかったら、またがわかりますよりことを確認し、残すことができます。その知識が、今後のみ役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p113">When upgrading, your decision-making should be based on what your farm does for your organization. What need does it satisfy? What's its role? Each farm in your company may have a different role. Some of your SharePoint farms may be  *critical*  , some may be file archives -- there for safe-keeping. Or, if your farm fills many roles at once, then you may need to know what site collections, webs, or even document libraries do, any customizations, and how important they are. Analyzing your data at this level may seem like a lot of work, but it saves time and effort to master your domain before you upgrade, or migrate, it. Once you know all the moving parts, and the most important bits, you'll also know what you've outgrown and can leave behind. That knowledge will only benefit you going forward.</span></span> 
  
<span data-ttu-id="a6ed6-162">では、ユーザーの声、SharePoint サーバー ファームに関する最も重要なことでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-162">So, what are users saying is most important about your SharePoint Server farm?</span></span>
  
- <span data-ttu-id="a6ed6-163">組み込みの SharePoint の機能</span><span class="sxs-lookup"><span data-stu-id="a6ed6-163">Built-in SharePoint features</span></span>
    
- <span data-ttu-id="a6ed6-164">(ファイルのアーカイブ) などの大規模なデータ コーパス</span><span class="sxs-lookup"><span data-stu-id="a6ed6-164">The large data corpus (such as an archive of files)</span></span>
    
- <span data-ttu-id="a6ed6-165">Availability</span><span class="sxs-lookup"><span data-stu-id="a6ed6-165">Availability</span></span>
    
- <span data-ttu-id="a6ed6-166">クリティカルなアプリケーション、web パーツ、またはファーム (ミッション クリティカルなファーム) 内のドキュメント</span><span class="sxs-lookup"><span data-stu-id="a6ed6-166">Critical apps, web parts, or docs in the farm (Mission critical farm)</span></span>
    
- <span data-ttu-id="a6ed6-167">コンプライアンス基準を満たす</span><span class="sxs-lookup"><span data-stu-id="a6ed6-167">The Compliance standards met</span></span>
    
- <span data-ttu-id="a6ed6-168">カスタマイズ</span><span class="sxs-lookup"><span data-stu-id="a6ed6-168">Customizations</span></span>
    
<span data-ttu-id="a6ed6-p114">SharePoint ファームからお客様のビジネスに不可欠なものを実行するなら、クライアント サービスの要件に関する重要なデータの大規模なカタログのように動作、'重要なアプリケーション] の横にチェック マークを配置することがありますが、また '可用性' - お客様のビジネスは、しばらくの間に SharePoint を使用することができなかった場合の影響を受けます。同様に、重要なサービス、ファームの提供は、に基づいてカスタム コード、サイト定義、または連携して動作するためのカスタマイズのために、'カスタマイズ' をチェックします。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p114">If you run something essential to your business from your SharePoint farm, say it acts like a large catalog of critical data about client service requirements, you may put a tick beside 'Critical apps', but also 'Availability' -- that is, your business would be impacted if you couldn't use SharePoint for a while. Likewise, you might check 'Customizations' because the critical services your farm offers are based on custom code, site definitions, or a number of customizations that work together.</span></span>
  
<span data-ttu-id="a6ed6-p115">場合 SharePoint では、それらのニーズを満たすとは、ソフトウェアに組み込まれて使用する以外では何も実行する必要はありませんし、通常更新し、通常の管理と保守を実行、' 組み込みの SharePoint' を選択した場合もあります、SharePoint の以前のバージョン上の理由です。つまり、既に必要な情報をまで、Microsoft Office SharePoint Server 2007 の終わりのサポートにアップグレードする必要があるしていません。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p115">If SharePoint met those needs without your having to do anything outside of using what's built-in to the software, and you generally update it and carry out normal administration and maintenance, you may have chosen 'Built-in SharePoint' -- this may also be your reason for sitting on an older version of SharePoint. In other words, it already does what you need it to and you haven't needed to upgrade until now, at Microsoft Office SharePoint Server 2007 end of support.</span></span>
  
<span data-ttu-id="a6ed6-p116">する箇条書きのリストこれらの操作では、アップグレードの条件を作成します。つまりのアップグレードは、考慮するには、このバーに対応する必要があります。これは、お客様のニーズに適合しない現在のメソッドを除外する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p116">When you bullet-list these things, you create criteria for your upgrade. In other words, any upgrade would have to meet this bar to be considered. This gives you a way to rule out methods that don't currently fit your needs.</span></span>
  
### <a name="a-simple-sample-plan"></a><span data-ttu-id="a6ed6-176">計画の簡単な例</span><span class="sxs-lookup"><span data-stu-id="a6ed6-176">A simple sample plan</span></span>

<span data-ttu-id="a6ed6-p117">リーダーシップと幅の広い合意し、SharePoint のアップグレードを実行するパス上の他の管理者にある必要があります。SharePoint サーバーの管理者は、Microsoft SQL Server の管理者と協力して多くの場合、複数のネットワークおよびセキュリティ チームとします。利害関係者の多くが、契約書を作成または、アップグレードと移行の計画を調整する必要があります。など、Office 365 で SharePoint のオンライン会社の一部を使用するようにデータを移行する場合があります必要がありますパフォーマンスのチューニングや、ネットワーク内のテストをします。影響を受けるチームは、事前に通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p117">There may need to be wider consensus with leadership and other admins on the path your SharePoint Upgrade will take. SharePoint Server Administrators often cooperate with Microsoft SQL Server admins, work with Networking and Security teams, and more. Where there are a lot of stakeholders, you may need to build agreement for, or adjust, your upgrade and migration plan. For example, if you migrate data so that part of your company uses SharePoint Online in Office 365, there will likely need to be performance tuning or testing inside your network. Affected teams should be informed ahead of time.</span></span>
  
<span data-ttu-id="a6ed6-p118">この単純なサンプルでは、SharePoint 管理者の提案を表示してすべての利害関係者が合意した計画を一覧表示し、します。わかりやすくするため、意思決定、契約を文書化します。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p118">In my simple sample, I show a SharePoint administrator's proposal and then list out the plan that all the stakeholders agreed upon. For clarity, document your agreements and decisions.</span></span>
  
<span data-ttu-id="a6ed6-p119">プランでは、ファームの徹底的な分析の後に開始し、ファーム、ペイン ・ ポイント、およびその他の重要な情報をいくつかのアップグレード オプションを絞り込むに至るまでの役割を識別しようとしています。後で、SharePoint の管理者がアップグレードの提案が行われ、アクション ・ プランの関係者が同意します。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p119">The plan starts after an in-depth analysis of a farm, and tries to identify the role of the farm, pain points, and other important information that will lead to narrowing down some upgrade options. Afterward, an upgrade proposal is made by SharePoint administrator, and stakeholders agree on an action plan.</span></span>
  
<span data-ttu-id="a6ed6-186">マイ '最も重要な' の箇条書きリスト:</span><span class="sxs-lookup"><span data-stu-id="a6ed6-186">My 'most important' bullet list:</span></span>
  
- <span data-ttu-id="a6ed6-187">可用性、sharepoint に組み込みの機能とコンプライアンス基準です。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-187">Availability, features built-in to SharePoint, and Compliance standards.</span></span>
    
- <span data-ttu-id="a6ed6-188">ほとんどのデータは、開発チームが特に重要で、複数のタイム ゾーンでの使用率を世界中で使用される 1 つの会議ワークスペースの 3 つのサイト コレクションには。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-188">Most of the data is on three site collections, with one Meeting Workspace used by a Dev team particularly important and in heavy use in multiple time-zones worldwide.</span></span>
    
- <span data-ttu-id="a6ed6-189">広く使用されている 17 の他のサイトがあります。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-189">There are seventeen other sites that are widely used.</span></span>
    
- <span data-ttu-id="a6ed6-p120">2 つのドキュメント ライブラリ (会議ワークスペースやドキュメント ルート サイト コレクション) は、最大 (8,000 名を超える文書ごと) です。多数のアーカイブされたドキュメントやスプレッドシートの添付ファイル付きのリストがあります。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p120">Two document libraries (Meeting Workspace and Documents on the root site collection) are largest (over 8000 docs each). We have a large number of archived docs and list with spreadsheet attachments.</span></span>
    
- <span data-ttu-id="a6ed6-192">コンプライアンスを維持する必要があります機密性の高いデータが存在するライブラリの 14 のリストはあります。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-192">There are fourteen lists of libraries that have sensitive data that MUST stay in Compliance.</span></span>
    
- <span data-ttu-id="a6ed6-193">私たちには、持ち運ぶことを保持し、電子的証拠開示を実行する機能が必要です。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-193">We MUST have the ability to do holds and e-discovery wherever we go.</span></span>
    
- <span data-ttu-id="a6ed6-194">設置、InfoSec の規則のためデータの一部維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-194">Some of this data MUST stay on-premises, due to InfoSec rules.</span></span>
    
 <span data-ttu-id="a6ed6-195">**[アップグレードと移行の選択肢:**</span><span class="sxs-lookup"><span data-stu-id="a6ed6-195">**My upgrade and migration choices:**</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="a6ed6-196">**○**</span><span class="sxs-lookup"><span data-stu-id="a6ed6-196">**Yes**</span></span> <br/> |<span data-ttu-id="a6ed6-197">**×**</span><span class="sxs-lookup"><span data-stu-id="a6ed6-197">**No**</span></span> <br/> |
|<span data-ttu-id="a6ed6-198">データベースとデータベースのアップグレードを添付します。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-198">Upgrade databases with database attach</span></span>  <br/> |<span data-ttu-id="a6ed6-199">一括アップグレード</span><span class="sxs-lookup"><span data-stu-id="a6ed6-199">In-place upgrade</span></span>  <br/> |
|<span data-ttu-id="a6ed6-200">ファーム サイド バイ サイドをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-200">Upgrade with farms side-by-side</span></span>  <br/> |<span data-ttu-id="a6ed6-201">ハイブリッドのアップグレード</span><span class="sxs-lookup"><span data-stu-id="a6ed6-201">Hybrid Upgrade</span></span>  <br/> |
|<span data-ttu-id="a6ed6-202">(個人用サイトのデータ) を Office 365 で SPO への移行 API</span><span class="sxs-lookup"><span data-stu-id="a6ed6-202">Migration API to SPO in Office 365 (for personal site data)</span></span>  <br/> |<span data-ttu-id="a6ed6-203">SharePoint のハイブリッド (まだ必要ありません)</span><span class="sxs-lookup"><span data-stu-id="a6ed6-203">SharePoint Hybrid (not needed yet)</span></span>  <br/> |
|<span data-ttu-id="a6ed6-204">重要なデータの SharePoint Online にいくつかの手動でのデータ移行</span><span class="sxs-lookup"><span data-stu-id="a6ed6-204">Some manual data migrations to SharePoint Online for critical data</span></span>  <br/> |<span data-ttu-id="a6ed6-205">Office 365 に FastTrack ウィザードのアップグレード</span><span class="sxs-lookup"><span data-stu-id="a6ed6-205">FastTrack wizard upgrade to Office 365</span></span>  <br/> |
   
 <span data-ttu-id="a6ed6-206">**提案されたプラン。**</span><span class="sxs-lookup"><span data-stu-id="a6ed6-206">**My proposed plan:**</span></span>
  
<span data-ttu-id="a6ed6-p121">アップグレード設置、SharePoint 側に並べて、仮想化、最初のデータベースをアップグレードできるように、いくつかのバージョンとします。SharePoint 2010 までは、SharePoint 2007 から移動します。管理者および開発者は、そのファームをテストします。ユーザーは、結果として得られるファームをテストします。この時間中に、スライド ショーを停止する問題を修正します。もう一度、サイド バイ サイド アップグレード SharePoint 2010 データベース SharePoint 2013 にします。パイロットまたはテスト ユーザーのテストです。この時間中に、スライド ショーを停止する問題を修正します。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p121">Upgrade on-premises, with versions of SharePoint side-by-side, some virtualized, so that we can upgrade the databases first. Go from SharePoint 2007 to SharePoint 2010. Admins and Devs test the resulting farm. Users test the resulting farm. Fix any show-stopping issues during this time. Again, side-by-side, upgrade SharePoint 2010 databases to SharePoint 2013. Test. User test/pilot. Fix any show-stopping issues during this time.</span></span>
  
- <span data-ttu-id="a6ed6-216">SPO の検索フェデレーション ハイブリッドがニーズを満たすかどうかに検討してください。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-216">Consider if a Search Federated Hybrid with SPO meets your needs.</span></span>
    
- <span data-ttu-id="a6ed6-217">ここでは、SharePoint Online にアップグレードしたい場合は、 [FastTrack の支援](https://fasttrack.microsoft.com)を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-217">Consider [FastTrack assistance](https://fasttrack.microsoft.com) if you would like to upgrade to SharePoint Online from here.</span></span> 
    
- <span data-ttu-id="a6ed6-p122">Office 365 サブスクリプションに対するすべてのサイト コレクションをオフロードすることができるかどうかを決定します。(Office 365 は、多くの[コンプライアンス基準](https://technet.microsoft.com/library/office-365-compliance.aspx)を満たしています。Office 365 が[電子的証拠開示](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da)およびコンプライアンス ・ センターを[保持している](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E)を実行できます。)</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p122">Determine if any site collections can be offloaded to an Office 365 Subscription. (Office 365 meets many [Compliance standards](https://technet.microsoft.com/library/office-365-compliance.aspx). Office 365 has [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) and can do [Holds](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) through the Compliance Centre.)</span></span> 
    
<span data-ttu-id="a6ed6-221">それ以外の場合、SharePoint サーバーの 2016年をサイド バイ サイド アップグレードを続行します。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-221">Otherwise, continue with a side-by-side upgrade to SharePoint Server 2016.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a6ed6-p123">推奨事項を計画する管理者によって行われたの間にアップグレードし、実際のプロセスは、アップグレードが依存している他の関係者との会話が発生します。なども経済性を強制的に計画を変更する管理者です。どのような最終的な決定は、合意に基づく計画とは、文書化する必要があります以降します。次のようなことがなります。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p123">In between recommendations made by the administrators planning the upgrade and the actual process are the conversations that happen with other stakeholders on which the upgrade relies. For example, sometimes economics force administrators to change their plans. Whatever the final decision is, you should document what the agreed-upon plan is, going forward. It might look something like this:</span></span> 
  
 <span data-ttu-id="a6ed6-226">**アクション プラン:**</span><span class="sxs-lookup"><span data-stu-id="a6ed6-226">**My action plan:**</span></span>
  
<span data-ttu-id="a6ed6-p124">設置型、既定の SharePoint Server 2010 と 2013 を構築する仮想環境を使用します。SharePoint サーバー 2016年 2016年のシステム要件を満たしている新しいハードウェア上でビルドされます。このようなデータベースのアタッチと SharePoint サーバーの 2016年の間のすべてのバージョンから SharePoint 2007 からのデータベースをアップグレードします。コアのカスタマイズの再作成されているとテスト SharePoint サーバーで 2016年環境、現時点でのネイティブな機能は当社のニーズを満たしている場合。私たちが成功した場合は、アップグレードされたデータベースを使用する新しいハードウェア上で、設置型のファームと少ないカスタマイズしなくてはなりません。テスト、テスト/パイロットのユーザー、SharePoint Server 2013 で、新しいサイト コレクションをアップグレードしたコンテンツ データベースを添付しは、DNS 切り替えライブ使用するための新しい SharePoint Server 2016 環境にします。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p124">On-premises, we use a virtual environment to build default SharePoint Server 2010, and 2013. SharePoint Server 2016 will be built on new hardware that meets system requirements for 2016. We will do database attaches to upgrade databases from SharePoint 2007 through all versions between it and SharePoint Server 2016. Core customizations are being recreated for and tested in the SharePoint Server 2016 environment at this time, if native features don't already meet our needs. If we are successful, we will have an on-premises farm on new hardware with upgraded databases, and fewer customizations. We'll attach the upgraded content databases to new site collections in SharePoint Server 2013, test, user test/pilot, and then do a DNS cut-over to the new SharePoint Server 2016 environment for live use.</span></span>
  
- <span data-ttu-id="a6ed6-233">私たちは考慮されません SharePoint サーバー 2016年と SharePoint Online との間のフェデレーションのハイブリッド今すぐ。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-233">We will not consider Federated Hybrid between SharePoint Server 2016 and SharePoint Online right now.</span></span>
    
- <span data-ttu-id="a6ed6-p125">コンテンツのサイトの見積もりの 35% は、修飾のドメインを持つ新しい SPO のサイトに変換または、最終的には、ビジネス ・ ストレージの OneDrive となります。サイトを変換または SPO を新しいサイトにルーティングするには、他の機会を求めています。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p125">An estimated 35% of our sites can be turned into new SPO sites with vanity domains, or, ultimately, become OneDrive for Business storage. Looking for other opportunities to convert sites, or route new sites to SPO.</span></span>
    
- <span data-ttu-id="a6ed6-236">移行 API でいくつかのドラッグ アンド ドロップ OneDrive に、個人用サイトのビジネスにして、手動による移行のこの部分の一部になります。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-236">Some of this part of the migration will be manual, by drag-and-drop to OneDrive for Business personal sites, and some by migration API.</span></span>
    
<span data-ttu-id="a6ed6-p126">さらに詳細な手順、または、特定のアップグレード手順へのリンクの多くが、計画に従う必要があります。MOSS 2007 のコンピューターの使用を停止しない必要があります。、および比較のために仮想環境を維持する必要があります。ただし、アップグレード完了となりますユーザーは SharePoint サーバーの 2016年にリダイレクトするとします。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p126">More detailed steps, or a number of links to specific upgrade directions should follow a plan. The MOSS 2007 computer should not be decommissioned, and virtual environments should be maintained for the sake of comparison; however, the upgrade will be complete when users are redirected to SharePoint Server 2016.</span></span>
  
<span data-ttu-id="a6ed6-p127">メソッドを選択する多くの場合の主な要因は、アップグレードのコスト (が表示されますこれについては、SharePoint 移行ロードマップ資料で) 時間のコストです。ただし、計画先は大いにを上手を選択する、期待値の設定で、どのような成功をフレームのようになります。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-p127">Often major factors in choosing a method are the total cost of the upgrade and the cost in time (you'll see more on this in the SharePoint Migration Roadmap article). However, planning ahead will benefit you greatly in setting expectations, choosing wisely, and framing what success will look like.</span></span>
  
## <a name="related-links"></a><span data-ttu-id="a6ed6-241">関連リンク</span><span class="sxs-lookup"><span data-stu-id="a6ed6-241">Related links</span></span>

[<span data-ttu-id="a6ed6-242">2007 のサーバーとクライアントの Office からアップグレードするためのリソース</span><span class="sxs-lookup"><span data-stu-id="a6ed6-242">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  
[<span data-ttu-id="a6ed6-243">マイクロソフト ライフ サイクル ポリシーとライフ サイクルを検索します。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-243">Microsoft Lifecycle Policy and Lifecycle search</span></span>](https://support.microsoft.com/en-us/lifecycle)
  
[<span data-ttu-id="a6ed6-244">アップグレードと移行を支援できるマイクロソフト パートナーを検索します。</span><span class="sxs-lookup"><span data-stu-id="a6ed6-244">Search for Microsoft Partners who can help with upgrade or migration</span></span>](https://partnercenter.microsoft.com/en-us/pcv/search)
  

