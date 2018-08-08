---
title: Office 365 クライアント アプリケーションのサポート - 条件付きアクセス
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
ms.collection: Strat_O365_Enterprise
description: Office 365 の条件付きアクセスのクライアント ・ アプリケーション ・ サポートを理解します。
ms.openlocfilehash: f9a1b4c022b00569a392d7f50bfcae583847ea3c
ms.sourcegitcommit: 4e654517825b74a3bbe171b915b134ba49231e2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2018
ms.locfileid: "21541967"
---
# <a name="office-365-client-app-support---conditional-access"></a>Office 365 クライアント アプリケーションのサポート - 条件付きアクセス

現代の職場では、ユーザーがどこからさまざまなデバイスやアプリケーションを使用して、組織のリソースをアクセスできます。その結果、リソースにアクセスできるユーザーにのみ焦点を当ててもはやではないための十分です。組織は、リソースのアクセス制御インフラストラクチャにアクセスされている場所と方法もサポートしなければなりません。Azure AD のデバイス、場所、および多要素認証に基づく条件付きのアクセスを持つには、この新しい要件を満たします。条件付きのアクセスは、Azure の Active Directory を使用すると、環境内で特定の条件に基づいてすべてのアプリケーションへのアクセスを制御し、中央の場所から管理の機能です。 

[デバイス ベース](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications)、[場所に基づく](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations)し、 [MFA ベース](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups)の条件付きアクセスの詳細を表示します。

## <a name="supported-platforms"></a>サポートされるプラットフォーム

 - 10 の Windows デスクトップ
 - 新しいアプリが Windows 10
 - Web ブラウザー
 - Android
 - iOS
 - macOS<sup>1</sup>

## <a name="supported-clients"></a>サポートされるクライアント

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![アイコンを説明します。](images/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![[Excel] アイコン](images/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![フロー アイコン](images/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![フォーム アイコン](images/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala アイコン](images/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office 365 管理者アイコン](images/o365-o365admin-64x64.png) <br> [Office 365<br>管理](https://products.office.com/business/manage-office-365-admin-app) | ![ビジネスのアイコンを OneDrive](images/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote アイコン](images/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook のアイコン](images/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![プランナーのアイコン](images/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) 
| ![PowerBI アイコン](images/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![[PowerPoint] アイコン](images/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![プロジェクト アイコン](images/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint のアイコン](images/o365-sharepoint-64x64.png) <br> [Sharepoint<sup>1</sup>](https://products.office.com/sharepoint) | ![Skype ビジネスのアイコン](images/o365-skypeforbusiness-64x64.png) <br> [Skype<br>ビジネス](https://www.skype.com/business/) 
| ![StaffHub アイコン](images/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![ストリーム アイコン](images/o365-stream-64x64.png) <br> [ストリーム](https://stream.microsoft.com) | ![アイコンをかきたてる](images/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![チーム アイコン](images/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![タスク アイコン](images/o365-todo-64x64.png) <br> [To Do](https://todo.microsoft.com) 
| ![Visio アイコン](images/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![[Word] アイコン](images/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer のアイコン](images/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> MacOS の準備中で SharePoint アプリケーションをサポートする<sup>1</sup> 。