---
title: SharePoint Online のコンテンツ配信ネットワークを使用して Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: 置かれる場所や、コンテンツにアクセスする方法に関係なく、SharePoint Online の資産のすべてのユーザーへの配信を高速化するのには Office 365 の組み込みコンテンツ配信ネットワーク (CDN) を使用する方法を説明します。
ms.openlocfilehash: 958f01419a74e4b8cd007b2627585884496bdfdf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541544"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a>SharePoint Online のコンテンツ配信ネットワークを使用して Office 365

Office 365 のコンテンツ配信ネットワーク (CDN) で、SharePoint Online のページのパフォーマンスを向上させるための静的なアセットをホストすることができます。静的なアセットは、画像、ビデオ、オーディオ、スタイル シート、フォント、および JavaScript ファイルと同じように非常に多くの場合は、変更されないファイルです。CDN では、それらを要求しているブラウザーに静的なアセットの近くにキャッシュすることによって、地理的に分散キャッシュ プロキシとして動作します。 
  
Cdn の動作に慣れている場合のみ、それを設定するのには、いくつかの手順を完了する必要があります。このトピックで説明する方法です。Office 365 の CDN と、静的なアセットをホストしているを開始する方法については、読み進んでください。
  
 **ヘッドは、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)をバックアップします。**
  
## <a name="office-365-cdn-basics"></a>Office 365 の CDN の基本

Office 365 の CDN は、SharePoint Online サブスクリプションの一部として含まれています。支払う必要はありません。Office 365 は、プライベートの両方をサポートし、パブリック アクセスを提供したり、複数の場所、または元の場所でホストの静的なアセットをできます。Office 365 の CDN は、Azure CDN と同じではありません。CDN の一般的な概念、または CDN を使用する理由に関する詳細が必要な場合は、[コンテンツ配信ネットワーク](content-delivery-networks.md)を参照してください。
  
## <a name="how-the-cdn-grants-access-to-end-users"></a>CDN がエンド ・ ユーザーにアクセスを許可する方法

Office 365 の CDN 内の静的なアセットへのアクセスを秘密は、SharePoint Online で生成されたトークンによって付与されます。フォルダーまたはライブラリの原点を基準にアクセスするアクセス許可を既に持っているユーザーは、トークン自動的に付与されます。SharePoint Online は項目レベルのアクセス許可、CDN のです。
  
あるファイルをたとえば、 `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`、次の指定します。
  
- ユーザー 1 は、folder1 と image1.jpg にアクセスを持っています。
    
- ユーザー 2 には、folder1 へのアクセスはありません。
    
- ユーザー 3 が folder1 へのアクセスはありませんが、SharePoint Online で image1.jpg にアクセスするための明示的なアクセス許可を付与
    
- ユーザー 4 は folder1 へのアクセス権を持つが、image1.jpg へのアクセスを明示的に拒否されています。
    
次に該当します。
  
- ユーザー 1 および 4 のユーザーは、CDN で image1.jpg にアクセスすることがされます。
    
- ユーザー 2 とユーザー 3 は、CDN で image1.jpg にアクセスすることができません。
    
    ただし、ユーザー 3 にアクセスできます資産 image1.jpg を使用して直接 SharePoint Online ユーザー 4、SharePoint Online を資産にアクセスできないときに。
    
## <a name="overview-of-working-with-the-office-365-cdn"></a>Office 365 の CDN の使用の概要

Office 365 の CDN を設定するには、以下の基本的な手順。
  
- CDN の展開を計画します。
    
  - Office 365 の CDN でホストする静的な資産を特定します。これらの項目を選択する方法の詳細については、[コンテンツ配信ネットワーク](content-delivery-networks.md)を参照してください。
    
  - [お客様の資産を格納するかを確認します](use-office-365-cdn-with-spo.md#CDNStoreAssets)。この場所は、フォルダーや SharePoint ライブラリし、基準点と呼びます。
    
  - 資産を公開するか非公開かどうかを決定します。場合にこの操作を行う[各元がパブリックまたはプライベートにするかどうかを選択](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)できます。する場合は、複数の基準をいくつかはパブリックにすることができます、いくつかプライベート。
    
- [を設定し、SharePoint のオンライン管理シェルを使用して Office 365 の CDN を構成する](use-office-365-cdn-with-spo.md#CDNSetupinPShell)です。この手順を完了する場合があります。
    
  - 組織の CDN を有効にします。
    
  - 元の場所を追加します。各パブリックまたはプライベートの原点を指定します。
    
1 回で時間の経過と共に[管理 Office 365 の CDN](use-office-365-cdn-with-spo.md#CDNManage)のセットアップが終了しました。 
  
- 追加、更新、および資産を削除します。
    
- 追加して、元の場所を削除します。
    
- CDN のポリシーを構成します。
    
- 必要に応じて、Office 365 の CDN を無効にします。
    
## <a name="determine-where-you-want-to-store-your-assets"></a>お客様の資産を格納する場所を決定します。

CDN では、基準点と呼ばれる場所からお客様の資産を取得します。Office 365 では、オリジナルの SharePoint ライブラリまたはフォルダーの URL でアクセスできます。組織の原点を指定するときに、高い柔軟性があります。たとえば、複数の原点、または、CDN のすべての資産を格納する 1 つの原点を指定できます。組織のパブリックまたはプライベートの両方の基準を選択できます。ほとんどの組織では、2 つの組み合わせを実装するために選択します。
  
何百もの原点を定義する場合可能性があります要求の処理にかかる時間に悪影響を与える可能性があります。約 100 社以上の原点がある場合は、アーキテクチャを見直すことをお勧めします。
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a>各原点がパブリックまたはプライベートにするかどうかを選択します。

基準点を指定するかどうかに行う必要がありますパブリックまたはプライベートを指定します。どちらのオプションを選択する、Microsoft はすべての面倒を自体 CDN を管理する際に。変更できますは、後で、CDN を設定し、元の場所を識別した後。
  
パブリックとプライベートの両方のオプションは、パフォーマンスの向上を提供ですが、それぞれ固有の属性との利点です。
  
 **属性と公開元の資産をホストしている場合の利点**
  
- 公開元に公開されている資産は、匿名でアクセスが可能です。
    
    > [!IMPORTANT]
    > CDN の公開元を識別する場合は、パブリックの原点または SharePoint Online ライブラリで、組織に機密性の高いと見なされているリソースを配置しないでください。 
  
- パブリックの原点からアセットを削除する場合、資産可能性がありますのままになって使用可能な最大 30 日間キャッシュからただし、15 分以内、CDN のアセットへのリンクを無効にはなります。
    
- 公開元のスタイル シート (CSS ファイル) をホストする場合は、コード内での相対パスと Uri を使用できます。つまり、背景イメージおよびその他のオブジェクトを呼び出すことは、資産の場所の場所を参照することができます。
    
- パブリック送信元の URL をハード コードすることができます、そのためはお勧めできません。この理由は、CDN へのアクセスができなくなった場合、URL に組織は、SharePoint Online で自動的に解決されませんで切断されたリンクやその他のエラーが発生する可能性があります。
    
- 公開元の場所に含まれている既定のファイルの種類は、.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf、および .woff です。追加ファイルの種類を指定できます。
    
- する場合は、指定したサイトの分類で特定されている資産を除外するポリシーを構成できます。など、許可されているファイルの種類には、パブリックの原点である場合でも、「社外秘」や「制限された」としてマークされているすべての資産を除外することができます。
    
 **属性とプライベートの元の資産をホストしている場合の利点**
  
- ユーザーからのみアクセスできます資産秘密の原点を行うために承認されている場合。これらの資産への匿名アクセスを禁止します。
    
- 資産をキャッシュから 1 時間を使用する続行可能性がありますプライベートの原点からアセットを削除する場合ただし、15 分以内、CDN のアセットへのリンクを無効にはなります。
    
- 秘密の原点に含まれている既定のファイルの種類は、.gif、.ico、.jpeg、.jpg、.js、および .png です。追加ファイルの種類を指定できます。
    
- 公開元の場所と同じように、フォルダーまたはサイトのライブラリ内のすべての資産を含むようにワイルドカードを使用する場合でも、指定したサイトの分類で特定されている資産を除外するポリシーを構成できます。
    
## <a name="default-office-365-cdn-origins"></a>既定の Office 365 の CDN の原点

指定しない限り、Office 365 をいくつかのデフォルトの原点の設定を Office 365 の CDN を有効にするとします。最初に除外する場合は、セットアップを完了した後これらの基準を追加できます。
  
プライベート原点の既定値:
  
- \*/userphoto.aspx
    
- \*/siteassets
    
公開元の既定値:
  
- \*/masterpage
    
- \*/style ライブラリ
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>設定し、SharePoint のオンライン管理シェルを使用して Office 365 の CDN を構成します。

このトピックの手順では、SharePoint のオンライン管理シェルを使用して SharePoint Online に接続する必要があります。手順については、 [SharePoint のオンライン PowerShell への接続](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)を参照してください。
  
設定し、SharePoint Online での静的なアセットをホストするのには Office 365 の CDN を構成する手順を完了します。
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a>Office 365 の CDN を使用する組織を有効にするには

**セット SPOTenantCdnEnabled**コマンドレットを使用して、Office 365 の CDN を使用する組織を有効にします。元のパブリック、プライベートの原点またはその、CDN の両方を使用する組織を有効にできます。有効にすると、元の既定の設定をスキップするのには Office 365 の CDN を構成することもできます。これらの原点はこのトピックで説明したように、後でいつでも追加できます。 
  
で SharePoint のオンラインの Windows Powershell:
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

など、CDN で元のパブリックとプライベートの両方を使用する組織を有効にするには、次のコマンドを入力します。
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

パブリックとプライベートの両方の基準を使用して、CDN では、元の既定の設定を省略して、組織を有効にするには、次のコマンドを入力します。
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

CDN とパブリックの原点を使用する組織を有効にするには、次のコマンドを入力します。
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

CDN とプライベートの原点を使用する組織を有効にするには、次のコマンドを入力します。
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

このコマンドレットの詳細については、[一連の SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)を参照してください。
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a>(省略可能)Office 365 の CDN に含めるファイルの種類の一覧を変更するのには
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> **セット SPOTenantCdnPolicy**コマンドレットを使用してファイルの種類を定義するときは、現在定義されているリストを上書きします。追加ファイルの種類を一覧に追加する場合は、最初にどのようなファイルの種類が既に許可されて、およびと、新規のリストに含めますコマンドレットを使用します。 
  
**セット SPOTenantCdnPolicy**コマンドレットを使用すると、CDN のパブリックおよびプライベートの原点でホストできる静的ファイルの種類を定義します。既定では、例の .css、.gif、.jpg、および .js の共通の資産の型が使用できます。 
  
で SharePoint のオンラインの Windows PowerShell:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

ファイルの種類は、現在許可されている、CDN でを表示するには、 **Get SPOTenantCdnPolicies**コマンドレットを使用します。 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

これらのコマンドレットの詳細については、[一連の SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)と[Get SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)を参照してください。
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>(省略可能)Office 365 の CDN から除外したいサイトの分類の一覧を変更するのには
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> **セット SPOTenantCdnPolicy**コマンドレットを使用してサイトの分類を除外するとは、現在定義されているリストを上書きします。その他のサイトの分類を除外する場合は、最初にどのような分類が既に除外されていることを確認し、追加、新しいものとコマンドレットを使用します。 
  
CDN を介して利用できるようにするのに必要がないサイトの分類を除外するのには、**セット SPOTenantCdnPolicy**コマンドレットを使用します。既定では、サイトの分類は除外されません。 
  
で SharePoint のオンラインの Windows PowerShell:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

どのようなサイトの分類は現在の制限を表示するには、 **Get SPOTenantCdnPolicies**コマンドレットを使用します。 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

これらのコマンドレットの詳細については、[一連の SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)と[Get SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)を参照してください。
  
### <a name="to-add-an-origin-for-your-assets"></a>資産の基準点を追加するのには
<a name="Office365CDNforSPOOrigin"> </a>

**追加 SPOTenantCdnOrigin**コマンドレットを使用すると、基準点を定義します。複数の基準を定義できます。原点は、SharePoint ライブラリまたは、CDN でホストされるように使用するアセットが含まれているフォルダーを指す URL です。 
  
> [!IMPORTANT]
> CDN の公開元を識別する場合は、パブリックの原点または SharePoint Online ライブラリで、組織に機密性の高いと見なされているリソースを配置しないでください。 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

パスには、資産が含まれるフォルダーへのパスです。相対パス以外のワイルドカードを使用できます。たとえば、masterpages フォルダーのすべてのサイトにすべての資産は、CDN 内のパブリックの原点としてするには、次のコマンドを入力します。
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

このコマンドとその構文の詳細については、[追加 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)を参照してください。
  
コマンドを実行すると、システムは、データ ・ センター内の構成を同期します。これは、15 分です。
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>例: SharePoint Online は、マスター ページとスタイル ライブラリのパブリックの原点を構成します。
<a name="ExamplePublicOrigin"> </a>

通常、これらの原点が設定されて既定で Office 365 の CDN の元の公開を有効にするとします。ただし、それらを手動で有効にする場合は、以下の手順を実行します。
  
- **追加 SPOTenantCdnOrigin**コマンドレットを使用すると、Office 365 の CDN 内の公開基準とスタイル ライブラリを定義します。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- **追加 SPOTenantCdnOrigin**コマンドレットを使用すると、Office 365 の CDN 内の公開基準とマスター ページを定義します。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- このコマンドとその構文の詳細については、[追加 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)を参照してください。
    
    コマンドを実行すると、システムは、データ ・ センター内の構成を同期します。これは、15 分です。
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>例: SharePoint online サイトの資産、サイト ページ、および発行イメージの秘密の原点を構成します。
<a name="ExamplePrivateOrigin"> </a>

- **追加 SPOTenantCdnOrigin**コマンドレットを使用すると、Office 365 の CDN 内の秘密の原点としてサイトの assets フォルダーを定義します。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- **追加 SPOTenantCdnOrigin**コマンドレットを使用すると、Office 365 の CDN 内の秘密の原点としてのサイトのページのフォルダーを定義します。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- **追加 SPOTenantCdnOrigin**コマンドレットを使用すると、Office 365 の CDN 内の秘密の原点として公開の画像フォルダーを定義します。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    このコマンドとその構文の詳細については、[追加 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)を参照してください。
    
    コマンドを実行すると、システムは、データ ・ センター内の構成を同期します。これは、15 分です。
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>例: SharePoint online サイト コレクションの秘密の原点を構成します。
<a name="ExamplePrivateOriginSiteCollection"> </a>

**追加 SPOTenantCdnOrigin**コマンドレットを使用すると、Office 365 の CDN 内の秘密の原点としてサイト コレクションを定義します。例えば 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

このコマンドとその構文の詳細については、[追加 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)を参照してください。
  
コマンドを実行すると、システムは、データ ・ センター内の構成を同期します。これは、15 分です。
  
## <a name="manage-the-office-365-cdn"></a>Office 365 を管理する CDN
<a name="CDNManage"> </a>

CDN を設定すると変更できます、構成にコンテンツを更新するように変更したり、お客様のニーズ、このセクションで説明したようです。
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a>追加、更新、または Office 365 の CDN からアセットを削除するには
<a name="Office365CDNforSPOaddremoveasset"> </a>

セットアップ手順が完了したら、新しい資産を追加および更新したりするたびに、既存の資産を削除できます。同じフォルダーまたは基準点として指定した SharePoint ライブラリ内の資産に変更を加えます。新しい資産を追加する場合は、CDN を通じて使用可能なすぐにただし、資産を更新する場合は、かかるを伝達し、CDN で使用可能になる新しいコピーを最大で 15 分間です。
  
原点の位置を取得する必要がある場合、は、 **Get SPOTenantCdnOrigins**コマンドレットを使用することができます。このコマンドレットを使用する方法については、 [Get SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx)を参照してください。
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a>Office 365 の CDN からオリジナルを削除するのには
<a name="Office365CDNforSPORemoveOrigin"> </a>

必要がある場合、基準点として指定した SharePoint ライブラリまたはフォルダーへのアクセスを削除できます。これを行うには、**削除 SPOTenantCdnOrigin**コマンドレットを使用します。このコマンドレットを使用する方法については、[削除 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx)を参照してください。
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a>Office 365 の CDN で基準点を変更するのには
<a name="Office365CDNforSPORemoveOrigin"> </a>

作成したオリジナルを変更することはできません。代わりに、原点を削除し、新しいします。詳細については、 [Office 365 の CDN からオリジナルを削除して](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) [、資産の基準点を追加するのに](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)はを参照してください。
  
### <a name="to-disable-the-office-365-cdn"></a>Office 365 の CDN を無効にするには
<a name="Office365CDNforSPODisable"> </a>

**セット SPOTenantCdnEnabled**コマンドレットを使用して、組織の CDN を無効にします。両方パブリックとプライベートの原点、CDN を有効になっている場合は、次の例に示すように 2 回のコマンドレットを実行する必要があります。 
  
CDN、SharePoint online では、Windows Powershell での公開元の場所の使用を無効にするには、次のコマンドを入力します。
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

秘密の原点、CDN での使用を無効にするには、次のコマンドを入力します。
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

このコマンドレットの詳細については、[一連の SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)を参照してください。
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a>Office 365 の CDN の構成のトラブルシューティング
<a name="CDNManage"> </a>

エンドポイントはすぐにできませんには、CDN に登録するための時間がかかるようです。構成では、15 分かかります。
  

