---
title: 検出し、Office 365 で不正な同意の補助金の修正
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 4/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: 認識し、Office 365 の不法な同意の補助金攻撃に対処する方法を説明します。
ms.openlocfilehash: f6576fccd7cac49dbbf2e9ea359e08257ddc42d0
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-illicit-consent-grants-in-office-365"></a>検出し、Office 365 で不正な同意の補助金の修正

**概要** 認識し、Office 365 の不法な同意の補助金攻撃に対処する方法を説明します。

## <a name="what-is-the-illicit-consent-grant-attack-in-office-365"></a>Office 365 の不法な同意の補助金攻撃とは何ですか。
不法の同意攻撃者が電子メール、連絡先情報などのデータへのアクセスを要求するか、ドキュメントを Azure に登録されているアプリケーションを作成、攻撃を付与します。攻撃者は、フィッシング攻撃、または信頼できる web サイトに不正なコードを挿入することによってデータにアクセスするのにはそのアプリケーションの承認を付与するのに、エンド ・ ユーザー、テクニックです。不正なアプリケーションは、同意を付与されていたが、組織のアカウントを必要とせずにデータをアカウント レベルのアクセス権があります。これらのサードパーティ製アプリケーションであり、組織の外部にあるために、侵害のアカウントのパスワードをリセットするか、アカウントの多要素認証 (MFA) を必要とするのと同様に、通常の改善の手順はこの種の攻撃に対して効果的ではありません。これらの攻撃では、情報を呼び出しているエンティティは、自動化と人間ではありませんを開始するには相互作用モデルを活用します。

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-office-365"></a>Office 365 の不法な同意許可攻撃の外観がください。
Office 365 の**ログを監査**インジケーターの危険にさらされる (IOC) のこのような攻撃とも呼ばれる記号を検索する検索する必要があります。Azure に登録されている多くのアプリケーションおよび大規模なユーザー ベースを持つ組織では、週単位で、組織の同意の許可を確認するが得策。
### <a name="steps-for-finding-signs-of-this-attack"></a>この攻撃の兆候を検索する手順を実行します。
1. Office 365 テナント内の**セキュリティとコンプライアンスのセンター**を開きます。
2. **検索と調査**] ノードに移動し、**監査ログ**の検索を選択します。
3. 検索 (すべての活動およびすべてのユーザー) を作成し、同意をアプリケーションに結果をフィルター処理し、OAuth2PermissionGrant を追加します。
4. IsAdminContent が True に設定を表示するには、拡張プロパティとチェックを確認します。


この値が true の場合、グローバル管理者のアクセス権を持つユーザー可能性があります広範なアクセス権を与えデータことを示します。これが予想される場合は、[攻撃を確認](detect-and-remediate-illicit-consent-grants.md#confirmattack)する手順を実行します。

<a name="confirmattack"> </a>
## <a name="how-to-confirm-an-attack"></a>攻撃を確認する方法
行う必要があるか、上、IOCs の複数のインスタンスの一覧に、確実に攻撃が発生したことを確認する調査をさらにします。攻撃を確認するのにには、これら 3 つの方法のいずれかを使用します。
- アプリケーションおよび Active Directory の Azure ポータルを使用してアクセス許可のインベントリを作成します。この方法は徹底したが、確認する必要が 1 つのユーザー非常に時間がかかる可能性がある時に確認するのには多くのユーザーがいる場合。
- アプリケーションおよび PowerShell を使用してアクセス許可のインベントリを作成します。これは、最小限のオーバーヘッドで、最速かつ最も詳細なメソッドです。
- ユーザーのアプリケーションとアクセス許可を個別に確認し、改善のための管理者に結果が報告があります。

## <a name="inventory-apps-with-access-in-your-organization"></a>在庫アプリケーションでは、組織内のアクセス
Azure Active ディレクトリのポータルまたは PowerShell のいずれかをユーザーに適用したり、ユーザーにそのアプリケーションへのアクセスを個別に列挙できます。

### <a name="steps-for-using-the-azure-active-directory-portal"></a>Azure Active Directory のポータルを使用するための手順
個々 のユーザー権限を与えた[Azure Active Directory のポータル](https://portal.azure.com/)を使用してアプリケーションを検索できます。 
1. 管理者権限を使用して、Azure ポータルにサインインします。
2. Azure Active Directory のブレードを選択します。
3. **ユーザー**を選択します。
4. 確認するユーザーを選択します。
5. **アプリケーション**を選択します。

ユーザーに割り当てられているアプリケーションが表示されます、アプリケーションがアクセスを許可します。

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>そのアプリケーションへのアクセスを列挙する、ユーザーの手順を実行します。
移動ユーザーが、https://myapps.microsoft.comし、独自アプリケーションへのアクセスがあります。アクセス権を持つすべてのアプリケーションを参照してください (アクセスのスコープを含む) に関する詳細を表示することし、不審なまたは不正なアプリケーションに権限を取り消すことができる必要があります。

### <a name="steps-for-doing-this-with-powershell"></a>PowerShell でこれを行う手順を実行します。
同意の許可を不正な攻撃を確認する最も簡単な方法では、 [Get AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09)、ダンプすべての OAuth 同意の補助金およびすべてのユーザー用のアプリケーションのアクセス許可、テナントの 1 つの .csv ファイルにするを実行します。 

#### <a name="pre-requisites"></a>前提条件
- Azure AD PowerShell ライブラリがインストールされています。
- テナントに対して実行するスクリプトのグローバル管理者の権限。
- 元のコンピューターのローカル管理者アカウントは、スクリプトで実行されます。

> [!IMPORTANT]
> 管理者アカウントには、多要素認証を要求することを強くお勧めします。 このスクリプトには、MFA の認証がサポートされています。

1. ローカルの管理者権限を持つからスクリプトを実行しているコンピューターにサインインします。
2. ダウンロードまたは GitHub から[Get AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09)スクリプトを scruipt を実行するフォルダーにコピーします。 出力の"permissions.csv"ファイルの書き込み先の同じフォルダーになります。
3. 管理者として PowerShell のインスタンスを開き、スクリプトを保存するフォルダーを開きます。
4. [接続 AzureAD](https://docs.microsoft.com/en-us/powershell/module/azuread/connect-azuread?view=azureadps-2.0)コマンドレットを使用して、ディレクトリに接続します。
5. この PowerShell コマンド ・ ラインを次のように実行します。`.Get-AzureASPSPermissions.ps1 | Export-csv -path "Permissions.csv" -NoTypeInformation`

スクリプトには、Permissions.csv という名前の 1 つのファイルが生成されます。不正なアプリケーションのアクセス許可の付与を検索する手順に従います。 
1. [ConsentType] 列 (列 G) には、"AllPrinciples"の値を検索します。AllPrincipals 許可では、借用地のすべてのユーザーのコンテンツにアクセスするクライアント アプリケーションを使用します。ネイティブの Office 365 アプリケーションでは、このアクセス許可を正常に動作する必要があります。すべて Microsoft 以外のアプリケーションにこのアクセス許可を慎重に検討する必要があります。
2.  アクセス許可の列 (列 F) レビュー コンテンツにアプリケーションを委任する各アクセス許可を持っています。「読み取り」および「書き込み」アクセス許可の確認、または"*。"すべてのアクセス許可、およびこれら慎重になる場合がありますので適切なレビューです。
3.  同意を得て許可を持つ特定のユーザーを確認します。高プロファイルまたはユーザーの高レベルの影響には不適切な同意を得て許可がある場合は、さらに調査する必要があります。
4.  [ClientDisplayName] 列 (列 C) には、疑わしいと思われるアプリケーションを探します。名のスペルが間違っている、スーパー ブランド名、または発音のハッカーの名前を持つアプリケーションを慎重に検討する必要があります。

## <a name="determine-the-scope-of-the-attack"></a>攻撃の範囲を決定します。
アプリケーションへのアクセスをインベントリが完了したら後、は、Office 365 の**監査ログ**、違反の完全なスコープを決定するを確認します。 検索組織、およびアプリケーションのアクセス許可を影響を受けるユーザーに不正なアプリケーションがあったタイム フレームにアクセスします。で[Office 365 のセキュリティとコンプライアンス ・ センター](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)の**監査ログ**を検索できます。 

> [!IMPORTANT]
> [メールボックスの監査](https://support.office.com/en-us/article/Enable-mailbox-auditing-in-Office-365-aaca8987-5b62-458b-9882-c28476a66918)と[管理者グループおよびユーザーの活動の監査](https://support.office.com/en-us/article/turn-office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014)する必要がありますが有効になって攻撃すると、この情報を取得する前にします。

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant--attack"></a>停止し、不正な同意付与攻撃を改善する方法
不正なアクセス許可を持つアプリケーションを見つけた場合は、そのアクセス権を削除するのにはいくつかの方法があります。
- Azure Active ディレクトリ ポータル内のアプリケーションのアクセス許可を失効にすることができます。
    - **Azure Active Directory のユーザー**のブレードで影響を受けるユーザーに移動します。
    - **アプリケーション**を選択します。
    - 不正なアプリケーションを選択します。
    - **削除**] をクリックしてで、ドリル ダウンします。
- [削除 AzureADOAuth2PermissionGrant](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant?view=azureadps-2.0)の手順に従って、PowerShell で OAuth 同意の許可を取り消すことができます。
- [削除 AzureADServiceAppRoleAssignment](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment?view=azureadps-2.0)の手順に従って、PowerShell でのサービス アプリケーション ロールの割り当てを取り消すことができます。
- サインイン用にそのアカウントのデータへのアクセスをアプリケーションが無効になりますが、影響を受けるアカウント全体を無効にできます。もちろん、これは、エンド ・ ユーザーの生産性に最適ですへの影響を簡単に制限する場合は、実行可能な短期的な改善となります。
- テナントの統合されたアプリケーションを無効にできます。これは、テナント単位での承認を付与するエンド ・ ユーザー向けの機能を無効にする非常に重大なステップです。これは、ユーザーが誤って悪意のあるアプリケーションへのアクセス権を付与することを防ぎます。サード パーティ製アプリケーションと生産性を向上する、ユーザーの機能が損なわれ深刻なように強くお勧めしません。 [オンまたはオフは、[統合されたアプリケーションにすること](https://support.office.com/en-us/article/Turning-Integrated-Apps-on-or-off-7e453a40-66df-44ab-92a1-96786cb7fb34)で手順を実行して、これを行うことができます。

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>Pro の cybersecurity のように Office 365 をセキュリティで保護します。
Office 365 サブスクリプションのデータとユーザーを保護するために使用できるセキュリティ機能の強力なセットが付属します。 使用、 [Office 365 のセキュリティ ロードマップ: 最初の 30 日、90 日間での内外の優先順位のトップ](https://support.office.com/en-us/article/office-365-security-roadmap-top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352)マイクロソフトが推奨する、Office 365 テナントのセキュリティに関するベスト プラクティスを実装します。
- 最初の 30 日以内に実行するタスクです。 即座に影響があり、影響の少ないのはこれらのユーザーにします。
- 90 日以内に実行するタスクです。これらにより、計画し実装しますが、セキュリティ体制を大幅に改善するに少し時間がかかります。
- 90 日が経過します。これらの拡張機能は、最初の 90 日間の作業でビルドします。

## <a name="see-also"></a>参照してください。
- [[アプリケーション] リストで予期しないアプリケーション](https://docs.microsoft.com/en-us/azure/active-directory/application-access-unexpected-application)が示す手順に従ってさまざまなアクションの後は、データへのアクセス権を持つ予期しないアプリケーションを実現することがあります。
- [Azure Active Directory と統合するアプリケーション] (https://docs.microsoft.com/en-us/azure/active-directory/active-directory-apps-permissions-consent)は、承認とアクセス許可の概要を説明します。 [承認フレームワークの概要](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#overview-of-the-consent-framework)のセクションに特に注意してください。
- [問題が自分のアプリケーションを開発](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-application-dev-development-content-map)すると、各種へのリンク関連の記事に同意するものが用意されています。
- [アプリケーションと Azure Active Directory (AD の Azure) でのサービス プリンシパル オブジェクト](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-application-objects)は、アプリケーション モデルの中核となるアプリケーションおよびサービスのプリンシパル オブジェクトの概要を提供します。
- [アプリケーションへのアクセス権の管理](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-managing-access-to-apps)は、管理者は、アプリケーションへのユーザー アクセスを管理する必要がある機能の概要です。