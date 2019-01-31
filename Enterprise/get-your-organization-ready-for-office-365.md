---
title: 組織で Office 365 Enterprise を使えるようにする
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Fasttrack という展開から脱退するいるし、基本的な展開の手順で必要な情報の検索は、ここでは起動します。
ms.openlocfilehash: bb522890880ec77969abe6e2559c3d0293aca372
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651201"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>組織で Office 365 Enterprise を使えるようにする

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>Office 365 用に準備するには、何をする必要がありますか。

ほとんどの組織では、Office 365 用に準備する必要はありません。Web 上のアプリケーションは、アカウントを持っているとすぐにそれを使用することがします。他の組織では、複数の場所、セキュリティ ・ プラクティス、または多くの計画の必要性を作成するその他の要件があります。エンタープライズ レベルの組織では、Office 365 を使い始めるには、次のチェックリストの項目に従ってください。
  
Office 365 セットアップでヘルプが必要な場合は、[FastTrack](https://fasttrack.microsoft.com/office) を使用すると Office 365 の展開を一番簡単に行えます。また、サインインして、[Office 365 サービスの展開アドバイザー](deployment-advisors-for-office-365.md)もご利用いただけます。
  
|**開始する 1 つ以上を選択します。**||
|:-----|:-----|
| [Office 365 のシステム要件](https://products.office.com/office-system-requirements) |Microsoft Office Professional、Office 365、Office 365 用リソース、および Windows、Mac、iOS および Android はすべての場合は、各 Office アプリケーションの特定のシステム要件があります。最小システム要件、ハードウェアとソフトウェアの対応を確認します。|
|**ほとんど**のお客様は、Office 365 の設置ディレクトリを接続します。[インストール](https://www.microsoft.com/download/details.aspx?id=36832)し、ネットワーク上の IdFix を実行しているディレクトリの準備を簡単に開始を取得します。<br> ガイダンスをカスタマイズした設定を取得するのには、[アドバイザーの AAD の接続](https://aka.ms/aadconnectpwsync)し、 [Azure AD プレミアムは、ガイドの設定](https://aka.ms/aadpguidance)を使用します。 <br> |ディレクトリに対してチェックを自動化された[検証の他のユーザーのアカウントの同期が正しく](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e)。 <br> -ディレクトリ オブジェクトへの変更を推奨して、変更作業を自動化するには。 <br> - [IdFix ツールの使用方法の詳細](prepare-directory-attributes-for-synch-with-idfix.md)です。 |
|**読み**することを確認するのには、ツールに最適なエクスペリエンスを提供するために必要な接続性とパフォーマンスの構成がある、[ネットワーク パフォーマンス ガイダンス](https://aka.ms/tune)および使用します。  <br> | -フィルター処理または送信をスキャンする場合、Office 365 に接続できることを確認してトラフィックを[Office 365 エンドポイントを管理する](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a)はどのような組織のことを意味を理解しておく必要があります。  <br>  - [モデルとネットワークの容量をテストする](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132)または予測可能なエクスペリエンスを[Office 365 の Azure ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)回路に移動します。   |
|[計画のチェックリスト](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0)の展開計画を作成するための出発点として**使用**します。  <br> | の可能な領域詳細な概要と計画に役立つ情報を参照または使用方法の説明へのリンクを計画する必要があります。 |
|**使用して** [Exchange Server の大きな項目のスクリプト](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6)を移行するには大きすぎる可能性があるメール アイテムを検索します。  <br> | -Exchange Web サービスを使用して偽装、アクセス、ファイルのサイズを指定してダンプ結果を CSV ファイルでのメールボックスをスキャンします。[スクリプトを使用する方法の詳細について](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx)を参照してください。 |
|支援できる計画からすべてのユーザーを支援する[マイクロソフトの展開の専門家](https://go.microsoft.com/fwlink/?LinkId=517115)**を**活用、新しいサービスやアプリケーションの使用を開始します。  <br> ガイダンスをカスタマイズした設定を取得するには、 [Office 365 サービスの展開ウィザード](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2)を使用します。  <br> | -契約時の中心は、パートナー企業と顧客と直接動作します。与える呼び出し今日。 |
|**使用して**[テンプレートと Office 365 の成功の中心にあるリソース](https://www.microsoft.com/fasttrack/resources)を共有、展開と契約時は、組織内のユーザーと予定です。  <br> | -前に、中、および Office 365 への移行後すべてのユーザーとの通信は重要です。  <br> -お客様の通信を向上させるために、テンプレート、ガイド、および配布資料を使用します。 |
|**読み取り**資料安全に Office 365 のトラフィックを管理し、最高のパフォーマンスを取得するための接続の原理を理解するのには[Office 365 のネットワーク接続の基本原則](https://aka.ms/o365networkingprinciples)です。  <br> | -この資料では Office 365 のネットワーク接続を安全に最適化するため、最新のガイダンスを理解できます。 |
   
Office 365 より広範なクラウド戦略に統合するためのより多くのリソースを選択しますか。を[マイクロソフトのクラウド IT アーキテクチャのリソース](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources)を次に示します。
  
## <a name="want-to-talk-with-support"></a>サポートに相談するとしています。

私たちは、ために、ビジネスの製品[サポートに問い合わせてください](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)います。
