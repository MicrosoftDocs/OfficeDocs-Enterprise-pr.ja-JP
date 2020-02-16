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
description: Office 365 Multi-Geo でサテライトの場所を削除する方法について説明します。
ms.openlocfilehash: 702f42eb9211d6c3c4f59812c6894855b169f587
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974866"
---
# <a name="delete-a-satellite-location-in-office-365-multi-geo"></a><span data-ttu-id="073ef-103">Office 365 Multi-Geo でサテライトの場所を削除する</span><span class="sxs-lookup"><span data-stu-id="073ef-103">Delete a satellite location in Office 365 Multi-Geo</span></span>

<span data-ttu-id="073ef-104">サテライトの場所が不要になった場合は、SharePoint 管理センターのテナントから削除できます。</span><span class="sxs-lookup"><span data-stu-id="073ef-104">If you no longer need a satellite location, you can delete it from your tenant from the SharePoint admin center.</span></span>

> [!WARNING]
> <span data-ttu-id="073ef-105">すべてのサテライトの場所のユーザー データは永久に削除されます。</span><span class="sxs-lookup"><span data-stu-id="073ef-105">All user data in the satellite location will be permanently deleted.</span></span> <span data-ttu-id="073ef-106">これには、OneDrive for Business のすべてのコンテンツ、SharePoint サイト、および Office 365 グループ メール ボックスを含む Exchangeメール ボックスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="073ef-106">This includes all OneDrive for Business content, SharePoint sites and Exchange mailboxes including Office 365 Group mailboxes.</span></span> <span data-ttu-id="073ef-107">サテライトの場所を削除する前に、データを別のサテライトの場所または集中管理する場所に移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="073ef-107">You must migrate any data to another satellite location or the central location before you delete the satellite location.</span></span> <span data-ttu-id="073ef-108">この操作は元に戻せません。</span><span class="sxs-lookup"><span data-stu-id="073ef-108">This action cannot be undone.</span></span>

<span data-ttu-id="073ef-109">サテライトの場所はグローバル管理者のみが削除できます。</span><span class="sxs-lookup"><span data-stu-id="073ef-109">Only global administrators can delete satellite locations.</span></span>

![地理的位置の削除の UI を表示する Multi-Geo 管理センターのスクリーンショット](media/multi-geo-delete-satellite-location.png)

<span data-ttu-id="073ef-111">サテライトの場所を削除するには</span><span class="sxs-lookup"><span data-stu-id="073ef-111">To delete a satellite location</span></span>

1. <span data-ttu-id="073ef-112">SharePoint 管理センターを開きます。</span><span class="sxs-lookup"><span data-stu-id="073ef-112">Open the SharePoint admin center</span></span>

2. <span data-ttu-id="073ef-113">**[地理的位置]** タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="073ef-113">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="073ef-114">マップ上で削除する地理的位置をクリックします。</span><span class="sxs-lookup"><span data-stu-id="073ef-114">On the map, click the geo location that you want to delete.</span></span>

4. <span data-ttu-id="073ef-115">**[場所の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="073ef-115">Click **Delete location**.</span></span>

5. <span data-ttu-id="073ef-116">確認のチェック ボックスをオンにして、削除を確認します。</span><span class="sxs-lookup"><span data-stu-id="073ef-116">Confirm the deletion by selecting the confirmation check boxes.</span></span>

6. <span data-ttu-id="073ef-117">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="073ef-117">Click **Delete**.</span></span>
