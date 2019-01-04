---
title: Office 365 のサード パーティ SSL 証明書の計画
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 概要:Exchange の社内およびハイブリッドと、AD FS、Exchange Online サービス、Exchange Web サービスを使用した SSO に必要な SSL 証明書について説明します。
ms.openlocfilehash: c9e968ef7ec9015be398b4eef9184451dd316bea
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546518"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Office 365 のサード パーティ SSL 証明書の計画

 **の概要:** Exchange の設置型とハイブリッドに、AD FS を使用して SSO に必要な SSL 証明書を説明し、Exchange のオンライン サービスは、Exchange Web サービス。 
  
クライアントと Office 365 環境の間の通信を暗号化するには、インフラストラクチャ サーバーのサード ・ パーティ製のセキュア ソケット レイヤー (SSL) 証明書をインストールしなければなりません。

||
|:-----|
| この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)の一部です。|
   
証明書は、次の Office 365 コンポーネントに必要となります。
  
- Exchange on-premises
    
- シングル サインオン (SSO) (Active Directory Federation Services (AD FS) フェデレーション サーバーと AD FS フェデレーション サーバー プロキシの両方)
    
- 自動検出、Outlook Anywhere では、Exchange Web サービスなどの Exchange のオンライン サービス
    
- Exchange ハイブリッド サーバー
    
## <a name="certificates-for-exchange-on-premises"></a>Exchange On-Premises のための証明書

TechNet の記事「[証明書要件について](https://go.microsoft.com/fwlink/p/?LinkID=243657)を参照してくださいくださいオンプレミスの Exchange 組織と Exchange Online との間の通信をセキュリティで保護されたデジタル証明書を使用する方法について説明します。
  
## <a name="certificates-for-single-sign-on"></a>シングル サインオンの証明書

ユーザーに提供する、シンプルなシングル サインオン エクスペリエンスを堅牢なセキュリティが含まれていますが、次の表に示すように証明書が、フェデレーション サーバーまたはフェデレーション サーバー プロキシのいずれかの必要があります。次の表は、Active Directory フェデレーション サービス (AD FS) に焦点を当てています、[サードパーティの id プロバイダーを使用する方法](https://go.microsoft.com/fwlink/?LinkId=532869)についてもあります。
  
||||
|:-----|:-----|:-----|
|**証明書の種類** <br/> |**説明** <br/> |**展開する前に把握しておくべき情報** <br/> |
|**SSL 証明書 (別名、サーバー認証証明書)** <br/> |これは、フェデレーション サーバー コンピューター、クライアント コンピューター、フェデレーション サーバー プロキシ コンピューター間の通信を保護するために使用される標準の SSL 証明書です。  <br/> |AD FS では、SSL 証明書が必要です。既定では、AD FS は、インターネット インフォメーション サービス (IIS) で既定の web サイトの構成されている SSL 証明書を使用します。<br/> この SSL 証明書のサブジェクト名は、フェデレーション サービス (FS) の名前を展開する AD FS の各インスタンスを決定する使用されます。あらゆる新しい証明機関 (CA) のサブジェクト名を選択することを検討してください-ベストが、会社や組織が Office 365 の名前を表すことの証明書を発行します。この名前は、インターネット ルーティング可能である必要があります。<br/>**注意:** AD FS では、この SSL 証明書があるないドットなしの (短い名前) サブジェクト名が必要です。          <br/> **推奨値:** パブリック (サード パーティの) CA またはを公的に信頼されたルートの下位の CA によって発行された SSL 証明書を使用することをお勧めため、この証明書は、AD FS のクライアントによって信頼されている必要があります、たとえば、VeriSign や Thawte などです。  <br/> |
|**トークン署名証明書** <br/> |これは、フェデレーション サーバーの問題と、Office 365 を受け入れるし、検証するすべてのトークンに安全に署名するために使用される標準的な X.509 証明書です。  <br/> |トークン署名証明書には、FS 内の信頼されたルートにチェーンする秘密キーを含める必要があります。既定では、AD FS は、自己署名証明書を作成します。ただし、組織のニーズに応じて変更できますこの証明書 CA が発行した証明書を AD FS の管理スナップインを使用しています。<br/>**注意:** トークン署名証明書は、FS の安定性に不可欠です。証明書を変更すると、Office 365 が変更を通知する必要があります。通知が指定されていない場合、ユーザーは、Office 365 サービスにサインインできません。<br/>**推奨値:** AD FS によって生成された自己署名のトークン署名証明を使用することをお勧めします。これによって、既定の証明書を管理します。たとえば、この証明書は有効期限が、AD FS は新しい自己署名証明書を生成します。<br/> |
   
フェデレーション サーバー プロキシには、次の表に示された証明書が必要です。
  
||||
|:-----|:-----|:-----|
|**証明書の種類** <br/> |**説明** <br/> |**展開する前に把握しておくべき情報** <br/> |
|SSL 証明書  <br/> |これは、フェデレーション サーバー コンピューター、フェデレーション サーバー プロキシ コンピューター、およびインターネット接続コンピューター間の通信を保護するために使用される標準の SSL 証明書です。  <br/> |AD FS フェデレーション サーバー プロキシの構成ウィザードを正常に実行する前に、この SSL 証明書を IIS で既定の web サイトにバインドしてください。  <br/> この証明書には、企業ネットワーク内のフェデレーション サーバーに構成された SSL 証明書と同じ件名を付ける必要があります。  <br/> **推奨事項:** このフェデレーション サーバー プロキシが接続されているフェデレーション サーバーに構成されているのと同じサーバー認証証明書を使うことをお勧めします。  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>証明書を自動検出、Outlook の任意の場所、および Active Directory の同期

外部に接続する Exchange 2013、Exchange 2010、Exchange 2007 および Exchange 2003 クライアント アクセス サーバー (CASs) では、セキュリティで保護された接続の自動検出、Outlook Anywhere および Active Directory の同期サービスのサード パーティの SSL 証明書が必要です。オンプレミス環境にインストールされているこの証明書が既にあります。
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Exchange ハイブリッド サーバーの証明書

外部に接続する Exchange ハイブリッド サーバーまたはサーバーは、Exchange のオンライン サービスとセキュリティで保護された接続のサードパーティの SSL 証明書を必要とします。サードパーティの SSL プロバイダーからこの証明書を取得する必要があります。
  
## <a name="office-365-certificate-chains"></a>Office 365 の証明書チェーン

この資料では、お客様のインフラストラクチャにインストールする必要があります証明書を説明します。Office 365 サーバーにインストールされている証明書の詳細については、 [Office 365 の証明書チェーン](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)を参照してください。
  

