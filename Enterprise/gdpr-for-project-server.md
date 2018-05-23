---
title: Project Server の GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: オンプレミスの Project Server で GDPR の要件に対応する方法について説明します。
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a><span data-ttu-id="bdea2-103">Project Server の GDPR</span><span class="sxs-lookup"><span data-stu-id="bdea2-103">Plan for Project Server</span></span>

<span data-ttu-id="bdea2-p101">Project Server では、Project Web App でユーザー データをエクスポートしたり編集したりするために、カスタム スクリプトが使用されます。基本的な処理は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdea2-p101">Project Server uses custom scripts to export and redact user data in Project Web App. The basic process is:</span></span>

1.  <span data-ttu-id="bdea2-106">ファーム内で Project Web App のサイトを検索します。</span><span class="sxs-lookup"><span data-stu-id="bdea2-106">Find the Project Web App sites in your farm.</span></span>

2.  <span data-ttu-id="bdea2-107">各サイトの中で、ユーザーが含まれているプロジェクトを検索します。</span><span class="sxs-lookup"><span data-stu-id="bdea2-107">Find the projects in each site that contain the user.</span></span>

3.  <span data-ttu-id="bdea2-108">確認対象となるタイプのデータをエクスポートし、確認します。</span><span class="sxs-lookup"><span data-stu-id="bdea2-108">Export and review the types of data that you want to review.</span></span>

4.  <span data-ttu-id="bdea2-109">必要に応じてデータを編集します。</span><span class="sxs-lookup"><span data-stu-id="bdea2-109">Redact data as needed.</span></span>

<span data-ttu-id="bdea2-110">これらの手順について、以下の記事で詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="bdea2-110">These three scenarios are covered in detail in the following articles:</span></span>

- [<span data-ttu-id="bdea2-111">Project Server からユーザー データをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="bdea2-111">Export user data from Project Server</span></span>](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [<span data-ttu-id="bdea2-112">Project Server からユーザー データを削除する</span><span class="sxs-lookup"><span data-stu-id="bdea2-112">Delete user data from Project Server</span></span>](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


<span data-ttu-id="bdea2-113">Project Server は SharePoint Server 上に構築されており、SharePoint ULS のログおよび利用状況データベースにイベントのログが出力されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bdea2-113">Note that Project Server is built on top of SharePoint Server and logs events to the SharePoint ULS logs and Usage database.</span></span>
