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
ms.openlocfilehash: 00e60693ad10b705765da9ed57142c893a74b034
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998223"
---
# <a name="manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="d591a-103">委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="d591a-103">Manage Microsoft 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="d591a-104">委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。</span><span class="sxs-lookup"><span data-stu-id="d591a-104">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="d591a-105">他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。</span><span class="sxs-lookup"><span data-stu-id="d591a-105">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="d591a-106">これらのサブスクリプションは、お客様に対して Microsoft 365 のサブスクリプションをサービス提供にバンドルしています。</span><span class="sxs-lookup"><span data-stu-id="d591a-106">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="d591a-107">Microsoft 365 サブスクリプションを販売する際には、顧客のテナンシーに対して管理およびレポートできるように、顧客テナンシーへの (AOBO) アクセス許可が自動的に付与されます。</span><span class="sxs-lookup"><span data-stu-id="d591a-107">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="d591a-108">このことは、Microsoft 365 管理センターでは、非常に困難で時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="d591a-108">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="d591a-109">顧客の **テナント ID** とそのドメインをすべて一覧表示する、または顧客テナンシーのユーザーおよび割り当てられているライセンスをすべて特定するなどの管理タスクは Office 365 の Windows PowerShell を使用して行う方がはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="d591a-109">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="d591a-110">場合によっては、これらの管理タスクは Office 365 の Windows PowerShell でのみ行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d591a-110">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="d591a-111">シンジケート パートナーと CSP パートナーが顧客テナンシーを管理するために最もよく使用するシナリオのサンプルは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d591a-111">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="d591a-112">委任アクセス許可 (DAP) パートナー用 Windows PowerShell で Microsoft 365 テナントを管理する</span><span class="sxs-lookup"><span data-stu-id="d591a-112">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="d591a-113">委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する</span><span class="sxs-lookup"><span data-stu-id="d591a-113">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="d591a-114">委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する</span><span class="sxs-lookup"><span data-stu-id="d591a-114">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="d591a-115">委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して顧客のテナント レポート データを取得する</span><span class="sxs-lookup"><span data-stu-id="d591a-115">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

