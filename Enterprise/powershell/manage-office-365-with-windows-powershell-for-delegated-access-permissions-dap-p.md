---
title: 委任アクセス許可 (DAP) パートナー用 Windows PowerShell で Office 365 を管理する
ms.author: chrfox
author: chrfox
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
description: 概要:シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナー は Windows PowerShell を使用して Office 365 の顧客テナントを管理できます。
ms.openlocfilehash: 35aca54af9dcfb6c9aa31c893f7213b053e111d2
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004170"
---
# <a name="manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="b2fad-103">委任アクセス許可 (DAP) パートナー用 Windows PowerShell で Office 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="b2fad-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="b2fad-104">**概要:** シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーは Windows PowerShell を使用して Office 365 の顧客テナントを管理できます。</span><span class="sxs-lookup"><span data-stu-id="b2fad-104">**Summary:** Syndication and Cloud Solution Provider (CSP) partners can use Windows PowerShell to manage Office 365 customer tenants.</span></span>
  
<span data-ttu-id="b2fad-105">委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。</span><span class="sxs-lookup"><span data-stu-id="b2fad-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="b2fad-106">他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。</span><span class="sxs-lookup"><span data-stu-id="b2fad-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="b2fad-107">それらの企業は、顧客に提供するサービスに Office 365 サブスクリプションをバンドルします。</span><span class="sxs-lookup"><span data-stu-id="b2fad-107">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="b2fad-108">Office 365のサブスクリプションを販売する際に、顧客テナンシーに対する「代理で管理」(AOBO) 権限が自動的に付与されるため、顧客テナンシーを管理し、顧客テナンシーに関するレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b2fad-108">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="b2fad-109">このことは、Microsoft 365 管理センターでは、非常に困難で時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="b2fad-109">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="b2fad-110">顧客の **テナント ID** とそのドメインをすべて一覧表示する、または顧客テナンシーのユーザーおよび割り当てられているライセンスをすべて特定するなどの管理タスクは Office 365 の Windows PowerShell を使用して行う方がはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="b2fad-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="b2fad-111">場合によっては、これらの管理タスクは Office 365 の Windows PowerShell でのみ行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b2fad-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="b2fad-112">シンジケート パートナーと CSP パートナーが顧客テナンシーを管理するために最もよく使用するシナリオのサンプルは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b2fad-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="b2fad-113">委任アクセス許可 (DAP) パートナー用 Windows PowerShell で Office 365 テナントを管理する</span><span class="sxs-lookup"><span data-stu-id="b2fad-113">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="b2fad-114">委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する</span><span class="sxs-lookup"><span data-stu-id="b2fad-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="b2fad-115">委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する</span><span class="sxs-lookup"><span data-stu-id="b2fad-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="b2fad-116">委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して顧客のテナント レポート データを取得する</span><span class="sxs-lookup"><span data-stu-id="b2fad-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

