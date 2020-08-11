---
title: Microsoft 365 のセッションタイムアウト
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- M365-security-compliance
description: セッションタイムアウトを使用して、Microsoft 365 クライアントアプリでのセキュリティと容易なアクセスのバランスを取る方法を説明します。
ms.openlocfilehash: 72146ca49e07bf3641982bc880897456699d0877
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605219"
---
# <a name="session-timeouts-for-microsoft-365"></a>Microsoft 365 のセッションタイムアウト

セッションの有効期限は、Microsoft 365 の認証の重要な部分であり、セキュリティのバランスの重要なコンポーネントであり、ユーザーが資格情報の入力を求められる回数です。
  
## <a name="session-times-for-microsoft-365-services"></a>Microsoft 365 サービスのセッション時間

ユーザーが Microsoft 365 web アプリまたはモバイルアプリのいずれかで認証を行うと、セッションが確立されます。 セッションの期間中は、ユーザーを再認証する必要はありません。 ユーザーがアクティブでないとき、ブラウザーまたはタブを閉じるとき、またはパスワードがリセットされたなどの理由で認証トークンの有効期限が切れたときに、セッションが期限切れになることがあります。 Microsoft 365 サービスでは、各サービスの一般的な使用に対応するセッションタイムアウトが異なります。
  
次の表に、Microsoft 365 サービスのセッション有効期間を示します。
  
|**Microsoft 365 サービス**|**セッションのタイムアウト**|
|:-----|:-----|
|Microsoft 365 管理センター  <br/> |管理センターの資格情報を8時間ごとに提供するように求められます。  <br/> |
|SharePoint Online  <br/> |ユーザーが **[サインイン状態を保持**] を選択した場合に限り、5日間非アクティブです。 以前のサインインから24時間以上経過した後に SharePoint Online にアクセスすると、タイムアウト値は5日にリセットされます。  <br/> |
|Outlook Web App  <br/> |6時間。  <br/> この値を変更するに[は、このコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=615378)の_Activityの authenticationtimeoutinterval_パラメーターを使用します。  <br/> |
|Azure Active Directory  <br/> (モダン認証が有効になっている Office 2013 Windows クライアントによって使用されます)  <br/> | モダン認証は、アクセストークンと更新トークンを使用して、Azure Active Directory を使用して Microsoft 365 リソースへのユーザーアクセスを許可します。 アクセストークンは、認証が成功した後に提供される JSON Web トークンで、1時間有効です。 有効期間の長い更新トークンも提供されます。 アクセストークンが期限切れになると、Office クライアントは有効な更新トークンを使用して新しいアクセストークンを取得します。 この exchange は、ユーザーの初期認証がまだ有効である場合に成功します。  <br/>  更新トークンは90日に有効であり、継続的に使用することで、失効するまで有効にすることができます。  <br/>  更新トークンは、次のようないくつかのイベントによって無効にすることができます。  <br/>  更新トークンが発行されてから、ユーザーのパスワードが変更されました。  <br/>  管理者は、ユーザーがアクセスしようとしているリソースへのアクセスを制限する条件付きアクセスポリシーを適用できます。  <br/> |
|Android、iOS、Windows 10 用の SharePoint および OneDrive モバイルアプリ  <br/> |アクセストークンの既定の有効期間は1時間です。 更新トークンの既定の最大非アクティブ時間は90日です。  <br/> [トークンの詳細とトークンの有効期間を構成する方法について](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> 更新トークンを取り消すには、ユーザーの Microsoft 365 パスワードをリセットします。  <br/> |
|Microsoft 365 サインインを使用した Yammer  <br/> |ブラウザーの有効期間。 ユーザーが新しいブラウザーでブラウザーを閉じて Yammer にアクセスすると、Yammer は Microsoft 365 を使用して再認証します。 ユーザーが cookie をキャッシュするサードパーティ製ブラウザーを使用している場合は、ブラウザーを再度開いたときに再認証する必要はありません。  <br/> > [!NOTE]> Yammer の Microsoft 365 サインインを使用しているネットワークに対してのみ有効です。           |
   

