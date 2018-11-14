---
title: Office 365 テナント間コラボレーション
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: テナントおよび組織間での Office 365 の共同作業のしくみについて説明します。
ms.openlocfilehash: ec844f78a0ae31469c2ca92c5cb97d965bdb3508
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219887"
---
# <a name="office-365-inter-tenant-collaboration"></a>Office 365 テナント間コラボレーション

この資料では、2 つの Office 365 テナント間での共同作業のいくつかの方法について説明します。Office 365 管理者のものです。
  
想定すると、Office 365 のテナントのビジネスがあるそれぞれ 2 つの組織、Fabrikam と contoso 社では、いくつかのプロジェクトで共同作業します。限られた時間のうちいくつかを実行し、継続的です。方法が Fabrikam と Contoso を有効にするセキュリティで保護された方法で、別の Office 365 テナント間でより効率的に共同作業を行うには、人やチームでしょうか。Azure Active Directory の B2B の共同作業と連携して、office 365 には、いくつかのオプションが用意されています。この資料では、Fabrikam と contoso 社が検討できるいくつかの主要なシナリオについて説明します。
  
Office 365 のテナントの間の共同作業オプションは、ファイルや予定表の共有、im の会話の中心的な場所を使用して、オーディオとビデオでは、通信およびリソースとアプリケーションへのアクセスをセキュリティで保護します。ソリューションを選択し、詳細については、次の表を使用します。
  
## <a name="exchange-online-collaboration-options"></a>Exchange オンラインの共同作業オプション

|**共有目標**|**管理操作**|**操作方法に関する情報**|
|:-----|:-----|:-----|
|別の Office 365 組織と予定表を共有する  <br/> |管理者を設定できますカレンダーへのアクセスのさまざまなレベルでは、Exchange オンライン他のユーザーとスケジュール (空き時間情報) を共有できるようにするのには他の企業との共同作業を可能に  <br/> |[Exchange Online での共有](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Exchange online 組織との関係](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [Exchange Online で組織の関係を作成する](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [変更および Exchange online 組織の関係](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Exchange Online で、組織の関係を削除します。](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [予定表を外部ユーザーと共有する](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|ユーザーが組織外のユーザーとカレンダーを共有する方法を制御します。  <br/> |管理者は、共有していると許可されているアクセスのレベルを制御するユーザーのメールボックスに共有ポリシーを適用します。  <br/> |[Exchange Online 内のポリシーを共有します。](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Exchange Online で共有ポリシーを作成します。](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [Exchange Online のメールボックスに共有ポリシーを適用します。](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [変更、無効化、または Exchange Online で共有ポリシーを削除します。](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|電子メールをセキュリティで保護されたチャネルを構成し、パートナー組織とのメールの流れを制御します。  <br/> |管理者は、取引先組織またはサービス プロバイダーとのやり取りはメールにセキュリティを適用するためのコネクタを作成します。コネクタがドメイン名の制限を許可すると、トランスポート層セキュリティ (TLS) 経由での暗号化を強制するか、IP アドレスの範囲をパートナーにメールを送信からです。  <br/> |[Exchange Online で電子メール接続をセキュリティで保護するために Office 365 で TLS を使用する方法](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Exchange Online のリモート ドメイン](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [パートナー組織とセキュリティで保護されたメール フローにコネクタを設定します](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Exchange Online および Office 365 でのメール フローのベスト プラクティス (概要)](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online およびビジネスの共同作業のオプションの OneDrive

|**ゴールの共有**|**管理操作**|**操作方法に関する情報**|
|:-----|:-----|:-----|
|外部ユーザーとサイトとドキュメントを共有します。  <br/> |管理者が、テナントで共有を構成するか、Microsoft アカウントの認証、職場または学校のサイト コレクション レベルのアカウントの認証、またはゲスト アカウント  <br/> |[SharePoint Online 環境の外部共有を管理する](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [制限されたドメインのビジネスのオンラインの SharePoint と OneDrive を Office 365 の共有](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [SharePoint Online を使用して、企業間 (B2B) エクストラネット ソリューションとして](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|進捗管理とエンド ・ ユーザー向けの外部共有を制御します。  <br/> |OneDrive ファイルの所有者のビジネスとエンド ・ ユーザーの SharePoint Online のサイトおよびドキュメントの共有を構成し、共有を追跡するための通知を確立  <br/> |[ビジネスの OneDrive の外部で共有するための通知を構成します。](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Office 365 で SharePoint のファイルやフォルダーを共有する](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype ビジネス コラボレーションのオプションについて

|**共有目標**|**管理操作**|**操作方法に関する情報**|
|:-----|:-----|:-----|
|ビジネス オンラインの IM、通話、およびプレゼンスのビジネス ユーザー向けの他の Skype での Skype  <br/> |管理者はビジネス オンライン ユーザーが IM、Skype を有効にする、オーディオとビデオ通話、および別の Office 365 テナント内のユーザーとのプレゼンスを参照してください。  <br/> |[ユーザーが外部の Skype for Business ユーザーに連絡できるようにする](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype ビジネス オンラインの IM、通話、および Skype (コンシューマー) のユーザーとのプレゼンスの  <br/> |管理者ことができます IM をオンライン ビジネスのユーザーに、Skype を有効にする呼び出しを行い、(コンシューマー) の Skype ユーザーとのプレゼンスを参照してください。  <br/> |[Skype 連絡先を追加、ビジネス ・ ユーザーの Skype を使用します。](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Azure AD B2B の共同作業オプション

|**共有目標**|**管理操作**|**操作方法に関する情報**|
|:-----|:-----|:-----|
|Azure AD B2B コラボレーション ・ コンテンツが組織のディレクトリ内のグループに外部ユーザーを追加することで共有  <br/> |グループにこれらの外部ユーザーを追加する Office 365 テナントの 1 つのグローバル管理者は、そのディレクトリに参加する別の Office 365 テナントに人を招待でき、SharePoint サイトとグループのライブラリなどのコンテンツへのアクセスを付与します。  <br/> |[Azure AD B2B コラボレーションのプレビューとは何ですか。](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure AD の B2B: 新しい更新プログラムを作成、企業間のグループ作業を簡単に](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Office 365 の外部の共有と Azure Active Directory B2B コラボレーション](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Azure Active Directory の B2B コラボレーション API とカスタマイズ](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD および識別情報の表示: Azure AD B2B (企業間のコラボレーション](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Office 365 の共同作業オプション

|**共有目標**|**管理操作**|**操作方法に関する情報**|
|:-----|:-----|:-----|
|Office 365 のグループの電子メール、予定表、OneNote、および中央の場所のファイル共有  <br/> |ビジネス プレミアム、ビジネスに関する重要事項、教育、およびエンタープライズ E1、E3、E5 の計画では、グループがサポートされています。1 つの Office 365 テナント内のユーザーは、グループを作成し、ゲスト ユーザーとして、別の Office 365 テナントに人を招待します。Dynamics CRM にも適用されます。  <br/> |[Office 365 グループについてください。](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Office 365 のグループでのゲスト アクセス](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Office 365 のグループを展開します。](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Yammer の共同作業オプション

|**共有目標**|**管理操作**|**操作方法に関する情報**|
|:-----|:-----|:-----|
|Yammer の企業のソーシャル メディアを介しての共同作業  <br/> |Yammer の管理者が外部のグループを作成する機能が無効な場合を除き、ユーザーは、会話をするように次の投稿、ファイルの共有、およびオンライン チャット機能を通じて、Yammer に共同作業を行う外部のグループを作成できます。  <br/> |[Yammer の外部グループを作成して管理する](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>チームの共同作業オプション

|**共有目標**|**管理操作**|**操作方法に関する情報**|
|:-----|:-----|:-----|
|組織外部のユーザーと、チームで共同作業します。  <br/> |招待側の Office 365 テナントのグローバル管理者は、チームの外部の共同作業を有効にする必要があります。グローバル管理者とチームの所有者はチームで共同作業するのには電子メール アドレスを持つユーザーを招待することになります。  <br/> 管理者は、管理し、来園者が、テナント内に既に存在を編集することができますもします。  <br/> |[ゲスト アクセスを許可します。](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [チームでゲスト アクセスを有効または無効に](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [PowerShell を使用して、ゲスト アクセスを制御する](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [ゲスト アクセスのチェックリスト](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [ゲスト ユーザーを表示します。](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [ゲスト ユーザー情報を編集します。](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|チームの所有者は、招待し、来園者が、チーム内で共同作業する方法を管理できます。  <br/> |チームの所有者には、チーム内で実行できる、来園者にその他のコントロールがあります。  <br/> |[来園者を追加します。](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [チームにゲストを追加します。](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [チームでのゲスト アクセスを管理します。](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [チームまたはチャネルでは、ユーザーを参照してください。](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|他のテナントには、来園者はチームの内容を表示でき、他のメンバーとの共同作業  <br/> |なし。  <br/> |[ゲスト アクセスの操作性](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>電源 BI の共同作業オプション

|**共有目標**|**管理操作**|**操作方法に関する情報**|
|:-----|:-----|:-----|
|電源の BI は、リンクを通じてそれらを共有するコンテンツを利用する外部のゲスト ユーザーを使用できます。これにより、組織間でセキュリティで保護された方法でコンテンツを配布するのには、組織内のユーザーです。<br/> | BI 管理者は、ユーザーが組織内のコンテンツを表示するのには、外部ユーザーを招待するかどうかを制御できます。 <br/> |[Azure AD B2B と外部のゲスト ユーザーが電源の BI コンテンツを配信します。](https://docs.microsoft.com/en-us/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Office 365 のテナントの間の共同作業についての注意点

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>ユーザー アカウント、ライセンス、サブスクリプション、およびストレージの共有

各組織は、独自のユーザー アカウント、ユーザー、セキュリティ グループ、サブスクリプション、ライセンス、および記憶域を管理します。人は、会社の資産の制御を維持しながら必要な情報へのアクセスを提供するのに共有ポリシーおよびセキュリティの設定と Office 365 での共同作業機能を使用します。
  
- **ユーザー アカウント:** アカウントを共有することはできませんし、テナントまたはオンプレミスの Active Directory ディレクトリ サービス内のパーティション間でアカウントを複製することはできません。 
    
- **ライセンス&amp;のサブスクリプション:**、Office 365 では、計画のライセンスからライセンス (も呼び出された Sku または Office 365 プラン) ユーザーにそれらの計画に定義されている Office 365 サービスへのアクセスを提供します。 
    
- **ストレージ:** Office 365 のプランでソフトウェアの境界と SharePoint Online の制限とは切り離して管理メールボックス格納域の制限です。メールボックス格納域の制限を設定し、Exchange Online を使用して管理します。両方のシナリオでは、テナント間のストレージを共有できません。 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>Office 365 のテナント間でのドメインの名前空間をご

違います。Fabrikam.com、tailspintoys.com などの修飾のドメインのみ関連付けられているし、使用できる 1 つのテナントに。各テナントが独自の名前空間にいる必要があります。UPN、SMTP、および SIP 名前空間は、テナントの間で共有することはできません。
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>ハイブリッド コンポーネントと Office 365 のテナントの間の共同作業について説明します。

など、Exchange 組織と Azure の AD 接続、設置型ハイブリッド コンポーネントは、複数のテナントの間で分割できません。
  

