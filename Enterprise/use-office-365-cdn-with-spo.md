---
title: SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Office 365 コンテンツ配信ネットワーク (CDN) を使用して、自分の場所やコンテンツへのアクセス方法に関係なく、すべてのユーザーに対して SharePoint Online アセットの配信を高速化する方法について説明します。
ms.openlocfilehash: 7ca9283348bda666b2de8c0ae07896164f40d240
ms.sourcegitcommit: 99bf8739dfe1842c71154ed9548ebdd013c7e59e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2019
ms.locfileid: "35017317"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用

組み込みの Office 365 コンテンツ配信ネットワーク (CDN) を使用して静的資産をホストすることで、SharePoint Online ページのパフォーマンスを向上させることができます。 Office 365 CDN では、静的資産を要求しているブラウザーの近くに静的資産をキャッシュするとパフォーマンスが向上します。これにより、ダウンロードが速くなり、待ち時間が短縮されます。 また、Office 365 CDN は、強化された圧縮と HTTP パイプライン処理に[http/2 プロトコル](https://en.wikipedia.org/wiki/HTTP/2)を使用します。 Office 365 CDN サービスは、SharePoint Online サブスクリプションの一部として含まれます。

> [!NOTE]
> Office 365 CDN を使用する場合の制限事項:
> + Office 365 CDN は、**運用環境**(世界規模) のクラウドのテナントでのみ使用できます。 米国政府機関のテナント、中国およびドイツのクラウドでは、現在 Office 365 CDN をサポートしていません。
> + Office 365 CDN は、現在、カスタムまたは "バニティ" ドメインで構成されているテナントをサポートしていません。 「 [Office 365 にドメインを追加](https://docs.microsoft.com/en-us/office365/admin/setup/add-domain?view=o365-worldwide)する」の手順を使用してテナントにドメインを追加した場合、cdn からコンテンツにアクセスしようとすると、OFFICE 365 CDN からエラーが返されます。

Office 365 CDN は静的資産を複数の場所 _(元の場所)_ でホストできる複数の CDN で構成されているため、静的資産をグローバルな高速ネットワークから提供することができます。 Office 365 CDN でホストするコンテンツの種類に応じて、**公開**、**非公開**、またはその両方の元の場所を追加できます。 パブリックとプライベートオリジンの違いに関する詳細については、[各配信元がパブリックかプライベートかを選択](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)するを参照してください。

![Office 365 CDN の概念図](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN の概念図")

CDNs のしくみに精通している場合は、テナントに対して Office 365 CDN を有効にするための手順をいくつか実行するだけで十分です。 このトピックでは、その方法について説明します。 静的アセットのホスティングを開始する方法については、「」を参照してください。

> [!TIP]
> 特別な使用シナリオで Office 365 と共に使用できるその他の Microsoft ホストされた CDNs がありますが、このトピックでは Office 365 CDN の範囲外にあるため、このトピックでは説明していません。 詳細については、「[その他の Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns)」を参照してください。

 **[Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に戻ります。**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>SharePoint Online での Office 365 CDN の使用の概要

組織で Office 365 CDN をセットアップするには、次の基本的な手順を実行します。

- [Office 365 CDN の展開を計画する](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - [CDN でホストする静的アセットを決定](use-office-365-cdn-with-spo.md#CDNAssets)します。
  - [アセットを格納する場所を決定](use-office-365-cdn-with-spo.md#CDNStoreAssets)します。 この場所は SharePoint サイト、ライブラリ、またはフォルダーで、_元_の名前と呼ばれます。
  - [各配信元をパブリックまたはプライベートにする必要があるかどうかを選択し](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)ます。 パブリックとプライベートの両方の種類のオリジンを複数追加できます。

- PowerShell または SharePoint Online CLI のいずれかを使用して CDN をセットアップおよび構成する

  - [SharePoint Online 管理シェルを使用して CDN を設定および構成する](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [Office 365 CLI を使用して CDN をセットアップおよび構成する](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  この手順を完了すると、次のことができます。

  - 組織の CDN を有効にしました。
  - オリジンを追加し、各オリジンをパブリックまたはプライベートとして識別しました。

セットアップが完了したら、次の方法で、時間の経過と共に[Office 365 CDN を管理](use-office-365-cdn-with-spo.md#CDNManage)できます。
  
- アセットの追加、更新、および削除
- オリジンを追加および削除する
- CDN ポリシーを構成する
- 必要に応じて、CDN を無効にする

最後に、「 [cdn アセットを使用](use-office-365-cdn-with-spo.md#using-your-cdn-assets)して、パブリックとプライベートの両方から cdn アセットにアクセスする方法について知る」を参照してください。

一般的な問題の解決に関するガイダンスについて[は、「Office 365 CDN のトラブルシューティング](use-office-365-cdn-with-spo.md#CDNTroubleshooting)」を参照してください。

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Office 365 CDN の展開を計画する

Office 365 テナントの Office 365 CDN を展開する前に、計画プロセスの一部として、以下の要因を考慮する必要があります。

  - [CDN でホストする静的アセットを決定する](use-office-365-cdn-with-spo.md#CDNAssets)
  - [アセットを格納する場所を決定する](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [各配信元をパブリックまたはプライベートにする必要があるかどうかを選択する](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>CDN でホストする静的アセットを決定する
<a name="CDNAssets"> </a>

通常、CDNs は_静的アセット_のホスティングや、頻繁に変更されないアセットに最も効果的です。 目安として、これらの条件の一部またはすべてを満たすファイルを特定することをお勧めします。

- ページの読み込み時間に大きな影響を与える可能性があるページ (スクリプトや画像など) に埋め込まれる静的ファイル
- 実行可能ファイルやインストールファイルなどの大きなファイル
- ストリーミングメディアファイル
- クライアント側のコードをサポートするリソースライブラリ

たとえば、サイトの画像やスクリプトなど繰り返し要求された小さいファイルは、サイトのレンダリングパフォーマンスを大幅に向上させ、CDN の配信元に追加するときに、SharePoint Online サイトの負荷を徐々に軽減できます。 インストールの実行可能ファイル、ビデオファイルなどの大規模なファイルは、CDN からダウンロードまたはストリーム転送することができます。これにより、頻繁にアクセスされていない場合でも、SharePoint Online サイトの負荷が大幅に低下します。

ファイル単位でのパフォーマンスの向上は、最も近い CDN エンドポイントへのクライアントの近接度、ローカルネットワーク上の一時的な状態など、多くの要因によって異なります。 多くの静的ファイルは非常に小さく、Office 365 からダウンロードできます。 ただし、web ページには、ダウンロード時間が数秒になる多くの埋め込みファイルが含まれている場合があります。 これらのファイルを CDN から処理することにより、ページ全体の読み込み時間が大幅に短縮されます。 CDN で提供される[パフォーマンスの向上](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)については、例を参照してください。

### <a name="determine-where-you-want-to-store-your-assets"></a>アセットを格納する場所を決定する
<a name="CDNStoreAssets"> </a>

CDN は、_送信元_と呼ばれる場所からアセットを取得します。 起点として、URL でアクセスできる SharePoint サイト、ドキュメントライブラリ、またはフォルダーを指定できます。 組織のオリジンを指定する場合は、非常に柔軟に設定できます。 たとえば、すべての CDN アセットを配置する複数のオリジンまたは単一の発信元を指定できます。 組織にパブリックまたはプライベートのどちらを使用するかを選択できます。 大部分の組織では、2つの組み合わせを実装することを選択します。

フォルダーやドキュメントライブラリなどの作成元に新しいコンテナーを作成し、CDN から使用できるようにするファイルを追加することができます。 これは、CDN から使用できるようにする特定のアセットのセットがあり、その一連の CDN アセットをコンテナー内のファイルのみに制限する場合に適した方法です。

既存のサイトコレクション、サイト、ライブラリ、またはフォルダーを作成元として構成することもできます。これにより、コンテナー内の対象となるすべてのアセットが CDN から利用できるようになります。 既存のコンテナーを送信元として追加する前に、そのコンテンツとアクセス許可を確認して、匿名アクセスや権限のないユーザーに資産を誤って公開しないようにすることが重要です。

Cdn_ポリシー_を定義して、その出所のコンテンツを cdn から除外することができます。 CDN ポリシーでは、_ファイルの種類_や_サイト分類_などの属性によってパブリックまたはプライベートの出所のアセットが除外されます。また、ポリシーで指定する CdnType (プライベートまたはパブリック) のすべてのオリジンに適用されます。 たとえば、複数のサブサイトが含まれるサイトで構成されるプライベートオリジンを追加する場合は、**機密**としてマークされたサイトを除外するポリシーを定義して、その分類を適用したサイトのコンテンツが CDN から提供されないようにすることができます。 このポリシーは、CDN に追加した_すべて_のプライベートオリジンのコンテンツに適用されます。
  
オリジンの数が大きいほど、CDN サービスが要求を処理するのにかかる時間に大きな影響があることに注意してください。 元の数を可能な限り制限することをお勧めします。
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>各配信元をパブリックまたはプライベートにする必要があるかどうかを選択する
<a name="CDNOriginChoosePublicPrivate"> </a>

発信元を識別する場合は、_パブリック_または_プライベート_にするかどうかを指定します。 公開されている出所の CDN アセットへのアクセスは匿名になり、プライベートな出所の CDN コンテンツは、セキュリティを強化するために動的に生成されたトークンによって保護されます。 どのオプションを選択したとしても、Microsoft では、CDN 自体の管理に関して、多くの処理が行われます。 また、CDN を設定して、出所を特定した後で、後で考えを変更することもできます。

パブリックおよびプライベートのどちらのオプションもパフォーマンスの向上に似ていますが、それぞれに固有の属性と利点があります。

Office 365 CDN 内の**公開**元は匿名でアクセス可能で、ホストされたアセットには、そのアセットへの URL を持つすべてのユーザーがアクセスできます。 公開されている元の場所のコンテンツへのアクセスは匿名になるため、アクセスしたコンテンツは、機密データ以外の一般的なコンテンツ (JavaScript ファイル、スクリプト、アイコン、画像など) をキャッシュする場合にのみ使用するようにしてください。

Office 365 CDN 内の**非公開**の元の場所は、SharePoint Online ドキュメント ライブラリ、サイト、メディア (例: 動画) など、ユーザー コンテンツへのプライベート アクセスを行う場合に使用します。 プライベートオリジンにあるコンテンツへのアクセスは、元のドキュメントライブラリまたは保存場所へのアクセス許可を持つユーザーのみがアクセスできるように、動的に生成されたトークンによってセキュリティ保護されます。 Office 365 CDN の出所は、SharePoint Online のコンテンツにのみ使用できます。また、SharePoint Online テナントからリダイレクトすることによって、プライベートの出所のアセットにのみアクセスできます。

プライベートな出所のアセットに対する CDN アクセスのしくみについては、「[プライベートオリジンでアセットを使用](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)する」を参照してください。

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>公共の出所でのアセットのホスティングの属性と利点
  
- パブリックの配信元で公開されている資産には、すべてのユーザーが匿名でアクセスできます。
    > [!IMPORTANT]
    > ユーザー情報が含まれているリソース、または組織にとって公共の出所であると見なされるリソースは、決して配置しないでください。
- パブリックの配信元から資産を削除した場合、その資産は最大 30 日間はキャッシュから引き続き使用できます。ただし、CDN 内の資産へのリンクは 15 分以内に無効になります。
- パブリックの配信元にスタイル シート (CSS ファイル) をホストする場合は、コード内で相対パスと URI を使用できます。 つまり、背景画像と他のオブジェクトの場所を、呼び出し元の資産の場所からの相対位置で参照することができます。
- パブリックの配信元の URL をハード コーディングすることはできますが、お勧めできません。 CDN にアクセスできなくなった場合、SharePoint Online でその URL は自動的に組織に対して解決されず、結果としてリンクが壊れて他のエラーが発生する可能性があるためです。
- パブリックの配信元用に含まれている既定のファイルの種類は、css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf、.woff です。 その他のファイルの種類を指定することもできます。
- 指定したサイト分類で識別されたアセットを除外するようにポリシーを構成できます。 たとえば、許可されているファイルの種類のもので、パブリックの配信元にある資産であっても、"社外秘" または "制限付き" としてマークされている資産はすべて除外する、といったことができます。

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>プライベートな出所でアセットをホスティングするための属性と利点

- プライベートオリジンは、SharePoint Online アセットにのみ使用できます。
- ユーザーは、コンテナーにアクセスする権限を持っている場合にのみ、プライベートの配信元からアセットにアクセスできます。 これらの資産に匿名でアクセスすることはできません。
- プライベートの出所のアセットは、SharePoint Online テナントから参照する必要があります。 プライベート CDN アセットへの直接アクセスは機能しません。
- プライベートオリジンからアセットを削除すると、キャッシュから1時間以内に資産が利用可能になります。ただし、アセットの削除から15分以内に CDN のアセットへのリンクが無効になります。
- プライベートの配信元用に含まれている既定のファイルの種類は、.gif、.ico、.jpeg、.jpg、.js、.png です。 その他のファイルの種類を指定することもできます。
- 公開元の場合と同様に、ワイルドカードを使用してフォルダーまたはドキュメントライブラリ内のすべてのアセットを含める場合でも、指定したサイト分類で識別されたアセットを除外するようにポリシーを構成できます。

Office 365 CDN、一般的な CDN 概念、および Office 365 テナントで使用できるその他の Microsoft CDNs を使用する理由の詳細については、「 [Content Delivery Networks](content-delivery-networks.md)」を参照してください。

### <a name="default-cdn-origins"></a>既定の CDN オリジン

特に指定しない限り、office 365 では、Office 365 CDN を有効にすると、既定の出所が設定されます。 最初に設定しなかった場合は、セットアップの完了後にこれらのオリジンを追加することができます。 既定の元の設定をスキップして、特定の理由がある場合は、CDN を有効にしたときに作成できるようにする必要があります。
  
既定のプライベート CDN の出所:
  
- \*/userphoto.aspx
- \*/siteassets

既定のパブリック CDN の出所:
  
- \*/マスター
- \*/スタイルライブラリ
- \*/clientsideアセット

> [!NOTE]
> _clientsideassets_は、2017年12月に OFFICE 365 CDN サービスに追加された既定のパブリックの配信元です。 CDN で SharePoint Framework ソリューションを動作させるには、この配信元が存在している必要があります。 2017年12月より前に Office 365 CDN を有効にした場合、または CDN を有効にしたときに既定の出所のセットアップをスキップした場合は、この配信元を手動で追加することができます。 詳細については、「[クライアント側の web パーツまたは SharePoint Framework ソリューションが動作しない](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)」を参照してください。

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>SharePoint Online 管理シェルを使用して Office 365 CDN をセットアップおよび構成する
<a name="CDNSetupinPShell"> </a>

このセクションの手順では、sharepoint online 管理シェルを使用して SharePoint Online に接続する必要があります。 手順については、「[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)」を参照してください。
  
SharePoint online 管理シェルを使用して SharePoint Online でアセットをホストする CDN を設定および構成するには、次の手順を実行します。
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>組織で Office 365 CDN を使用できるようにする

テナントの CDN 設定に変更を加える前に、Office 365 テナントのプライベート CDN 構成の現在の状態を取得する必要があります。 SharePoint Online 管理シェルを使用して、テナントに接続します。

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

次に、 **SPOTenantCdnEnabled**コマンドレットを使用して、テナントから CDN の状態設定を取得します。

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

指定した CdnType の CDN の状態は、画面に出力されます。

**SPOTenantCdnEnabled**コマンドレットを使用して、組織で OFFICE 365 CDN を使用できるようにします。 組織でパブリックオリジン、プライベートオリジン、またはその両方を一度に使用できるようにすることができます。 既定のオリジンのセットアップを有効にした場合にスキップするように CDN を構成することもできます。 このトピックで説明されているように、いつでもこれらのオリジンを追加できます。
  
SharePoint Online の Windows Powershell の場合:

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

たとえば、組織でパブリックオリジンとプライベートオリジンの両方を使用できるようにするには、次のコマンドを入力します。

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

組織でパブリックとプライベートの両方を使用できるようにし、既定のオリジンの設定をスキップするには、次のコマンドを入力します。

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Office 365 CDN を有効にしたときに既定でプロビジョニングされるオリジンに関する情報、および既定のオリジンのセットアップをスキップすることによる影響を受ける可能性がある場合は、「 [DEFAULT CDN オリジン](use-office-365-cdn-with-spo.md#default-cdn-origins)」を参照してください。

組織でパブリックオリジンを使用できるようにするには、次のコマンドを入力します。

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

組織でプライベートオリジンを使用できるようにするには、次のコマンドを入力します。

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

このコマンドレットの詳細については、「 [SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)」を参照してください。
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Office 365 CDN に含めるファイルの種類のリストを変更する (オプション)
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> **Set-spotenantcdnpolicy**コマンドレットを使用してファイルの種類を定義するときは、現在定義されているリストを上書きします。 他のファイルの種類を一覧に追加する場合は、コマンドレットを最初に使用して、既に許可されているファイルの種類を確認し、新しいファイルの種類を一覧に含めます。
  
**Set-spotenantcdnpolicy**コマンドレットを使用して、CDN でパブリックおよびプライベートの出所でホストできる静的ファイルの種類を定義します。 既定では、css、.gif、.jpg、.js などの一般的なアセットタイプが許可されています。

SharePoint Online の Windows PowerShell の場合:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

たとえば、CDN を有効にして .css ファイルと .png ファイルをホストできるようにするには、次のコマンドを入力します。

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

CDN で現在許可されているファイルの種類を確認するには、 **get-spotenantcdnpolicies**コマンドレットを使用します。

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

これらのコマンドレットの詳細については、「 [set-spotenantcdnpolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) 」および「 [get-spotenantcdnpolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)」を参照してください。
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Office 365 CDN から除外するサイト分類の一覧を変更する (オプション)
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> **Set-spotenantcdnpolicy**コマンドレットを使用してサイト分類を除外する場合は、現在定義されているリストを上書きします。 追加のサイト分類を除外する場合は、最初にコマンドレットを使用して、既に除外されている分類を確認し、新しい分類項目と共にそれらを追加します。


  **Set-SPOTenantCdnPolicy** コマンドレットを使用して、CDN で利用できるようにしないサイトの分類を除外します。 既定で除外されるサイトの分類はありません。

SharePoint Online の Windows PowerShell の場合:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

現在制限されているサイト分類を確認するには、 **get-spotenantcdnpolicies**コマンドレットを使用します。

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

返されるプロパティには、 _IncludeFileExtensions_、 _ExcludeRestrictedSiteClassifications_ 、 _excludeifnoscriptdisabled_があります。

_IncludeFileExtensions_プロパティには、CDN から提供されるファイル拡張子の一覧が含まれています。

> [!NOTE]
> 既定のファイル拡張子は、パブリックとプライベートの間で異なります。

_ExcludeRestrictedSiteClassifications_プロパティには、CDN から除外するサイトの分類が含まれています。 たとえば、**機密**としてマークされたサイトを除外して、その分類が適用されたサイトのコンテンツが CDN から提供されないようにすることができます。

_Excludeifnoscriptdisabled_プロパティは、サイトレベルの_NoScript_属性の設定に基づいて CDN からコンテンツを除外します。 既定では、 _NoScript_属性は_モダン_サイトに対し**て [有効**] に設定され、_クラシック_サイトでは**無効**になっています。 これはテナントの設定によって異なります。

これらのコマンドレットの詳細については、「 [set-spotenantcdnpolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) 」および「 [get-spotenantcdnpolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)」を参照してください。
  
### <a name="add-an-origin-for-your-assets"></a>アセットの送信元を追加する
<a name="Office365CDNforSPOOrigin"> </a>

**Add-spotenantcdnorigin**コマンドレットを使用して、発信元を定義します。 複数の配信元を定義できます。 配信元は、CDN でホストする資産が含まれる SharePoint ライブラリまたはフォルダーを指す URL です。
  
> [!IMPORTANT]
> ユーザー情報が含まれているリソース、または組織にとって公共の出所であると見なされるリソースは、決して配置しないでください。

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

_Path_の値は、アセットが格納されているライブラリまたはフォルダーへの相対パスです。 相対パスに加え、ワイルドカードも使用できます。 オリジンは、URL に付加されたワイルドカードをサポートします。 これにより、複数のサイトにまたがるオリジンを作成できます。 たとえば、すべてのサイトのすべてのアセットを CDN 内のパブリックの配信元として masterpages フォルダーに含めるには、次のコマンドを入力します。

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- ワイルドカード修飾子は**/** 、パスの先頭にのみ使用でき、指定した url の下にあるすべての url セグメントに一致します。
- パスは、ドキュメントライブラリ、フォルダー、またはサイトを指すことができます。 たとえば、パス _*/site1_は、サイトのすべてのドキュメントライブラリに一致します。

特定の相対パスを持つ発信元を追加できます。 完全なパスを使用して発信元を追加することはできません。

この例では、特定のサイトに siteassets ライブラリのプライベートオリジンを追加します。

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

この例では、サイトコレクションのサイトアセットライブラリに_folder1_フォルダーのプライベートオリジンを追加します。

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

パスにスペースが含まれている場合は、パスを二重引用符で囲むか、スペースを URL エンコーディング% 20 に置き換えることができます。 次の例では、サイトコレクションのサイトアセットライブラリに_フォルダー 1_フォルダーのプライベートオリジンを追加します。

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

このコマンドとその構文の詳細については、「 [add-spotenantcdnorigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)」を参照してください。

> [!NOTE]
> プライベートオリジンでは、送信元から共有されるアセットは、CDN からアクセスする前に、メジャーバージョンを発行する必要があります。
  
コマンドを実行すると、システムによってデータセンター間の構成が同期されます。 これには最大15分かかることがあります。
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>例: SharePoint Online 用のマスターページおよびスタイルライブラリのパブリックの配信元を構成する
<a name="ExamplePublicOrigin"> </a>

通常、これらの出所は、Office 365 CDN を有効にしたときに既定で設定されます。 ただし、これらを手動で有効にする場合は、次の手順を実行します。
  
- **Add-spotenantcdnorigin**コマンドレットを使用して、スタイルライブラリをパブリックの配信元として定義します。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- **Add-spotenantcdnorigin**コマンドレットを使用して、マスターページをパブリックの配信元として定義します。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

このコマンドとその構文の詳細については、「 [add-spotenantcdnorigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)」を参照してください。

コマンドを実行すると、システムによってデータセンター間の構成が同期されます。 これには最大15分かかることがあります。

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>例: SharePoint Online のサイトアセット、サイトページ、および発行画像のプライベートオリジンを構成する
<a name="ExamplePrivateOrigin"> </a>

- **Add-spotenantcdnorigin**コマンドレットを使用して、サイトの assets フォルダーをプライベートの配信元として定義します。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- **Add-spotenantcdnorigin**コマンドレットを使用して、サイトページフォルダーをプライベートの配信元として定義します。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- **Add-spotenantcdnorigin**コマンドレットを使用して、公開画像フォルダーをプライベートの配信元として定義します。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

このコマンドとその構文の詳細については、「 [add-spotenantcdnorigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)」を参照してください。

コマンドを実行すると、システムによってデータセンター間の構成が同期されます。 これには最大15分かかることがあります。

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>例: SharePoint Online のサイトコレクションのプライベートオリジンを構成する
<a name="ExamplePrivateOriginSiteCollection"> </a>

**Add-spotenantcdnorigin**コマンドレットを使用して、サイトコレクションをプライベートの配信元として定義します。 次に例を示します。

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

このコマンドとその構文の詳細については、「 [add-spotenantcdnorigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)」を参照してください。
  
コマンドを実行すると、システムによってデータセンター間の構成が同期されます。 SharePoint Online テナントが CDN サービスに接続すると予想される_構成保留_メッセージが表示される場合があります。 これには最大15分かかることがあります。

### <a name="manage-the-office-365-cdn"></a>Office 365 CDN を管理する
<a name="CDNManage"> </a>

CDN を設定したら、このセクションで説明するように、コンテンツを更新するとき、または必要に応じて変更を加えたときに構成を変更できます。
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Office 365 CDN でアセットを追加、更新、または削除する
<a name="Office365CDNforSPOaddremoveasset"> </a>

セットアップの手順を完了すると、必要に応じて、新しいアセットを追加したり、既存のアセットを更新または削除したりできます。 元として識別したフォルダーまたは SharePoint ライブラリのアセットを変更するだけです。 新しいアセットを追加すると、そのアセットは CDN ですぐに使用できるようになります。 ただし、アセットを更新する場合は、新しいコピーが伝達されて CDN で利用可能になるまで最大15分かかります。
  
送信元の場所を取得する必要がある場合は、 **get-spotenantcdnorigins**コマンドレットを使用できます。 このコマンドレットの使用方法については、「 [get-spotenantcdnorigins](https://technet.microsoft.com/en-us/library/mt790770.aspx)」を参照してください。
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Office 365 CDN から発信元を削除する
<a name="Office365CDNforSPORemoveOrigin"> </a>

送信元として指定したフォルダーまたは SharePoint ライブラリへのアクセスを削除することができます。 これを行うには、 **add-spotenantcdnorigin**コマンドレットを使用します。

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

このコマンドレットの使用方法については、「 [add-spotenantcdnorigin](https://technet.microsoft.com/en-us/library/mt790761.aspx)」を参照してください。
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Office 365 CDN の配信元を変更する
<a name="Office365CDNforSPORemoveOrigin"> </a>

作成した元を変更することはできません。 代わりに、元を削除してから、新しいものを追加します。 詳細については、「 [Office 365 CDN から発信元を削除する](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin)」および「[アセットの送信元を追加](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)するには」を参照してください。
  
#### <a name="disable-the-office-365-cdn"></a>Office 365 CDN を無効にする
<a name="Office365CDNforSPODisable"> </a>

組織の CDN を無効にするには、 **SPOTenantCdnEnabled**コマンドレットを使用します。 CDN に対してパブリックおよびプライベートオリジンの両方を有効にしている場合は、次の例に示すように、コマンドレットを2回実行する必要があります。
  
CDN でパブリックオリジンを使用できないようにするには、次のコマンドを入力します。

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

CDN でプライベートオリジンを使用できないようにするには、次のコマンドを入力します。

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

このコマンドレットの詳細については、「 [SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)」を参照してください。

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a>Office 365 CLI を使用して Office 365 CDN をセットアップおよび構成する
<a name="CDNSetupinCLI"> </a>

このセクションの手順では、 [Office 365 CLI](https://aka.ms/o365cli)がインストールされている必要があります。 次に、[spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) コマンドを使用してご利用の SharePoint Online テナントに接続します。

Office 365 CLI を使用して SharePoint Online でアセットをホストする CDN を設定および構成するには、次の手順を実行します。

### <a name="enable-the-office-365-cdn"></a>Office 365 CDN を有効にする

テナントの Office 365 CDN の状態は [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) コマンドを使用して管理できます。

テナントで Office 365 パブリック CDN を有効にするには、次のように実行します。

```sh
spo cdn set --type Public --enabled true
```

Office 365 SharePoint CDN を有効にするには、次のように実行します。

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Office 365 CDN の現在の状況を確認する

特定の種類の Office 365 CDN が有効か無効かを確認するには、 [spo CDN get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/)コマンドを使用します。

Office 365 パブリック CDN が有効かどうかを確認するには、次のように実行します。

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Office 365 CDN の配信元を表示する

現在構成されている Office 365 パブリック CDN の配信元を確認するには、次のように実行します。

```sh
spo cdn origin list --type Public
```

Office 365 CDN を有効にしたときに既定でプロビジョニングされるオリジンに関する情報については、「 [DEFAULT CDN オリジン](use-office-365-cdn-with-spo.md#default-cdn-origins)」を参照してください。

### <a name="add-an-office-365-cdn-origin"></a>Office 365 CDN の配信元を追加する

> [!IMPORTANT]
> パブリックの配信元として構成された SharePoint ドキュメントライブラリで、組織に機密であると見なされるリソースを決して配置しないでください。

[spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) コマンドを使用して CDN の配信元を定義します。 複数の配信元を定義できます。 配信元は、CDN でホストする資産が含まれる SharePoint ライブラリまたはフォルダーを指す URL です。

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

ここ`path`で、はアセットを含むフォルダーへの相対パスです。 相対パスに加え、ワイルドカードも使用できます。

すべてのサイトの**マスターページギャラリー**内のすべてのアセットをパブリックの配信元として含めるには、次のように実行します。

```sh
spo cdn origin add --type Public --origin */masterpage
```

特定のサイト コレクションのプライベートの配信元を構成するには、次のように実行します。

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> CDN の配信元の追加後、CDN サービス経由でファイルを取得できるようになるまで最大 15 分かかることがあります。 特定の配信元が既に有効かどうかは、[spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) コマンドを使用して検証できます。

### <a name="remove-an-office-365-cdn-origin"></a>Office 365 CDN の配信元を削除する

[spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) コマンドを使用して、指定した種類の CDN の配信元を削除します。

CDN 構成からパブリックの配信元を削除するには、次のように実行します。

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> CDN の配信元を削除しても、その配信元に一致するドキュメントライブラリに格納されているファイルには影響しません。 これらのアセットが SharePoint URL を使用して参照されている場合、SharePoint はドキュメントライブラリを指す元の URL に自動的に切り替えます。 ただし、アセットがパブリック CDN URL を使用して参照されている場合は、発信元を削除するとリンクが解除され、手動で変更する必要があります。

### <a name="modify-an-office-365-cdn-origin"></a>Office 365 CDN の配信元を変更する

既存の CDN の配信元を変更することはできません。 代わりに、`spo cdn origin remove` コマンドを使用して定義済みの CDN の配信元を削除して、`spo cdn origin add` コマンドで新しい配信元を作成する必要があります。

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Office 365 CDN に含めるファイルの種類を変更する

既定で CND に含まれるファイルの種類は、_.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf、.woff_ です。 CDN に他の種類のファイルを含める必要がある場合、[spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) コマンドを使用して CDN 構成を変更できます。

> [!NOTE]
> ファイルの種類のリストを変更する場合、現在定義されているリストを上書きします。 他のファイルの種類を追加する場合は、[spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) コマンドを最初に使用して現在構成されているファイルの種類を確認します。

_JSON_ファイルの種類を、パブリック CDN に含まれるファイルの種類の既定のリストに追加するには、次のように実行します。

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Office 365 CDN から除外するサイトの分類のリストを変更する

[spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) コマンドを使用して、CDN で利用できるようにしないサイトの分類を除外します。 既定で除外されるサイトの分類はありません。

> [!NOTE]
> 除外するサイトの分類のリストを変更する場合、現在定義されているリストを上書きします。 他の分類を除外する場合は、[spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) コマンドを最初に使用して現在構成されている分類を確認します。

_HBI_として分類されたサイトをパブリック CDN から除外するには、execute

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Office 365 CDN を無効にする

Office 365 CDN を無効にするには、`spo cdn set` コマンドを使用します。たとえば、次のように実行します。

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a>CDN アセットの使用

CDN および構成されたオリジンとポリシーが有効になったので、CDN アセットの使用を開始できます。

このセクションでは、sharepoint ページとコンテンツで CDN Url を使用する方法を理解するのに役立ちます。これにより、SharePoint はパブリックとプライベートの両方のアセットに対する要求を CDN にリダイレクトします。

- [CDN アセットへのリンクの更新](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [パブリックの出所でアセットを使用する](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [プライベートの出所でアセットを使用する](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

クライアント側の web パーツをホストするために CDN を使用する方法については、「 [Office 365 CDN からクライアント側の web パーツをホストする (Hello World パート 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)」を参照してください。

### <a name="updating-links-to-cdn-assets"></a>CDN アセットへのリンクの更新

オリジナルに追加したアセットを使用するには、元のファイルへのリンクを元のファイルへのパスで更新するだけです。

- 送信元に追加したアセットへのリンクが含まれているページまたはコンテンツを編集します。 また、複数の方法のうちの1つを使用して、サイトまたはサイトコレクション内の特定のアセットにリンクを更新する場合は、そのすべてのリンクをグローバルに検索して置換することもできます。
- 送信元のアセットへのリンクごとに、パスを CDN の配信元のファイルへのパスに置き換えます。 相対パスを使用できます。
- ページまたはコンテンツを保存します。

たとえば、ドキュメントライブラリフォルダー _/site¥_/site/SiteAssets/images/image.png にコピーしたイメージの__ について考えてみましょう。 CDN アセットを使用するには、元のパスを画像ファイルの場所に置き換え、新しい URL の _/site/CDN_origins/public/image.png_を作成します。

相対パスではなく、アセットへの完全な URL を使用する場合は、次のようなリンクを作成します。

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> 一般的に、CDN のアセットに直接 Url をハードコーディングしないでください。 ただし、必要に応じて、パブリックの出所でアセットの Url を手動で作成することができます。 詳細については、「[パブリックアセットのハード CDN url](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets)」を参照してください。

CDN からアセットが提供されているかどうかを確認する方法については、「 [Office 365 cdn のトラブルシューティング](use-office-365-cdn-with-spo.md#CDNTroubleshooting)」セクションの「[アセットが cdn によって提供さ](use-office-365-cdn-with-spo.md#CDNConfirm)れていることを確認する方法」を参照してください。

### <a name="using-assets-in-public-origins"></a>パブリックの出所でアセットを使用する

SharePoint Online の**発行機能**によって、パブリックの配信元に格納されているアセットの url が自動的に cdn に書き換えられ、アセットが SharePoint ではなく cdn サービスから提供されるようになります。

発行機能が有効になっているサイトに送信元があり、CDN にオフロードするアセットが次のいずれかのカテゴリに含まれている場合、SharePoint はそのアセットが CDN によって除外されていないことを前提として、送信元のアセットの Url を自動的にリライトします。 原則.

SharePoint 発行機能によって自動的に書き換えられるのは次のようなリンクです。

- 従来の発行ページの HTML 応答の IMG/LINK/CSS URL
  - これには、ページの HTML コンテンツ内に作成者によって追加された画像が含まれます。
- 画像ライブラリ スライドショー Web パーツの画像 URL
- SPList REST API (RenderListDataAsStream) 結果の画像フィールド
  - 新しいプロパティ_Imagefieldstotryrewritetocdnurls_を使用して、フィールドのコンマ区切りリストを指定します。
  - ハイパーリンクフィールドと発行先イメージフィールドをサポートします。
- SharePoint image レンディション

次の図は、SharePoint がパブリックの配信元からアセットを含むページに対する要求を受信した場合のワークフローを示しています。

![ワークフローダイアグラム: パブリックの配信元から Office 365 CDN アセットを取得する](media/O365-CDN/o365-cdn-public-steps-transparent.svg "ワークフロー: パブリックの配信元から Office 365 CDN アセットを取得する")

> [!TIP]
> ページ上の特定の Url に対する自動書き換えを無効にする場合は、ページをチェックアウトし、クエリ文字列パラメーターを追加し**ます。** 無効にする各リンクの最後に、NoAutoReWrites = true を指定します。

#### <a name="hardcoding-cdn-urls-for-public-assets"></a>パブリックアセットの CDN の Url をハードコーディングする

_発行_機能がパブリックの配信元に対して有効になっていない場合、またはアセットが cdn サービスの自動リライト機能によってサポートされているリンクの種類のいずれでもない場合は、アセットの cdn の場所に url を手動で作成して、コンテンツ内でこれらの url を使用することができます。

> [!NOTE]
> URL の最後のセクションを形成する必要なアクセストークンがリソースの要求時に生成されるため、プライベートな出所のアセットに CDN Url をハードコーディングすることはできません。

パブリック CDN アセットの場合、URL の形式は次のようになります。

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

**TenantHostName**をテナント名に置き換えます。 例:

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a>プライベートの出所でアセットを使用する

プライベートオリジンでアセットを使用するには、追加の構成は必要ありません。 SharePoint Online は、プライベートの送信元でアセットの Url を自動的にリライトするので、それらのアセットに対する要求は常に CDN から提供されます。 これらの Url には、アセットが要求されたときに SharePoint Online によって自動生成される必要があるトークンが含まれるため、プライベートの出所に CDN アセットの Url を手動で作成することはできません。

プライベートオリジン内のアセットへのアクセスは、次のセクションで説明する警告を使用して、発信元へのユーザーの権限に基づいて、動的に生成されたトークンによって保護されます。 コンテンツをレンダリングするには、ユーザーが CDN に対して少なくとも**読み取り**アクセス権を持っている必要があります。

次の図は、SharePoint が私的な出所からアセットを含むページに対する要求を受信した場合のワークフローを示しています。

![ワークフローダイアグラム: 私的な出所から Office 365 CDN アセットを取得する](media/O365-CDN/o365-cdn-private-steps-transparent.svg "ワークフロー: 私的な出所から Office 365 CDN アセットを取得する")

#### <a name="token-based-authorization-in-private-origins"></a>プライベートオリジンでのトークンベース認証

Office 365 CDN のプライベートオリジンにあるアセットへのアクセスは、SharePoint Online によって生成されたトークンによって付与されます。 送信元によって指定されたフォルダーまたはライブラリへのアクセス許可を持っているユーザーには、アクセス許可レベルに基づいてファイルへのアクセスをユーザーに許可するトークンが自動的に与えられます。 これらのアクセストークンは、トークンリプレイ攻撃を防ぐために生成されてから90分以内に有効になります。

アクセストークンが生成されると、SharePoint Online は、2つの承認パラメーター (エッジ認証__ トークン) と_oat_ (元の認証トークン) を含むクライアントにカスタム URI を返します。 各トークンの構造は、「 _>__< ' secure signature ' >」の「< の有効期限 (エポック時間形式_)」です。 次に例を示します。

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> トークンを所有するすべてのユーザーが CDN 内のリソースにアクセスできます。 ただし、これらのアクセストークンを含む Url は HTTPS でのみ共有されるため、トークンの有効期限が切れる前にエンドユーザーが URL を明示的に共有しない限り、権限のないユーザーがアセットにアクセスすることはできません。

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>アイテムレベルのアクセス許可は、プライベートな出所のアセットではサポートされていません。

SharePoint Online では、プライベートな出所のアセットに対してアイテムレベルのアクセス許可がサポートされていないことに注意してください。 たとえば、に`https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`あるファイルの場合、次の条件に該当するファイルへのアクセスが有効になります。

|ユーザー  |アクセス許可  |有効なアクセス  |
|---------|---------|---------|
|ユーザー1     |Folder1 へのアクセス権         |CDN から image1 にアクセスできる         |
|User 2     |Folder1 へのアクセス権がありません。         |CDN から image1 にアクセスできません         |
|ユーザー3     |Folder1 にはアクセスできませんが、SharePoint Online で image1 にアクセスするための明示的なアクセス許可が付与されます。         |SharePoint Online から直接アセット image1 にアクセスできますが、CDN からはアクセスできません。         |
|ユーザー4     |Folder1 にはアクセスできますが、SharePoint Online で image1 へのアクセスを明示的に拒否されています。         |SharePoint Online からアセットにアクセスすることはできませんが、SharePoint Online でのファイルへのアクセスが拒否されているにもかかわらず、CDN からアセットにアクセスできます。         |

## <a name="troubleshooting-the-office-365-cdn"></a>Office 365 CDN のトラブルシューティング
<a name="CDNTroubleshooting"> </a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>アセットが CDN によって提供されていることを確認するにはどうすればよいですか?
<a name="CDNConfirm"> </a>

CDN アセットへのリンクをページに追加すると、そのページを参照して、アセットが CDN から提供されていることを確認できます。これにより、イメージを表示した後、イメージの URL を表示して確認することができます。

また、ブラウザーの開発者ツールを使用して、ページ上の各アセットの URL を表示したり、サードパーティのネットワークトレースツールを使用したりすることもできます。

> [!NOTE]
> Fiddler などのネットワークツールを使用して、SharePoint ページからアセットをレンダリングするのではない状態でアセットをテストする場合は、URL が SharePoint `https://yourdomain.sharepoint.com`Online テナントのルート url である GET 要求に、参照元のヘッダー "参照元" を手動で追加する必要があります。

SharePoint Online からの参照が必要になるため、web ブラウザーで CDN Url を直接テストすることはできません。 ただし、CDN アセット URL を SharePoint ページに追加し、そのページをブラウザーで開くと、CDN アセットがページに表示されます。

Microsoft Edge ブラウザーでの開発者ツールの使用の詳細については、「 [Microsoft Edge Developer tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide)」を参照してください。

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>新しい配信元からのアセットが利用できないのはなぜですか?
新しいオリジンにあるアセットは、登録が CDN 経由で伝達され、アセットを送信元から CDN ストレージにアップロードするのに時間がかかるため、すぐに使用できなくなります。 CDN でアセットを使用できるようになるために必要な時間は、アセットとファイルのサイズによって異なります。

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>クライアント側の web パーツまたは SharePoint Framework ソリューションが動作していない

パブリックの配信元に対して Office 365 CDN を有効にすると、CDN サービスによってこれらの既定のオリジンが自動的に作成されます。

- */マスターページ
- */スタイルライブラリ
- */Clientsideアセット

*/Clientsideassets の送信元が見つからない場合、SharePoint Framework ソリューションは失敗し、警告やエラーメッセージは生成されません。 このオリジンは、 _-nodefaultorigins_パラメーターが **$true**に設定されているか、または送信元が手動で削除されたために、CDN が有効になっていない可能性があります。

*/Clientsideassets の送信元が存在するかどうかは、次の PowerShell コマンドを使用して確認できます。

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

または、Office 365 CLI を使用して確認することもできます。

``` powershell
spo cdn origin list
```

PowerShell で送信元を追加するには:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Office 365 CLI で送信元を追加するには、次のようにします。

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Office 365 CDN を操作するために必要な PowerShell モジュールと CLI シェルは何ですか。

Office 365 CDN の操作は、 **SharePoint Online Management Shell** PowerShell モジュールまたは**office 365 CLI**のどちらかを使用して行うことができます。

- [SharePoint Online 管理シェルの概要](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [Office 365 CLI のインストール](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a>関連項目

[Content Delivery Network](https://aka.ms/o365cdns)

[Office 365 のネットワーク計画とパフォーマンス チューニング](https://aka.ms/tune)

