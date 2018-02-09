---
title: "SharePoint Online サイトとファイルをセキュリティで保護する"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "概要: SharePoint Online および Office 365 内のファイルを保護するために推奨されている構成を取り上げます。"
ms.openlocfilehash: 78e29b12bad2d9ba91524fecf4fa66b8729715ae
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a>SharePoint Online サイトとファイルをセキュリティで保護する

 **概要:**SharePoint Online および Office 365 内のファイルを保護するために推奨されている構成を取り上げます。
  
この記事では、SharePoint Online チーム サイトとファイルの保護を、セキュリティとコラボレーションのしやすさのバランスを取りながら構成するための推奨事項を示します。この記事では、4 つの異なる構成を定義します。最初は、最もオープンな共有ポリシーを使用した、組織内のパブリック サイトです。それ以外の各構成は、保護のセットアップには有効な手段ですが、リソースへのアクセスやリソース上でのコラボレーションは、関連したユーザーのセットに限定されます。これらの推奨事項を開始点として使用し、組織のニーズを満たすように構成を調整してください。 
  
この記事で示されている構成は、データ、ID、デバイスを保護するための 3 つの層に関する Microsoft の推奨事項と調和しています。
  
- 基準の保護
    
- 機密の保護
    
- 非常に機密性の高い社外秘の保護
    
以上の層と各層に推奨される機能については、次の情報源をご覧ください。 
  
- [Office 365 の ID とデバイス保護](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Office 365 のファイル保護ソリューション](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>機能の概要

SharePoint Online チーム サイトの推奨事項は、Office 365 のさまざまな機能に基づいています。高機密サイトに関しては、Azure Information Protection が推奨されています。これは Enterprise Mobility + Security (EMS) に含まれています。 
  
次の図は、4 つの SharePoint Online チーム サイトについて推奨されている構成を示しています。
  
![SharePoint サイトの推奨構成](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
次の点が示されています。
  
- ベースライン保護には、SharePoint Online チーム サイト用の 2 つのオプション、つまりパブリック サイトとプライベート サイトが含まれます。パブリック サイトは、組織内のだれもが検出およびアクセスできます。プライベート サイトは、サイトのメンバーのみが検出とアクセスを行うことができます。どちらのサイト構成においても、グルーブの外部との共有を行うことができます。 
    
- 機密および高機密保護のためのサイトは、アクセスを特定のグループのメンバーのみに限定しているプライベート サイトになります。
    
- Office 365 ラベルでは、必要な保護レベルを使用してデータを分類できます。それぞれの SharePoint Online チーム サイトは、サイトの既定ラベルを使用して、ドキュメント ライブラリ内のファイルに自動的にラベルを適用するよう構成されています。4 つのサイト構成に応じて、この例ではラベルを内部パブリック、プライベート、機密、高機密としています。ユーザーはラベルを変更できますが、この構成ではすべてのファイルに既定ラベルが適用されます。
    
- データ損失防止 (DLP) ポリシーは、Office 365 の機密および高機密ラベル向けに構成されており、これらのタイプのファイルをユーザーが組織外に送信しようとすると警告を表示したり、その処理を防止したりします。 
    
- 機密性の高い社外秘の保護が構成されているサイトの場合、Azure Information Protection がファイルを暗号化し、アクセス許可を与えます。
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>SharePoint Online と OneDrive for Business に関するテナント全体の設定

SharePoint Online と OneDrive for Business には、すべてのサイトとユーザーに影響を及ぼすテナント全体の設定が含まれています。これらの設定の中には、サイト レベルにおいてより制限の強いもの (ただし、既定以下にはできません) に調整できるものもあります。このセクションでは、セキュリティとコラボレーションに影響を与えるテナント全体の設定について取り上げます。 
  
### <a name="sharing"></a>共有

このソリューションでは、次のテナント全体設定を推奨しています。
  
- 匿名の共有を含む、あらゆるアカウント タイプとのあらゆる共有を許可する既定の共有ポリシーを維持します。
    
- 必要に応じて、匿名リンクの有効期間を設定します。
    
- 既定のリンクの種類を「内部」に変更します。これにより、組織外で意図せずデータが漏洩する事態を避けることができます。
    
外部共有を許可することは直感に反しているように思えるかもしれませんが、これは電子メールでファイルを送信するよりもファイル共有をより制御できます。SharePoint Online と Outlook は連携して、セキュリティで保護されたファイルのコラボレーションを提供します。 
  
- 既定では、Outlook は、電子メールでファイルを送信する代わりに、ファイルへのリンクを共有します。 
    
- SharePoint Online と OneDrive for Business を使用すると、組織の内部と外部の共同作成者にファイルへのリンクを簡単に共有できます。
    
また、外部共有を管理することもできます。たとえば、以下の事柄が可能です。
  
- 匿名ゲスト リンクを無効にします。
    
- サイトへのユーザー アクセスを取り消す。
    
- 特定のサイトまたはドメインにアクセスできるユーザーを確認する。
    
- 匿名の共有リンクに期限を設定する (テナント設定)。
    
- 組織外で共有できるユーザーを制限する (テナント設定)。
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>データ損失防止 (DLP) を外部共有と併用します。

外部共有を許可しない場合、ビジネスで必要なユーザーは、代替のツールと手段を使用することになります。Microsoft は、機密ファイルおよび高機密ファイルを保護するために DLP ポリシーと外部共有を組み合わせることをお勧めします。
  
### <a name="device-access-settings"></a>デバイス アクセスの設定

SharePoint Online と OneDrive for Business のデバイス アクセスの設定では、アクセスを参照のみ (ファイルをダウンロードすることはできません) に限定するか、アクセスをブロックするかを指定できます。現在これらの設定は先行リリースに含まれ、テナント全体で適用されます。まもなく、デバイス アクセス ポリシーをサイト レベルで構成できるようになります。このソリューションの場合、テナント全体で適用されるデバイス アクセスの設定を使用しないことをお勧めします。
  
先行リリースのデバイス アクセスの設定を使用するには、「[Office 365 で標準または先行リリース オプションを設定する](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)」を参照してください。
  
### <a name="onedrive-for-business"></a>OneDrive for Business

これらの設定を確認し、OneDrive for Business サイトの既定の設定を変更するかどうかを判断してください。現在、共有とデバイス アクセスの設定は SharePoint Online 管理センターの設定からコピーされており、両方の環境に適用されます。
  
## <a name="sharepoint-team-site-configuration"></a>SharePoint チーム サイトの構成

次の表に、この記事で前述した各チーム サイトの構成をまとめます。これらの構成を開始点の推奨事項として使用し、組織のニーズに合うようサイトの種類と構成を調整します。すべての組織がすべてのサイトの種類を必要とするわけではありません。高機密保護が必要となる組織はごくわずかです。
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**ベースライン保護 1** <br/> |**基準の保護 #2** <br/> |**機密の保護** <br/> |**非常に機密性の高い社外秘** <br/> |
|説明  <br/> |組織内ではアクセスや共同作業が自由。  <br/> |グループ外で共有が許可されている、プライベート サイトとグループ。  <br/> |アクセス レベルが特定のグループのメンバーシップによって定義されている、独立したサイト。共有はサイトのメンバーにのみ許可されます。組織外にファイルを送信しようとすると、DLP はユーザーに警告します。  <br/> |独立したサイトと、Azure Information Protection によるファイルの暗号化とアクセス許可。DLP はユーザーがファイルを組織の外部に送信できないようにします。  <br/> |
|プライベート サイトまたはパブリック チーム サイト  <br/> |パブリック  <br/> |Kirkland  <br/> |Kirkland  <br/> |Kirkland  <br/> |
|誰にアクセス権が与えられるか  <br/> |B2B のユーザーとゲスト ユーザーを含む、組織の全員。  <br/> |サイトのメンバーのみ。他のユーザーは、アクセス権を要求できます。  <br/> |サイトのメンバーのみ。他のユーザーは、アクセス権を要求できます。  <br/> |メンバーのみ。他のユーザーは、アクセス権を要求できません。  <br/> |
|サイト レベルの共有制御  <br/> |すべてのユーザーと共有できます。既定の設定です。  <br/> |すべてのユーザーと共有できます。既定の設定です。  <br/> |メンバーはサイトへのアクセスを共有できません。  <br/> メンバー以外の人はサイトへのアクセスを要求できますが、要求はサイトの管理者に対して行う必要があります。  <br/> |メンバーはサイトへのアクセスを共有できません。  <br/> メンバー以外の人はサイトまたはコンテンツへのアクセスを要求できません。  <br/> |
|サイトレベルのデバイス アクセス制御  <br/> |付加的な制御はありません。  <br/> |追加制御はありません。  <br/> |サイト レベルの制御は準備中です。ユーザーは、非対応デバイスまたはドメインに参加していないデバイスにファイルをダウンロードできません。他のすべてのデバイスからは参照専用のアクセスが許可されます。  <br/> |サイト レベルの制御は準備中です。非対応デバイスまたはドメインに参加していないデバイスへのファイルのダウンロードをブロックします。  <br/> |
|Office 365 ラベル  <br/> |内部公開  <br/> |Kirkland  <br/> |機密  <br/> |非常に機密性の高い社外秘  <br/> |
|DLP ポリシー  <br/> |||機密ラベルが付けられたファイルを組織の外に送信しようとするとユーザーに警告が表示されます。  <br/> クレジット カード番号や他の個人データなど、機密データの種類の外部共有をブロックするには、これらのデータの種類 (自分で構成したカスタム データの種類を含む) に追加の DLP ポリシーを構成できます。  <br/> |ユーザーが高機密のラベルが付けられているファイルを組織の外部に送信できないようにします。ファイルの共有相手など、理由を提供することよって、ユーザーはこの設定を上書きできます。  <br/> |
|Azure Information Protection  <br/> ||||Azure Information Protection を使用して、ファイルの暗号化とファイルへのアクセス許可の付与を自動化します。この保護は、リークが発生した場合に備えて、移動するファイルに適用されます。  <br/> Office 365 は、Azure Information Protection で暗号化されたファイルを読み取ることができません。さらに、DLP ポリシーが操作できるのはメタデータ (ラベルを含む) のみで、これらのファイルのコンテンツ (ファイル内のクレジット カード番号など) を操作することはできません。  <br/> |
   
このソリューションで 4 つの異なる種類の SharePoint Online チーム サイトを展開する手順については、「[3 つの層による保護用のサイトを展開する](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)」を参照してください。開発/テスト環境の作成手順については、「[開発/テスト環境の SharePoint Online サイトをセキュリティで保護する](secure-sharepoint-online-sites-in-a-dev-test-environment.md)」を参照してください。 
  
## <a name="office-365-classification-and-labels"></a>Office 365 の分類とラベル

機密データを含む環境では、Office 365 のラベルを使用することをお勧めします。Office 365 ラベルの構成と発行が完了した後、次のことを行えるようになります。
  
- SharePoint Online チーム サイトのドキュメント ライブラリに既定のラベルを適用することにより、それらのライブラリ内のすべてのドキュメントに既定のラベルを適用することができます。 
    
- コンテンツが特定の条件に一致するときには、ラベルを自動的に適用できます。
    
- Office 365 のラベルに基づいた DLP ポリシーを適用できます。
    
- 組織内のユーザーは、Outlook on the web、Outlook 2010 以降、OneDrive for Business、SharePoint Online、Office 365 グループのコンテンツに手動でラベルを適用できます。ユーザーは自分が操作するコンテンツの種類を最もよく知っているので、コンテンツを分類して適切な DLP ポリシーを適用できます。
    
![SharePoint サイトの推奨構成](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
示されているように、このソリューションでは次のラベルを作成します。
  
- 非常に機密性の高い社外秘
    
- 機密
    
- Kirkland
    
- 内部パブリック
    
これらのラベルは、図で推奨されているサイトと、この記事で前述したグラフにマップされます。このソリューションでは、機密および高機密というラベルの付いたファイルの漏洩を防ぐために DLP ポリシーを構成することをお勧めします。
  
このソリューションで Office 365 のラベルと DLP ポリシーを構成する手順については、「[Office 365 のラベルと DLP の SharePoint Online のファイルを保護します。](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)」を参照してください。
  
## <a name="azure-information-protection"></a>Azure Information Protection

Azure Information Protection を使用して、ファイルが移動する場所に関係なく、ラベルと保護を適用します。このソリューションでは、スコープ付きの Azure Information Protection ポリシーと高機密ラベルのサブラベルを使用して、最高レベルのセキュリティによる保護が必要なファイルを暗号化して、それらのファイルにアクセス許可を付与することをお勧めします。 
  
Azure Information Protection 暗号化が Office 365 に格納されているファイルに適用される場合、このサービスはこれらのファイルのコンテンツを処理することはできないことにご注意ください。共同編集、電子情報開示、検索、Delve、他の共同作業機能は動作しません。DLP ポリシーが操作できるのはメタデータ (Office 365 ラベルを含む) のみで、それらのファイルのコンテンツ (ファイル内のクレジットカード番号など) を操作することはできません。
  
![Azure Information Protection は Azure で設定され、ラベルはクライアント ツールバーに表示される](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
次の点が示されています。
  
- Azure Information Protection ポリシーとラベルは Microsoft Azure ポータルで構成します。スコープ付きの Azure Information Protection ポリシーのサブラベルを構成することをお勧めします。
    
- Azure Information Protection のラベルは、Office アプリケーションで **[Information Protection]** バーとして表示されます。
    
### <a name="adding-permissions-for-external-users"></a>外部ユーザーに対するアクセス許可の追加

Azure Information Protection で保護されているファイルにアクセス権を外部ユーザーに付与するためには 2 つの方法があります。どちらの場合も、外部ユーザーは Azure AD アカウントが必要です。外部ユーザーが Azure AD を使用する組織のメンバーではない場合、サインアップ ページ ([https://aka.ms/aip-signup](https://aka.ms/aip-signup)) を使用して個人で Azure AD アカウントを取得できます。
  
- 外部ユーザーを、ラベルの保護の構成に使用する Azure AD グループに追加します。
    
     最初に、ご使用のディレクトリでアカウントを B2B ユーザーとして追加する必要があります。[Azure Rights Management によるグループ メンバーシップのキャッシュ](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management) には、数時間かかることがあります。この方法を使用すると、ラベルで保護された既存のファイルすべてに、アクセス許可が付与されます (ユーザーが Azure AD グループに追加される前に保護されていたファイルも含む)。
    
- 外部ユーザーを、ラベル保護に直接追加します。
    
     組織 (例: Fabrikam.com) のすべてのユーザー、Azure AD グループ (例: 組織内の財務グループ)、個々のユーザーを追加できます。たとえば、ラベルの保護に、規制機関の外部ユーザーを追加できます。この方法を使用すると、外部エンティティが保護に追加された後にラベルを使用して保護されたファイルにのみ、アクセス許可が付与されます。
    
### <a name="deploying-and-using-azure-information-protection"></a>Azure Information Protection の展開と使用

このソリューションで Azure Information Protection を構成する手順については、「[Azure Information Protection を使用して SharePoint Online ファイルを保護する](protect-sharepoint-online-files-with-azure-information-protection.md)」を参照してください。
  
## <a name="see-also"></a>関連項目

[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[セキュリティ ソリューション](security-solutions.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
[開発/テスト環境の SharePoint Online サイトをセキュリティで保護する](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



