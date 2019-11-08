---
title: Office 365 のセッションタイムアウト
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- M365-security-compliance
description: セッションタイムアウトを使用して、Office 365 クライアントアプリでのセキュリティと容易なアクセスのバランスを取ることができます。
ms.openlocfilehash: e39d578f0a5f193691724e3b3a0c42db0ad1011b
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030922"
---
# <a name="session-timeouts-for-office-365"></a>Office 365 のセッションタイムアウト

セッションの有効期限は、Office 365 の認証の重要な部分であり、セキュリティのバランスの重要なコンポーネントであり、ユーザーが資格情報の入力を求められる回数です。
  
## <a name="session-times-for-office-365-services"></a>Office 365 サービスのセッション時間

ユーザーが Office 365 web apps またはモバイルアプリのいずれかで認証を行うと、セッションが確立されます。 セッションの期間中は、ユーザーを再認証する必要はありません。 ユーザーがアクティブでないとき、ブラウザーまたはタブを閉じるとき、またはパスワードがリセットされたなどの理由で認証トークンの有効期限が切れたときに、セッションが期限切れになることがあります。 Office 365 サービスのセッションタイムアウトは、各サービスの一般的な使用に対応しています。
  
次の表に、Office 365 サービスのセッション有効期間を示します。
  
|**Office 365 サービス**|**セッションのタイムアウト**|
|:-----|:-----|
|Microsoft 365 管理センター  <br/> |管理センターの資格情報を8時間ごとに提供するように求められます。  <br/> |
|SharePoint Online  <br/> |ユーザーが **[サインイン状態を保持**] を選択した場合に限り、5日間非アクティブです。 以前のサインインから24時間以上経過した後に SharePoint Online にアクセスすると、タイムアウト値は5日にリセットされます。  <br/> |
|Outlook Web App  <br/> |6時間。  <br/> この値を変更するに[は、このコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=615378)の_Activityの authenticationtimeoutinterval_パラメーターを使用します。  <br/> |
|Azure Active Directory  <br/> (モダン認証が有効になっている Office 2013 Windows クライアントによって使用されます)  <br/> | モダン認証は、アクセストークンと更新トークンを使用して、Azure Active Directory を使用して Office 365 リソースへのユーザーアクセスを付与します。 アクセストークンは、認証が成功した後に提供される JSON Web トークンで、1時間有効です。 有効期間の長い更新トークンも提供されます。 アクセストークンが期限切れになると、Office クライアントは有効な更新トークンを使用して新しいアクセストークンを取得します。 この exchange は、ユーザーの初期認証がまだ有効である場合に成功します。  <br/>  更新トークンは90日に有効であり、継続的に使用することで、失効するまで有効にすることができます。  <br/>  更新トークンは、次のようないくつかのイベントによって無効にすることができます。  <br/>  更新トークンが発行されてから、ユーザーのパスワードが変更されました。  <br/>  管理者は、ユーザーがアクセスしようとしているリソースへのアクセスを制限する条件付きアクセスポリシーを適用できます。  <br/> |
|Android、iOS、Windows 10 用の SharePoint および OneDrive モバイルアプリ  <br/> |アクセストークンの既定の有効期間は1時間です。 更新トークンの既定の最大非アクティブ時間は90日です。  <br/> [トークンの詳細とトークンの有効期間を構成する方法について](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> 更新トークンを取り消すには、ユーザーの Office 365 パスワードをリセットします。  <br/> |
|Office 365 サインインを使用する Yammer  <br/> |ブラウザーの有効期間。 ユーザーが新しいブラウザーでブラウザーを終了し、Yammer にアクセスすると、Yammer は Office 365 を使用してそれらを再認証します。 ユーザーが cookie をキャッシュするサードパーティ製ブラウザーを使用している場合は、ブラウザーを再度開いたときに再認証する必要はありません。  <br/> > [!NOTE]> Yammer の Office 365 サインインを使用しているネットワークに対してのみ有効です。           |
   

