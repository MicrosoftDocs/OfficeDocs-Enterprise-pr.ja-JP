---
title: Office 365 でのディレクトリ同期エラーの表示
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Microsoft 365 管理センターでディレクトリ同期エラーを表示する方法について説明します。
ms.openlocfilehash: 8450c2e26c9c9ae194be46d81018a20c91e35f29
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491267"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="f3b62-103">Office 365 でのディレクトリ同期エラーの表示</span><span class="sxs-lookup"><span data-stu-id="f3b62-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="f3b62-104">[Microsoft 365 管理センター](https://admin.microsoft.com)でディレクトリ同期エラーを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f3b62-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="f3b62-105">ユーザーオブジェクトのエラーのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3b62-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="f3b62-106">PowerShell を使用してエラーを表示するには、「 [dirsyncプロビジョニングエラーでオブジェクトを識別](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3b62-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="f3b62-107">表示された後、「 [Office 365 のディレクトリ同期に関する問題を解決](fix-problems-with-directory-synchronization.md)して、特定の問題を修正する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3b62-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="f3b62-108">管理センターでディレクトリ同期エラーを表示する</span><span class="sxs-lookup"><span data-stu-id="f3b62-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="f3b62-109">管理センターでエラーを表示するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="f3b62-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="f3b62-110">職場または学校のアカウントを使用して、Office 365 にサインインします。</span><span class="sxs-lookup"><span data-stu-id="f3b62-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="f3b62-111">[[管理センターについて](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)] に移動します。</span><span class="sxs-lookup"><span data-stu-id="f3b62-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="f3b62-112">**ホーム**ページに [ **DirSync Status** ] タイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3b62-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![管理センタープレビューの [DirSync Status] タイル](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="f3b62-114">タイルの [ **DirSync status** ] を選択して、[**ディレクトリ同期の状態**] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="f3b62-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="f3b62-115">ページの下部に、DirSync エラーがあるかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3b62-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![[ディレクトリ同期の状態] ページで、DirSync オブジェクトエラーが発生しているかどうかを確認できます。](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="f3b62-117">ディレクトリ同期エラーの詳細表示に移動するには、 **DirSync オブジェクトのエラーが検出**されたことを選択します。</span><span class="sxs-lookup"><span data-stu-id="f3b62-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="f3b62-118">dirsync の**状態**のタイルで**dirsync オブジェクトのエラーが検出**された場合は、[ **dirsync errors** ] ページに移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="f3b62-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![DirSync errors ページ](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="f3b62-120">[ **DirSync errors** ] ページで、表示されているいずれかのエラーを選択して詳細ウィンドウにエラーに関する情報とその修正方法に関するヒントを表示します。</span><span class="sxs-lookup"><span data-stu-id="f3b62-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
