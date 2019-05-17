---
title: Office 365 Enterprise を組織で展開する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: 次の手順の概要は、Office 365 の展開、Active Directory の接続、データの移行、および最新バージョンの Office 2016 の利用開始に向けて組織のユーザーのヘルプを行う際に役立つよう作られています。
ms.openlocfilehash: 2530b170c607f635f6f1baebf1d83fa7745d23a6
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102545"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a>Office 365 Enterprise を組織で展開する
オンプレミス インフラストラクチャで Office 365 Enterprise の展開と統合を開始します。次の手順の概要は、ディレクトリの接続、データの移行、および最新バージョンの Office 2016 の利用開始に向けて組織のユーザーのヘルプを行う際に役立つよう作られています。
  
次の手順は、Office 365 Enterprise のカスタム展開を開始する企業と[非営利団体](https://go.microsoft.com/fwlink/?LinkId=627221) に向けたものです。 
  
Office 365 Enterprise をお持ちでない場合は、「[一般法人向け Office 365 のセットアップ](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)」で中小企業向けの手順を参照してください。 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a>FastTrack を使ったガイドに沿ったエンタープライズ Office 365 のセットアップ プロセス
Office 365 の**[FastTrack](https://docs.microsoft.com/fasttrack)** は、Office 365 を展開するための最適な方法です。FastTrack は最も一般的な展開構成の手順をご案内し、途中で質問にお答えすることもできます。セルフ ヘルプまたはパートナーによるガイダンスをご希望する場合は、「[Office 365 のセットアップ](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa)」、「[Office 365 のセットアップ ウィザード](https://aka.ms/o365fasttrack)」、または「[認定パートナーを見つける](https://partnercenter.microsoft.com/en-us/pcv/search)」をご利用ください。

## <a name="self-deployment-of-office-365"></a>管理者自身による Office 365 の展開
管理者自身がOffice 365 を導入する場合は、次の展開の手順をお役立てください。

1. **[Office 365 のための準備](get-your-organization-ready-for-office-365.md)**。Office 365 の導入に向けて、ネットワーク、ディレクトリ、およびエンド ユーザーの準備をお手伝いするツールやリソースを提供します。

2. **サインインして、Office 365 にインターネットドメインを追加**します。 [Microsoft 365 管理センター](https://portal.microsoft.com)にサインインし、[**セットアップ > Domains**] をクリックして、[**新しいドメイン**] をクリックします。 ユーザーを追加したり、メールを移行したりせずに、1つ以上のドメインを Office 365 サブスクリプションに追加します。 

>[!IMPORTANT] 
>オンプレミスのディレクトリからユーザーを同期したりシングル サインオンを利用したりする場合は、基本的なセットアップ手順はお使いいただけません。

3. **[ディレクトリを Office 365 に接続](about-office-365-identity.md)** します。ID の同期やシングル サインオンの構成オプションに関するガイドです。[AAD Connect アドバイザー](https://aka.ms/aadconnectpwsync)、[Azure AD Premium セットアップ ガイド](https://aka.ms/aadpguidance)を使用して、カスタマイズしたセットアップ ガイダンスを使います。
4. **[Office 365 のサービスとアプリケーションを構成](configure-services-and-applications.md)** します。メール、ファイル共有、インスタント メッセージング、またはその他の Office 365 サービスとアプリケーションのいずれかを構成するには、ここから開始します。
5. **[Office 365 へデータの移行](migrate-data-to-office-365.md)** をします。サービスを構成すると、データの移行を開始できるようになります。
6. **[ユーザーが Office 365 を使用できるようにする](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)** します。組織内のユーザーが Office 365 の利用に慣れるためのお手伝いをするには、このリソースをお使いください。