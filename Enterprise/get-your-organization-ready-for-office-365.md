---
title: 組織で Office 365 Enterprise を使えるようにする
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: fasttrack の展開を除外していて、基本的な展開手順で必要な情報が見つからない場合は、ここから開始してください。
ms.openlocfilehash: a15bd73efe2fd2e2dfd13b3a444f77b9d0bfc764
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085376"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>組織で Office 365 Enterprise を使えるようにする

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>Office 365 の準備が整ったらどうすればよいですか?

ほとんどの組織では、Office 365 を準備するために何もする必要はありません。これは web 上のアプリケーションで、ユーザーはアカウントを持ってすぐに使用できます。他の組織には、より多くの場所、セキュリティプラクティス、またはその他の計画を必要とするその他の要件があります。エンタープライズレベルの組織の場合は、以下のチェックリストの項目に従って Office 365 を使い始めることができます。
  
Office 365 セットアップでヘルプが必要な場合は、[FastTrack](https://fasttrack.microsoft.com/office) を使用すると Office 365 の展開を一番簡単に行えます。また、サインインして、[Office 365 サービスの展開アドバイザー](deployment-advisors-for-office-365.md)もご利用いただけます。
  
|**開始するには、次のいずれかを選択します。**||
|:-----|:-----|
| [Office 365 のシステム要件](https://products.office.com/office-system-requirements) |-Microsoft office Professional、office 365、office 365 ProPlus、および Windows、Mac、iOS、および Android 用の各 office アプリケーションには、特定のシステム要件があります。ハードウェアとソフトウェアが最小のシステム要件を満たしていることを確認します。|
|**ほとんど**のお客様は、オンプレミスのディレクトリを Office 365 に接続します。[ネットワークに idfix をインストールして実行](https://www.microsoft.com/download/details.aspx?id=36832)することにより、ディレクトリの準備を開始します。<br> カスタマイズされたセットアップガイダンスを取得するには、 [AAD Connect advisor](https://aka.ms/aadconnectpwsync)および[Azure AD Premium セットアップガイド](https://aka.ms/aadpguidance)を使用します。 <br> |-ディレクトリに対する自動チェックにより、[ユーザーのアカウントが正しく同期される](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e)ことを検証します。 <br> -ディレクトリオブジェクトを変更することをお勧めします。変更を自動化するためのサービスを提供します。 <br> - [idfix ツールの使用方法に](prepare-directory-attributes-for-synch-with-idfix.md)ついて詳しく説明します。 |
|[ネットワークパフォーマンスガイダンス](https://aka.ms/tune)を**読ん**で、ツールを使用して、ユーザーに最適な環境を提供するために必要な接続性とパフォーマンスの構成があることを確認してください。  <br> | -office 365 に接続できることを確認してください。送信トラフィックをフィルター処理またはスキャンする場合は、組織にとって[office 365 エンドポイントを管理](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a)する方法を理解しておく必要があります。  <br>  - [ネットワーク容量をモデル化してテスト](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132)するか、または[Office 365 回路の Azure ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)に移動して、より予測可能な環境を使用します。   |
|[計画チェックリスト](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0)は、独自の展開計画を作成するための出発点として**使用**します。  <br> | また、計画に役立つ参照情報へのリンクを計画する必要がある分野の詳細な概要について説明します。 |
|[Exchange Server ラージアイテムスクリプト](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6)を**使用**して、移行するには大きすぎるメールアイテムを検索します。  <br> | -Exchange Web サービスを使用して、指定したファイルサイズのメールボックスを偽装、アクセス、スキャンし、結果を CSV ファイルにダンプします。スクリプトを[使用する方法の詳細に](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx)ついては、「」を参照してください。 |
|**** [Microsoft の展開エキスパート](https://go.microsoft.com/fwlink/?LinkId=517115)を活用して、すべてのユーザーが新しいサービスおよびアプリケーションの使用を開始できるように計画を支援します。  <br> [Office 365 サービスの展開ウィザード](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2)を使用して、カスタマイズしたセットアップガイダンスを取得します。  <br> | -オンボードセンターは、顧客とパートナー組織と直接連携します。今すぐ電話をかけましょう。 |
|[Office 365 サクセスセンターのテンプレートとリソース](https://www.microsoft.com/fasttrack/resources)を**使用**して、組織内のユーザーと展開およびオンボードプランを共有します。  <br> | -Office 365 への移行前、移行中、および移行後のすべてのユーザーとの通信は重要です。  <br> -テンプレート、ガイド、および配布資料を使用して、コミュニケーションを改善します。 |
|office 365 のトラフィックを安全に管理し、最適なパフォーマンスを得るための接続の原則については、記事「 [office 365 ネットワーク接続の原則](https://aka.ms/o365networkingprinciples)」を**参照**してください。  <br> | -この記事では、Office 365 のネットワーク接続を安全に最適化するための最新のガイダンスを理解するのに役立ちます。 |
   
Office 365 をより広範なクラウド戦略と統合するために役立つリソースを増やすことをお勧めします。[Microsoft クラウド IT アーキテクチャのリソース](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources)を以下に示します。
  
## <a name="want-to-talk-with-support"></a>サポートと話しますか?

ここでは、ビジネス製品に関する[サポートにお問い合わせ](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)ください。
