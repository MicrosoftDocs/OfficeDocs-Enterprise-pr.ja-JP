---
title: SharePoint Server での GDPR への対応
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: オンプレミスの SharePoint Server で GDPR の要件に対応する方法について説明します。
ms.openlocfilehash: 392b83b080ea111a5be070e9b9383caefe05d0be
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240612"
---
# <a name="gdpr-for-sharepoint-server"></a><span data-ttu-id="bda1d-103">SharePoint Server での GDPR への対応</span><span class="sxs-lookup"><span data-stu-id="bda1d-103">GDPR for SharePoint Server</span></span>

<span data-ttu-id="bda1d-104">個人情報保護の一部として、次のことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bda1d-104">As part of safeguarding personal information, we recommend the following:</span></span>

-   <span data-ttu-id="bda1d-105">Azure Information Protection を使用してデータを分類します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-105">Classify your data, using Azure Information Protection.</span></span>

-   <span data-ttu-id="bda1d-p101">SharePoint Server を最小特権構成で実行します。詳細については、「[SharePoint Server で最小特権管理を計画する](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration)」と「[SharePoint Server のセキュリティ](https://docs.microsoft.com/ja-JP/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p101">Run SharePoint Server in a least-privileged configuration. See [Plan for least-privileged administration in SharePoint Server](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration) and [Security for SharePoint Server](https://docs.microsoft.com/ja-JP/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server) for more information.</span></span>

-   <span data-ttu-id="bda1d-108">[サーバーで BitLocker 暗号化を有効にします](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server)。</span><span class="sxs-lookup"><span data-stu-id="bda1d-108">[Enable BitLocker encryption on your servers](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server).</span></span>

## <a name="user-generated-content"></a><span data-ttu-id="bda1d-109">ユーザー生成コンテンツ</span><span class="sxs-lookup"><span data-stu-id="bda1d-109">User Generated content</span></span>

<span data-ttu-id="bda1d-110">SharePoint Server のサイトとライブラリに含まれているユーザー生成コンテンツについて推奨される基本的な操作を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-110">The basic recommended approach for user generated content contained in SharePoint Server sites and libraries is:</span></span>

-   <span data-ttu-id="bda1d-111">Azure Information Protection を使用して機密データにラベルを付けます。</span><span class="sxs-lookup"><span data-stu-id="bda1d-111">Use Azure Information Protection to label sensitive data.</span></span>

-   <span data-ttu-id="bda1d-112">[SharePoint Server 検索](https://docs.microsoft.com/SharePoint/search/search)と[電子情報開示](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server)を使用して機密データを取得します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-112">Use [SharePoint Server search](https://docs.microsoft.com/SharePoint/search/search) and [eDiscovery](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server) to retrieve sensitive data.</span></span>

<span data-ttu-id="bda1d-113">ファイル共有、SharePoint のサイトおよびライブラリについて推奨される作業の手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-113">The recommended approach for files shares and SharePoint sites and libraries includes these steps:</span></span>

1.  <span data-ttu-id="bda1d-114">**Azure Information Protection スキャナーをインストールし、構成します。**</span><span class="sxs-lookup"><span data-stu-id="bda1d-114">**Install and configure Azure Information Protection scanner.**</span></span>

    -   <span data-ttu-id="bda1d-115">使用する機密データの種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-115">Decide which sensitive data types to use.</span></span>

    -   <span data-ttu-id="bda1d-116">使用する SharePoint サイトを指定します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-116">Specify which SharePoint sites to use.</span></span>

2.  <span data-ttu-id="bda1d-117">**検出サイクルを完了します。**</span><span class="sxs-lookup"><span data-stu-id="bda1d-117">**Complete a discovery cycle.**</span></span>

    -   <span data-ttu-id="bda1d-118">検出モードでスキャナーを実行し、検出結果を検証します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-118">Run the scanner in discovery mode and validate the findings.</span></span>

    -   <span data-ttu-id="bda1d-119">必要に応じて、条件と機密情報の種類を最適化します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-119">If needed, optimize the conditions and sensitive information types.</span></span>

    -   <span data-ttu-id="bda1d-120">自動的に適用されるラベルの予期される影響を評価します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-120">Assess the expected impact of automatically applying labels.</span></span>

3.  <span data-ttu-id="bda1d-121">**Azure Information Protection スキャナーを実行して、対象となるドキュメントにラベルを適用します**。</span><span class="sxs-lookup"><span data-stu-id="bda1d-121">**Run the Azure Information Protection scanner to apply labels to qualifying documents**.</span></span>

4.  <span data-ttu-id="bda1d-122">**保護のために次の操作を実行します。**</span><span class="sxs-lookup"><span data-stu-id="bda1d-122">**For protection:**</span></span>

    <span data-ttu-id="bda1d-p102">a. 目的としたラベルのドキュメントを保護するための Exchange データ損失防止ルールを構成します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p102">a.  Configure Exchange data loss prevention rules to protect documents with the desired label.</span></span>

    <span data-ttu-id="bda1d-p103">b. アクセス許可を使用して、ファイルにアクセスできるユーザーを制限するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p103">b.  Be sure permissions to limit who can access files.</span></span>

    <span data-ttu-id="bda1d-p104">c. SharePoint では、ライブラリを IRM により保護します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p104">c.  For SharePoint, use IRM-protection for libraries.</span></span>

5.  <span data-ttu-id="bda1d-129">**監視のため、Windows Server のログを SIEM ツールに統合します。**</span><span class="sxs-lookup"><span data-stu-id="bda1d-129">**For monitoring, integrate Windows Server logs with a SIEM tool.**</span></span>

    <span data-ttu-id="bda1d-p105">a. データ主体要求の個人データを検索するには、Search Center または電子情報開示を使用します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p105">a.  To find personal data for data subject requests, use Search Center or eDiscovery.</span></span>

<span data-ttu-id="bda1d-p106">機密データにラベルを適用するときには、保護機能が設定されていないラベルを必ず使用してください。保護機能には、サービスがファイルの機密データを検出できない原因となる暗号化などがあります。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p106">When applying labels to sensitive data, be sure to use a label that is not configured with protection. Protection includes encryption which prevents services from detecting sensitive data in the files.</span></span>

<span data-ttu-id="bda1d-134">Azure Information Protection スキャナーを使用して個人データを検索したりラベル付けしたりすることに関する詳細については、[Microsoft GDPR Data Discovery Toolkit](http://aka.ms/gdprpartners) (http://aka.ms/gdprpartners)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-134">For more information on using Azure Information Protection scanner to find and label personal data, see the [Microsoft GDPR Data Discovery Toolkit](http://aka.ms/gdprpartners) (http://aka.ms/gdprpartners).</span></span>

<span data-ttu-id="bda1d-p107">さまざまな条件でスキャナーを構成すること、また Office 365 データ損失防止 (DLP) のさまざまな機密情報タイプを使用することに関する情報については、「[Azure Information Protection 用の自動および推奨分類の条件を構成する方法](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification)」を参照してください。新しいタイプの Office 365 機密情報はスキャナーですぐに利用できるようになるわけではなく、カスタム機密情報タイプはスキャナーで使用できないことに注意ください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p107">For information on configuring the scanner for conditions and using the Office 365 data loss prevention (DLP) sensitive information types, see [How to configure conditions for automatic and recommended classification for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification). Note that new Office 365 sensitive information types will not be immediately available to use with the scanner and custom sensitive information types cannot be used with the scanner.</span></span>

## <a name="removing-personal-information-from-office-files"></a><span data-ttu-id="bda1d-137">Office ファイルから個人情報を削除する</span><span class="sxs-lookup"><span data-stu-id="bda1d-137">Removing personal information from Office files</span></span>

<span data-ttu-id="bda1d-p108">SharePoint ドキュメント ライブラリに保存されている Office ファイルから個人情報 (Word ドキュメントのメタデータやコメントなど) を削除する作業は、次の手順に従って手動で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p108">Removing personal information (such as metadata or comments in a Word document) from Office files that are stored in a SharePoint document library must be done manually. Follow these steps:</span></span>

1.  <span data-ttu-id="bda1d-140">SharePoint Server からドキュメントのコピーをローカル ディスクにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="bda1d-140">Download a copy of the document from SharePoint Server to your local disk.</span></span>

2.  <span data-ttu-id="bda1d-141">SharePoint ドキュメント ライブラリからドキュメントを削除します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-141">Delete the document from the SharePoint document library.</span></span>

3.  <span data-ttu-id="bda1d-142">「[ドキュメントを調べ非表示のデータと個人情報を削除する](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="bda1d-142">Follow the steps in [Remove hidden data and personal information by inspecting documents](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F).</span></span>

4.  <span data-ttu-id="bda1d-143">ドキュメントを SharePoint ドキュメント ライブラリに再びアップロードします。</span><span class="sxs-lookup"><span data-stu-id="bda1d-143">Upload the document back to the SharePoint document library.</span></span>

## <a name="telemetry-and-log-files"></a><span data-ttu-id="bda1d-144">テレメトリ ファイルとログ ファイル</span><span class="sxs-lookup"><span data-stu-id="bda1d-144">Telemetry and log files</span></span>

### <a name="uls-logs"></a><span data-ttu-id="bda1d-145">ULS ログ</span><span class="sxs-lookup"><span data-stu-id="bda1d-145">ULS Logs</span></span>

<span data-ttu-id="bda1d-p109">SharePoint Server の統合ログ サービス (ULS) と利用状況ログは、さまざまなシステム機能を追跡することから、ユーザー情報が含まれている可能性があります。ULS ログと利用状況ログはテキスト ファイルであり、各種検索ツールを使用して検索できます。[Merge-SPLogFile PowerShell コマンドレット](https://docs.microsoft.com/ja-JP/powershell/module/sharepoint-server/merge-splogfile)は、ファーム内の複数サーバー上の ULS ログのレコードを戻します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p109">Unified Logging Service (ULS) and Usage logging in SharePoint Server track a variety of system functions and can contain user information. ULS logs and usage logs are text files and can be searched using a variety of searching tools. The [Merge-SPLogFile PowerShell cmdlet](https://docs.microsoft.com/ja-JP/powershell/module/sharepoint-server/merge-splogfile) provides a way to return records from the ULS logs on multiple servers in a farm.</span></span>

<span data-ttu-id="bda1d-p110">ログ保存ポリシーを、ビジネスの目標に必要な最小値に設定することを検討してください。SharePoint Server でのログの構成の詳細については、「[SharePoint Server で診断ログを構成する](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p110">Consider setting log retention policies to the minimum value needed for your business purposes. For information about configuring logging in SharePoint Server, see [Configure diagnostic logging in SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).</span></span>

<span data-ttu-id="bda1d-151">一部のシステム イベントも Windows イベント ログに記録されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-151">Note that some system events are also logged to the Windows Event Log.</span></span>

### <a name="usage-database"></a><span data-ttu-id="bda1d-152">利用状況データベース</span><span class="sxs-lookup"><span data-stu-id="bda1d-152">Usage Database</span></span>

<span data-ttu-id="bda1d-p111">SharePoint Server 利用状況データベース (既定の名前は WSS_Logging) には、ULS ログの情報のサブセットが保存されています。このデータベースのデータの最大保存期間は 30 日です。この日数を、ビジネス ニーズで許容可能な最も短い期間に設定することをお勧めします。詳細については、「[SharePoint Server で診断ログを構成する](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p111">The SharePoint Server Usage database (default name WSS_Logging) contains a subset of the information found in the ULS logs. The maximum retention of data in this database is 30 days. We recommend that you configure it for the shortest duration allowable by your business needs. For more information, see [Configure diagnostic logging in SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).</span></span>

## <a name="personal-information-and-search"></a><span data-ttu-id="bda1d-157">個人情報と検索</span><span class="sxs-lookup"><span data-stu-id="bda1d-157">Personal information and search</span></span>

<span data-ttu-id="bda1d-158">検索クエリの履歴と利用状況レコードには、ユーザー名への参照が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bda1d-158">The search query history and usage records contain references to user names.</span></span>

### <a name="query-history-and-favorite-queries"></a><span data-ttu-id="bda1d-159">クエリの履歴とよく利用するクエリ</span><span class="sxs-lookup"><span data-stu-id="bda1d-159">Query history and favorite queries</span></span>

<span data-ttu-id="bda1d-p112">SharePoint Server では、クエリの履歴と「よく利用する」クエリは 365 日経過後に自動的に期限切れとなります。ユーザーが組織を離れた場合、次の手順に従ってクエリの履歴からユーザーの名前への参照を削除できます。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p112">In SharePoint Server 2013 and SharePoint Server 2016, query histories and ‘favorite’ queries automatically expire after 365 days. If a user leaves your organization, it is possible to remove references to a user's name from the query history using the steps below..</span></span>

<span data-ttu-id="bda1d-162">以下に示す SQL クエリは、SharePoint Server に適用されます。これらのクエリでは次の操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="bda1d-162">The following SQL queries apply to SharePoint 2013 and SharePoint 2016 and make it possible to:</span></span>

-   <span data-ttu-id="bda1d-163">ユーザーのクエリ履歴またはよく利用するクエリをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="bda1d-163">Export a user’s query history or favorite queries</span></span>

-   <span data-ttu-id="bda1d-164">クエリの履歴からユーザー名への参照を削除する</span><span class="sxs-lookup"><span data-stu-id="bda1d-164">Remove references to user names in the query history</span></span>

#### <a name="export-a-users-queries-since-a-specific-date"></a><span data-ttu-id="bda1d-165">特定の日付以降のユーザーのクエリをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="bda1d-165">Export a user’s queries since a specific date</span></span> 

<span data-ttu-id="bda1d-166">@StartTime 以降に @UserName によって実行されたクエリを、Link Store クエリ ログ テーブルからエクスポートするには、次のプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-166">Use the following procedure to export queries from the Link Store query log tables, performed by @UserName since @StartTime.</span></span>

```sql
[In dbo].[LinkStore_<ID>]:
CREATE PROCEDURE proc_MSS_GetQueryTermsForUser 
( 
    @UserName nvarchar(256), 
    @StartTime datetime 
) 
AS 
BEGIN 
    SET NOCOUNT ON; 
    SELECT searchTime, queryString 
    FROM 
        dbo.MSSQLogPageImpressionQuery 
    WITH 
        (NOLOCK) 
    WHERE 
        userName = @UserName AND 
        searchTime > @StartTime 
END 
GO 
```

#### <a name="export-a-users-queries-from-the-past-100-days"></a><span data-ttu-id="bda1d-167">過去 100 日間のユーザー クエリをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="bda1d-167">Export a user’s queries from the past 100 days</span></span>

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetQueryTermsForUser '0#.w|domain\username', @FROMDATE 
```

#### <a name="export-a-users-favorite-queries"></a><span data-ttu-id="bda1d-168">ユーザーがよく利用するクエリをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="bda1d-168">Export a user’s favorite queries</span></span>

<span data-ttu-id="bda1d-169"><DateTime> 以降に @UserName が実行した、ユーザーがよく利用するクエリを、検索管理 DB の個人結果テーブルからエクスポートするには、次のプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-169">Use the following procedure to export a user's favorite queries from the Search Admin DB personal result tables, performed by @UserName, since <DateTime>.</span></span>

```sql
In [dbo].[Search_<ID>]:
CREATE PROCEDURE proc_MSS_GetPersonalFavoriteQueries 
( 
    @UserName nvarchar(256), 
    @SearchTime datetime 
) 
AS 
BEGIN 
    SET NOCOUNT ON; 
    SELECT max(queries.SearchTime) as SearchTime, 
           max(queries.querystring) as queryString, 
           max(url.url) as URL 
    FROM MSSQLogOwner owners WITH(NOLOCK) 
    JOIN MSSQLogPersonalResults results WITH(NOLOCK) on owners.OwnerId = results.OwnerId 
    JOIN MSSQLogUrl url WITH(NOLOCK) on results.ClickedUrlId = url.urlId 
    JOIN MSSQLogPersonalQueries queries WITH(NOLOCK) on results.OwnerId = queries.OwnerId 
    WHERE queries.SearchTime > @SearchTime 
        AND queries.UserName = @UserName 
        GROUP BY queries.QueryString,url.url 
END 
GO 
```

#### <a name="export-a-users-favorite-queries-from-the-past-100-days"></a><span data-ttu-id="bda1d-170">過去 100 日間のユーザーのよく利用するクエリをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="bda1d-170">Export a user’s favorite queries from the past 100 days</span></span> 

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetPersonalFavoriteQueries '0#.w|domain\username', @FROMDATE 
```

#### <a name="remove-references-to-user-names-that-are-more-than-x-days-old"></a><span data-ttu-id="bda1d-171">過去 X 日よりも古いユーザー名への参照を削除する</span><span class="sxs-lookup"><span data-stu-id="bda1d-171">Remove references to user names that are more than X days old</span></span>

<span data-ttu-id="bda1d-p113">Links Store クエリ ログ テーブルから、経過日数が @Days を超えている*すべての*ユーザー名への参照を削除するには、次のプロシージャを使用します。このプロシージャは、@LastCleanupTime 以降の参照だけを削除します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p113">Use the following procedure to remove references to *all* user names that are more than @Days old, from the Links Store query log tables. The procedure only removes references backwards in time until it reaches the @LastCleanupTime.</span></span>

```sql
In [dbo].[LinksStore_<ID>]:  
CREATE PROCEDURE proc_MSS_QLog_Cleanup_Users 
( 
    @LastCleanupTime datetime, 
    @Days int 
) 
AS 
BEGIN 
    DECLARE @TooOld datetime 
    SET @TooOld = DATEADD(day, -@Days, GETUTCDATE()) 
    DECLARE @FromLast datetime 
    SET @FromLast = DATEADD(day, -@Days, @LastCleanupTime) 
    BEGIN TRANSACTION 
         UPDATE MSSQLogPageImpressionQuery 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld 
    UPDATE MSSQLogO14PageClick 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld 
    COMMIT TRANSACTION 
END 
GO 
```

#### <a name="remove-references-to-a-specific-user-name-thats-more-than-x-days-old"></a><span data-ttu-id="bda1d-174">経過日数が X 日を超えている特定のユーザー名への参照を削除する</span><span class="sxs-lookup"><span data-stu-id="bda1d-174">Remove references to a specific user name that’s more than X days old</span></span>

<span data-ttu-id="bda1d-p114">Links Store クエリ ログ テーブルから、経過日数が @Days を超えている*特定の*ユーザー名への参照を削除するには、次のプロシージャを使用します。このプロシージャは、@LastCleanupTime 以降の参照だけを削除します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p114">Use the following procedure to remove references to a *specific* user name from the Links Store query log tables, where the references are more than @Days old. The procedure only removes references backwards in time until it reaches the @LastCleanupTime.</span></span>

```sql
In [dbo].[LinksStore_<ID>]:
CREATE PROCEDURE proc_MSS_QLog_Cleanup_Users 
( 
    @UserName nvarchar(256),
    @LastCleanupTime datetime, 
    @Days int 
) 
AS 
BEGIN 
    DECLARE @TooOld datetime 
    SET @TooOld = DATEADD(day, -@Days, GETUTCDATE()) 
    DECLARE @FromLast datetime 
    SET @FromLast = DATEADD(day, -@Days, @LastCleanupTime) 
    BEGIN TRANSACTION 
         UPDATE MSSQLogPageImpressionQuery 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld AND userName = @UserName
    UPDATE MSSQLogO14PageClick 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld AND userName = @UserName
    COMMIT TRANSACTION 
END 
GO 
```

#### <a name="remove-references-to-all-user-names-in-the-query-history-from-a-date-and-up-to-the-past-30-days"></a><span data-ttu-id="bda1d-177">クエリ履歴から、指定されている日付から過去 30 日間のすべてのユーザー名への参照を削除する</span><span class="sxs-lookup"><span data-stu-id="bda1d-177">Remove references to all user names in the query history from a date and up to the past 30 days</span></span>

```sql
EXECUTE proc_MSS_QLog_Cleanup_Users '1-1-2017', 30 
```

### <a name="delete-usage-records"></a><span data-ttu-id="bda1d-178">利用状況レコードを削除する</span><span class="sxs-lookup"><span data-stu-id="bda1d-178">Delete usage records</span></span>

<span data-ttu-id="bda1d-p115">SharePoint Server では、3 年経過した利用状況レコードは自動的に削除されます。次の手順に従って、このようなレコードを手動で削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p115">SharePoint Server 2013 and SharePoint Server 2016 automatically deletes usage records after 3 years. You can manually delete such records using the procedure below:</span></span>

<span data-ttu-id="bda1d-181">削除されたドキュメントに関連付けられているすべての利用状況レコードを削除するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="bda1d-181">To delete all usage records associated with deleted documents:</span></span> 

1.  <span data-ttu-id="bda1d-182">最新の SharePoint 更新プログラムがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-182">Ensure that you have the latest SharePoint update installed.</span></span> 

2.  <span data-ttu-id="bda1d-183">SharePoint 管理シェルを開始します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-183">Start a SharePoint Management shell.</span></span>

3.  <span data-ttu-id="bda1d-184">利用状況分析による分析を停止してクリアします。</span><span class="sxs-lookup"><span data-stu-id="bda1d-184">Stop and Clear the Usage Analytics analysis:</span></span> 

    ```powershell
    $tj = Get-SPTimerJob -Type Microsoft.Office.Server.Search.Analytics.UsageAnalyticsJobDefinition 
    $tj.StopAnalysis() 
    $tj.ClearAnalysis() 
    ```

4.  <span data-ttu-id="bda1d-185">分析が再び開始されるまで待ちます (最大 24 時間かかります)。</span><span class="sxs-lookup"><span data-stu-id="bda1d-185">Wait for the analysis to start again (might take up to 24 hours).</span></span> 

5.  <span data-ttu-id="bda1d-p116">分析の次回実行時に、分析レポート データベースからすべてのレコードがダンプされます。多数のエントリが保存されている大きなデータベースでは、この完全ダンプに時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p116">On the next run of the analysis, it will dump all records from the Analytics Reporting database. This full dump may take a while for a large database with many entries.</span></span>

6.  <span data-ttu-id="bda1d-p117">10 日間待ちます。分析は毎日実行され、10 回目の実行後に、削除されているドキュメントに関連付けられているレコードが削除されます。削除する必要があるレコードが多数存在する場合、この実行には通常よりも時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p117">Wait for 10 days. The analysis runs daily, and records associated with deleted documents will be removed after the 10^th^ run. This run may take longer than normal if many records need to be deleted.</span></span> 

### <a name="personal-information-and-search-in-sharepoint-server-2010"></a><span data-ttu-id="bda1d-191">SharePoint Server 2010 での個人情報と検索</span><span class="sxs-lookup"><span data-stu-id="bda1d-191">Personal information and search in SharePoint Server 2010</span></span>

#### <a name="fast-search-server-2010-for-sharepoint"></a><span data-ttu-id="bda1d-192">FAST Search Server 2010 for SharePoint</span><span class="sxs-lookup"><span data-stu-id="bda1d-192">FAST Search Server 2010 for SharePoint</span></span> 

<span data-ttu-id="bda1d-p118">FAST Search Server 2010 アドオンは、ファイルをインデックスに保存する以外に、ファイルを FixML と呼ばれる中間形式でも保存します。FiXML ファイルは定期的に (既定では午前 3 時から午前 5 時までの間に) 圧縮されます。この圧縮により、削除済みファイルが FiXML ファイルから自動的に削除されます。削除されているユーザーまたはドキュメントに属する情報が適切な時点で削除されるようにするには、圧縮が常に有効であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p118">In addition to storing files in the index, the FAST Search Server 2010 Add-On also stores files in an intermediate format called FixML. FiXML files are compacted regularly, by default between 3 am and 5 am every night. Compaction removes deleted files from the FiXML files automatically. To ensure timely removal of information belonging to deleted users or documents, ensure that compaction is always enabled.</span></span>

### <a name="hybrid-search"></a><span data-ttu-id="bda1d-197">ハイブリッド検索</span><span class="sxs-lookup"><span data-stu-id="bda1d-197">Hybrid Search</span></span> 

<span data-ttu-id="bda1d-p119">ハイブリッド検索ソリューションについて推奨されるアクションは、SharePoint Server または SharePoint Online での検索の場合と同じです。次の 2 種類のハイブリッド検索ソリューションがあります。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p119">The recommended actions for hybrid search solutions are the same as for search in SharePoint Server or SharePoint Online. There are two hybrid search solutions:</span></span>

<span data-ttu-id="bda1d-p120">**クラウド ハイブリッド検索ソリューション -** SharePoint 用クラウド ハイブリッド検索ソリューションでは、オンプレミスのコンテンツを含めてクロールしたすべてのコンテンツのインデックスを Office 365 の検索インデックスに作成します。ユーザーは Office 365 の検索インデックスをクエリすることで、オンプレミスと Office 365 の両方のコンテンツからの検索結果を取得します。ドキュメントが SharePoint Server 環境から削除されると、そのドキュメントは Office 365 の検索インデックスからも削除されます。GDPR によるハイブリッド環境への影響を理解するため、「[SharePoint Server 用のクラウド ハイブリッド検索について](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint)」と「[SharePoint のクラウド ハイブリッド検索を計画する](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p120">**The cloud hybrid search solution -** With the cloud hybrid search solution for SharePoint, you index all your crawled content, including on-premises content, in your search index in Office 365. When users query your search index in Office 365, they get search results from both on-premises and Office 365 content. When documents are deleted from the SharePoint Server environment, they are also deleted from the search index in Office 365. [Read more about the cloud hybrid search solution](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint) and [how search components and databases interact in cloud hybrid search](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint) to understand better how GDPR affects the hybrid environment.</span></span>

<span data-ttu-id="bda1d-p121">**ハイブリッド フェデレーション検索 -** ハイブリッド フェデレーション検索では、SharePoint Server のインデックスと Office 365 のインデックスの両方を使用します。SharePoint Server と SharePoint Online の両方の Search サービスは、他方の環境の検索インデックスに対するクエリを実行して、統合された結果を返すことができます。ユーザーが検索センターから検索を実行すると、検索結果は SharePoint Server の検索インデックスと Office 365 の検索インデックスから取得されます。GDPR によるハイブリッド環境への影響について理解するため、「[SharePoint 用のハイブリッド フェデレーション検索について](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p121">**The hybrid federated search solution -** With the hybrid federated search solution, you use both your index in SharePoint Server and your index in Office 365. Both SharePoint Server and SharePoint Online Search services can query the search index in the other environment and return federated results. When users search from a Search Center, the search results come from both your search index in SharePoint Server and your search index in Office 365. [Read more about the hybrid federated search solution](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint) to understand better how GDPR affects the hybrid environment.</span></span>

## <a name="on-prem-to-cloud-migrations"></a><span data-ttu-id="bda1d-208">オンプレミスからクラウドへの移行</span><span class="sxs-lookup"><span data-stu-id="bda1d-208">On Prem to Cloud Migrations</span></span>

<span data-ttu-id="bda1d-p122">SharePoint Server から SharePoint Online への移行中には、特定の時点で両方のロケーションに重複データが存在することがあります。移行中のデータを削除する必要がある場合には、最初に移行を完了してから、データを両方のロケーションから削除することをお勧めします。いずれのロケーションでも、エクスポートするデータをクエリできます。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p122">While migrating data from SharePoint Server to SharePoint Online, duplicate data may exist in both locations for a time. If you have data that you need to delete that is in mid-migration, we recommend that you complete the migration first, and then delete the data from both locations. You can query data for export from either location.</span></span>

## <a name="user-profile-data"></a><span data-ttu-id="bda1d-212">ユーザー プロファイル データ</span><span class="sxs-lookup"><span data-stu-id="bda1d-212">User Profile data</span></span>

<span data-ttu-id="bda1d-p123">User Profile Service により、さまざまな外部ソースからプロファイル データをインポートできます。このようなユーザー プロファイル データに対するクエリと更新は、データのマスターが存在するシステムで処理する必要があります。外部システムを更新した場合は、SharePoint Server のユーザー プロファイルを再度同期してください。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p123">The User Profile Service allows for import of profile data from a variety of external sources. Queries for and update of such user profile data should be handled in the systems in which the data is mastered. If you make updates to the external system, be sure to synchronize the user profiles in SharePoint Server again.</span></span>

<span data-ttu-id="bda1d-216">SharePoint ユーザー プロファイルからユーザーの個人情報を削除するには、次の基本的な手順に従います。</span><span class="sxs-lookup"><span data-stu-id="bda1d-216">Follow these basic steps to remove a user’s personal information from their SharePoint Server user profile:</span></span>

1.  <span data-ttu-id="bda1d-p124">SharePoint Server ユーザー プロファイルにフィードを提供するすべての外部システムから、ユーザー情報を削除します。ディレクトリ同期を使用している場合は、オンプレミスの Active Directory 環境からユーザーを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p124">Remove the user information from any external systems that feed into the SharePoint Server user profile. If you are using directory synchronization, the user must be removed from the on-premises Active Directory environment.</span></span>

2.  <span data-ttu-id="bda1d-219">SharePoint Server で[プロファイル同期](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually)を実行します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-219">Run a [profile synchronization](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually) on SharePoint Server.</span></span>

3.  <span data-ttu-id="bda1d-p125">SharePoint Server からプロファイルを削除します。削除完了後 30 日以内に、SharePoint Server によりユーザー プロファイル データベースからそのプロファイルが完全に削除されます。また、ユーザーのプロファイル ページと個人用サイトが削除されます。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p125">Delete the profile from SharePoint Server. Once this is done, SharePoint Server will fully remove the profile from the User Profile Database in 30 days. The user’s profile page and personal site will be deleted.</span></span>

<span data-ttu-id="bda1d-p126">ユーザーのプロファイルの削除後に、ユーザーが訪問したことのあるサイト コレクションに、一部の情報 (ユーザー ID など) が記録されたままになることがあります。特定のサイト コレクションからこのデータを削除する場合は、CSOM を使用して削除できます。次にサンプル スクリプトを示します。</span><span class="sxs-lookup"><span data-stu-id="bda1d-p126">After deleting a user’s profile, some limited information (such as user ID) may still be recorded in site collections that the user has visited. If you choose to delete this data from a given site collection, this can be done using CSOM. A sample script is provided below:</span></span>

```powershell
$username = "<admin@company.sharepoint.com>"
$password = "password"
$url = "<https://site.sharepoint.com>"
$securePassword = ConvertTo-SecureString $Password -AsPlainText -Force

# the path here may need to change if you used e.g. C:Lib.
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\16ISAPIMicrosoft.SharePoint.Client.dll"
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\16ISAPIMicrosoft.SharePoint.Client.Runtime.dll"

# connect/authenticate to SharePoint Online and get ClientContext object.
$clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($url)
$credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($username, $securePassword)
$clientContext.Credentials = $credentials
if (!$clientContext.ServerObjectIsNull.Value)
{
    Write-Host "Connected to SharePoint Online site: '$Url'" -ForegroundColor Green
}

# Get user
$user = $clientContext.Web.SiteUsers.GetByLoginName("i:0#.f|membership|user@company.sharepoint.com")

# Redact user
$user.Email = "Redacted"
$user.Title = "Redacted"
$user.Update()
$clientContext.Load($user)
$clientContext.ExecuteQuery()

# Get users
$users = $clientContext.Web.SiteUsers

# Remove user from site
$users.RemoveById($user.Id)
$clientContext.Load($users)
$clientContext.ExecuteQuery()
```