---
title: SharePoint Server 2007 のサポート終了ロードマップ
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1.keywords:
- CSH
ms.custom:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: On October 10, 2017, support ended for SharePoint Server 2007. Read this article to learn about your upgrade options, troubleshooting, best practices, system requirements, upgrade steps, and how to get assistance from Microsoft Partners.
ms.openlocfilehash: 561619559fd43131518a0032d3b28dc556f2d8b0
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996531"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>SharePoint Server 2007 のサポート終了ロードマップ

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

**2017 年10月 10**日に、Microsoft Office SharePoint Server 2007 はサポート終了になりました。 SharePoint Server 2007 から Microsoft 365 またはオンプレミスの SharePoint Server の新しいバージョンへの移行を開始していない場合は、計画を開始する時期になります。 この記事では、ユーザーがデータを SharePoint Online に移行したり、オンプレミスの SharePoint Server をアップグレードしたりするのに役立つリソースについて説明します。 
  
## <a name="what-does-end-of-support-mean"></a>サポートが終了するとどうなるのか

SharePoint Server, like almost all Microsoft products, has a support lifecycle during which Microsoft provides new features, bug fixes, security fixes, and so on. This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support. At end of support, Microsoft no longer provides:
  
- 発生する可能性のある問題のテクニカル サポート。
    
- サーバーの安定性と運用に影響を与える可能性のある問題が検出された場合のバグ修正プログラム。
    
- セキュリティ違反に対するサーバーの精度を低下させるような脆弱性が検出された場合のセキュリティ修正プログラム。 
    
- タイム ゾーンの更新。
    
Though your SharePoint Server 2007 farm will still be operational after October 10, 2017, no further updates, patches, or fixes will be shipped for the product (including security patches/fixes), and Microsoft Support will have fully shifted its support efforts to more recent versions of the product. Because your installation will no longer supported or patched, as end of support approaches you should upgrade the product, or migrate important data.
  
> [!TIP]
> アップグレードまたは移行を計画していない場合は、「 [SharePoint 2007 移行オプション](sharepoint-2007-migration-options.md)」を参照してください。その例については、以下を参照してください。 また、アップグレードまたは Microsoft 365 の移行 (またはその両方) を支援する[Microsoft パートナー](https://go.microsoft.com/fwlink/?linkid=841249)を検索することもできます。 
  
Office 2007 サーバーのサポート終了の詳細については、「[Office 2007 のサーバーとクライアントからのアップグレードに役立つリソース](upgrade-from-office-2007-servers-and-products.md)」を参照してください。
  
## <a name="what-are-my-options"></a>使用できるオプション

Your first stop should be the [Product Lifecycle site](https://go.microsoft.com/fwlink/?linkid=843148). If you have an on-premises Microsoft product that is aging, you should check for its end of support date so that, a year or so out - or as long as your migrations generally require - you can schedule upgrade or migrations. When choosing the next step, it might help to think in terms of what would be good enough, better, and best when it comes to product features. Here's an example:
  
|**標準**|**良い**|**最良**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint ハイブリッド  <br/> |SharePoint Server 2016  <br/> |
|||SharePoint ハイブリッド  <br/> |
   
If you choose options on the low end of the scale (good enough), remember you will need to begin planning for upgrade very soon after migration from SharePoint Server 2007 is complete. (end of support for SharePoint Server 2007 is October 10, 2017. Please note that these dates are subject to change and check the [Product Lifecycle site](https://support.microsoft.com/lifecycle).)
  
## <a name="where-can-i-go-next"></a>次に行う操作

SharePoint Server は、社内のサーバーにインストールできます。または、Microsoft 365 の一部であるオンラインサービスである SharePoint Online を使用することもできます。 次のいずれかを選択できます。
  
- SharePoint Online への移行
    
- オンプレミスの SharePoint Server のアップグレード
    
- 上記の両方の実施
    
- [SharePoint ハイブリッド](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) ソリューションの実装 
    
Be aware of hidden costs associated with maintaining a server farm going forward, maintaining or migrating customizations, and upgrading the hardware upon which SharePoint Server depends. Having an on-premises SharePoint Server farm is rewarding if it is a necessity; otherwise, if you run your farm on legacy SharePoint Servers, without heavy customization, you can benefit from a planned migration to SharePoint Online.
  
> [!IMPORTANT]
> SharePoint 2007 のコンテンツがあまり使用されない場合は、もう1つのオプションがあります。 一部の SharePoint 管理者は、Microsoft 365 サブスクリプションを作成し、新しい SharePoint Online サイトをセットアップした後、SharePoint 2007 から削除して、最新の SharePoint Online サイトに対して最も重要なドキュメントのみを削除することができます。 そのため、SharePoint 2007 サイトからアーカイブにデータをドレインすることができます。 ユーザーが SharePoint 2007 インストールのデータを操作する方法について検討します。 この問題を解決するには、クリエイティブな方法があります。 
  
|**SharePoint Online (SPO)**|**オンプレミスの SharePoint Server**|
|:-----|:-----|
|時間コストが高い (計画 / 実行 / 確認)  <br/> |時間コストが高い (計画 / 実行 / 確認)  <br/> |
|資金コストが安い (ハードウェアの購入の必要なし)  <br/> |資金コストが高い (ハードウェア + 開発/管理者)  <br/> |
|一度の移行でのコスト  <br/> |将来繰り返される一度の移行でのコスト  <br/> |
|所有権および保守の費用合計が低い  <br/> |所有権および保守の費用合計が高い  <br/> |
   
Microsoft 365 に移行する場合、データを整理し、クラウドに何を残すかを決定している間に、1回限りのコストが高くなります。 ただし、その時点からアップグレードが自動で行われるため、ハードウェアおよびソフトウェアの更新プログラムを管理する必要がなくなります。また、ファームの稼働時間は、Microsoft サービスレベル契約 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) によって支えられます。
  
### <a name="migrate-to-sharepoint-online"></a>SharePoint Online への移行

関連するサービスの説明を確認して、SharePoint Online に必要なすべての機能が含まれていることを確認してください。 「 [Microsoft 365 および Office 365 サービスの説明」を](https://docs.microsoft.com/office365/servicedescriptions/office-365-service-descriptions-technet-library)参照してください。
  
There is no direct way to migrate from SharePoint 2007 to SharePoint Online; your move to SharePoint Online would be done manually. If you upgrade to SharePoint Server 2013 or SharePoint Server 2016, your move might also involve using the SharePoint Migration API (to migrate information into OneDrive for Business, for example).
  
|**オンラインの利点**|**オンラインの欠点**|
|:-----|:-----|
|Microsoft が SPO ハードウェアおよびすべてのハードウェアの管理を行う。  <br/> |オンプレミスの SharePoint Server で利用できる機能と、SPO で利用できる機能が異なる。  <br/> |
|サブスクリプションの全体管理者であると、SPO サイトに管理者を割り当てることができる。  <br/> |SharePoint Server オンプレミスのファーム管理者が使用できる一部のアクションは、Microsoft 365 の SharePoint 管理者の役割に含まれていないか、または必要ありません。  <br/> |
|Microsoft が、基になるハードウェアとソフトウェアに、パッチ、修正プログラム、更新プログラムを適用する。  <br/> |サービスの基となるファイル システムへのアクセスがないため、一部のカスタマイズが制限される。  <br/> |
|Microsoft が[サービス レベル契約](https://go.microsoft.com/fwlink/?linkid=843153)を発行し、サービス レベルの問題に迅速に対応する。  <br/> |バックアップと復元、その他の回復オプションは、SharePoint Online のサービスによって自動化される。バックアップは、使用されていない場合に上書きされる。  <br/> |
|セキュリティ テストとサーバーのパフォーマンス チューニングは、Microsoft によって、継続的なサービスとして実施される。  <br/> |ユーザー インターフェイスとその他の SharePoint 機能の変更はサービスによってインストールされ、オン/オフの切り替えが必要な場合がある。  <br/> |
|Microsoft 365 は、さまざまな業界標準を満たしています。 [microsoft コンプライアンスサービス](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |移行の際に [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) でできることが限られる。  <br/> アップグレードの多くは、手動か、[SharePoint Online と OneDrive 移行コンテンツ ロードマップ](https://go.microsoft.com/fwlink/?linkid=843184)に記載されている SPO 移行 API により実施される。  <br/> |
|Microsoft のサポート エンジニアもデータセンターの従業員も、ユーザーのサブスクリプションに対する無制限の管理アクセス権はない。  <br/> |新しいバージョンの SharePoint に対応するために、ハードウェア インフラストラクチャをアップグレードする必要がある場合や、アップグレードにセカンダリ ファームが必要な場合は、追加のコストがかかる可能性がある。  <br/> |
|パートナーが、SharePoint Online へのデータの移行を一度で行えるようにサポートできる。  <br/> ||
|オンライン製品に関しては、サービス全体における更新が自動的に行われる。機能は廃止になる可能性もあるが、サポート自体は継続する。  <br/> ||
   
新しい Microsoft 365 サイトを作成することを決定し、必要に応じてデータを手動で移行する場合は、 [microsoft 365 のオプション](https://www.microsoft.com/microsoft-365/)を参照してください。
  
### <a name="upgrade-sharepoint-server-on-premises"></a>オンプレミスの SharePoint Server のアップグレード

There is historically no way to skip versions in SharePoint Upgrades, at least not as of the release of SharePoint Server 2016. That means upgrades go serially:
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
To take the entire path from SharePoint 2007 to SharePoint Server 2016 will mean a significant investment of time and will involve a cost in terms of upgraded hardware (be aware that SQL servers must also be upgraded), software, and administration. Customizations will need to be upgraded or abandoned, according to the criticality of the feature.
  
> [!NOTE]
> It's possible to maintain your end-of-life SharePoint 2007 farm, install a SharePoint Server 2016 farm on new hardware (so the separate farms run side-by-side), and then plan and execute a manual migration of content (for downloading and re-uploading content, for example). Be aware of some of the gotchas of manual moves (such as moves of documents replacing the last modified account with the alias of the account doing the manual move), and the work that must be done ahead of time (such as recreating sites, sub-sites, permissions and list structures). Again, this is the time to consider what data you can move into storage, or no longer need, an action that can reduce the impact of migration.
  
Either way, clean your environment prior to upgrade. Be certain your existing farm is functional before you upgrade, and (for sure) before you decommission! 
  
以下の、**サポートされるアップグレード パスとサポート外のアップグレード パス**を確認してください。 
  
- [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
**カスタマイズ**を行っている場合は、移行パスの手順ごとにアップグレードの計画を立てることが重要となります。詳細は以下を参照してください。 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**オンプレミスの利点**|**オンプレミスの欠点**|
|:-----|:-----|
|サーバー ハードウェアからの、SharePoint ファームの機能すべての完全なコントロール。  <br/> |下記の破損と修理のすべてが貴社の責任になる (製品のサポートが終了していない場合は、有料の Microsoft サポートの利用が可能)。  <br/> |
|ハイブリッドの SharePoint Online サブスクリプションにオンプレミス ファームを接続するオプションを備えた、オンプレミスの SharePoint Server のフル機能一式。  <br/> |オンプレミスに管理される SharePoint Server のアップグレード、パッチ、セキュリティ修正プログラム、およびすべての保守。  <br/> |
|高度なカスタマイズのためのフル アクセス許可。  <br/> |[Microsoft コンプライアンスサービス](https://go.microsoft.com/fwlink/?linkid=843165)は、オンプレミスで手動で構成する必要があります。  <br/> |
|オンプレミスで実行される、セキュリティ テストとサーバーのパフォーマンス チューニング (自分でコントロール)。  <br/> |Microsoft 365 では、オンプレミスの SharePoint Server と相互運用できない SharePoint Online の機能を使用することができます  <br/> |
|パートナーが、SharePoint Server の次のバージョン (さらにその先も対象) へのデータ移行をサポートできる。  <br/> |SharePoint Server サイトでは、SharePoint Online で表示される [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) 証明書が自動的に使用されることはない。  <br/> |
|オンプレミスの SharePoint Server での、名前付け規則、バックアップと復元、その他の回復オプションの完全なコントロール。  <br/> |製品のライフサイクルによって、オンプレミスの SharePoint Server の機能が異なる。  <br/> |
   
### <a name="upgrade-resources"></a>アップグレードのリソース

ハードウェアとソフトウェアの要件を満たしていることを確認してから、サポートされているアップグレード方法に従って操作を行ってください。
  
- **ハードウェア/ソフトウェア要件**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **ソフトウェアの境界と制限**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **アップグレード プロセスの概要**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>SharePoint Online とオンプレミスの間で、SharePoint ハイブリッド ソリューションを作成する

If the answer to your migration needs is somewhere between the self-control offered by on-premises, and the lower cost of ownership offered by SharePoint Online, you can connect SharePoint Server 2013 or 2016 farms to SharePoint Online, through hybrids. [Learn about SharePoint hybrid solutions](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
ハイブリッド SharePoint Server ファームにメリットがあると判断した場合は、既存のハイブリッドの種類と、オンプレミスの SharePoint ファームと Microsoft 365 サブスクリプションとの間の接続を構成する方法について理解しておく必要があります。
  
[Microsoft コンプライアンスサービス](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |移行に関する[Fasttrack](https://www.microsoft.com/fasttrack/microsoft-365)のサポートは制限されています。  <br/> アップグレードの多くは、手動か、[SharePoint Online と OneDrive 移行コンテンツ ロードマップ](https://go.microsoft.com/fwlink/?linkid=843184)に記載されている SPO 移行 API により実施される。  <br/> | |Microsoft のサポートエンジニアやデータセンターの従業員は、サブスクリプションに対する無制限の管理者アクセス権を持ちません。  <br/> |新しいバージョンの SharePoint をサポートするようにハードウェアインフラストラクチャをアップグレードする必要がある場合や、アップグレードにセカンダリファームが必要な場合は、追加のコストがかかることがあります。  <br/> | |パートナーは、データを SharePoint Online に移行するための1回限りのジョブを支援できます。  <br/> |||オンライン製品は、サービスによって自動的に更新されますが、機能は廃止される可能性があります。ただし、サポートの終了が実際にはありません。  <br/> ||
   
新しい Microsoft 365 サイトを作成することを決定し、必要に応じてデータを手動で移行する場合は、 [microsoft 365 のオプション](https://www.microsoft.com/microsoft-365/)を参照してください。
  
### <a name="upgrade-sharepoint-server-on-premises"></a>オンプレミスの SharePoint Server のアップグレード

There is historically no way to skip versions in SharePoint Upgrades, at least not as of the release of SharePoint Server 2016. That means upgrades go serially:
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
To take the entire path from SharePoint 2007 to SharePoint Server 2016 will mean a significant investment of time and will involve a cost in terms of upgraded hardware (be aware that SQL servers must also be upgraded), software, and administration. Customizations will need to be upgraded or abandoned, according to the criticality of the feature.
  
> [!NOTE]
> It's possible to maintain your end-of-life SharePoint 2007 farm, install a SharePoint Server 2016 farm on new hardware (so the separate farms run side-by-side), and then plan and execute a manual migration of content (for downloading and re-uploading content, for example). Be aware of some of the gotchas of manual moves (such as moves of documents replacing the last modified account with the alias of the account doing the manual move), and the work that must be done ahead of time (such as recreating sites, sub-sites, permissions and list structures). Again, this is the time to consider what data you can move into storage, or no longer need, an action that can reduce the impact of migration.
  
Either way, clean your environment prior to upgrade. Be certain your existing farm is functional before you upgrade, and (for sure) before you decommission! 
  
以下の、**サポートされるアップグレード パスとサポート外のアップグレード パス**を確認してください。 
  
- [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
**カスタマイズ**を行っている場合は、移行パスの手順ごとにアップグレードの計画を立てることが重要となります。詳細は以下を参照してください。 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**オンプレミスの利点**|**オンプレミスの欠点**|
|:-----|:-----|
|サーバー ハードウェアからの、SharePoint ファームの機能すべての完全なコントロール。  <br/> |下記の破損と修理のすべてが貴社の責任になる (製品のサポートが終了していない場合は、有料の Microsoft サポートの利用が可能)。  <br/> |
|ハイブリッドの SharePoint Online サブスクリプションにオンプレミス ファームを接続するオプションを備えた、オンプレミスの SharePoint Server のフル機能一式。  <br/> |オンプレミスに管理される SharePoint Server のアップグレード、パッチ、セキュリティ修正プログラム、およびすべての保守。  <br/> |
|高度なカスタマイズのためのフル アクセス許可。  <br/> |[Microsoft コンプライアンスサービス](https://go.microsoft.com/fwlink/?linkid=843165)は、オンプレミスで手動で構成する必要があります。  <br/> |
|オンプレミスで実行される、セキュリティ テストとサーバーのパフォーマンス チューニング (自分でコントロール)。  <br/> |Microsoft 365 では、オンプレミスの SharePoint Server と相互運用できない SharePoint Online の機能を使用することができます  <br/> |
|パートナーが、SharePoint Server の次のバージョン (さらにその先も対象) へのデータ移行をサポートできる。  <br/> |SharePoint Server サイトでは、SharePoint Online で表示される [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) 証明書が自動的に使用されることはない。  <br/> |
|オンプレミスの SharePoint Server での、名前付け規則、バックアップと復元、その他の回復オプションの完全なコントロール。  <br/> |製品のライフサイクルによって、オンプレミスの SharePoint Server の機能が異なる。  <br/> |
   
### <a name="upgrade-resources"></a>アップグレードのリソース

ハードウェアとソフトウェアの要件を満たしていることを確認してから、サポートされているアップグレード方法に従って操作を行ってください。
  
- **ハードウェア/ソフトウェア要件**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **ソフトウェアの境界と制限**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **アップグレード プロセスの概要**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>SharePoint Online とオンプレミスの間で、SharePoint ハイブリッド ソリューションを作成する

If the answer to your migration needs is somewhere between the self-control offered by on-premises, and the lower cost of ownership offered by SharePoint Online, you can connect SharePoint Server 2013 or 2016 farms to SharePoint Online, through hybrids. [Learn about SharePoint hybrid solutions](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
ハイブリッド SharePoint Server ファームにメリットがあると判断した場合は、既存のハイブリッドの種類と、オンプレミスの SharePoint ファームと Microsoft 365 サブスクリプションとの間の接続を構成する方法について理解しておく必要があります。
  
これがどのように機能するかを確認する方法の1つは、Microsoft 365 開発/テスト環境を作成することです。これは、[テストラボガイド](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)を使用してセットアップできます。 試用版または購入済みの Microsoft 365 サブスクリプションを取得したら、SharePoint Online にサイトコレクション、web、およびドキュメントライブラリを作成して、データを移行できるようにします (手動で移行 API を使用するか、個人用サイトのコンテンツを OneDrive for Business に移行する場合は-ハイブリッドウィザードを経由します)。
  
> [!NOTE]
> なお、ハイブリッド オプションを使用するには、SharePoint Server 2007 ファームを SharePoint Server 2013 または SharePoint Server 2016 にオンプレミスでアップグレードする必要があります 
  
## <a name="related-topics"></a>関連項目

[アップグレードのトラブルシューティングおよび再開 (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[アップグレードの問題のトラブルシューティング (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[SharePoint 2013 でのデータベース アップグレードの問題のトラブルシューティング](https://go.microsoft.com/fwlink/?linkid=843195)
  
[アップグレードを支援する Microsoft パートナーの検索](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Office 2007 のサーバーとクライアントからのアップグレードに役立つリソース](upgrade-from-office-2007-servers-and-products.md)
  

