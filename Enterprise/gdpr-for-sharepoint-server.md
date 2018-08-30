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
# <a name="gdpr-for-sharepoint-server"></a>SharePoint Server での GDPR への対応

個人情報保護の一部として、次のことをお勧めします。

-   Azure Information Protection を使用してデータを分類します。

-   SharePoint Server を最小特権構成で実行します。詳細については、「[SharePoint Server で最小特権管理を計画する](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration)」と「[SharePoint Server のセキュリティ](https://docs.microsoft.com/ja-JP/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server)」を参照してください。

-   [サーバーで BitLocker 暗号化を有効にします](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server)。

## <a name="user-generated-content"></a>ユーザー生成コンテンツ

SharePoint Server のサイトとライブラリに含まれているユーザー生成コンテンツについて推奨される基本的な操作を次に示します。

-   Azure Information Protection を使用して機密データにラベルを付けます。

-   [SharePoint Server 検索](https://docs.microsoft.com/SharePoint/search/search)と[電子情報開示](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server)を使用して機密データを取得します。

ファイル共有、SharePoint のサイトおよびライブラリについて推奨される作業の手順を次に示します。

1.  **Azure Information Protection スキャナーをインストールし、構成します。**

    -   使用する機密データの種類を決定します。

    -   使用する SharePoint サイトを指定します。

2.  **検出サイクルを完了します。**

    -   検出モードでスキャナーを実行し、検出結果を検証します。

    -   必要に応じて、条件と機密情報の種類を最適化します。

    -   自動的に適用されるラベルの予期される影響を評価します。

3.  **Azure Information Protection スキャナーを実行して、対象となるドキュメントにラベルを適用します**。

4.  **保護のために次の操作を実行します。**

    a. 目的としたラベルのドキュメントを保護するための Exchange データ損失防止ルールを構成します。

    b. アクセス許可を使用して、ファイルにアクセスできるユーザーを制限するようにしてください。

    c. SharePoint では、ライブラリを IRM により保護します。

5.  **監視のため、Windows Server のログを SIEM ツールに統合します。**

    a. データ主体要求の個人データを検索するには、Search Center または電子情報開示を使用します。

機密データにラベルを適用するときには、保護機能が設定されていないラベルを必ず使用してください。保護機能には、サービスがファイルの機密データを検出できない原因となる暗号化などがあります。

Azure Information Protection スキャナーを使用して個人データを検索したりラベル付けしたりすることに関する詳細については、[Microsoft GDPR Data Discovery Toolkit](http://aka.ms/gdprpartners) (http://aka.ms/gdprpartners)) を参照してください。

さまざまな条件でスキャナーを構成すること、また Office 365 データ損失防止 (DLP) のさまざまな機密情報タイプを使用することに関する情報については、「[Azure Information Protection 用の自動および推奨分類の条件を構成する方法](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification)」を参照してください。新しいタイプの Office 365 機密情報はスキャナーですぐに利用できるようになるわけではなく、カスタム機密情報タイプはスキャナーで使用できないことに注意ください。

## <a name="removing-personal-information-from-office-files"></a>Office ファイルから個人情報を削除する

SharePoint ドキュメント ライブラリに保存されている Office ファイルから個人情報 (Word ドキュメントのメタデータやコメントなど) を削除する作業は、次の手順に従って手動で行う必要があります。

1.  SharePoint Server からドキュメントのコピーをローカル ディスクにダウンロードします。

2.  SharePoint ドキュメント ライブラリからドキュメントを削除します。

3.  「[ドキュメントを調べ非表示のデータと個人情報を削除する](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F)」の手順に従います。

4.  ドキュメントを SharePoint ドキュメント ライブラリに再びアップロードします。

## <a name="telemetry-and-log-files"></a>テレメトリ ファイルとログ ファイル

### <a name="uls-logs"></a>ULS ログ

SharePoint Server の統合ログ サービス (ULS) と利用状況ログは、さまざまなシステム機能を追跡することから、ユーザー情報が含まれている可能性があります。ULS ログと利用状況ログはテキスト ファイルであり、各種検索ツールを使用して検索できます。[Merge-SPLogFile PowerShell コマンドレット](https://docs.microsoft.com/ja-JP/powershell/module/sharepoint-server/merge-splogfile)は、ファーム内の複数サーバー上の ULS ログのレコードを戻します。

ログ保存ポリシーを、ビジネスの目標に必要な最小値に設定することを検討してください。SharePoint Server でのログの構成の詳細については、「[SharePoint Server で診断ログを構成する](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)」を参照してください。

一部のシステム イベントも Windows イベント ログに記録されることに注意してください。

### <a name="usage-database"></a>利用状況データベース

SharePoint Server 利用状況データベース (既定の名前は WSS_Logging) には、ULS ログの情報のサブセットが保存されています。このデータベースのデータの最大保存期間は 30 日です。この日数を、ビジネス ニーズで許容可能な最も短い期間に設定することをお勧めします。詳細については、「[SharePoint Server で診断ログを構成する](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)」を参照してください。

## <a name="personal-information-and-search"></a>個人情報と検索

検索クエリの履歴と利用状況レコードには、ユーザー名への参照が含まれています。

### <a name="query-history-and-favorite-queries"></a>クエリの履歴とよく利用するクエリ

SharePoint Server では、クエリの履歴と「よく利用する」クエリは 365 日経過後に自動的に期限切れとなります。ユーザーが組織を離れた場合、次の手順に従ってクエリの履歴からユーザーの名前への参照を削除できます。

以下に示す SQL クエリは、SharePoint Server に適用されます。これらのクエリでは次の操作が実行されます。

-   ユーザーのクエリ履歴またはよく利用するクエリをエクスポートする

-   クエリの履歴からユーザー名への参照を削除する

#### <a name="export-a-users-queries-since-a-specific-date"></a>特定の日付以降のユーザーのクエリをエクスポートする 

@StartTime 以降に @UserName によって実行されたクエリを、Link Store クエリ ログ テーブルからエクスポートするには、次のプロシージャを使用します。

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

#### <a name="export-a-users-queries-from-the-past-100-days"></a>過去 100 日間のユーザー クエリをエクスポートする

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetQueryTermsForUser '0#.w|domain\username', @FROMDATE 
```

#### <a name="export-a-users-favorite-queries"></a>ユーザーがよく利用するクエリをエクスポートする

<DateTime> 以降に @UserName が実行した、ユーザーがよく利用するクエリを、検索管理 DB の個人結果テーブルからエクスポートするには、次のプロシージャを使用します。

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

#### <a name="export-a-users-favorite-queries-from-the-past-100-days"></a>過去 100 日間のユーザーのよく利用するクエリをエクスポートする 

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetPersonalFavoriteQueries '0#.w|domain\username', @FROMDATE 
```

#### <a name="remove-references-to-user-names-that-are-more-than-x-days-old"></a>過去 X 日よりも古いユーザー名への参照を削除する

Links Store クエリ ログ テーブルから、経過日数が @Days を超えている*すべての*ユーザー名への参照を削除するには、次のプロシージャを使用します。このプロシージャは、@LastCleanupTime 以降の参照だけを削除します。

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

#### <a name="remove-references-to-a-specific-user-name-thats-more-than-x-days-old"></a>経過日数が X 日を超えている特定のユーザー名への参照を削除する

Links Store クエリ ログ テーブルから、経過日数が @Days を超えている*特定の*ユーザー名への参照を削除するには、次のプロシージャを使用します。このプロシージャは、@LastCleanupTime 以降の参照だけを削除します。

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

#### <a name="remove-references-to-all-user-names-in-the-query-history-from-a-date-and-up-to-the-past-30-days"></a>クエリ履歴から、指定されている日付から過去 30 日間のすべてのユーザー名への参照を削除する

```sql
EXECUTE proc_MSS_QLog_Cleanup_Users '1-1-2017', 30 
```

### <a name="delete-usage-records"></a>利用状況レコードを削除する

SharePoint Server では、3 年経過した利用状況レコードは自動的に削除されます。次の手順に従って、このようなレコードを手動で削除することもできます。

削除されたドキュメントに関連付けられているすべての利用状況レコードを削除するには、次の手順に従います。 

1.  最新の SharePoint 更新プログラムがインストールされていることを確認します。 

2.  SharePoint 管理シェルを開始します。

3.  利用状況分析による分析を停止してクリアします。 

    ```powershell
    $tj = Get-SPTimerJob -Type Microsoft.Office.Server.Search.Analytics.UsageAnalyticsJobDefinition 
    $tj.StopAnalysis() 
    $tj.ClearAnalysis() 
    ```

4.  分析が再び開始されるまで待ちます (最大 24 時間かかります)。 

5.  分析の次回実行時に、分析レポート データベースからすべてのレコードがダンプされます。多数のエントリが保存されている大きなデータベースでは、この完全ダンプに時間がかかることがあります。

6.  10 日間待ちます。分析は毎日実行され、10 回目の実行後に、削除されているドキュメントに関連付けられているレコードが削除されます。削除する必要があるレコードが多数存在する場合、この実行には通常よりも時間がかかることがあります。 

### <a name="personal-information-and-search-in-sharepoint-server-2010"></a>SharePoint Server 2010 での個人情報と検索

#### <a name="fast-search-server-2010-for-sharepoint"></a>FAST Search Server 2010 for SharePoint 

FAST Search Server 2010 アドオンは、ファイルをインデックスに保存する以外に、ファイルを FixML と呼ばれる中間形式でも保存します。FiXML ファイルは定期的に (既定では午前 3 時から午前 5 時までの間に) 圧縮されます。この圧縮により、削除済みファイルが FiXML ファイルから自動的に削除されます。削除されているユーザーまたはドキュメントに属する情報が適切な時点で削除されるようにするには、圧縮が常に有効であることを確認してください。

### <a name="hybrid-search"></a>ハイブリッド検索 

ハイブリッド検索ソリューションについて推奨されるアクションは、SharePoint Server または SharePoint Online での検索の場合と同じです。次の 2 種類のハイブリッド検索ソリューションがあります。

**クラウド ハイブリッド検索ソリューション -** SharePoint 用クラウド ハイブリッド検索ソリューションでは、オンプレミスのコンテンツを含めてクロールしたすべてのコンテンツのインデックスを Office 365 の検索インデックスに作成します。ユーザーは Office 365 の検索インデックスをクエリすることで、オンプレミスと Office 365 の両方のコンテンツからの検索結果を取得します。ドキュメントが SharePoint Server 環境から削除されると、そのドキュメントは Office 365 の検索インデックスからも削除されます。GDPR によるハイブリッド環境への影響を理解するため、「[SharePoint Server 用のクラウド ハイブリッド検索について](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint)」と「[SharePoint のクラウド ハイブリッド検索を計画する](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint)」を参照してください。

**ハイブリッド フェデレーション検索 -** ハイブリッド フェデレーション検索では、SharePoint Server のインデックスと Office 365 のインデックスの両方を使用します。SharePoint Server と SharePoint Online の両方の Search サービスは、他方の環境の検索インデックスに対するクエリを実行して、統合された結果を返すことができます。ユーザーが検索センターから検索を実行すると、検索結果は SharePoint Server の検索インデックスと Office 365 の検索インデックスから取得されます。GDPR によるハイブリッド環境への影響について理解するため、「[SharePoint 用のハイブリッド フェデレーション検索について](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint)」を参照してください。

## <a name="on-prem-to-cloud-migrations"></a>オンプレミスからクラウドへの移行

SharePoint Server から SharePoint Online への移行中には、特定の時点で両方のロケーションに重複データが存在することがあります。移行中のデータを削除する必要がある場合には、最初に移行を完了してから、データを両方のロケーションから削除することをお勧めします。いずれのロケーションでも、エクスポートするデータをクエリできます。

## <a name="user-profile-data"></a>ユーザー プロファイル データ

User Profile Service により、さまざまな外部ソースからプロファイル データをインポートできます。このようなユーザー プロファイル データに対するクエリと更新は、データのマスターが存在するシステムで処理する必要があります。外部システムを更新した場合は、SharePoint Server のユーザー プロファイルを再度同期してください。

SharePoint ユーザー プロファイルからユーザーの個人情報を削除するには、次の基本的な手順に従います。

1.  SharePoint Server ユーザー プロファイルにフィードを提供するすべての外部システムから、ユーザー情報を削除します。ディレクトリ同期を使用している場合は、オンプレミスの Active Directory 環境からユーザーを削除する必要があります。

2.  SharePoint Server で[プロファイル同期](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually)を実行します。

3.  SharePoint Server からプロファイルを削除します。削除完了後 30 日以内に、SharePoint Server によりユーザー プロファイル データベースからそのプロファイルが完全に削除されます。また、ユーザーのプロファイル ページと個人用サイトが削除されます。

ユーザーのプロファイルの削除後に、ユーザーが訪問したことのあるサイト コレクションに、一部の情報 (ユーザー ID など) が記録されたままになることがあります。特定のサイト コレクションからこのデータを削除する場合は、CSOM を使用して削除できます。次にサンプル スクリプトを示します。

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