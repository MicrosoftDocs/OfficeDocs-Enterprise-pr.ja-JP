---
title: Office 365 のグローバル管理者アカウントを保護する
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
description: 次の3つの手順に従って、Office 365 サブスクリプションへのグローバル管理者アクセスを保護します。
ms.openlocfilehash: 23d47ec1f5fc4126113dd69e1ac6400d003ca41f
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573921"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Office 365 のグローバル管理者アカウントを保護する

 **概要:** グローバル管理者アカウントの侵害に基づいて、Office 365 サブスクリプションを攻撃から保護します。 
  
office 365 サブスクリプションのセキュリティ侵害 (情報の収集、フィッシング攻撃など) は、通常、office 365 全体管理者アカウントの資格情報を侵害することによって行われます。 クラウドのセキュリティは、お互いと Microsoft の間のパートナーシップです。
  
- Microsoft クラウドサービスは、信頼とセキュリティの基礎に基づいて構築されています。 Microsoft は、データとアプリケーションを保護するためのセキュリティ制御と機能を提供しています。
    
- データと id、およびそれらを保護する責任、オンプレミスのリソースのセキュリティ、および管理するクラウドコンポーネントのセキュリティを所有しています。
    
Microsoft は、組織を保護するための機能を提供していますが、使用する場合にのみ有効です。 これらを使用しないと、攻撃にさらされる可能性があります。 全体管理者アカウントを保護するために、Microsoft は次のことを行うための詳細な指示にお役立てください。
  
1. 専任の Office 365 グローバル管理者アカウントを作成し、必要な場合にのみ使用します。
    
2. 専用の Office 365 のグローバル管理者アカウントに対して多要素認証を構成し、最強のセカンダリ認証形式を使用します。
    
3. Office 365 Cloud App Security を有効にして構成し、不審な全体管理者アカウントアクティビティを監視します。
    
> [!NOTE]
> この記事ではグローバル管理者アカウントに重点を置いていますが、サブスクリプション内のデータにアクセスするための広範な権限を持つその他のアカウント (電子情報開示管理者やセキュリティ、コンプライアンスなど) についても考慮する必要があります。管理者アカウントは、同じ方法で保護する必要があります。 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>手順 1. 専任の Office 365 グローバル管理者アカウントを作成し、必要な場合にのみ使用する

グローバル管理者特権を必要とする、ユーザーアカウントへの役割の割り当てなど、比較的少数の管理タスクがあります。 そのため、グローバル管理者の役割が割り当てられている日常のユーザーアカウントを使用する代わりに、次の手順を実行します。
  
1. グローバル管理者の役割が割り当てられているユーザーアカウントのセットを決定します。 これを行うには、Windows PowerShell コマンドプロンプトの Microsoft Azure Active Directory モジュールで次のコマンドを実行します。
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. グローバル管理者の役割が割り当てられているユーザーアカウントを使用して、Office 365 サブスクリプションにサインインします。
    
3. 少なくとも1つの専用のグローバル管理者ユーザーアカウントを作成します。 **少なくとも12文字の強力なパスワードを使用してください。** 詳細について[は、「強力なパスワードを作成する](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)」を参照してください。 新しいアカウントのパスワードを安全な場所に格納します。 
    
4. 新しい専用のグローバル管理者ユーザーアカウントに、グローバル管理者の役割を割り当てます。
    
5. Office 365 からサインアウトします。
    
6. 新しい専用のグローバル管理者ユーザーアカウントのいずれかを使用してサインインします。
    
7. 手順1でグローバル管理者の役割が割り当てられている既存のユーザーアカウントごとに、次の操作を行います。
    
  - グローバル管理者ロールを削除します。
    
  - そのユーザーのジョブ機能と責任に応じて、管理者の役割をアカウントに割り当てます。 office 365 のさまざまな管理者ロールの詳細については、「 [office 2013 管理者の役割につい](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)て」を参照してください。
    
8. Office 365 からサインアウトします。
    
結果は次のようになります。
  
- グローバル管理者の役割を持つサブスクリプションで唯一のユーザーアカウントは、専用のグローバル管理者アカウントの新しいセットです。 このことを確認するには、次の PowerShell コマンドを使用します。
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- サブスクリプションを管理するその他の通常のユーザー アカウントには、各自の職務に関連する管理ロールが割り当てられています。
    
この時点から、グローバル管理者特権を必要とするタスクに対してのみ、専用のグローバル管理者アカウントを使用してサインインします。 他のすべての Office 365 管理は、他の管理役割をユーザーアカウントに割り当てることによって実行する必要があります。
  
> [!NOTE]
> はい。これには、日常のユーザーアカウントとしてサインアウトし、専用のグローバル管理者アカウントでサインインするための追加の手順が必要になります。 ただし、この操作を実行する必要があるのは、全体管理者の操作の場合だけです。 グローバル管理者アカウント違反の後に Office 365 サブスクリプションを回復するには、さらに多くの手順が必要になることに注意してください。 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>手順 2. 専用の Office 365 のグローバル管理者アカウントに対して多要素認証を構成し、最強のセカンダリ認証形式を使用する

グローバル管理者アカウントの多要素認証 (MFA) には、アカウント名とパスワード以外の追加情報が必要です。 Office 365 では、次の認証方法がサポートされています。
  
- 電話
    
- ランダムに生成されるパス コード
    
- スマート カード (仮想または物理)
    
- 生体認証デバイス
    
クラウド (クラウド id モデル) のみに格納されているユーザーアカウントを使用している小規模な企業では、次の手順を使用して、電話呼び出しまたはスマートフォンに送信されたテキストメッセージ検証コードを使用して MFA を構成します。
  
1. [MFA を有効に](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)します。
    
2. [Office 365 の2段階認証をセットアップ](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)して、認証方法として電話呼び出しまたはテキストメッセージの各専用のグローバル管理者アカウントを構成します。 
    
Office 365 ハイブリッド id モデルを使用している大規模な組織の場合は、さらに多くの検証オプションがあります。 より強力なセカンダリ認証方法に対してセキュリティインフラストラクチャが既に配置されている場合は、次の手順を実行します。
  
1. [MFA を有効に](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)します。
    
2. [Office 365 の2段階認証をセットアップ](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)して、適切な検証方法にそれぞれの専用のグローバル管理者アカウントを構成します。 
    
目的の強力な検証方法のセキュリティインフラストラクチャが、Office 365 MFA に適していない場合は、電話呼び出しまたはテキストメッセージを使用して MFA で専用のグローバル管理者アカウントを構成することを強くお勧めします。中間のセキュリティ対策として、グローバル管理者アカウントのスマートフォンに送信される検証コード。 MFA で提供される追加の保護を行わずに、専用のグローバル管理者アカウントを残さないようにします。
  
詳細については、「[Office 365 展開用の多要素認証の計画](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)」を参照してください。
  
MFA と PowerShell を使用して Office 365 サービスに接続するには、[この記事](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)を参照してください。
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>手順 3. 疑わしいグローバル管理者アカウントアクティビティを監視する

Office 365 Cloud App Security では、サブスクリプションの不審な動作を通知するポリシーを作成できます。 Cloud App Security は Office 365 E5 に組み込まれていますが、別のサービスとしても利用できます。 たとえば、Office 365 E5 がない場合は、グローバル管理者、セキュリティ管理者、およびコンプライアンス管理者の役割が割り当てられているユーザーアカウントの個別の Cloud App Security ライセンスを購入することができます。
  
Office 365 サブスクリプションに Cloud App Security がある場合は、次の手順を実行します。
  
1. セキュリティ管理者またはコンプライアンス管理者の役割が割り当てられているアカウントを使用して、Microsoft 365 管理センターにサインインします。
    
2. [Office 365 Cloud App Security を有効](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)にします。
    
3. [Office 365 Cloud App Security の異常検出ポリシー](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6)を確認して、特権のある管理アクティビティの異常なパターンを電子メールで通知します。 
    
ユーザーアカウントをセキュリティ管理者の役割に追加するには、専用のグローバル管理者アカウントと MFA を使用して[Office 365 PowerShell に接続](https://technet.microsoft.com/library/dn975125.aspx#step3)し、ユーザーアカウントのユーザープリンシパル名を入力してから、次のコマンドを実行します。 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

ユーザーアカウントをコンプライアンス管理者の役割に追加するには、ユーザーアカウントのユーザープリンシパル名を入力してから、次のコマンドを実行します。
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>エンタープライズ組織のための追加の保護

手順1-3 の後に、次の追加の方法を使用して、全体管理者アカウントと、それを使用して実行する構成を可能な限り安全なものにするようにします。
  
### <a name="privileged-access-workstation-paw"></a>特権アクセスワークステーション (PAW)

高度な権限のあるタスクの実行が可能な限り安全であることを確認するには、PAW を使用します。 PAW は、グローバル管理者アカウントを必要とする Office 365 構成など、機密性の高い構成タスクにのみ使用される専用のコンピューターです。 このコンピューターはインターネットブラウジングや電子メールで毎日使用されていないため、インターネット攻撃および脅威から保護するのが適切です。
  
PAW をセットアップする方法については、「 [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)」を参照してください。
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Azure AD Privileged Identity Management (PIM)

グローバル管理者アカウントにグローバル管理者の役割を永続的に割り当てずに、Azure AD PIM を使用して、必要に応じて、グローバル管理者の役割をオンデマンドで一度だけ割り当てることができます。
  
全体管理者アカウントを永続的な管理者として使用するのではなく、管理者となります。 グローバル管理者の役割は、ユーザーが必要とするまで非アクティブです。 次に、アクティブ化プロセスを完了して、グローバル管理者の役割を、あらかじめ決められた時間だけグローバル管理者アカウントに追加します。 時間が経過すると、PIM はグローバル管理者アカウントから全体管理者の役割を削除します。
  
PIM を使用すると、このプロセスによって、グローバル管理者アカウントが悪意のあるユーザーの攻撃および使用に対して脆弱になる時間が大幅に短縮されます。
  
詳細については、「 [Azure AD の特権 id 管理を構成する](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)」を参照してください。
  
> [!NOTE]
> PIM は、Enterprise Mobility + Security (EMS) E5 に含まれる Azure Active Directory Premium P2 で利用できます。また、全体管理者アカウントの個別のライセンスを購入することもできます。 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Office 365 ログ用のセキュリティ情報およびイベント管理 (SIEM) ソフトウェア

サーバー上での SIEM ソフトウェア実行では、アプリケーションとネットワークハードウェアによって作成されたセキュリティ通知とイベントのリアルタイム分析を実行します。 SIEM サーバーに Office 365 のセキュリティの警告とイベントを分析およびレポート機能に含めることができるようにするには、これらを SIEM システムに統合します。
  
- Azure AD
    
    詳細については、「 [Azure リソースからのログを SIEM システムに統合する](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)」を参照してください。
    
- Office 365 Cloud App Security
    
    詳細については、「 [SIEM server を Office 365 Cloud App Security と統合する](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)」を参照してください。
    
## <a name="next-step"></a>次の手順

「 [Office 365 のセキュリティのベストプラクティス」を](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)参照してください。
  

