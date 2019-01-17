---
title: Office 365 のディレクトリ同期のエラーを表示します
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Office 365 管理センターのディレクトリ同期のエラーを表示する方法について説明します。
ms.openlocfilehash: 8beeeebbb24936abd7c93f4c04c0fa4e27c85c12
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327339"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="f5ba3-103">Office 365 のディレクトリ同期のエラーを表示します</span><span class="sxs-lookup"><span data-stu-id="f5ba3-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="f5ba3-p101">Office 365 の管理センターでは、ディレクトリ同期のエラーを表示できます。ユーザー オブジェクトのエラーのみが表示されます。PowerShell を使用してエラーを表示するには、 [DirSyncProvisioningErrors を識別するオブジェクト](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="f5ba3-107">表示後、は、特定された問題を修正するのには[Office 365 のディレクトリ同期の問題を解決する](fix-problems-with-directory-synchronization.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="f5ba3-108">管理センターのディレクトリ同期のエラーを表示します。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="f5ba3-109">管理センターのすべてのエラーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="f5ba3-110">職場または学校のアカウントを使用して、Office 365 にサインインします。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="f5ba3-111">[[Office 365 の管理センター](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)に移動します。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="f5ba3-112">**[ホーム**] ページで、**ディレクトリ同期の状態**のタイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![管理センターのプレビュー] で、ディレクトリ同期の状態を並べて表示します。](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="f5ba3-114">並べて表示]、[**ディレクトリ同期の状態**] ページに移動するのには**ディレクトリ同期のステータス**を選択します。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="f5ba3-115">ページの下部には、ディレクトリ同期のエラーがあるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![[ディレクトリ同期の状態] ページで、ディレクトリ同期オブジェクトのエラーがあるかどうかを確認できます。](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="f5ba3-117">**ディレクトリ同期オブジェクトのエラーを検出**ディレクトリ同期のエラーの詳細なビューに移動するを選択します。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="f5ba3-118">[**ディレクトリ同期の状態**] タイル**ディレクトリ同期オブジェクトのエラーが検出されたこと**を選択した場合も、目的の**ディレクトリ同期のエラー**ページに移動できます。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![ディレクトリ同期エラーのページ](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="f5ba3-120">**ディレクトリ同期エラー** ] ページで、エラーとその修正方法に関するヒントについての情報の詳細ペインを表示するには、エラーのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f5ba3-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
