---
title: Office 365 PowerShell による Office 365 の管理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 932d57c0-1520-4f0f-8ec9-9966d646480f
description: '概要: Office 365 ユーザーとライセンス、Skype for Business Online、SharePoint Online、Exchange Online、Office 365 セキュリティ/コンプライアンス センターで Office 365 PowerShell を使用する方法について説明します。'
ms.openlocfilehash: fbc10833d3ee1e7377e6ed68adb7d2299fce72fa
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004570"
---
# <a name="manage-office-365-with-office-365-powershell"></a><span data-ttu-id="f4f7e-103">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="f4f7e-103">Manage Office 365 with Office 365 PowerShell</span></span>

<span data-ttu-id="f4f7e-104">*この記事は、Office 365 と Microsoft 365 の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="f4f7e-104">*This article applies to both Office 365 and Microsoft 365.*</span></span>

<span data-ttu-id="f4f7e-105">Office 365 PowerShell は、Microsoft 365 管理センターを補完する強力な管理ツールです。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-105">Office 365 PowerShell is a powerful management tool that complements the Microsoft 365 admin center.</span></span> <span data-ttu-id="f4f7e-106">たとえば、Office 365 PowerShell の自動化機能を使用すると、複数のユーザー アカウントとライセンスをより簡単に管理したり、レポートを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-106">For example, you can use Office 365 PowerShell automation to more quickly manage multiple user accounts and licenses and create reports.</span></span> <span data-ttu-id="f4f7e-107">Office 365 ユーザーとライセンス、Skype for Business Online、SharePoint Online、Exchange Online、および Office 365 Security & コンプライアンスセンターで Office 365 PowerShell を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-107">Learn how to use Office 365 PowerShell with Office 365 users and licenses, Skype for Business Online, SharePoint Online, Exchange Online, and the Office 365 Security & Compliance Center.</span></span>
  
<span data-ttu-id="f4f7e-108">以下から必要に合うトピックを選択してください。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-108">Select the topic based on your needs:</span></span>
  
- [<span data-ttu-id="f4f7e-109">概要</span><span class="sxs-lookup"><span data-stu-id="f4f7e-109">Get started</span></span>](getting-started-with-office-365-powershell.md)

    <span data-ttu-id="f4f7e-110">Office 365 PowerShell に慣れておらず、office 365 PowerShell モジュールをインストールして Office 365 サブスクリプションに接続する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-110">Start here if you are not familiar with Office 365 PowerShell and want to install the Office 365 PowerShell modules and connect to your Office 365 subscription.</span></span>

- [<span data-ttu-id="f4f7e-111">ユーザーアカウント、ライセンス、およびグループ</span><span class="sxs-lookup"><span data-stu-id="f4f7e-111">User accounts, licenses, and groups</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)

    <span data-ttu-id="f4f7e-112">Office 365 PowerShell モジュールをインストールしてあり、オートメーションコマンドを使用してユーザーアカウント、ライセンス、グループを管理する方法について詳しく知りたい場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-112">Start here if you have installed the Office 365 PowerShell modules and want to learn more about using automation commands to manage user accounts, licenses, and groups.</span></span>

- [<span data-ttu-id="f4f7e-113">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f4f7e-113">SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-sharepoint-online-with-office-365-powershell)

    <span data-ttu-id="f4f7e-114">Office 365 PowerShell モジュールをインストールしてあって、オートメーション コマンドを使用して SharePoint Online の管理を実行する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-114">Start here if you have installed the Office 365 PowerShell modules and want to use automation commands to perform management of SharePoint Online.</span></span>

- [<span data-ttu-id="f4f7e-115">Exchange Online の PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4f7e-115">Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)

    <span data-ttu-id="f4f7e-116">オートメーション コマンドを使用して Exchange Online を管理する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-116">Start here if you want to use automation commands to manage Exchange Online.</span></span>

- [<span data-ttu-id="f4f7e-117">Office 365 への電子メールの移行</span><span class="sxs-lookup"><span data-stu-id="f4f7e-117">Email migration to Office 365</span></span>](use-powershell-for-email-migration-to-office-365.md)

    <span data-ttu-id="f4f7e-118">Office 365 PowerShell モジュールを既にインストールしてあって、既存のシステムからメールを移行する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-118">Start here if you have installed the Office 365 PowerShell modules and want to migrate your email from existing systems.</span></span>

- [<span data-ttu-id="f4f7e-119">セキュリティ/コンプライアンス センター</span><span class="sxs-lookup"><span data-stu-id="f4f7e-119">Security & Compliance Center</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell)

    <span data-ttu-id="f4f7e-120">オートメーション コマンドを使用してセキュリティ/コンプライアンス センターを管理する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-120">Start here if you want to use automation commands to manage the Security & Compliance Center.</span></span>

- [<span data-ttu-id="f4f7e-121">代理アクセス許可 (DAP) パートナー</span><span class="sxs-lookup"><span data-stu-id="f4f7e-121">Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-p.md)

    <span data-ttu-id="f4f7e-122">シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーを使用して顧客の Office 365 テナントを管理する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-122">Start here if you want to use Syndication and Cloud Solution Provider (CSP) partners to manage your Office 365 customer tenants.</span></span>

- [<span data-ttu-id="f4f7e-123">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="f4f7e-123">Skype for Business Online</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)

    <span data-ttu-id="f4f7e-124">Office 365 PowerShell モジュールをインストールしてあって、Skype for Business Online の管理を実行する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="f4f7e-124">Start here if you have installed the Office 365 PowerShell modules and want to perform management of Skype for Business Online.</span></span>
