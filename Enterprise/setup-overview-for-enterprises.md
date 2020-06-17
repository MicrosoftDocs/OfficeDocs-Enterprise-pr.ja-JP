---
title: 組織に Microsoft 365 Enterprise を展開する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: これらの概要手順は、ネットワークのセットアップ、id の作成、エンタープライズ向けの Microsoft 365 アプリの展開、データの移行、組織内のユーザーが Microsoft 365 の使用を開始する際に役立つように設計されています。
ms.openlocfilehash: 274cd4ae285ae97825b4d46a125cd9eeecf83312
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735945"
---
# <a name="deploy-microsoft-365-enterprise-for-your-organization"></a>組織に Microsoft 365 Enterprise を展開する

Microsoft 365 Enterprise を展開し、オンプレミスのインフラストラクチャと統合し、従業員がクラウドベースの生産性とコラボレーションを活用できるようにする準備ができていますか。

この記事では、2つの展開オプションについて説明します。 いずれの場合も、展開が成功するには、次に示すガイド付きのパスが提供されます。

## <a name="guided-microsoft-365-enterprise-setup-process-with-fasttrack"></a>FastTrack でのガイド付き Microsoft 365 Enterprise のセットアッププロセス

Microsoft 365 を展開するための最適な方法は、「 **[microsoft 365 の Fasttrack](https://www.microsoft.com/fasttrack/microsoft-365)** 」です。 FastTrack を使用すると、最も一般的な展開を構成する手順が表示され、質問に回答しながら構成できます。 

一連のセットアップガイドにアクセスするには、Microsoft 365 サブスクリプションにサインインして、[[セットアップガイダンス](https://aka.ms/o365fasttrack)] に移動します。

>[!Note]
>[Microsoft パートナー](https://www.microsoft.com/solution-providers/home)からサポートを受けることもできます。
>

## <a name="do-it-yourself-guided-deployment-of-microsoft-365-enterprise"></a>Microsoft 365 Enterprise のガイド付き展開

Microsoft 365 Enterprise を独自に展開するには、Microsoft 365 のサービス構成とユーザーの採用を合理化する設計上の決定を行うために詳細な調査を実行する必要があります。 [ここ](get-your-organization-ready-for-office-365.md)から計画を開始します。

計画を完了した後に Microsoft 365 Enterprise を独自に展開するには、以下の手順を実行することをお勧めします。

1. [ネットワークをセットアップする](set-up-network-for-office-365.md)

   インターネットドメインの追加とオンプレミスユーザーのネットワークパフォーマンスの最適化について説明します。
 
2. [Id を設定する](protect-your-global-administrator-accounts.md)

   Id モデル (クラウドのみまたはハイブリッド) を決定し、ハイブリッド id に対して、オンプレミスの Active Directory ドメインサービス (AD DS) と Microsoft 365 サブスクリプションとの間のディレクトリ同期をセットアップします。

3. [セキュリティを実装する](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)

   最初の30日間、90日以降に、テナントと id に対する基本および強化されたセキュリティ、脅威、情報保護を構成およびロールアウトする方法を示します。
 
4. [クライアントソフトウェアを展開する](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)

   エンタープライズ向け Microsoft 365 Apps (旧称 Office 365 ProPlus)、クラウド更新版の Office スイート (Word、Excel、PowerPoint、その他のバージョン) をデバイスに展開する方法が含まれています。 Microsoft 365 のすべてのクライアントライセンスには、エンタープライズ向けの Microsoft 365 アプリのライセンスが含まれています。
 
5. [モバイルデバイス管理の設定](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)

   Microsoft 365 Enterprise には、ユーザーのモバイルデバイスをセキュリティで保護し、管理するのに役立つモバイルデバイス管理機能が含まれています。
 
6. [サービスとアプリケーションを構成する](configure-services-and-applications.md)

   データの移行についての情報と、Exchange Online、SharePoint Online、Teams などの Microsoft 365 の主要な生産性向上アプリを開始する記事へのリンクが含まれています。
 
7. [ユーザーをトレーニングする](https://docs.microsoft.com/office365/admin/admin-overview/get-started-with-office-365#training-resources-for-your-users)

   ユーザーが Microsoft 365 をすばやく利用できるようにするための短いビデオが含まれています。
 

>[!Note]
>これらの手順は、Microsoft 365 Enterprise のカスタム展開で開始する必要があるビジネスおよび[非](https://go.microsoft.com/fwlink/?LinkId=627221)営利団体にも適用されます。 
>
