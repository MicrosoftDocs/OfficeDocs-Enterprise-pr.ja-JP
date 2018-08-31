---
title: Office 365 全体管理者アカウントを保護する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: これら 3 つの手順で Office 365 サブスクリプションをグローバル管理者のアクセスを保護します。
ms.openlocfilehash: 7260e903ea007735c87ab8aa826e3b97e7bd28c1
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541766"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Office 365 全体管理者アカウントを保護する

 **の概要:** Office 365 サブスクリプションをグローバル管理者アカウントの侵害に基づく攻撃から保護します。 
  
情報収集を含め、Office 365 サブスクリプション、およびフィッシング攻撃では、セキュリティ侵害は通常、Office 365 のグローバル管理者アカウントの資格情報を侵害することで行われます。クラウドでのセキュリティは、お客様とマイクロソフトとのパートナーシップです。
  
- マイクロソフトのクラウド サービスは、信頼とセキュリティの基盤が構築されます。マイクロソフトでは、セキュリティ ・ コントロールと、データとアプリケーションを保護する機能を提供します。
    
- データと id、および、設置型リソースのセキュリティ、および制御するクラウド コンポーネントのセキュリティを保護するための責任を所有します。
    
マイクロソフトは、お客様の組織を保護するための機能を提供していますが、それらを使用する場合にのみ有効です。それらを使用しない場合、は、攻撃に対する脆弱性が存在する必要があります。グローバル管理者アカウントを保護するには、マイクロソフトがお手伝いするに詳細が記載。
  
1. 専用の Office 365 のグローバル管理者アカウントを作成し、必要な場合のみに使用します。
    
2. 専用の Office 365 のグローバル管理者アカウントの複数要素の認証を構成し、最強の第 2 の認証を使用します。
    
3. 有効にし、不審なグローバル ・ アドミニストレータ ・ アカウント ・ アクティビティを監視する Office 365 のクラウド アプリケーションのセキュリティを構成します。
    
> [!NOTE]
> 追加するかどうかを検討する必要がありますもこの資料は、グローバル ・ アドミニストレータ ・ アカウントに焦点を当てています、電子的証拠開示の管理者またはセキュリティやコンプライアンスなど、サブスクリプションのデータにアクセスするための広範なアクセス許可を持つアカウント同様に、管理者アカウントを保護する必要があります。 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>手順 1 です。専用の Office 365 のグローバル管理者アカウントを作成し、必要な場合のみに使用

グローバル管理者権限を必要とするユーザー アカウントにロールを割り当てるなど、比較的少数の管理タスクがあります。したがって、グローバル管理者ロールが割り当てられている日常的なユーザー アカウントを使用するには、代わりに次の手順操作を行います。
  
1. グローバル管理者ロールが割り当てられているユーザー アカウントのセットを決定します。Microsoft Azure Active Directory モジュールを Windows PowerShell コマンド プロンプトでこのコマンドを使用してこれを行うことができます。
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. グローバル管理者ロールが割り当てられているユーザー アカウントで Office 365 サブスクリプションに署名します。
    
3. 少なくとも 1 つを作成し、最大で 5 つのグローバル管理者ユーザー アカウントを専用です。**強力なパスワードには、少なくとも 12 文字長の使用**詳細については、[強力なパスワードを作成する](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)を参照してください。新しいアカウントのパスワードを安全な場所に格納します。 
    
4. 新しい専用のグローバル管理者のユーザー アカウントのそれぞれには、グローバル管理者ロールを割り当てます。
    
5. Office 365 からサインアウトします。
    
6. 新しい専用のグローバル管理者ユーザー アカウントのいずれかでサインインします。
    
7. 既存ユーザー アカウントごとに手順 1 からグローバル管理者ロールが割り当てられていました。
    
  - グローバル管理者の役割を削除します。
    
  - ユーザーの職務と責任に対応するアカウントに管理者の役割を割り当てます。Office 365 のさまざまな管理者の役割の詳細については、 [Office 365 の管理者の役割](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)を参照してください。
    
8. Office 365 からサインアウトします。
    
結果は次のようになります。
  
- グローバル管理者の役割を持つサブスクリプションの場合、唯一のユーザー アカウントとは、専用のグローバル管理者アカウントの新しいセットです。次の PowerShell コマンドを使用してこれを確認します。
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- サブスクリプションを管理するその他の通常のユーザー アカウントには、各自の職務に関連する管理ロールが割り当てられています。
    
この時点以降から署名する専用のグローバル管理者アカウントを使用してグローバル管理者権限を必要とするタスクに対してのみです。ユーザー アカウントにその他の管理役割を割り当てることによって、他のすべての Office 365 の管理を行う必要があります。
  
> [!NOTE]
> [はい] を日常的なユーザー アカウントでサインインし、専用のグローバル管理者アカウントを使ってサインインする追加の手順が必要です。グローバル管理者の操作が実行するだけで済みますが。グローバル管理者アカウントの侵害がより多くの手順を必要とした後、Office 365 サブスクリプションを回復することを検討してください。 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>手順 2 です。専用の Office 365 のグローバル管理者アカウントに対して多要素認証を構成して、最強の第 2 の認証を使用します。

グローバル管理者アカウントには、多要素認証 (MFA) には、アカウント名とパスワード以外の追加情報が必要です。Office 365 には、これらの検証メソッドがサポートされています。
  
- 電話をかける
    
- パスをランダムに生成されたコード
    
- スマート カード (仮想または物理)
    
- 生体認証デバイス
    
クラウド (クラウドの識別情報モデル) にのみ保存されているユーザー アカウントを使用しているスモール ビジネスの場合は、電話またはスマート フォンに送信されるテキスト メッセージの検証コードを使用して MFA を構成するのには次の手順を使用します。
  
1. [MFA を有効に](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)します。
    
2. 検証方法として専用電話またはテキスト メッセージのグローバル管理者アカウントのそれぞれを構成するのには[Office 365 の 2 段階の検証を設定](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)します。 
    
Office 365 ハイブリッドの識別情報モデルを使用している大規模な組織である場合は、検証オプションが増えました。セキュリティ インフラストラクチャを既により強力な代替の認証方法のためにある場合は、次の手順を使用します。
  
1. [MFA を有効に](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)します。
    
2. それぞれを構成するのには[Office 365 の 2 段階の検証の設定](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)は、適切な検証メソッドのグローバル管理者アカウントを専用です。 
    
Office 365 の MFA の機能している目的のより強力な検証方法のセキュリティ インフラストラクチャがない場合は、強くお勧め MFA では、専用のグローバル管理者アカウントを構成すること、電話またはテキスト メッセージを使用して検証コードが暫定的なセキュリティ対策として、グローバル管理者アカウントにスマート フォンに送信します。MFA によって提供される追加の保護機能なし、専用のグローバル管理者アカウントをしないでください。
  
詳細については、「[Office 365 展開用の多要素認証の計画](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)」を参照してください。
  
MFA と PowerShell を Office 365 サービスに接続するには、[この資料](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)を参照してください。
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>ステップ 3 です。不審なグローバル ・ アドミニストレータ ・ アカウント ・ アクティビティの監視

Office 365 のクラウド アプリケーションのセキュリティを使用すると、サブスクリプションの場合、不審な動作を通知するためのポリシーを作成できます。クラウド アプリケーションのセキュリティは、Office 365 の E5 に組み込まれていますが、個別のサービスとしても利用。などの Office 365 の E5 がない場合は、グローバル管理者、セキュリティ管理者、およびコンプライアンス管理者ロールに割り当てられているユーザー アカウント用の個々 のクラウド アプリケーションのセキュリティ ライセンスを購入できます。
  
クラウド アプリケーションのセキュリティがある場合、Office 365 サブスクリプションで、以下の手順を実行します。
  
1. セキュリティ管理者やコンプライアンス管理者の役割が割り当てられたアカウントを使用して Office 365 ポータルにサインインします。
    
2. [Office 365 のクラウド アプリケーションのセキュリティを有効](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)します。
    
3. 特権の管理活動の異常なパターンの e メールで通知する、 [Office 365 のクラウド アプリケーションのセキュリティでの異常検出ポリシー](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6)を確認します。 
    
セキュリティ管理者ロールにユーザー アカウントを追加するには専用のグローバル管理者アカウントと、MFA、 [Office 365 の PowerShell への接続](https://technet.microsoft.com/library/dn975125.aspx#step3)ををユーザー アカウントのユーザー プリンシパル名を入力し、し、これらのコマンドを実行します。 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

コンプライアンス管理者ロールにユーザー アカウントを追加するのにはユーザー アカウントのユーザー プリンシパル名を入力し、これらのコマンドを実行します。
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>企業向けの付加的な保護

手順 1 ~ 3 は、グローバル管理者アカウント、および構成を使用することを実行することを確認するのにはこれらのメソッドを使用して後、は、可能な限り安全です。
  
### <a name="privileged-access-workstation-paw"></a>特権アクセス ワークステーション (PAW)

高い特権を持つタスクの実行が可能な限り安全であることを確認するのには、PAW を使用します。PAW は、Office 365 の構成は、グローバル管理者アカウントを必要とするなど、機密性の高い構成のタスクにのみ使用される専用のコンピューターです。このコンピューターがインターネットの閲覧や電子メールを毎日使用しないためインターネットへの攻撃や脅威からよりよく保護されています。
  
PAW を設定する方法の詳細についてを参照してください[http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)。
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Azure AD 特権 Id 管理 (PIM)

グローバル管理者アカウントをグローバル管理者ロールを割り当てられる恒久的にするのではなく、グローバル管理者ロールの割り当てをオン ・ デマンド、ジャスト ・ イン ・ タイムを有効にすることが必要なときに Azure AD の PIM を使用できます。
  
永続的な管理をされている、グローバル管理者アカウントではなく管理者を対象となります。誰かが必要となるまで、グローバル管理者ロールはアクティブではありません。あらかじめ決められた時間数のグローバル管理者アカウントに、グローバル管理者ロールを追加するのには、ライセンス認証プロセスを完了するとします。時間が経過すると、PIM は、グローバル ・ アドミニストレータ ・ アカウントから、グローバル管理者ロールを削除します。
  
PIM を使用して、このプロセスは、グローバル ・ アドミニストレータ ・ アカウントは攻撃や悪意のあるユーザーが使用する脆弱性が存在する時間を大幅に削減します。
  
詳細については、 [Azure AD の特権の構成の Id 管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)を参照してください。
  
> [!NOTE]
> Azure Active ディレクトリ プレミアム p2、エンタープライズ ・ モビリティとセキュリティ (EMS) E5 に含まれては、使用可能な PIM を使用するか、グローバル管理者アカウントに個々 のライセンスを購入することができます。 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Office 365 のログのセキュリティ情報およびイベント管理 (SIEM) ソフトウェア

SIEM ソフトウェアがサーバー上で実行では、セキュリティ警告は、アプリケーションおよびネットワークのハードウェアによって作成されるイベントのリアルタイムの分析を実行します。SIEM サーバーなど、Office 365 のセキュリティの警告イベントの分析とレポート作成機能では、SIEM システムでは、これらを統合します。
  
- Azure AD
    
    詳細については、 [SIEM システムに Azure のリソースの統合ログ](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)を参照してください。
    
- Office 365 Cloud App Security
    
    詳細については、 [Office 365 のクラウド アプリケーションのセキュリティと SIEM サーバーの統合](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)を参照してください。
    
## <a name="next-step"></a>次の手順

[Office 365 のセキュリティのベスト プラクティス](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)を参照してください。
  

