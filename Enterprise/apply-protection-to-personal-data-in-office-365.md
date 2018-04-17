---
title: Office 365 の個人データに保護を適用する
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
description: DLP ポリシーを使用して、Office 365 の個人データを保護する方法について説明します。
ms.openlocfilehash: 8753ffe2b051e18e0790fba14c7a063200a74758
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="apply-protection-to-personal-data-in-office-365"></a>Office 365 の個人データに保護を適用する

Office 365 の個人情報の保護にはデータ損失防止機能の使用が含まれます。Office 365 セキュリティ/コンプライアンス センターでデータ損失防止 (DLP) ポリシーを使用することにより、Office 365 全体で機密情報を識別、監視、および自動的に保護することができます。

このトピックでは、DLP を使用して、個人データを保護する方法について説明します。さらに、SharePoint ライブラリでのアクセス許可の設定やデバイス アクセス ポリシーの使用など、GDPR 準拠を実現するために使用できその他の保護機能もリストします。

## <a name="apply-protection-using-data-loss-prevention-in-office-365"></a>Office 365 のデータ損失防止を使用して保護を適用する

DLP では、次のことができます。

-   複数の場所にわたって機密情報を識別します。

-   機密情報を誤って共有することを防ぎます。

-   ユーザーがワークフローを中断せずに、コンプライアンスを準拠しつづける方法を学ぶよう支援します。

-   組織の DLP ポリシーと一致するコンテンツを示す DLP レポートを表示します。

詳しくは、「[データ損失防止ポリシーの概要](https://support.office.com/ja-JP/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)」を参照してください。

![データ損失防止ポリシーを作成するためのオプション](Media/Apply-protection-to-personal-data-in-Office-365-image1.png)

この図は、DLP ポリシーを作成するためのオプションを示しています。

-   適用する保護を選択します。保護には以下を含めることができます。

    -   ユーザーのポリシー ヒント

    -   管理者のメール レポート

    -   外部、内部、またはその両方で共有できないようにする

-   保護を適用する条件を選択します。この種類のコンテンツを含むドキュメントに保護を適用します。機密情報の種類やラベルを使用するポリシーを構成することができます。

### <a name="using-dlp-for-gdpr-compliance"></a>GDPR 準拠のための DLP の使用

Office 365 DLP の主な用途の 1 つは、Office 365 環境内の EU データ サブジェクトに関連する個人データを特定することです。Office 365 DLP は、SharePoint Online と OneDrive for Business で個人情報が保存されている場所や、ユーザーが個人情報を含むメールを送信した旨をコンプライアンス チームに通知することができます。さらに、EU 居住者に関連する個人情報を処理する場合、従業員にポリシー ヒントを提供します。

Office 365 DLP を使用した情報の保護レベルの 1 つは、環境内の EU 居住者のデータの保存場所や、従業員にその処理を許可する方法について教育し、意識を高めることです。多くの場合、この種類の情報へのアクセスを持つ従業員は日常の作業を実行するためにこのアクセスを必要としています。GDPR に準拠する DLP ポリシーの適用では、アクセスを制限する必要はありません。

ただし、GDPR の準拠には通常、法的事項と情報セキュリティの両方の観点から見た、組織に関するリスク ベースの評価、個人情報の種類と保存場所の識別、その情報を保存および処理する法的な理由があるかどうかの判断が含まれます。この評価に基づいて、組織を保護し、GDPR に準拠するためのポリシーを実装する場合、EU のデータ サブジェクトの個人情報が含まれているドキュメントへの従業員のアクセスを削除しなければならない場合があります。さらに保護が必要な場合には、追加の DLP 保護を構成できます。

次の表は、DLP を使用して保護を強化する 3 つの構成を表示しています。最初の構成である認識は出発点であり、GDPR の保護の最小レベルとして使用できます。

### <a name="example-protection-levels-that-can-be-configured-with-dlp-policies-and-used-for-gdpr-compliance"></a>DLP ポリシーを使用して構成し、GDPR 準拠に使用できる保護レベルの例

<table>
<thead>
<tr class="header">
<th align="left"><strong>保護レベル</strong></th>
<th align="left"><strong>EU のデータ サブジェクトに関連する個人情報が含まれるドキュメントの DLP 構成</strong></th>
<th align="left"><strong>メリットとリスク</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">認識</td>
<td align="left"><p>このデータが SharePoint Online と OneDrive for Business のドキュメントで検出されたときに、コンプライアンス チームにメール通知を送信します。</p>
<p>SharePoint と OneDrive for Business で従業員がこのデータを含むドキュメントにアクセスするときに、ポリシー ヒントをカスタマイズして表示します。</p>
<p>このデータが共有されているときは、それを検出して報告します。</p></td>
<td align="left"><p>このデータの保存場所に関するコンプライアンス チームおよび従業員の意識を向上させます。</p>
<p>このデータを含むドキュメントを処理するための企業ポリシーについて従業員に教育します。</p>
<p>従業員がこのデータを内部または外部で共有できなくなることはありません。</p>
<p>共有データの DLP レポートを確認し、保護を強化する必要があるかどうか決定できます。</p></td>
</tr>
<tr class="even">
<td align="left">外部共有を禁止する</td>
<td align="left"><p>外部ユーザーとそのコンテンツを共有している場合、SharePoint Online と OneDrive for Business でこのデータを含むドキュメントへのアクセスを制限します。</p>
<p>このデータを含むドキュメントが含まれるメールを外部の受信者に送信できないようにします。</p>
<p>このデータが共有されているときは、それを検出して報告します。</p></td>
<td align="left"><p>このデータの外部共有を禁止しますが、従業員はこのデータを内部的に使用することができます。</p>
<p>内部共有データの DLP レポートを確認し、この保護を強化する必要があるかどうか決定できます。</p></td>
</tr>
<tr class="odd">
<td align="left">内部共有および外部共有を禁止する</td>
<td align="left"><p>内部または外部でそのコンテンツを共有している場合、SharePoint Online と OneDrive for Business でこのデータを含むドキュメントへのアクセスを制限します。</p>
<p>このデータを含むメールを内部と外部両方の受信者に送信できないようにします。</p></td>
<td align="left"><p>このデータの内部共有および外部共有を禁止します。</p>
<p>従業員は、このデータの処理を必要とするタスクを完了できない場合があります。</p>
<p>内部または外部の共有データの DLP レポートを確認し、エンドユーザーのトレーニングを強化する必要があるかどうか決定できます。</p></td>
</tr>
</tbody>
</table>

注: 保護のレベルが上がるにつれて、情報にアクセスするユーザーの能力が場合によって低下する可能性があり、日常業務の生産性や能力に影響を及ぼす可能性があります。従業員に影響を与えるポリシーを実装することで保護レベルを上げることには、エンドユーザーのトレーニングを実施し、より安全な環境で生産性を維持するための新しいセキュリティ ポリシーと手順についてユーザーに教育することが関係しています。

### <a name="example-dlp-policy-for-gdpr--awareness"></a>GDPR 用の DLP ポリシーの例 - 認識 

名前: GDPR の対象となる個人データの認識。

説明: 従業員にポリシーのヒントを表示し、このデータが SharePoint Online と OneDrive for Business のドキュメントで検出されたときはコンプライアンス チームに通知し、このデータが組織外で共有されている場合にはそれを検出して報告します。

<table>
<thead>
<tr class="header">
<th align="left"><strong>コントロール</strong></th>
<th align="left"><strong>設定</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">保護する情報を選択する</td>
<td align="left">カスタム ポリシー テンプレートを選択します。</td>
</tr>
<tr class="even">
<td align="left">場所</td>
<td align="left">Office 365 のすべての場所</td>
</tr>
<tr class="odd">
<td align="left">含まれているコンテンツを検索する</td>
<td align="left">[編集] をクリックし、環境に合わせて設定したすべての機密情報の種類を追加します。</td>
</tr>
<tr class="even">
<td align="left">このコンテンツが共有されている場合に検出する</td>
<td align="left">このボックスをチェックし、[自分の所属組織外のユーザー] を選択します。</td>
</tr>
<tr class="odd">
<td align="left">コンテンツがポリシーの設定に一致する場合にユーザーに通知する</td>
<td align="left"><p>このボックスをチェックします ([ユーザーにポリシー ヒントを表示して電子メール通知を送信する])。</p>
<p>[ヒントとメールをカスタマイズする] をクリックし、環境に合わせてこれらを更新します。この記事の既定の通知 [<a href="https://support.office.com/en-us/article/Send-email-notifications-and-show-policy-tips-for-DLP-policies-87496bc5-9601-4473-8021-cb05c71369c1?ui=en-US&amp;rs=en-US&amp;ad=US">メール通知を送信し、DLP ポリシーのポリシー ヒントを表示する</a>] を参照してください。</p></td>
</tr>
<tr class="even">
<td align="left">特定の量の機密情報が同時に共有されている場合に検出します。</td>
<td align="left"><p>[共有コンテンツが含まれている場合に検出: 機密性タイプが同じ情報の最小インスタンス数] - これを 1 に設定します。</p>
<p>[インシデント レポートを電子メールで送信] - このボックスをチェックします。[レポートに含める内容とそれを受け取るユーザーを選択] をクリックします。コンプライアンス チームを必ず追加してください。</p>
<p>[コンテンツにアクセスしてポリシーを上書きするユーザーを制限する] - ユーザーが機密情報にアクセスするのを妨げることなくその情報に関する通知を受信するには、このチェック ボックスをクリアします。</p></td>
</tr>
</tbody>
</table>

すべての場所には次のものが含まれます。

-   SharePoint Online

-   OneDrive for Business アカウント

-   Exchange メールボックス

コンテンツ検索では、電子メールで機密情報の種類をテストできないため、各ポリシーの機密情報タイプのサブセットと Exchange の個別ポリシーを作成し、これらのポリシーのロールアウトを監視することを検討してください。

## <a name="additional-protection-you-can-apply-to-protect-personal-data-in-office-365"></a>Office 365 の個人データの保護に適用できる追加の保護

機密情報の種類、ラベル、およびデータ損失保護ポリシーでは、特定のデータを含むドキュメントを特定し、保護を適用できます。ただし、これらの保護は、データへのアクセス用に設定されている適切なアクセス許可、侵害されていないアカウントを持つユーザー、および正常なデバイスに依存します。

次の図では、個人データへのアクセスを保護するために適用できる追加の保護について説明しています。

![個人データへのアクセスを保護するための追加の保護](Media/Apply-protection-to-personal-data-in-Office-365-image2.png)

次の表では、図での情報と同じものを見やすいように記載しています。

<table>
<thead>
<tr class="header">
<th align="left"><strong>保護の範囲</strong></th>
<th align="left"><strong>機能</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">ドキュメントと電子メール レベルの保護 (転送中のメールを含みますが、現在メールボックスに保存されているメールは含まない)</td>
<td align="left"><p>機密情報の種類</p>
<p>Office のラベル</p>
<p>データ損失防止ポリシー</p>
<p>電子メール用の Office 365 Message Encryption</p></td>
</tr>
<tr class="even">
<td align="left">サイトとライブラリ レベルの保護 (SharePoint Online と OneDrive for Business サイトを含む)</td>
<td align="left"><p>SharePoint と OneDrive for Business のサイトとライブラリに関するアクセス許可</p>
<p>SharePoint Online と OneDrive for Business に関する外部共有ポリシー (サイト レベル)</p>
<p>サイトレベルのデバイス アクセス ポリシー</p></td>
</tr>
<tr class="odd">
<td align="left">サービスのアクセス保護 (Office 365 のすべてのサービスへのアクセスを含む)</td>
<td align="left"><p>Enterprise Mobility + Security (EMS) スイートの ID およびデバイスのアクセス保護</p>
<p>特権アクセスの管理</p>
<p>Windows 10 のセキュリティ機能</p></td>
</tr>
</tbody>
</table>

この記事の残りの部分では、これらの各カテゴリの保護の詳細について説明します。

### <a name="capabilities-that-are-ok-to-use-with-gdpr"></a>GDPR で使用できる機能

GDPR 準拠用に構成された環境では、次の機能を使用できます。これらの機能には、GDPR 準拠に必ずしも必要ではありませんが、GDPR 準拠に関連するデータの検出、保護、監視、レポートの機能に悪影響を及ぼすことなく使用できます。

顧客キー - Office 365 内に保存されているデータを暗号化するために使用される暗号化キーを顧客に提供し、制御できるようにします。独自の暗号化キーを管理する規制上の必要がある顧客にのみ推奨されます。

カスタマー ロックボックス - カスタマー ロックボックスを使用すると、必要に応じて、Microsoft のサポート エンジニアが自分のデータにアクセスして、ケースごとに技術的な問題を解決する方法を制御できます。サポート エンジニアにデータへのアクセス権を付与するかどうかを制御できます。要求ごとに有効期限が指定されます。

## <a name="site-and-library-level-protection"></a>サイトおよびライブラリ レベルの保護

### <a name="permissions-for-sharepoint-and-onedrive-for-business-libraries"></a>SharePoint と OneDrive for Business のライブラリに関するアクセス許可

SharePoint のアクセス許可を使用して、サイトまたはそのコンテンツへのユーザーのアクセスを制限します。個々のユーザーまたは Azure Active Directory グループを既定の SharePoint グループに追加します。または、細かくコントロールするためにカスタム グループを作成します。

![フル コントロールから表示のみまでのアクセス許可レベル](Media/Apply-protection-to-personal-data-in-Office-365-image3.png)

この図は、フル コントロールから表示のみまでのアクセス許可レベルを示しています。次の表には、同じ情報が含まれています。

<table>
<thead>
<tr class="header">
<th align="left"><strong>フル コントロール</strong></th>
<th align="left"><strong>デザイン</strong></th>
<th align="left"><strong>編集</strong></th>
<th align="left"><strong>投稿</strong></th>
<th align="left"><strong>読み取り</strong></th>
<th align="left"><strong>表示のみ</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left">投稿 + 承認してカスタマイズする</td>
<td align="left">投稿 + リストを追加、編集、削除する (リスト アイテムだけでない)</td>
<td align="left">リスト アイテムおよびドキュメントを表示、追加、更新、削除する</td>
<td align="left">表示およびダウンロードする</td>
<td align="left">表示するが、ダウンロードしない</td>
</tr>
</tbody>
</table>

詳しくは、以下の資料を参照してください。

-   [SharePoint でのアクセス許可レベルについて](https://support.office.com/ja-JP/article/Understanding-permission-levels-in-SharePoint-87ecbb0e-6550-491a-8826-c075e4859848)

-   [SharePoint グループについて](https://support.office.com/ja-JP/article/Understanding-SharePoint-groups-94d9b261-161e-4ace-829e-eca1c8cd2eb8)

### <a name="external-sharing-policies-for-sharepoint-and-onedrive-for-business-libraries"></a>SharePoint と OneDrive for Business ライブラリに関する外部共有ポリシー

多くの組織では、コラボレーションをサポートする外部共有が許可されています。テナント全体の設定を構成する方法について説明します。さらに、個人データが含まれているサイトの外部共有設定を確認します。

外部ユーザーとは、SharePoint Online または Microsoft Office 365 サブスクリプションのライセンスはありませんが、SharePoint Online サイトやドキュメントにアクセスするように招待された組織外のユーザーです。

外部共有ポリシーは、SharePoint Online と OneDrive for Business の両方に適用されます。

-   共有ポリシーを構成するには、SharePoint Online 管理者でなければなりません。

-   サイトの所有者であるか、外部ユーザーとサイトまたはドキュメントを共有するフル コントロール アクセス許可を持っている必要があります。

次の表は、構成できるコントロールの要約を示しています。

<table>
<thead>
<tr class="header">
<th align="left"><strong>コントロールのカテゴリ</strong></th>
<th align="left"><strong>オプション</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">共有の種類</td>
<td align="left"><p>組織外の共有を許可しない (個別のサイト コレクションに対して設定できます)</p>
<p>認証された外部ユーザーにのみ共有を許可する (新規ユーザーを許可するか、または既存のユーザーに制限する。個別のサイト コレクションに対して設定できます)*</p>
<p>匿名アクセス リンクを持つ外部ユーザーに共有を許可する (個別のサイト コレクションに対して設定できます)</p>
<p>ドメインを使用して外部共有を制限する (許可および拒否の一覧)</p>
<p>既定のリンクの種類 (匿名、会社で共有可能、または制限) を選択します。</p>
</td>
</tr>
<tr class="even">
<td align="left">外部ユーザーが実行できる操作</td>
<td align="left"><p>外部ユーザーが自分の所有していないファイル、フォルダー、サイトを共有できないようにする</p>
<p>外部ユーザーに、招待の送信元と同じアカウントで招待の共有を承諾するように要求する</p></td>
</tr>
<tr class="odd">
<td align="left">通知</td>
<td align="left"><p>現在、OneDrive for Business でのみ使用できます。次の場合に所有者に通知します。</p>
- <p>ユーザーが追加の外部ユーザーを共有ファイルに招待する</p>
- <p>外部ユーザーがファイルへのアクセスの招待を承諾する</p>
- <p>匿名アクセス リンクが作成または変更される</p></td>
</tr>
</tbody>
</table>

詳しくは、以下の資料を参照してください。

-   
  [SharePoint Online 環境の外部共有を管理する](https://support.office.com/en-us/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&rs=en-US&ad=US)

-   [組織外部のユーザーとのサイトまたはドキュメントの共有](https://support.office.com/ja-JP/article/Share-sites-or-documents-with-people-outside-your-organization-80e49744-e30f-44db-8d51-16661b1d4232)

### <a name="site-level-device-access-policies"></a>サイトレベルのデバイス アクセス ポリシー

SharePoint Online と OneDrive for Business を使用して、サイト レベルでデバイス アクセス ポリシーを構成できます。これにより、機密データを含むサイトに対して追加の保護を構成できます。

サイト レベルのデバイス アクセス ポリシーを構成する場合は、必ずテナント レベルのポリシーと Azure Active Directory、Intune、Intune App Management で構成されているアクセス ポリシーと一緒に調整してください。

SharePoint と OneDrive for Business のデバイス アクセス ポリシーには、実装するシナリオによっては Azure Active Directory と Microsoft Intune でのサポート ポリシーが必要です。次の表は、デバイス アクセス ポリシーを使用して実行できる目標の要約を示し、サポート ポリシーが必要な製品を示します。

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">特定の IP アドレスの場所からのアクセスのみを許可する</th>
<th align="left">ドメインに参加していないデバイスにユーザーがファイルをダウンロードできないようにする</th>
<th align="left">ドメインに参加していないデバイスでのアクセスをブロックする</th>
<th align="left">ユーザーが非準拠デバイスにファイルをダウンロードできないようにする</th>
<th align="left">非準拠デバイスでのアクセスをブロックする</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">SharePoint 管理センター</td>
<td align="left">はい</td>
<td align="left">はい</td>
<td align="left">はい</td>
<td align="left">はい</td>
<td align="left">はい</td>
</tr>
<tr class="even">
<td align="left">Azure Active Directory</td>
<td align="left"></td>
<td align="left">はい</td>
<td align="left">はい</td>
<td align="left">はい</td>
<td align="left">はい</td>
</tr>
<tr class="odd">
<td align="left">Microsoft Intune</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left">はい</td>
<td align="left">はい</td>
</tr>
</tbody>
</table>

詳細: [SharePoint Online 管理センター: 非管理対象デバイスからのアクセスをコントロールします](https://support.office.com/en-us/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622?ui=en-US&rs=en-US&ad=US)。

## <a name="service-access-protection-for-identities-and-devices"></a>ID とデバイスのサービス アクセスの保護

サービスにアクセスする ID とデバイスの保護を構成することをお勧めします。Office 365 サービスへのアクセスを保護する作業は、他の SaaS サービス、PaaS サービス、さらには他のクラウド プロバイダーのアプリへのアクセスを保護するためにも使用できます。

ID とデバイスのアクセス保護は、ID が侵害されず、デバイスが安全で、デバイス上でアクセスされる組織データが分離され保護されるようにする保護のベースラインを提供します。

開始時の推奨事項と構成のガイダンスについては、「[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](https://docs.microsoft.com/ja-JP/microsoft-365-enterprise/microsoft-security-guidance)」を参照してください。

AD FS を使用するハイブリッド ID 環境については、「[推奨されるセキュリティ ポリシーと構成](https://docs.microsoft.com/ja-JP/microsoft-365-enterprise/microsoft-security-guidance)」を参照してください。

次の図は、クラウド サービス (SaaS、PaaS)、アカウントの種類 (テナント ドメイン アカウントと B2B アカウント)、およびサービス アクセス機能の関連について説明しています。どの機能を B2B アカウントで使用できるかを銘記することが重要です。

![クラウド サービス、アカウントの種類、およびアクセス機能](Media/Apply-protection-to-personal-data-in-Office-365-image4.png)

アクセシビリティのため、このセクションの残りの部分でこの図について説明します。

### <a name="cloud-services"></a>クラウド サービス

Azure Active Directory は、Amazon Web サービスなどの Microsoft 以外のプロバイダーを含む、任意のクラウド サービスへの ID アクセスを提供します。この図は、Office 365、「その他の SaaS アプリ」、および「PaaS アプリ」を示しています。Azure Active Directory からこれらの各サービスを指す矢印は、Azure Active Directory がこれらすべてのアプリの種類への認証に使用できることを示します。

### <a name="types-of-accounts"></a>アカウントの種類

テナント ドメイン アカウントは、テナントに追加して、直接管理するためのアカウントです。B2B アカウントは、共同作業に招待する組織外のユーザーのアカウントです。これには、他の Office 365 のアカウント、他の組織のアカウント、またはコンシューマー アカウント (Gmail など) があります。この図は、Azure Active Directory 内での両方のアカウントの種類を示します。

### <a name="capabilities"></a>機能

次の表にある機能は、ID およびデバイスを保護します。この表は、図にあるように B2B アカウントでも使用できる機能を示しています。

<table>
<thead>
<tr class="header">
<th align="left"><strong>機能</strong></th>
<th align="left"><strong>テナント ドメイン アカウントを処理する</strong></th>
<th align="left"><strong>Azure B2B アカウントを処理する (追加ライセンスを使用しない)</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">多要素認証および条件付きアクセス</td>
<td align="left">はい</td>
<td align="left">はい</td>
</tr>
<tr class="even">
<td align="left">Azure AD Identity Protection</td>
<td align="left">はい</td>
<td align="left">はい</td>
</tr>
<tr class="odd">
<td align="left">Azure AD Privileged Identity Management</td>
<td align="left">はい</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">モバイル アプリケーション管理 (MAM)</td>
<td align="left">はい</td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left">デバイスの登録と管理</td>
<td align="left">はい</td>
<td align="left">1 つの組織のみがデバイスを管理できる</td>
</tr>
<tr class="even">
<td align="left">Windows 10 のセキュリティ機能 (デバイスの準拠に基づく条件付きアクセスにはデバイスの管理が必要です)</td>
<td align="left">はい</td>
<td align="left">はい</td>
</tr>
</tbody>
</table>

B2B アカウントにライセンスを追加すると、必要に応じてこれらのユーザーに追加の機能を提供して、ご使用の環境内で個人データへのアクセスを保護できます。
