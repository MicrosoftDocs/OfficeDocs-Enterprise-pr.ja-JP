---
title: Office 2013 および Office 2016 のクライアント アプリの先進認証のしくみ
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
description: Office 365 最新認証のしくみが異なる Office 2013 および 2016 クライアント アプリケーションについて説明します。
ms.openlocfilehash: 2a5e218ca751f341e2a3a0ffd164f000ee503279
ms.sourcegitcommit: fd7a56f38ba2c2d2e7fcd6e165ec58b31be299d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "27378503"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Office 2013 および Office 2016 のクライアント アプリの先進認証のしくみ

Office 365 テナントに認証の構成を Exchange Online、SharePoint Online では、Skype のオンライン ビジネスのに基づいて、Office 2013 および 2016 の Office クライアント アプリケーションの最新の認証機能を使用する方法を学習するには、この資料を参照してください。
  
## <a name="availability-of-modern-authentication-for-office-365-services"></a>Office 365 サービスの最新の認証の可用性

Office 365 サービスは、最新の認証の既定の状態は次のとおりです。
  
- オンラインの Exchange の既定で有効**に**します。[を有効または無効にする最新の認証では、Exchange オンライン](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662)を無効または有効にするを参照してください。 
    
- SharePoint Online に既定でオン**に**します。 
    
- Skype のオンライン ビジネスの既定で有効**に**します。オフまたはオンにするには、[現代の認証のビジネスのオンラインの Skype を有効にする](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)を参照してください。
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Office クライアント アプリケーションのサインインの問題

Office 2013 のクライアント アプリケーションは、既定で、従来の認証をサポートします。レガシは、サインインのマイクロソフト オンライン アシスタント認証または基本認証をサポートすることを意味します。クライアントは、Windows ではこれらのクライアントを最新の認証機能を使用するためには、レジストリ キーの設定があります。手順については、 [Windows デバイスでの Office 2013 の最新認証を有効にする](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910)を参照してください。
  
ビジネス用の Skype との連携について説明する[ビジネス用の Skype で最新の認証 (ADAL) を使用する方法](https://go.microsoft.com/fwlink/p/?LinkId=785431)を確認するには。 
  
2016 の Office クライアントは、既定では、最新の認証をサポートし、これらの新しいフローを使用するクライアントの操作は必要ありません。ただし、従来の認証を使用する明示的なアクションが必要です。
  
現代の認証を有効にするかどうかによって Office 365 サービスを使用して Office 2013 および Office 2016 のクライアント認証の動作を確認するのには以下のリンクをクリックします。
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

次の表は、最新の認証の有無にかかわらず、Exchange Online に接続するときに Office 2013 または Office 2016 のクライアント アプリケーションの認証の動作を説明します。
  
|Office クライアント アプリケーションのバージョン。|レジストリ キーが存在します。|現代の認証をします。|テナント (既定値) の最新の認証と認証動作が有効に。|現代の認証と認証動作電源をオフにテナント。|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |いいえ、または EnableADAL = 1  <br/> |Yes  <br/> |現代の認証が試みられます。現代認証接続を拒否して、基本認証が使用されます。テナントが有効でない場合、サーバーは最新の認証を拒否します。  <br/> |現代の認証が試みられます。現代認証接続を拒否して、基本認証が使用されます。テナントが有効でない場合、サーバーは最新の認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 1  <br/> |Yes  <br/> |現代の認証が試みられます。現代認証接続を拒否して、基本認証が使用されます。テナントが有効でない場合、サーバーは最新の認証を拒否します。  <br/> |現代の認証が試みられます。現代認証接続を拒否して、基本認証が使用されます。テナントが有効でない場合、サーバーは最新の認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |基本認証  <br/> |基本認証  <br/> |
|Office 2013  <br/> |いいえ  <br/> |いいえ  <br/> |基本認証  <br/> |基本認証  <br/> |
|Office 2013  <br/> |はい、EnableADAL = 1  <br/> |Yes  <br/> |現代の認証が試みられます。現代認証接続を拒否して、基本認証が使用されます。テナントが有効でない場合、サーバーは最新の認証を拒否します。  <br/> |現代の認証が試みられます。現代認証接続を拒否して、基本認証が使用されます。テナントが有効でない場合、サーバーは最新の認証を拒否します。  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

次の表は、最新の認証の有無にかかわらず、SharePoint Online に接続するときに Office 2013 または Office 2016 のクライアント アプリケーションの認証の動作を説明します。
  
|Office クライアント アプリケーションのバージョン。|レジストリ キーが存在します。|現代の認証をします。|テナント (既定値) の最新の認証と認証動作が有効に。|現代の認証と認証動作電源をオフにテナント。|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |いいえ、または EnableADAL = 1  <br/> |Yes  <br/> |現代認証のみです。  <br/> |接続に失敗しました。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 1  <br/> |Yes  <br/> |現代認証のみです。  <br/> |接続に失敗しました。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |マイクロソフト オンライン サインイン アシスタントのみです。  <br/> |マイクロソフト オンライン サインイン アシスタントのみです。  <br/> |
|Office 2013  <br/> |いいえ  <br/> |いいえ  <br/> |マイクロソフト オンライン サインイン アシスタントのみです。  <br/> |マイクロソフト オンライン サインイン アシスタントのみです。  <br/> |
|Office 2013  <br/> |はい、EnableADAL = 1  <br/> |Yes  <br/> |現代認証のみです。  <br/> |接続に失敗しました。  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business Online
<a name="BK_SFBO"> </a>

次の表は、接続するとき Skype オンライン ビジネスの最新の認証の有無にかかわらず、Office 2013 または 2016 の Office クライアント アプリケーションの認証の動作を説明します。
  
|Office クライアント アプリケーションのバージョン。|レジストリ キーが存在します。|現代の認証をします。|現代の認証と認証動作が有効のテナント。|テナント (既定値) の最新の認証と認証動作が無効になって。|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |いいえ、または EnableADAL = 1  <br/> |Yes  <br/> |現代の認証が試みられます。現代認証接続を拒否して、マイクロソフトのオンラインでサインイン アシスタントが使用されます。Skype オンライン ビジネスのテナントに対しては有効でない場合、サーバーは最新の認証を拒否します。  <br/> |現代の認証が試みられます。現代認証接続を拒否して、マイクロソフトのオンラインでサインイン アシスタントが使用されます。Skype オンライン ビジネスのテナントに対しては有効でない場合、サーバーは最新の認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 1  <br/> |Yes  <br/> |現代の認証が試みられます。現代認証接続を拒否して、マイクロソフトのオンラインでサインイン アシスタントが使用されます。Skype オンライン ビジネスのテナントに対しては有効でない場合、サーバーは最新の認証を拒否します。  <br/> |現代の認証が試みられます。現代認証接続を拒否して、マイクロソフトのオンラインでサインイン アシスタントが使用されます。Skype オンライン ビジネスのテナントに対しては有効でない場合、サーバーは最新の認証を拒否します。  <br/> |
|Office 2016  <br/> |はい、EnableADAL = 0  <br/> |いいえ  <br/> |マイクロソフト オンライン サインイン アシスタントのみです。  <br/> |マイクロソフト オンライン サインイン アシスタントのみです。  <br/> |
|Office 2013  <br/> |いいえ  <br/> |いいえ  <br/> |マイクロソフト オンライン サインイン アシスタントのみです。  <br/> |マイクロソフト オンライン サインイン アシスタントのみです。  <br/> |
|Office 2013  <br/> |はい、EnableADAL = 1  <br/> |Yes  <br/> |現代の認証が試みられます。現代認証接続を拒否して、マイクロソフトのオンラインでサインイン アシスタントが使用されます。Skype オンライン ビジネスのテナントに対しては有効でない場合、サーバーは最新の認証を拒否します。  <br/> |マイクロソフト オンライン サインイン アシスタントのみです。  <br/> |
   
## <a name="see-also"></a>関連項目

[Windows デバイスの Office 2013 の先進認証を有効にする](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[(Office 365 の管理者) の Office 365 の展開の多要素認証の計画](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[(エンドユーザー用) の 2 段階の検証を Office 365 にサインインします。](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)