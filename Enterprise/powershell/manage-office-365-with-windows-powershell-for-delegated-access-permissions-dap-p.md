---
title: 委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して Microsoft 365 を管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: '概要: シンジケートおよびクラウドソリューションプロバイダー (CSP) パートナーは Windows PowerShell を使用して、Microsoft 365 の顧客テナントを管理できます。'
ms.openlocfilehash: 22fd26fb89d15cc036d52ed49ec61319c7e13a52
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230483"
---
# <a name="manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="ac44a-103">委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="ac44a-103">Manage Microsoft 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="ac44a-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="ac44a-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="ac44a-105">委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。</span><span class="sxs-lookup"><span data-stu-id="ac44a-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="ac44a-106">他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。</span><span class="sxs-lookup"><span data-stu-id="ac44a-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="ac44a-107">これらのサブスクリプションは、お客様に対して Microsoft 365 のサブスクリプションをサービス提供にバンドルしています。</span><span class="sxs-lookup"><span data-stu-id="ac44a-107">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="ac44a-108">Microsoft 365 サブスクリプションを販売する際には、顧客のテナンシーに対して管理およびレポートできるように、顧客テナンシーへの (AOBO) アクセス許可が自動的に付与されます。</span><span class="sxs-lookup"><span data-stu-id="ac44a-108">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="ac44a-109">このことは、Microsoft 365 管理センターでは、非常に困難で時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="ac44a-109">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="ac44a-110">お客様のテナント内のすべてのユーザーを一覧表示したり、Microsoft 365 の PowerShell を使用して、お**客様の**テナント内のすべてのユーザーと割り当てられているライセンスを特定したりするなど、管理タスクを実行するのは非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="ac44a-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using PowerShell for Microsoft 365.</span></span> <span data-ttu-id="ac44a-111">場合によっては、Microsoft 365 の PowerShell でのみこれらの管理タスクを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="ac44a-111">In some cases, it is possible to do these administrative tasks only in PowerShell for Microsoft 365.</span></span> <span data-ttu-id="ac44a-112">シンジケート パートナーと CSP パートナーが顧客テナンシーを管理するために最もよく使用するシナリオのサンプルは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac44a-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="ac44a-113">委任アクセス許可 (DAP) パートナー用 Windows PowerShell で Microsoft 365 テナントを管理する</span><span class="sxs-lookup"><span data-stu-id="ac44a-113">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="ac44a-114">委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する</span><span class="sxs-lookup"><span data-stu-id="ac44a-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="ac44a-115">委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する</span><span class="sxs-lookup"><span data-stu-id="ac44a-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="ac44a-116">委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して顧客のテナント レポート データを取得する</span><span class="sxs-lookup"><span data-stu-id="ac44a-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

