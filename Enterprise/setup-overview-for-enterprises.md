---
title: Office 365 Enterprise を組織で展開する
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: ITPro
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
ms.openlocfilehash: a49d57978faabfac7131db3178cbff02b500667f
ms.sourcegitcommit: 0c775dbd2325f95e3f006424d1446f76caadb588
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2019
ms.locfileid: "31004408"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a><span data-ttu-id="11d0e-103">Office 365 Enterprise を組織で展開する</span><span class="sxs-lookup"><span data-stu-id="11d0e-103">Deploy Office 365 Enterprise for your organization</span></span>
<span data-ttu-id="11d0e-p101">オンプレミス インフラストラクチャで Office 365 Enterprise の展開と統合を開始します。次の手順の概要は、ディレクトリの接続、データの移行、および最新バージョンの Office 2016 の利用開始に向けて組織のユーザーのヘルプを行う際に役立つよう作られています。</span><span class="sxs-lookup"><span data-stu-id="11d0e-p101">Ready to deploy and integrate Office 365 Enterprise with your on-premises infrastructure? These overview steps are designed to help you connect your directory, migrate your data, and help the people in your organization begin using the latest version of Office 2016.</span></span>
  
<span data-ttu-id="11d0e-106">次の手順は、Office 365 Enterprise のカスタム展開を開始する企業と[非営利団体](https://go.microsoft.com/fwlink/?LinkId=627221) に向けたものです。</span><span class="sxs-lookup"><span data-stu-id="11d0e-106">These steps are for businesses and [nonprofits](https://go.microsoft.com/fwlink/?LinkId=627221) that want to start with a custom deployment of Office 365 Enterprise.</span></span> 
  
<span data-ttu-id="11d0e-p102">Office 365 Enterprise をお持ちでない場合は、「[一般法人向け Office 365 のセットアップ](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)」で中小企業向けの手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11d0e-p102">Don't have Office 365 Enterprise? See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for instructions for small businesses.</span></span> 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a><span data-ttu-id="11d0e-109">FastTrack を使ったガイドに沿ったエンタープライズ Office 365 のセットアップ プロセス</span><span class="sxs-lookup"><span data-stu-id="11d0e-109">Guided enterprise Office 365 setup process with FastTrack</span></span>
<span data-ttu-id="11d0e-p103">Office 365 の**[FastTrack](https://docs.microsoft.com/fasttrack)** は、Office 365 を展開するための最適な方法です。FastTrack は最も一般的な展開構成の手順をご案内し、途中で質問にお答えすることもできます。セルフ ヘルプまたはパートナーによるガイダンスをご希望する場合は、「[Office 365 のセットアップ](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa)」、「[Office 365 のセットアップ ウィザード](https://aka.ms/o365fasttrack)」、または「[認定パートナーを見つける](https://partnercenter.microsoft.com/ja-JP/pcv/search)」をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="11d0e-p103">Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** is the best method for deploying Office 365. FastTrack guides you through the most common deployment configurations and can answer questions along the way. If you want to self-help or guidance from a partner, use our [Office 365 setup guide](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), our [Office 365 setup wizards](https://aka.ms/o365fasttrack), or [find a qualified partner](https://partnercenter.microsoft.com/ja-JP/pcv/search).</span></span>

## <a name="self-deployment-of-office-365"></a><span data-ttu-id="11d0e-113">管理者自身による Office 365 の展開</span><span class="sxs-lookup"><span data-stu-id="11d0e-113">Self-deployment of Office 365</span></span>
<span data-ttu-id="11d0e-114">管理者自身がOffice 365 を導入する場合は、次の展開の手順をお役立てください。</span><span class="sxs-lookup"><span data-stu-id="11d0e-114">If you want to deploy Office 365 on your own, the following deployment steps are here to help.</span></span>

1. <span data-ttu-id="11d0e-p104">**[Office 365 のための準備](get-your-organization-ready-for-office-365.md)**。Office 365 の導入に向けて、ネットワーク、ディレクトリ、およびエンド ユーザーの準備をお手伝いするツールやリソースを提供します。</span><span class="sxs-lookup"><span data-stu-id="11d0e-p104">**[Get ready for Office 365](get-your-organization-ready-for-office-365.md)**. These tools and resources will help you get your network, directory, and end users ready for Office 365.</span></span>

2. <span data-ttu-id="11d0e-p105">**[サインインしてインターネット ドメインを Office 365 に追加](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)** します。ポータルにサインインし、ユーザーの追加やメールの移行はしないまま、ドメインを Office 365 サブスクリプションに追加します。すべてのユーザーとサービスも同時に構成する場合は、「[基本的なセットアップ手順](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa)」に従ってください。</span><span class="sxs-lookup"><span data-stu-id="11d0e-p105">**[Sign in and add your internet domain(s) to Office 365](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)**. Sign into the portal and add one or more domains to your Office 365 subscription without adding users or migrating email. If you want to configure all your users and services at the same time, follow our [basic set up instructions](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa).</span></span>

>[!IMPORTANT] 
><span data-ttu-id="11d0e-120">オンプレミスのディレクトリからユーザーを同期したりシングル サインオンを利用したりする場合は、基本的なセットアップ手順はお使いいただけません。</span><span class="sxs-lookup"><span data-stu-id="11d0e-120">The basic set up instructions won't work if you want to synchronize your users from an on-premises directory or utilize Single Sign-On.</span></span>

3. <span data-ttu-id="11d0e-p106">**[ディレクトリを Office 365 に接続](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)** します。ID の同期やシングル サインオンの構成オプションに関するガイドです。[AAD Connect アドバイザー](https://aka.ms/aadconnectpwsync)、[Azure AD Premium セットアップ ガイド](https://aka.ms/aadpguidance)を使用して、カスタマイズしたセットアップ ガイダンスを使います。</span><span class="sxs-lookup"><span data-stu-id="11d0e-p106">**[Connect your directory to Office 365](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)**. Guide to the identity synchronization and/or single sign-on configuration options. Use the [AAD Connect advisor](https://aka.ms/aadconnectpwsync) and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance) to get customized set up guidance.</span></span>
4. <span data-ttu-id="11d0e-p107">**[Office 365 のサービスとアプリケーションを構成](configure-services-and-applications.md)** します。メール、ファイル共有、インスタント メッセージング、またはその他の Office 365 サービスとアプリケーションのいずれかを構成するには、ここから開始します。</span><span class="sxs-lookup"><span data-stu-id="11d0e-p107">**[Configure Office 365 services and applications](configure-services-and-applications.md)**. Start here to configure email, file sharing, instant messaging, or any of the other Office 365 services and applications.</span></span>
5. <span data-ttu-id="11d0e-p108">**[Office 365 へデータの移行](migrate-data-to-office-365.md)** をします。サービスを構成すると、データの移行を開始できるようになります。</span><span class="sxs-lookup"><span data-stu-id="11d0e-p108">**[Migrate data to Office 365](migrate-data-to-office-365.md)**. Once the services are configured, you can start migrating data.</span></span>
6. <span data-ttu-id="11d0e-p109">**[ユーザーが Office 365 を使用できるようにする](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)** します。組織内のユーザーが Office 365 の利用に慣れるためのお手伝いをするには、このリソースをお使いください。</span><span class="sxs-lookup"><span data-stu-id="11d0e-p109">**[Get people using Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Help people in your organization build confidence using Office 365 with these resources.</span></span>