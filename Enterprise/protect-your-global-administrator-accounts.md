---
title: Office 365 グローバル管理者アカウントの保護
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/15/2020
audience: Admin
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
f1.keywords:
- NOCSH
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Office 365 サブスクリプションへのグローバル管理者アクセスを保護します。
ms.openlocfilehash: 4f3e7dcb23f467768d647b7a5e8db9c41af2d076
ms.sourcegitcommit: fa25333a28ad300a7be990c1491d95f09a214a12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2020
ms.locfileid: "44253294"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Office 365 グローバル管理者アカウントの保護

*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*

Office 365 サブスクリプションのセキュリティ侵害 (情報の収集、フィッシング攻撃など) は、通常、Office 365 全体管理者アカウントの資格情報を侵害することによって行われます。 クラウドのセキュリティは、お互いと Microsoft の間のパートナーシップです。
  
- Microsoft クラウドサービスは、信頼とセキュリティの基礎に基づいて構築されています。 Microsoft は、データとアプリケーションを保護するためのセキュリティ制御と機能を提供しています。
    
- データと id、およびそれらを保護する責任、オンプレミスのリソースのセキュリティ、および管理するクラウドコンポーネントのセキュリティを所有しています。
    
Microsoft は、組織を保護するための機能を提供していますが、使用する場合にのみ有効です。 これらを使用しないと、攻撃にさらされる可能性があります。 全体管理者アカウントを保護するために、Microsoft は次のことを行うための詳細な指示にお役立てください。
  
1. 専任の Office 365 グローバル管理者アカウントを作成し、必要な場合にのみ使用します。
    
2. 専用の Office 365 のグローバル管理者アカウントに対して多要素認証を構成し、最強のセカンダリ認証形式を使用します。
    
> [!注] この記事ではグローバル管理者アカウントに重点を置いていますが、サブスクリプション内のデータにアクセスするための広範な権限を持つ追加のアカウント (電子情報開示管理者やセキュリティまたはコンプライアンス管理者アカウントなど) を同じ方法で保護する必要があるかどうかを検討する必要があります。 <br > グローバル管理者アカウントは、ライセンスを追加することなく作成できます。
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>手順 1. 専任の Office 365 グローバル管理者アカウントを作成し、必要な場合にのみ使用する

グローバル管理者特権を必要とする、ユーザーアカウントへの役割の割り当てなど、比較的少数の管理タスクがあります。 そのため、グローバル管理者の役割が割り当てられている日常のユーザーアカウントを使用する代わりに、次の手順を実行します。
  
1. グローバル管理者の役割が割り当てられているユーザーアカウントのセットを決定します。 これを行うには、Azure Active (Azure AD) Directory PowerShell for Graph コマンドを使用します。
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. グローバル管理者の役割が割り当てられているユーザーアカウントを使用して、Office 365 サブスクリプションにサインインします。
    
3. 最大4つの専用のグローバル管理者ユーザーアカウントを作成します。 **少なくとも12文字の強力なパスワードを使用してください。** 詳細について[は、「強力なパスワードを作成する](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)」を参照してください。 新しいアカウントのパスワードを安全な場所に格納します。 
    
4. 新しい専用のグローバル管理者ユーザーアカウントに、グローバル管理者の役割を割り当てます。
    
5. Office 365 からサインアウトします。
    
6. 新しい専用のグローバル管理者ユーザーアカウントのいずれかを使用してサインインします。
    
7. 手順1でグローバル管理者の役割が割り当てられている既存のユーザーアカウントごとに、次の操作を行います。
    
  - グローバル管理者ロールを削除します。
    
  - そのユーザーのジョブ機能と責任に応じて、管理者の役割をアカウントに割り当てます。 Office 365 のさまざまな管理者ロールの詳細については、「[管理者の役割につい](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles)て」を参照してください。
    
8. Office 365 からサインアウトします。
    
結果は次のようになります。
  
- グローバル管理者ロールを持つ、サブスクリプションのユーザー アカウントのみが、新しい専用のグローバル管理者アカウント セットとなります。 このことを確認するには、次の PowerShell コマンドを使用します。
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- サブスクリプションを管理するその他の通常のユーザー アカウントには、各自の職務に関連する管理ロールが割り当てられています。
    
この時点から、グローバル管理者特権を必要とするタスクに対してのみ、専用のグローバル管理者アカウントを使用してサインインします。 他のすべての Office 365 管理は、他の管理役割をユーザーアカウントに割り当てることによって実行する必要があります。
  
> [!NOTE]
> これには、日常のユーザーアカウントとしてサインアウトし、専用のグローバル管理者アカウントでサインインするための追加の手順が必要になります。 ただし、この操作を実行する必要があるのは、全体管理者の操作の場合だけです。 グローバル管理者アカウント違反の後に Office 365 サブスクリプションを回復するには、さらに多くの手順が必要になることに注意してください。
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-additional-verification"></a>手順 2.  専用の Office 365 のグローバル管理者アカウントに対して多要素認証を構成し、強力な検証方法を使用する

多要素認証 (MFA) には、アカウント名とパスワード以外の追加情報が必要です。 Office 365 では、次の追加の検証方法がサポートされています。
  
- Microsoft Authenticator アプリ

- 電話
    
- テキストメッセージを使用して送信された、ランダムに生成された検証コード
    
- スマート カード (仮想または物理)
    
- 生体認証デバイス
    
>[!Note]
>米国標準規格とテクノロジ (NIST) 標準に準拠する必要がある組織では、電話またはテキストメッセージベースの追加の検証方法を使用することは制限されています。 詳細については、[ここ](https://pages.nist.gov/800-63-FAQ/#q-b01)をクリックしてください。
>

クラウドのみに格納されているユーザーアカウントを使用している小規模な企業 (クラウドのみの id モデル) の場合は、次の手順を使用して、電話呼び出しまたはスマートフォンに送信されたテキストメッセージの検証コードを使用して MFA を構成します。
  
1. [MFA を設定](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)します。
    
2. [Office 365 の MFA をセットアップ](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)して、認証方法として電話番号またはテキストメッセージのそれぞれの専用のグローバル管理者アカウントを構成します。 
    
Office 365 ハイブリッド id モデルを使用している大規模な組織の場合は、さらに多くの検証オプションがあります。 より強力なセカンダリ認証方法に対してセキュリティインフラストラクチャが既に配置されている場合は、次の手順を実行します。
  
1. [MFA を設定](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)します。
    
2. [Office 365 の MFA をセットアップ](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)して、適切な検証方法にそれぞれの専用のグローバル管理者アカウントを構成します。 
    
目的の強力な検証方法のセキュリティインフラストラクチャが、Office 365 MFA に適していない場合は、一時的なセキュリティ対策として、グローバル管理者アカウントのスマートフォンに送信されるテキストメッセージ検証コードを使用して、専用のグローバル管理者アカウントを MFA で構成することを強くお勧めします。 MFA で提供される追加の保護を行わずに、専用のグローバル管理者アカウントを残さないようにします。
  
詳細については、「[Office 365 展開用の多要素認証の計画](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan)」を参照してください。
  
MFA と PowerShell を使用して Office 365 サービスに接続するには、次の記事を参照してください。

- [ユーザーアカウント、グループ、ライセンスの Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-by-using-mfa)
- [SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [Skype for Business Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a>エンタープライズ組織のための追加の保護

手順1と2の後に、グローバル管理者アカウントと、それを使用して実行する構成ができる限り安全であることを確認するために、これらの追加の方法を使用します。
  
### <a name="privileged-access-workstation"></a>特権アクセスワークステーション

高い権限を持つタスクの実行が可能な限り安全であることを確認するには、特権アクセスワークステーション (PAW) を使用します。 PAW は、グローバル管理者アカウントを必要とする Office 365 構成など、機密性の高い構成タスクにのみ使用される専用のコンピューターです。 このコンピューターはインターネットブラウジングや電子メールで毎日使用されていないため、インターネット攻撃および脅威から保護するのが適切です。
  
PAW をセットアップする方法については、「」を参照してください [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw) 。
  
### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

グローバル管理者アカウントにグローバル管理者の役割を永続的に割り当てるのではなく、Azure AD Privileged Identity Management (PIM) を使用して、必要に応じて、グローバル管理者の役割をオンデマンドで一度だけ割り当てられるようにすることができます。
  
全体管理者アカウントを永続的な管理者として使用するのではなく、管理者となります。 グローバル管理者の役割は、ユーザーが必要とするまで非アクティブです。 次に、アクティブ化プロセスを完了して、グローバル管理者の役割を、あらかじめ決められた時間だけグローバル管理者アカウントに追加します。 時間が経過すると、PIM はグローバル管理者アカウントから全体管理者の役割を削除します。
  
PIM を使用すると、このプロセスによって、グローバル管理者アカウントが悪意のあるユーザーの攻撃および使用に対して脆弱になる時間が大幅に短縮されます。

PIM は、Microsoft 365 Enterprise E5 または Enterprise Mobility + Security (EMS) E5 に含まれている Azure AD Premium P2 で利用できます。また、全体管理者アカウントの個別のライセンスを購入することもできます。
  
詳細については、「 [AZURE AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)」を参照してください。
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Office 365 ログ用のセキュリティ情報およびイベント管理 (SIEM) ソフトウェア

サーバー上での SIEM ソフトウェア実行では、アプリケーションとネットワークハードウェアによって作成されたセキュリティ通知とイベントのリアルタイム分析を実行します。 SIEM サーバーに Office 365 のセキュリティの警告とイベントを分析およびレポート機能に含めることができるようにするには、Azure AD をお客様の SEIM に統合します。 「 [Azure ログ統合の概要」を](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)参照してください。

## <a name="next-step"></a>次の手順

Office 365 サブスクリプションの id を設定している場合は、次を参照してください。

- クラウドのみの id を使用している場合は、[クラウドのみの id](cloud-only-identities.md)
- ハイブリッド id を使用している場合[にディレクトリ同期を準備](prepare-for-directory-synchronization.md)する

  
## <a name="see-also"></a>関連項目

[Office 365 のセキュリティロードマップ](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)。
