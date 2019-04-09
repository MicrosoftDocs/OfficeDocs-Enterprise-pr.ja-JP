---
title: Office 365 クライアントアプリケーションのサポート-モバイルアプリケーション管理
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: モバイルアプリケーション管理のための Office 365 クライアントアプリケーションサポートについて
ms.openlocfilehash: b75b992bf45ff1a899e71a9f6b7903e3f78a34d4
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517551"
---
# <a name="office-365-client-app-support---mobile-application-management"></a><span data-ttu-id="13d95-103">Office 365 クライアントアプリケーションのサポート-モバイルアプリケーション管理</span><span class="sxs-lookup"><span data-stu-id="13d95-103">Office 365 Client App Support - Mobile Application Management</span></span>

<span data-ttu-id="13d95-104">Intune 管理機能のスイートを利用することにより、モバイルアプリケーション管理 (MAM) を使用して、ユーザーのモバイルアプリの公開、プッシュ、構成、セキュリティで保護、監視、および更新を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="13d95-104">Leveraging the suite of Intune management features, mobile application management (MAM) lets you publish, push, configure, secure, monitor, and update mobile apps for your users.</span></span> <span data-ttu-id="13d95-105">MAM では、Intune に登録されているかどうかにかかわらず、アプリケーション内のすべてのデバイスに対して組織のデータを保護することができます。</span><span class="sxs-lookup"><span data-stu-id="13d95-105">MAM can protect an organization's data within an application for all devices, whether enrolled in Intune or not.</span></span>

<span data-ttu-id="13d95-106">詳細については、「[モバイルアプリケーション管理](https://docs.microsoft.com/intune/mam-faq)と[マルチ id MAM](https://docs.microsoft.com/intune/app-protection-policy)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13d95-106">Learn more about [mobile application management](https://docs.microsoft.com/intune/mam-faq) and [multi-identity MAM](https://docs.microsoft.com/intune/app-protection-policy).</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="13d95-107">サポートされるプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="13d95-107">Supported platforms</span></span>

 - <span data-ttu-id="13d95-108">Android</span><span class="sxs-lookup"><span data-stu-id="13d95-108">Android</span></span>
 - <span data-ttu-id="13d95-109">iOS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="13d95-109">iOS<sup>1</sup></span></span>

<span data-ttu-id="13d95-110">office 365 のプラットフォームサポートの詳細については、「 [office 365 のシステム要件](https://products.office.com/office-system-requirements)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13d95-110">For more information about platform support in Office 365, see [System requirements for Office 365](https://products.office.com/office-system-requirements).</span></span>

## <a name="supported-clients"></a><span data-ttu-id="13d95-111">サポートされるクライアント</span><span class="sxs-lookup"><span data-stu-id="13d95-111">Supported clients</span></span>

<span data-ttu-id="13d95-112">次のクライアントの最新バージョンは、モバイルアプリケーション管理をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="13d95-112">The latest versions of the following clients support mobile application management:</span></span>

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Dynamics 365 アイコン](media/o365-dynamics365-64x64.png) <br> [<span data-ttu-id="13d95-114">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="13d95-114">Dynamics 365</span></span>](https://dynamics.microsoft.com) | ![エッジアイコン](media/o365-edge-64x64.png) <br> [<span data-ttu-id="13d95-116">エッジ</span><span class="sxs-lookup"><span data-stu-id="13d95-116">Edge</span></span>](https://www.microsoft.com/windows/microsoft-edge) | ![[Excel] アイコン](media/o365-excel-64x64.png) <br> [<span data-ttu-id="13d95-118">Excel</span><span class="sxs-lookup"><span data-stu-id="13d95-118">Excel</span></span>](https://products.office.com/excel) | ![フローアイコン](media/o365-flow-64x64.png) <br> [<span data-ttu-id="13d95-120">フロー</span><span class="sxs-lookup"><span data-stu-id="13d95-120">Flow</span></span>](https://flow.microsoft.com) | ![Kaizala アイコン](media/o365-kaizala-64x64.png) <br> [<span data-ttu-id="13d95-122">Kaizala</span><span class="sxs-lookup"><span data-stu-id="13d95-122">Kaizala</span></span>](https://products.office.com/en/business/microsoft-kaizala) 
| ![OneDrive for business アイコン](media/o365-OneDrive-64x64.png) <br> [<span data-ttu-id="13d95-124">OneDrive</span><span class="sxs-lookup"><span data-stu-id="13d95-124">OneDrive</span></span>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote アイコン](media/o365-OneNote-64x64.png) <br> [<span data-ttu-id="13d95-126">OneNote</span><span class="sxs-lookup"><span data-stu-id="13d95-126">OneNote</span></span>](https://products.office.com/onenote) | ![Outlook アイコン](media/o365-outlook-64x64.png) <br> [<span data-ttu-id="13d95-128">Outlook</span><span class="sxs-lookup"><span data-stu-id="13d95-128">Outlook</span></span>](https://products.office.com/outlook) | ![Planner アイコン](media/o365-planner-64x64.png) <br> [<span data-ttu-id="13d95-130">プランナー</span><span class="sxs-lookup"><span data-stu-id="13d95-130">Planner</span></span>](https://products.office.com/business/task-management-software) | ![PowerApps アイコン](media/o365-powerapps-64x64.png) <br> [<span data-ttu-id="13d95-132">PowerApps</span><span class="sxs-lookup"><span data-stu-id="13d95-132">PowerApps</span></span> ](https://powerapps.microsoft.com) 
| ![PowerBI アイコン](media/o365-powerbi-64x64.png) <br> [<span data-ttu-id="13d95-134">Power BI</span><span class="sxs-lookup"><span data-stu-id="13d95-134">Power BI</span></span>](https://powerbi.microsoft.com) | ![[PowerPoint] アイコン](media/o365-powerpoint-64x64.png) <br> [<span data-ttu-id="13d95-136">PowerPoint</span><span class="sxs-lookup"><span data-stu-id="13d95-136">PowerPoint</span></span>](https://products.office.com/powerpoint) | ![SharePoint アイコン](media/o365-sharepoint-64x64.png) <br> [<span data-ttu-id="13d95-138">Sharepoint</span><span class="sxs-lookup"><span data-stu-id="13d95-138">Sharepoint</span></span>](https://products.office.com/sharepoint) | ![Skype for business アイコン](media/o365-skypeforbusiness-64x64.png) <br> [<span data-ttu-id="13d95-140">Skype for <br> business</span><span class="sxs-lookup"><span data-stu-id="13d95-140">Skype for <br> Business</span></span>](https://www.skype.com/business/) | ![StaffHub アイコン](media/o365-staffhub-64x64.png) <br> [<span data-ttu-id="13d95-142">StaffHub</span><span class="sxs-lookup"><span data-stu-id="13d95-142">StaffHub</span></span>](https://products.office.com/microsoft-staffhub/staff-scheduling-software) 
| ![ストリームアイコン](media/o365-stream-64x64.png) <br> [<span data-ttu-id="13d95-144">Stream</span><span class="sxs-lookup"><span data-stu-id="13d95-144">Stream</span></span>](https://stream.microsoft.com) | ![Sway アイコン](media/o365-sway-64x64.png) <br> [<span data-ttu-id="13d95-146">Sway<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="13d95-146">Sway<sup>1</sup></span></span>](https://sway.com) | ![Teams アイコン](media/o365-teams-64x64.png) <br> [<span data-ttu-id="13d95-148">チーム</span><span class="sxs-lookup"><span data-stu-id="13d95-148">Teams</span></span>](https://products.office.com/microsoft-teams/group-chat-software) | ![To do アイコン](media/o365-todo-64x64.png) <br> [<span data-ttu-id="13d95-150">To Do</span><span class="sxs-lookup"><span data-stu-id="13d95-150">To-Do</span></span>](https://todo.microsoft.com) | ![Visio アイコン](media/o365-visio-64x64.png) <br> [<span data-ttu-id="13d95-152">Visio</span><span class="sxs-lookup"><span data-stu-id="13d95-152">Visio</span></span>](https://products.office.com/visio/flowchart-software) 
| ![[Word] アイコン](media/o365-word-64x64.png) <br> [<span data-ttu-id="13d95-154">Word</span><span class="sxs-lookup"><span data-stu-id="13d95-154">Word</span></span>](https://products.office.com/word) | ![Yammer アイコン](media/o365-yammer-64x64.png) <br> [<span data-ttu-id="13d95-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="13d95-156">Yammer</span></span>](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <span data-ttu-id="13d95-157"><sup>1</sup> iOS での Sway のサポートが近日中に提供されます。</span><span class="sxs-lookup"><span data-stu-id="13d95-157"><sup>1</sup> Support for Sway on iOS coming soon.</span></span>