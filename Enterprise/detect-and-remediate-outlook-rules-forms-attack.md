---
title: 検出し、修復の Outlook の仕訳ルールとカスタム フォーム インジェクション攻撃の Office 365 の
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: 認識し、Office 365 のインジェクション攻撃をカスタム フォームと Outlook の仕訳ルールを修正する方法を学習します。
ms.openlocfilehash: d0f54a0dc47d7a3602a7b4ce57a04c83d15d9301
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks-in-office-365"></a>検出し、Outlook の仕訳ルールと Office 365 でユーザー設定フォームのインジェクション攻撃を修正

**概要**認識し、Outlook の仕訳ルールと Office 365 のユーザー設定のフォーム インジェクション攻撃に対処する方法を説明します。

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Outlook の仕訳ルールとユーザー設定フォームのインジェクション攻撃とは何ですか。
攻撃者は、テナントのアカウントが侵害される可能性取得後、あるしようとしてくださいし、連絡を取り合う方法、または、検出して削除した後バックアップを取得する方法を確立します。永続化メカニズムを確立することで、これが呼び出されます。これを行うことの 2 つの方法は、Outlook の仕訳ルールを利用することによって、または Outlook にカスタム フォームを挿入することによってです。どちらの場合も、ルールやフォームの同期をデスクトップのクライアントでは、クラウド サービスから注入機構を排除しない、完全なフォーマットとクライアント ソフトウェアを再インストールするようにします。Outlook クライアント ソフトウェアは、クラウド内のメールボックスに再接続するときに再ダウンロード ルールとクラウドのためです。規則とフォームがあると後、攻撃者はローカル コンピューターにマルウェアをインストールするには、通常、リモート、またはカスタムのコードを実行するのにそれらを使用します。マルウェアは、資格情報を盗んで再またはその他の不法な活動を実行します。良いニュースは、ここでは、最新バージョンに更新プログラムを適用、クライアントを保持する場合は、脅威に対する脆弱性が現在の Outlook クライアントの既定値は両方のメカニズムをブロックするようです。 

攻撃は、通常これらのパターンを次実行します。

この脆弱性の規則
1. 攻撃者は、ユーザー名とパスワード、ユーザーのいずれかを盗みます。
2. 攻撃者サインインすると、そのユーザーの Exchange メールボックスにします。メールボックス使用できる Exchange オンラインまたは Exchange で設置します。
3. 攻撃者は、メールボックスのメールボックスのルールの条件に一致する電子メールを受信するときにトリガーされる、転送ルールを作成します。ルールの条件とトリガーの電子メールの内容は、互いのテーラーメイド。
4. 攻撃者は、自分のメールボックスを通常使用しているユーザーにトリガーの電子メールを送信します。
5. 電子メールを受信すると、ルールがトリガーされます。ルールのアクションは、通常リモート (WebDAV) サーバー上でアプリケーションを起動します。
6. アプリケーション通常インストール マルウェア[Powershell 帝国](https://www.powershellempire.com/)、ローカル ユーザーのコンピューターでされます。
7. マルウェアにより、攻撃者がユーザーのユーザー名とパスワードまたはローカル コンピューターから、他の資格情報を盗み出し、再、その他の悪意のあるアクティビティを実行できます。

フォームの脆弱性に対する攻撃
1. 攻撃者は、ユーザー名とパスワード、ユーザーのいずれかを盗みます。
2. 攻撃者はし、そのユーザーの Exchange メールボックスにサインインします。メールボックス使用できる Exchange オンラインまたは Exchange で設置します。
3. 攻撃者は、ユーザー設定のメール フォーム テンプレートを作成し、ユーザーのメールボックス内に挿入します。 ユーザー設定フォームは、メールボックスがユーザー設定フォームをロードするのにはメールボックスを必要とする電子メールを受信するときにトリガーされます。ユーザー設定フォームおよび電子メールの形式は、互いのテーラーメイド。
4. 攻撃者は、ユーザーに、通常のメールボックスを使用して、トリガーの電子メールを送信します。
5. 電子メールが受信されると、フォームが読み込まれます。フォームでは、リモート (WebDAV) サーバー上のアプリケーションを起動します。
6. アプリケーション通常インストール マルウェア[Powershell 帝国](https://www.powershellempire.com/)、ローカル ユーザーのコンピューターでされます。
7. マルウェアにより、攻撃者がユーザーのユーザー名とパスワードまたはローカル コンピューターから、他の資格情報を盗み出し、再、その他の悪意のあるアクティビティを実行できます。


## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>どのような規則と、ユーザー設定フォームのインジェクション攻撃が Office 365 のようになりますでしょうか。

これらの永続化メカニズムは、ユーザーが意識することはありませんし、可能性がある場合に表示されませんをします。 この資料では、7 つの兆候 (状況説明マークの侵害) のいずれかを次の一覧を検索する方法を指示します。次のいずれかを検索する場合は、改善策を講じる必要があります。

- 妥協の規則の評価指標
    - ルールの処理では、アプリケーションを起動します。
    - ルールでは、EXE、郵便番号、または URL を参照します。
    - ローカルのマシンでは、新しいプロセスが起動し、Outlook の PID から発信されたを探します。
- カスタム フォームのセキュリティ侵害のインジケーター 
    - ユーザー設定フォームに存在、独自のメッセージ クラスとして保存します。
    - メッセージ クラスには、実行可能コードが含まれています。
    - 通常、個人用フォーム ライブラリまたは受信トレイ フォルダーに格納されます。
    - IPM フォームの名前です。注意してください。[カスタム名]。

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>この攻撃の兆候を見つけて、それを確認する手順を実行します。
攻撃を確認するのにには、これら 2 つの方法のいずれかを使用します。
- ルールおよび Outlook クライアントを使用する各メールボックス用のフォームを手動で確認します。 この方法は徹底したが、確認する必要があるユーザーのメールボックスに非常に時間がかかる可能性があるを確認するのには多くのユーザーがいる場合。 チェックを実行しているコンピューターの侵害にも増加します。
- テナントのルールと、すべてのユーザー用のユーザー設定フォームを転送するすべてのメールを自動的にダンプするのにには、 [Get AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell スクリプトを使用します。これは、最小限のオーバーヘッドで最速かつ最も安全な方法です。


### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>ルールの攻撃を使用して、Outlook クライアントを確認します。
1. ユーザーとして、ユーザーの Outlook クライアントを開きます。 ユーザーは、自分のメールボックスにルールを調べることで、ヘルプを必要があります。
2. 手順については、outlook 2007、2010 または 2013 のバージョンでルールのインターフェイスを開く方法の[管理の規則を使用してメッセージを電子メールで送信](https://support.office.com/en-us/article/manage-email-messages-by-using-rules-c24f5dea-9465-4df4-ad17-a50704d66c59#ID0EAABAAA=2010)の記事を参照してください。
3. ルール、ユーザーは作成していない、または予期しないルールや不審な名前を持つルールを検索します。
4. ルールの処理のルールの説明で検索を開始し、アプリケーションを参照してくださいまたは、します。実行可能ファイルをします。ZIP ファイルまたは URL を起動します。
5. Outlook のプロセス ID の使用を開始する新しいプロセスを探します [プロセス ID を検索](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/finding-the-process-id)するを参照してください。

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Outlook クライアントを使用してフォームの攻撃を確認する手順を実行します。
1. ユーザーとして、ユーザーの Outlook クライアントを開きます。
2. ユーザーのバージョンの Outlook で、 [[開発] タブを表示する](https://support.office.com/en-us/article/show-the-developer-tab-e1192344-5e56-4d45-931b-e5fd9bea2d45)手順に従います。
3. Outlook で表示されるようになりました [開発] タブを開くし、**フォームのデザイン**] をクリックします。
4. **[探す場所**] ボックスの一覧から **[受信トレイ]** を選択します。ユーザー設定フォームを検索します。 カスタム フォームは、珍しいこと、すべての任意のカスタム フォームがある場合は詳しく見て価値があります。
5. 非表示としてマークされたものでは特に、ユーザー設定フォームを調査します。
6. 任意のカスタム フォームを開くし、[**フォーム**] の [**コードの表示**、フォームが読み込まれたときの実行を参照してください] をクリックします。

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>PowerShell を使用する規則とフォームの攻撃を確認する手順を実行します。
規則を確認する最も簡単な方法か、ユーザー設定フォームの攻撃とは、 [Get AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell スクリプトを実行します。 このスクリプトでは、すべての規則のダンプしし、フォームの 2 つの .csv ファイルに、テナントのすべてのメールボックスに接続します。

#### <a name="pre-requisites"></a>前提条件
スクリプトは、ルールやフォームにテナントのすべてのメールボックスに接続するためにスクリプトを実行するのには、グローバル管理者権限を持っている必要があります。

1. ローカルの管理者権限を持つからスクリプトを実行しているコンピューターにサインインします。
2. ダウンロードまたは GitHub から Get AllTenantRulesAndForms.ps1 スクリプトを実行元となるフォルダーにコピーします。 スクリプトでは、このフォルダー、MailboxFormsExport 日の mm dd.csv、および MailboxRulesExport yyyy mm dd.csv の 2 つの日付のスタンプ ファイルを作成します。
3. 管理者として PowerShell のインスタンスを開き、スクリプトを保存するフォルダーを開きます。
4. この PowerShell コマンドラインの実行を次のように`.\Get-AllTenantRulesAndForms.ps1`.\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>出力を解釈します。

MailboxRulesExport-*年年年年-月月-日日*.csv – アプリケーションまたは実行可能ファイルが含まれるアクションの条件の (1 行につき 1 つ) の規則を確認します。
- ファイアウォール (列 A):"ID_ACTION_CUSTOM"、値が表示される場合、ルールは、可能性があります悪意のあります。
- IsPotentiallyMalicious (列 D) – ルールはこの値が TRUE の場合は、悪意のあります。
- ActionCommand (G 列) – アプリケーションまたは .exe や .zip 拡張子であることを想定していませんが、URL を参照するエントリを指定したファイルの一覧が表示このルール可能性が悪意のあります。

MailboxFormsExport-*年年年年-月月-日日*.csv – 一般に、ユーザー設定フォームの使用は非常にまれです。 このブックのいずれかの場合は、そのユーザーのメールボックスを開くし、フォーム自体を確認します。 可能性が場合は、組織は置いていない、意図的に、悪意のあります。



## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>停止し、Outlook の仕訳ルールとフォームの攻撃を改善する方法
対策としては、単純な場合は、これらの攻撃のいずれかの証拠がある場合、メールボックスからルールまたはフォームを削除します。Outlook クライアントまたはリモート PowerShell を使用してルールを削除すると、これを行うことができます。

### <a name="using-outlook"></a>Outlook を使用してください。
1. ユーザーが Outlook で使用されるすべてのデバイスを識別します。 すべてに必要な潜在的なマルウェアを除去します。 署名し、すべてのデバイスを削除するまで電子メールを使用するユーザーを許可しません。
2. デバイスごとに[ルールを削除する](https://support.office.com/en-us/article/Delete-a-rule-2F0E7139-F696-4422-8498-44846DB9067F)の手順に従います。
3. に関するその他のマルウェアの存在を確認できない場合は、書式を設定し、デバイス上のすべてのソフトウェアを再インストールできます。 モバイル デバイスの出荷時イメージにデバイスをリセットするのには製造元の手順はします。
4. 最新のバージョンの Outlook をインストールします。 Outlook の現在のバージョンが既定でこのような攻撃の両方の種類をブロックすることに注意してください。
5. メールボックスのすべてのオフライン コピーを削除するは、ユーザーのパスワード (いずれかの高品質を使用します) をリセットし、 [Office 365 のユーザーに対して多要素認証のセットアップ](https://support.office.com/en-us/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)の手順を MFA が既に有効になっていない場合。これにより、フィッシング詐欺やパスワードを再利用) などの他の手段を使用してユーザーの資格情報が公開されていません。

### <a name="using-powershell"></a>PowerShell を使用します。
2 つのリモート PowerShell コマンドレットを削除または危険なルールを無効にするを使用することがあります。手順だけです。
 
メールボックスを Exchange サーバー上の手順を実行します。

1. リモート PowerShell を使用して Exchange サーバーに接続します。[リモート PowerShell を使用して Exchange サーバーに接続する](https://docs.microsoft.com/en-us/powershell/exchange/exchange-server/connect-to-exchange-servers-using-remote-powershell?view=exchange-ps)の手順を実行します。
2. メールボックスを[削除-受信トレイ ルールのコマンドレット](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps)の 1 つのルール、複数の規則またはすべてのルールを完全に削除する場合は、メールボックスから、これが完全に削除、1 つ、複数またはすべてのルールを使用します。
3. ルールを保持する必要が、さらに調査のためには、その内容が[無効にする InboxRule コマンドレット](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx)を使用します。 

Exchange Online のメールボックスの手順を実行します。
1. [PowerShell を使用して Exchange Online への接続](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps)の手順を実行します。
2.  1 つのルールを完全に削除する場合は、複数のルール、またはメールボックスからすべてのルールは、[受信トレイの削除ルールのコマンドレット](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps)を使用します。
3.  ルールを保持する必要が、さらに調査のためには、その内容が[無効にする InboxRule コマンドレット](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx)を使用します。 

## <a name="how-to-minimize-future-attacks"></a>将来の攻撃を最小限に抑える方法

### <a name="first-protect-your-accounts"></a>: 最初に、アカウントを保護します。

規則とフォームの攻撃は、盗難またはユーザーのアカウントの 1 つが破られた攻撃者によってのみ使用されます。組織に対して、これらの脆弱性の使用を禁止するのには、まず積極的にユーザー アカウントを保護します。 アカウントが侵害されている最も一般的な方法をいくつか、フィッシング詐欺や[パスワードをかけ](http://www.dabcc.com/microsoft-defending-against-password-spray-attacks/)攻撃です。



ユーザー アカウント、および特に、管理者アカウントを保護する最善の方法は、 [Office 365 のユーザーに対して多要素認証を設定](https://support.office.com/en-us/article/set-up-multi-factor-authentication-for-office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)すること。 する必要があります。
<ol>
    <li>ユーザー アカウントが<a href="https://docs.microsoft.com/en-us/azure/active-directory/active-directory-view-access-usage-reports">アクセスし使用</a>方法を監視します。初期の違反をしないことがありますが、期間とセキュリティ侵害の影響をより早く検出することによって短縮されます。これらを使用することができます: アカウントおよび異常なアクティビティのアラートを監視するには、 <a href="https://support.office.com/en-us/article/overview-of-office-365-cloud-app-security-81f0ee9a-9645-45ab-ba56-de9cbccab475">Office 365 のクラウド アプリケーションのセキュリティ ポリシー</a>です。<ol type="a">
            <li><b>複数の失敗したログイン</b>このポリシーでは、ユーザーが学習した基準計画、実行しようとした、侵害の可能性について 1 つのセッションで複数のログイン失敗のアクティビティを実行するとき、環境とアラートのトリガーをプロファイルします。</li>
            <li><b>ない旅行</b>-このポリシーは、プロファイルをお客様の環境と同じユーザーに別の場所から 2 つの場所の間で予想される時間よりも短い時間内のアクティビティが検出されたときにアラートをトリガーします。別のユーザーが同じ資格情報を使用している可能性があります。この異常な動作を検出すると、初期の学習期間 7 日間の新しいユーザーの利用状況のパターンを学習するが必要です。</li>
            <li><b>不審なアクティビティのユーザーによって) を偽装します。</b>-このポリシーは、プロファイルをお客様の環境と、ユーザー アクティビティを実行複数偽装、ベースラインを基準の 1 つのセッションで実行しようとした、違反を示している可能性があるときに、アラートをトリガーします。</li>
        </ol>
    </li>
    <li>アカウントのセキュリティの構成と動作を管理するために<a href="https://securescore.office.com/">Office 365 のセキュリティで保護されたスコア</a>のようなツールを活用します。 
    </li>
</ol> 

### <a name="second-keep-your-outlook-clients-current"></a>2 番目: Outlook クライアントを最新に保つ
Outlook 2013 年および 2016 の完全な更新とパッチを適用したバージョンでは、既定でアプリケーションを起動ルール] の [フォーム アクションを無効にします。 これは、ように、場合でも、攻撃者は、アカウントを侵害、ルールおよびフォームの操作対象となります。 最新の更新プログラムおよびセキュリティ修正プログラムをインストールするには、 [Office のインストールの更新プログラム](https://support.office.com/en-us/article/Install-Office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5)の手順を実行します。

Outlook 2013 と 2016 のクライアントの修正プログラムのバージョンを以下に示します。
- Outlook 2013: 15.0.4937.1000 またはそれ以上
- Outlook 2016: 16.0.4534.1001 またはそれ以上

個々 のセキュリティ更新プログラムの詳細についてを参照してください。

- [Outlook 2013 のセキュリティ更新プログラム](https://support.microsoft.com/en-us/help/3191938) 
- [Outlook 2016 のセキュリティ更新プログラム](https://support.microsoft.com/en-us/help/3191883)

### <a name="third-monitor-your-outlook-clients"></a>3 番目: Outlook クライアントを監視します。
修正プログラムと更新プログラムをインストールした場合でも、攻撃者がアプリケーションを起動動作を再度有効にするローカル コンピューターの構成を変更するのにはください。監視し、クライアントにローカル コンピューター ポリシーを適用する[グループ ポリシーの管理の詳細設定](https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/agpm/)を使用できます。  
かどうかアプリケーションを起動が再度有効になって、レジストリの上書きを[64 ビット バージョンの Windows を使用して、システム レジストリを表示する方法](https://support.microsoft.com/en-us/help/305097/how-to-view-the-system-registry-by-using-64-bit-versions-of-windows)で情報を使用して参照してくださいすることができます。 これらのサブキーを確認します。 

- Outlook 2016: HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\
- Outlook 2013: HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\

EnableUnsafeClientMailRules のキーを探します。1 に設定されて場合、Outlook のセキュリティ修正プログラムが上書きされているとコンピューターがフォームのルール/攻撃に対して脆弱になります。値が 0 の場合は、アプリケーションを起動"アクションが無効です。 更新とパッチが適用されたバージョンの Outlook がインストールされている、このレジストリ キーが存在しない場合は、システムはこれらの攻撃に対する脆弱性がありません。

オンプレミスの Exchange のインストールでは、パッチが利用可能ではありませんが、Outlook の古いバージョンのブロックを検討してください。このプロセスの詳細については、[ブロックを構成する Outlook クライアント](https://technet.microsoft.com/en-us/library/dd335207(v=exchg.150).aspx)の資料にはあります。

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>Pro の cybersecurity のように Office 365 をセキュリティで保護します。
Office 365 サブスクリプションのデータとユーザーを保護するために使用できるセキュリティ機能の強力なセットが付属します。 使用、 [Office 365 のセキュリティ ロードマップ: 最初の 30 日、90 日間での内外の優先順位のトップ](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352)マイクロソフトが推奨する、Office 365 テナントのセキュリティに関するベスト プラクティスを実装します。
- 最初の 30 日以内に実行するタスクです。 即座に影響があり、影響の少ないのはこれらのユーザーにします。
- 90 日以内に実行するタスクです。これらにより、計画し実装しますが、セキュリティ体制を大幅に改善するに少し時間がかかります。
- 90 日が経過します。これらの拡張機能は、最初の 90 日間の作業でビルドします。

## <a name="see-also"></a>参照してください。
- SilentBreak セキュリティの投稿ルールのベクトルは、 [Outlook の仕訳ルールを悪意のある](https://silentbreaksecurity.com/malicious-outlook-rules/)方法の詳細なレビューを提供する Outlook の仕訳ルールです。 
- Mailrule Pwnage の Sensepost のブログ上の[MAPI over HTTP や Mailrule の Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/)は、メールボックスを Outlook の仕訳ルールを悪用できるルーラーと呼ばれるツールについて説明します。
- [Outlook のフォーム、およびシェル](https://sensepost.com/blog/2017/outlook-forms-and-shells/)フォーム脅威のベクトルに関する Sensepost のブログです。 
- [ルーラーのコードベース](https://github.com/sensepost/ruler)
- [妥協のルーラー マーク](https://github.com/sensepost/notruler/blob/master/iocs.md)