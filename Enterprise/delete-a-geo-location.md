---
title: サテライトの場所を削除する
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Office 365 Multi-Geo でサテライトの場所を削除する方法を説明します。
ms.openlocfilehash: 840c1bf494ddcd7e6558b134655b5cb708bf6e7b
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057643"
---
# <a name="delete-a-satellite-location-in-microsoft-365-multi-geo"></a><span data-ttu-id="4a569-103">Office 365 Multi-Geo でサテライトの場所を削除する</span><span class="sxs-lookup"><span data-stu-id="4a569-103">Delete a satellite location in Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="4a569-104">サテライトの場所が不要になった場合は、SharePoint 管理センターのテナントから削除できます。</span><span class="sxs-lookup"><span data-stu-id="4a569-104">If you no longer need a satellite location, you can delete it from your tenant from the SharePoint admin center.</span></span>

> [!WARNING]
> <span data-ttu-id="4a569-105">すべてのサテライトの場所のユーザー データは永久に削除されます。</span><span class="sxs-lookup"><span data-stu-id="4a569-105">All user data in the satellite location will be permanently deleted.</span></span> <span data-ttu-id="4a569-106">これには、すべての OneDrive for Business コンテンツ、SharePoint サイトと Exchange メールボックス (Microsoft 365 グループ メールボックスを含む) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4a569-106">This includes all OneDrive for Business content, SharePoint sites and Exchange mailboxes including Microsoft 365 Group mailboxes.</span></span> <span data-ttu-id="4a569-107">サテライトの場所を削除する前に、データを別のサテライトの場所または集中管理する場所に移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a569-107">You must migrate any data to another satellite location or the central location before you delete the satellite location.</span></span> <span data-ttu-id="4a569-108">この操作は元に戻せません。</span><span class="sxs-lookup"><span data-stu-id="4a569-108">This action cannot be undone.</span></span>

<span data-ttu-id="4a569-109">サテライトの場所はグローバル管理者のみが削除できます。</span><span class="sxs-lookup"><span data-stu-id="4a569-109">Only global administrators can delete satellite locations.</span></span>

![地理的位置の削除の UI を表示する Multi-Geo 管理センターのスクリーンショット](media/multi-geo-delete-satellite-location.png)

<span data-ttu-id="4a569-111">サテライトの場所を削除するには</span><span class="sxs-lookup"><span data-stu-id="4a569-111">To delete a satellite location</span></span>

1. <span data-ttu-id="4a569-112">SharePoint 管理センターを開きます。</span><span class="sxs-lookup"><span data-stu-id="4a569-112">Open the SharePoint admin center</span></span>

2. <span data-ttu-id="4a569-113">**[地理的位置]** タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="4a569-113">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="4a569-114">マップ上で削除する地理的位置をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4a569-114">On the map, click the geo location that you want to delete.</span></span>

4. <span data-ttu-id="4a569-115">**[場所の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4a569-115">Click **Delete location**.</span></span>

5. <span data-ttu-id="4a569-116">確認のチェック ボックスをオンにして、削除を確認します。</span><span class="sxs-lookup"><span data-stu-id="4a569-116">Confirm the deletion by selecting the confirmation check boxes.</span></span>

6. <span data-ttu-id="4a569-117">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4a569-117">Click **Delete**.</span></span>
