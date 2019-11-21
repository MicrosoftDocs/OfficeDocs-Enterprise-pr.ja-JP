---
title: Office 365 のサード パーティ SSL 証明書の計画
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: '概要: Exchange の社内およびハイブリッドに必要な SSL 証明書、AD FS を使用する SSO、Exchange Online サービス、および Exchange Web サービスについて説明します。'
ms.openlocfilehash: 74540fb612bd515443912114ebec20cd8ed5e1aa
ms.sourcegitcommit: 6639b0f0171f7552111267a64d6b199755bf34fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "38756616"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Office 365 のサード パーティ SSL 証明書の計画

*この記事は、Office 365 Enterprise と Microsoft 365 Enterprise の両方に適用されます。*

クライアントと Office 365 環境の間の通信を暗号化するには、サードパーティの Secure Sockets Layer (SSL) 証明書をインフラストラクチャサーバーにインストールする必要があります。

||
|:-----|
| この記事は[、Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。|
   
次の Office 365 コンポーネントには、証明書が必要です。
  
- オンプレミスの Exchange
    
- シングルサインオン (SSO) (Active Directory フェデレーションサービス (AD FS) フェデレーションサーバーと AD FS フェデレーションサーバープロキシの両方)
    
- Exchange Online サービス (自動検出、Outlook Anywhere、Exchange Web サービスなど)
    
- Exchange ハイブリッドサーバー
    
## <a name="certificates-for-exchange-on-premises"></a>オンプレミスの Exchange の証明書

デジタル証明書を使用してオンプレミスの Exchange 組織と Exchange Online の間の通信を確立する方法の概要については、TechNet の記事「[証明書の要件につい](https://go.microsoft.com/fwlink/p/?LinkID=243657)て」を参照してください。
  
## <a name="certificates-for-single-sign-on"></a>シングルサインオンの証明書

堅牢なセキュリティを備えたシングルサインオンのシンプルな操作性をユーザーに提供するには、フェデレーションサーバーまたはフェデレーションサーバープロキシのどちらかに、次の表に示す証明書が必要です。 下の表では、Active Directory フェデレーションサービス (AD FS) について重点的に説明します。また、[サードパーティの id プロバイダーを使用する方法](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)についても詳しく説明します。
  
||||
|:-----|:-----|:-----|
|**証明書の種類** <br/> |**説明** <br/> |**を展開する前に把握しておくべき情報** <br/> |
|**SSL 証明書 (サーバー認証証明書とも呼ばれる)** <br/> |これは、フェデレーションサーバー、クライアント、およびフェデレーションサーバープロキシコンピューター間の通信をセキュリティで保護するために使用される標準の SSL 証明書です。  <br/> |AD FS には SSL 証明書が必要です。 既定では、AD FS は、インターネットインフォメーションサービス (IIS) 内の既定の web サイトに対して構成された SSL 証明書を使用します。  <br/> この SSL 証明書のサブジェクト名は、展開する AD FS の各インスタンスのフェデレーションサービス (FS) 名を決定するために使用されます。 Office 365 に対して会社または組織の名前を最もよく表す新しい証明機関 (CA) で発行された証明書のサブジェクト名を選択することを検討してください。 この名前は、インターネット経由でルーティング可能である必要があります。  <br/>**注意:** AD FS では、この SSL 証明書に、ドット形式 (省略形) のサブジェクト名が含まれていないことが必要です。          <br/> **推奨事項:** この証明書は AD FS のクライアントによって信頼される必要があるため、パブリック (サードパーティ) CA または公的に信頼されたルートに従属する CA によって発行される SSL 証明書を使用することをお勧めします。たとえば、VeriSign または Thawte のようになります。  <br/> |
|**トークン署名証明書** <br/> |これは、フェデレーションサーバーが発行するすべてのトークンに安全に署名するために使用される標準の x.509 証明書で、Office 365 が受け入れて検証します。  <br/> |トークン署名証明書には、FS の信頼されたルートにチェーンする秘密キーが含まれている必要があります。 既定では、AD FS は自己署名証明書を作成します。 ただし、組織のニーズによっては、AD FS 管理スナップインを使用して、この証明書を CA によって発行された証明書に変更することができます。  <br/>**注意:** トークン署名証明書は、FS の安定性にとって重要です。 証明書が変更された場合、Office 365 に変更を通知する必要があります。 通知が提供されていない場合、ユーザーは Office 365 サービスオファーリングにサインインできません。<br/>**推奨事項:** AD FS によって生成される自己署名入りのトークン署名証明書を使用することをお勧めします。 これにより、既定でこの証明書が管理されます。 たとえば、この証明書が期限切れになると、AD FS は新しい自己署名証明書を生成します。  <br/> |
   
フェデレーションサーバープロキシには、次の表に記載されている証明書が必要です。
  
||||
|:-----|:-----|:-----|
|**証明書の種類** <br/> |**説明** <br/> |**を展開する前に把握しておくべき情報** <br/> |
|SSL 証明書  <br/> |これは、フェデレーションサーバー、フェデレーションサーバープロキシ、およびインターネットクライアントコンピューター間の通信をセキュリティで保護するために使用される標準の SSL 証明書です。  <br/> |AD FS フェデレーションサーバープロキシ構成ウィザードを正常に実行するには、この SSL 証明書を IIS の既定の web サイトにバインドする必要があります。  <br/> この証明書のサブジェクト名は、企業ネットワークのフェデレーションサーバーで構成された SSL 証明書と同じである必要があります。  <br/> **推奨事項:** このフェデレーションサーバープロキシが接続するフェデレーションサーバーで構成されているのと同じサーバー認証証明書を使用することをお勧めします。  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>自動検出、Outlook Anywhere、および Active Directory 同期の証明書

外部に接続された Exchange 2013、Exchange 2010、Exchange 2007、および Exchange 2003 クライアントアクセスサーバー (CASs) には、自動検出、Outlook Anywhere、および Active Directory 同期サービスのために、サードパーティの SSL 証明書が必要です。 この証明書は、オンプレミス環境に既にインストールされている可能性があります。
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Exchange ハイブリッドサーバーの証明書

外部に接続された Exchange ハイブリッドサーバーでは、Exchange Online サービスとの接続をセキュリティで保護するために、サードパーティの SSL 証明書が必要です。 この証明書は、サードパーティの SSL プロバイダーから入手する必要があります。
  
## <a name="office-365-certificate-chains"></a>Office 365 証明書チェーン

この記事では、インフラストラクチャにインストールする必要がある証明書について説明します。 Office 365 サーバーにインストールされている証明書の詳細については、「 [office 365 証明書チェーン](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)」を参照してください。
  
## <a name="see-also"></a>関連項目

[Microsoft 365 Enterprise の概要](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
