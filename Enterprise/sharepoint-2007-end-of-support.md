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
description: SharePoint Server 2007 のサポートは 2017 年 10 月 10 日に終了しました。アップグレード オプション、トラブルシューティング、ベスト プラクティス、システム要件、アップグレード手順、および Microsoft パートナーからサポートを受ける方法については、この記事をお読みください。
ms.openlocfilehash: 6f0bd60d1f1201750ae1f0e4cc1a001ab4ed2ef6
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844008"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>SharePoint Server 2007 のサポート終了ロードマップ

*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*

Microsoft Office SharePoint Server 2007 のサポートは **2017 年 10 月 10 日**に終了しました。SharePoint Server 2007 から Office 365 またはオンプレミスの新しいバージョンの SharePoint Server への移行を開始していない場合は、今すぐ移行を実施する必要があります。この記事では、ユーザーが SharePoint Online にデータを移行したり、オンプレミスの SharePoint Server をアップグレードしたりする際に役立つリソースについて詳しく説明します。 
  
## <a name="what-does-end-of-support-mean"></a>サポートが終了するとどうなるのか

ほとんどの Microsoft 製品と同様に、SharePoint Server にはサポート ライフサイクルがあり、該当期間内に Micosoft は新しい機能、バグ修正プログラム、セキュリティ修正プログラムなどを提供しています。このライフサイクルは通常、製品の最初のリリース日から 10 年間続きます。このライフサイクルが終わると、製品のサポートも終了となります。サポートが終了すると、以下のものが提供されなくなります。
  
- 発生する可能性のある問題のテクニカル サポート。
    
- サーバーの安定性と運用に影響を与える可能性のある問題が検出された場合のバグ修正プログラム。
    
- セキュリティ違反に対するサーバーの精度を低下させるような脆弱性が検出された場合のセキュリティ修正プログラム。 
    
- タイム ゾーンの更新。
    
2017 年 10 月 10 日以降も、SharePoint Server 2007 ファームは引き続き稼働しますが、製品の更新プログラム、パッチ、修正プログラム (セキュリティのパッチや修正プログラムも含む) のサポートは行われません。Microsoft サポートによるサポート対象も製品の最新バージョンに切り替わります。製品のサポートが終了すると、パッチなどのサポートの対象外となるため、製品をアップグレードするか、重要なデータを移行する必要があります。
  
> [!TIP]
> アップグレードまたは移行の計画をまだ行っていない場合は、「[考慮すべき SharePoint 2007 の移行オプション](sharepoint-2007-migration-options.md)」で、実施すべき作業の例を参照してください。アップグレードまたは Office 365 の移行 (あるいはその両方) を支援する [Microsoft パートナー](https://go.microsoft.com/fwlink/?linkid=841249)を検索することもできます。 
  
Office 2007 サーバーのサポート終了の詳細については、「[Office 2007 のサーバーとクライアントからのアップグレードに役立つリソース](upgrade-from-office-2007-servers-and-products.md)」を参照してください。
  
## <a name="what-are-my-options"></a>使用できるオプション

まず、[製品のライフサイクルのサイト](https://go.microsoft.com/fwlink/?linkid=843148)にアクセスします。オンプレミスの古い Microsoft 製品を使用している場合は、サポート終了日を確認する必要があります。そうすれば、1 年ほどでサポートが終わる、あるいは、一般的に移行が必要とされる限度などを考慮に入れて、アップグレードまたは移行のスケジュールを立てることができます。次の手順を選ぶときには、製品機能に関して段階的 (標準、良い、最良の 3 段階) に検討すると良いでしょう。以下に例を示します。
  
|**標準**|**良い**|**最良**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint ハイブリッド  <br/> |SharePoint Server 2016  <br/> |
|||SharePoint ハイブリッド  <br/> |
   
終了までの期間が短い (標準) オプションを選択した場合は、SharePoint Server 2007 からの移行が完了したらすぐにアップグレードの計画を立てる必要があります。(SharePoint Server 2007 のサポート終了日は 2017 年 10 月 10 日ですが、この日付は変更される可能性がありますので、[製品のライフサイクルのサイト](https://support.microsoft.com/lifecycle)を確認するようにしてください。)
  
## <a name="where-can-i-go-next"></a>次に行う操作

SharePoint Server は、オンプレミスの自分のサーバー上にインストールすることができます。あるいは、Microsoft Office 365 の一部を成すオンライン サービスである SharePoint Online を使用できます。以下を選択することができます。
  
- SharePoint Online への移行
    
- オンプレミスの SharePoint Server のアップグレード
    
- 上記の両方の実施
    
- [SharePoint ハイブリッド](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) ソリューションの実装 
    
サーバー ファームの管理、カスタマイズの保守や移行、および SharePoint Server が依存するハードウェアのアップグレードには、関連する潜在的コストが発生しますので、ご注意ください。オンプレミスの SharePoint Server ファームが必要な場合、このファームを使用することには価値があります。一方、大幅なカスタマイズをせずに、従来の SharePoint Server でファームを実行している場合は、SharePoint Online への計画的な移行から益を得ることができます。
  
> [!IMPORTANT]
> SharePoint 2007 のコンテンツを頻繁に使用しない場合は、別のオプションを使用できます。一部の SharePoint 管理者は、[Office 365 サブスクリプションを作成](https://go.microsoft.com/fwlink/?linkid=843152)し、新しい SharePoint Online サイトをセットアップすることを選択するかもしれません。新しい SharePoint Online サイトに必要なドキュメントのみが取り入れられた、完全に独立したサイトとなり、SharePoint 2007 からは切り離されます。そしてデータは、SharePoint 2007 サイトからアーカイブに排出することができます。SharePoint 2007 インストールでのデータの操作方法については、ユーザーが検討します。この問題を解決する創造的な方法が登場することでしょう。 
  
|**SharePoint Online (SPO)**|**オンプレミスの SharePoint Server**|
|:-----|:-----|
|時間コストが高い (計画 / 実行 / 確認)  <br/> |時間コストが高い (計画 / 実行 / 確認)  <br/> |
|資金コストが安い (ハードウェアの購入の必要なし)  <br/> |資金コストが高い (ハードウェア + 開発/管理者)  <br/> |
|一度の移行でのコスト  <br/> |将来繰り返される一度の移行でのコスト  <br/> |
|所有権および保守の費用合計が低い  <br/> |所有権および保守の費用合計が高い  <br/> |
   
Office 365 に移行する場合、データを整理して、クラウドに取り入れるべきものと残すべきものを決定しますが、一度の移行ではコストがかかります。ただし、移行の時点からアップグレードが自動的に行われるため、ハードウェアとソフトウェアの更新を管理する必要はなくなり、ファームの稼働時間は Microsoft サービス レベル契約 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) に基づいたものとなります。
  
### <a name="migrate-to-sharepoint-online"></a>SharePoint Online への移行

関連するサービスの説明を確認し、SharePoint Online に必要なすべての機能が備わっていることを確認してください。以下のリンクをクリックすると、Office 365 サービスのすべての説明を確認できます。
  
[Office 365 サービスの説明](https://go.microsoft.com/fwlink/?linkid=272060)
  
SharePoint 2007 から SharePoint Online に直接移行する方法はありません。SharePoint Online への移行は手動で行います。SharePoint Server 2013 または SharePoint Server 2016 にアップグレードする際には、SharePoint 移行 API の使用が必要になる場合があります (OneDrive for Business への情報の移行などのため)。
  
|**オンラインの利点**|**オンラインの欠点**|
|:-----|:-----|
|Microsoft が SPO ハードウェアおよびすべてのハードウェアの管理を行う。  <br/> |オンプレミスの SharePoint Server で利用できる機能と、SPO で利用できる機能が異なる。  <br/> |
|サブスクリプションの全体管理者であると、SPO サイトに管理者を割り当てることができる。  <br/> |オンプレミスの SharePoint Server のファーム管理者が使用できる操作の一部が、Office 365 の SharePoint 管理者ロールに含まれない (または必要ない)。  <br/> |
|Microsoft が、基になるハードウェアとソフトウェアに、パッチ、修正プログラム、更新プログラムを適用する。  <br/> |サービスの基となるファイル システムへのアクセスがないため、一部のカスタマイズが制限される。  <br/> |
|Microsoft が[サービス レベル契約](https://go.microsoft.com/fwlink/?linkid=843153)を発行し、サービス レベルの問題に迅速に対応する。  <br/> |バックアップと復元、その他の回復オプションは、SharePoint Online のサービスによって自動化される。バックアップは、使用されていない場合に上書きされる。  <br/> |
|セキュリティ テストとサーバーのパフォーマンス チューニングは、Microsoft によって、継続的なサービスとして実施される。  <br/> |ユーザー インターフェイスとその他の SharePoint 機能の変更はサービスによってインストールされ、オン/オフの切り替えが必要な場合がある。  <br/> |
|Office 365 が、[Office 365 のコンプライアンス](https://go.microsoft.com/fwlink/?linkid=843165)に記載されている多くの業界標準に対応している。  <br/> |移行の際に [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) でできることが限られる。  <br/> アップグレードの多くは、手動か、[SharePoint Online と OneDrive 移行コンテンツ ロードマップ](https://go.microsoft.com/fwlink/?linkid=843184)に記載されている SPO 移行 API により実施される。  <br/> |
|Microsoft のサポート エンジニアもデータセンターの従業員も、ユーザーのサブスクリプションに対する無制限の管理アクセス権はない。  <br/> |新しいバージョンの SharePoint に対応するために、ハードウェア インフラストラクチャをアップグレードする必要がある場合や、アップグレードにセカンダリ ファームが必要な場合は、追加のコストがかかる可能性がある。  <br/> |
|パートナーが、SharePoint Online へのデータの移行を一度で行えるようにサポートできる。  <br/> ||
|オンライン製品に関しては、サービス全体における更新が自動的に行われる。機能は廃止になる可能性もあるが、サポート自体は継続する。  <br/> ||
   
新しい Office 365 サイトを作成し、必要に応じてデータを手動で移行することにした場合は、以下の Office 365 のオプションを確認してください。
  
[Office 365 プランのオプション](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>オンプレミスの SharePoint Server のアップグレード

SharePoint のバージョンをスキップしてアップグレードする方法はありません。SharePoint Server 2016 のリリースの場合も同様です。アップグレードは以下のように順次に行われます。
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
SharePoint 2007 から SharePoint Server 2016 へのパス全体を取得するには、多くの時間を要します。また、アップグレードされたハードウェア (SQL サーバーもアップグレードする必要があります)、ソフトウェア、管理に関するコストも発生します。機能の重要度に応じて、カスタマイズをアップグレードしたり、カスタマイズした内容を破棄したりする必要があります。
  
> [!NOTE]
> サポートが終了した SharePoint 2007 ファームの使用を継続し、新しいハードウェアに SharePoint Server 2016 ファームをインストールして (ファームが共存している状態で別々に実行)、コンテンツの手動による移行 (コンテンツのダウンロードや再アップロードなど) を計画したり実行したりすることは可能です。ただし、手動による移動 (最後に変更されたアカウントを、手動で移動するアカウントのエイリアスに置き換えたドキュメントの移動など) に関する問題には注意を払う必要があり、サイト、サブサイト、アクセス許可、リスト構造の再構成などの作業は早めに行う必要があります。ストレージに移行するデータと、必要ないデータを区別し、どういった操作が移行による負担を軽減できるのかを今検討することが非常に重要です。
  
いずれにしても、アップグレードする前に環境を整えることが重要です。アップグレードする前に既存のファームが機能していることを確認してください。使用を停止するものについても、念のため確認してください。 
  
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
|高度なカスタマイズのためのフル アクセス許可。  <br/> |[Office 365 でサポートされるコンプライアンス基準](https://go.microsoft.com/fwlink/?linkid=843165)を、オンプレミスで手動で構成しなければならない。  <br/> |
|オンプレミスで実行される、セキュリティ テストとサーバーのパフォーマンス チューニング (自分でコントロール)。  <br/> |オンプレミスの SharePoint Server と相互運用しない SharePoint Online での機能が、Office 365 によって、有効になることがある  <br/> |
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

オンプレミスでの完全コントロールでの移行か、SharePoint Online の低コストの所有権による移行かを検討している場合、SharePoint Server 2013 のファームあるいは 2016 のファームをハイブリッドとして、SharePoint Online に接続できます。[SharePoint ハイブリッド ソリューションの詳細情報](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
ハイブリッドの SharePoint Server ファームをビジネスに活用することにした場合は、既存のハイブリッドの種類はもちろん、オンプレミスの SharePoint ファームと Office 365 サブスクリプションとの接続方法を理解することが重要です。
  
動作を確認するお勧めの方法の 1 つは、[Office 365 の開発/テスト環境](https://go.microsoft.com/fwlink/?linkid=843152)を作成することです。試用版や購入済みの Office 365 サブスクリプションがあれば、SharePoint Online でサイト コレクション、Web、ドキュメント ライブラリを作成し、データを移行できるようになります (手動で、移行 API を使用して、あるいは個人用サイトのコンテンツを OneDrive for Business に移行する場合は、ハイブリッド ウィザードで行うこともできます)。
  
> [!NOTE]
> なお、ハイブリッド オプションを使用するには、SharePoint Server 2007 ファームを SharePoint Server 2013 または SharePoint Server 2016 にオンプレミスでアップグレードする必要があります 
  
## <a name="related-topics"></a>関連項目

[アップグレードのトラブルシューティングおよび再開 (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[アップグレードの問題のトラブルシューティング (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[SharePoint 2013 でのデータベース アップグレードの問題のトラブルシューティング](https://go.microsoft.com/fwlink/?linkid=843195)
  
[アップグレードを支援する Microsoft パートナーの検索](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Office 2007 のサーバーとクライアントからのアップグレードに役立つリソース](upgrade-from-office-2007-servers-and-products.md)
  

