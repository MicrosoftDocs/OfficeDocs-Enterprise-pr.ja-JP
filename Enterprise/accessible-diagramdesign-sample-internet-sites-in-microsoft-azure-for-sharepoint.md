---
title: "アクセス可能な図 - 設計サンプル SharePoint 2013 のための Microsoft Azure のインターネット サイト"
ms.author: adammil
author: adammil
manager: laurawi
ms.date: 11/16/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: "この記事は、「設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト」という名前の図のアクセス可能なテキスト バージョンです。"
---

# アクセス可能な図 - 設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト

この記事は、「設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト」という名前の図のアクセス可能なテキスト バージョンです。
  
SharePoint 2013 を使って、インターネットに直接接続されているサイトの開始点としてこの設計例を使用してください。
  
このポスターは、SharePoint 2013 の次の側面を設計する方法の例を示しています。
  
- ユーザー
    
- 領域と認証
    
- サーバー ファーム
    
- 管理サイト
    
- サービス
    
- アプリケーション プールと Web アプリケーション
    
- サイト コレクション
    
- サイト
    
- コンテンツ データベース
    
- 領域と URL
    
## ユーザー、領域、認証

この設計には、4 種類のユーザー アカウントがあります。各種類のアカウントは、アクセス用のサイト、および特定の種類の認証を使用する領域と関連付けられています。 
  
- 匿名の顧客  匿名の顧客は、http://www.contoso.com などのサイトを介してアクセスします。使用する領域は、匿名認証を使用する "Internet zone / anonymous" です。
    
- 認証済みの顧客  認証済みの顧客は、https://secure.contoso.com などのサイトを介してアクセスします。使用する領域は、Azure Active Directory および SAML 認証を使用する "Extranet zone / SAML" です。
    
- サイトの作成者と開発者  サイトの作成者と開発者は、http://authoring.contoso.com:8000 または http://www.contoso.com:8000 などのサイトを介してアクセスします。使用する領域は、Active Directory ドメイン サービス (AD DS) を使用する "Default zone / Windows integrated" です。
    
- 検索クロール アカウント  検索クロール アカウントは、http://authoring.contoso.com:8000 または http://www.contoso.com:8000 などのサイトを介してアクセスします。使用する領域は、AD DS および Windows NTLM 認証を使用する "Default zone / Windows integrated" です。
    
## サーバー ファーム

ユーザーは、Azure を経由してサーバー ファームにアクセスします。サーバー ファームには 1 つ以上の Web サーバーがあります。
  
## 管理サイト

管理サイトには、複数のアプリケーション サーバーがあります。これらのサーバーは、Web アプリケーションの全体管理サイトを使用するアプリケーション プール (例ではアプリケーション プール 1) と通信します。全体管理サイトでは、組織内のサイト コレクションにアクセスできます。
  
管理サイトには、SQL Database サーバーも含まれています。これは、SQL クラスタリング、ミラーリング、または AlwaysOn (AlwaysOn は SQL Server 2012 にのみ適用されます) をサポートするようにインストールおよび構成された SQL Server を持つデータベース サーバーです。
  
## サービス

設計例は、インターネット インフォメーション サービス (IIS) Web サイト、SharePoint Web サービスを示しています。SharePoint Web サービスには、ユーザー プロファイル、検索、および管理されたメタデータという 3 つのサービスがあるアプリケーション プール (アプリケーション プール 2) が含まれています。
  
インターネット サイト向けのサービスに関する注意事項:
  
> 管理されたメタデータ  必ず " **このサービス アプリケーションは列固有の用語セットの既定の格納場所です**" を選択してください。
    
> アプリケーション管理  Azure では、一般向けのインターネット サイトでアプリを使用することはお勧めしていません。
    
## アプリケーション プールと Web アプリケーション

Azure の既定のグループは、Contoso Sites という名前の Web アプリケーションを含むアプリケーション プール 3 を示しています。このパスベースのサイト コレクションは http://internal:8000 にあります。
  
## サイト コレクションおよびサイト

アプリケーション プールに含まれるサイト コレクションは次のとおりです。
  
- クロール用のホスト名付きサイト コレクション 1 (場所の例: http://authoring.contoso.com:8000)
    
- クエリ用のホスト名付きサイト コレクション 2 (場所の例: http://www.contoso.com、https://secure.contoso.com、http://www.contoso.com:8000)
    
- クエリ用のホスト名付きサイト コレクション 3 (場所の例: http://assets.contoso.com、https://secureassets.contoso.com、http://assets.contoso.com:8000)
    
## コンテンツ データベース

例は、2 つのコンテンツ データベースを示しています。1 つは、クロール用のサイト コレクション 1 (http://authoring.contoso.com:8000) です。もう 1 つは、クエリ用の 2 つのサイト コレクション (サイト コレクション 2 および 3) (http://www.contoso.com、https://secure.contoso.com、http://www.contoso.com:8000、または http://assets.contoso.com、https://secureassets.contoso.com、http://assets.contoso.com:8000) です。
  
## 領域と URL

例は、異なるユーザー アカウントで使用される、3 つの領域と関連する負荷分散された URL を示しています。 
  
最初の領域と URL のリストはサイト コレクション 1 と関係し、次の情報が含まれています。
  
- ユーザー - サイトの作成者
    
- 領域 - 既定
    
- 負荷分散された URL - http://authoring.contoso.com:8000
    
2 番目の領域と URL のリストには、3 つの異なる領域に 3 種類のユーザーが含まれています。このリストはサイト コレクション 2 と関係し、次の情報が含まれています。
  
最初の領域:
  
- ユーザー - サイトの作成者
    
- 領域 - 既定
    
- 負荷分散された URL - http://www.contoso.com:8000
    
2 番目の領域:
  
- ユーザー - 匿名の顧客
    
- 領域 - インターネット
    
- 負荷分散された URL - http://www.contoso.com
    
3 番目の領域:
  
- ユーザー - 認証済みの顧客
    
- 領域 - エクストラネット
    
- 負荷分散された URL - https://secure.contoso.com
    
3 番目の領域と URL のリストには、3 つの異なる領域に 3 種類のユーザーが含まれています。このリストはサイト コレクション 3 と関係し、次の情報が含まれています。
  
最初の領域:
  
- ユーザー - サイトの作成者
    
- 領域 - インターネット
    
- 負荷分散された URL - http://assets.contoso.com:8000
    
2 番目の領域:
  
- ユーザー - 匿名の顧客
    
- 領域 - インターネット
    
- 負荷分散された URL - http://assets.contoso.com
    
3 番目の領域:
  
- ユーザー - 認証済みの顧客
    
- 領域 - エクストラネット
    
- 負荷分散された URL - http://secureassets.contoso.com
    

