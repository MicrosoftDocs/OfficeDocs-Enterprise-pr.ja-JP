---
title: Office 365 のディレクトリ同期のセットアップ
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365 と、オンプレミスの Active Directory のディレクトリ同期をセットアップする方法について説明します。
ms.openlocfilehash: e406eec08b34a694602c756235533f8b1ff6651e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541545"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Office 365 のディレクトリ同期のセットアップ
Office 365 は、ユーザーを管理するのにクラウド ベースのユーザー id の管理の Azure Active Directory サービスを使用します。Azure AD を Office 365 で、オンプレミス環境を同期することにより、オンプレミスの Active Directory を統合することも。同期を設定すると、Azure AD 内で、または、設置ディレクトリ内のユーザー認証を決定できます。
  
## <a name="office-365-directory-synchronization"></a>Office 365 ディレクトリ同期
同期の id や、設置型の組織と Office 365 の間でフェデレーション id を使用することができます。同期の id で、ユーザー設置を管理すると、同じパスワードを使用、クラウドでオンプレミスと Azure の AD によって認証します。これは、最も一般的なディレクトリ同期シナリオです。パススルー認証] または [フェデレーション id は、ユーザーの設置型を管理することをでき、オンプレミス ディレクトリで認証します。フェデレートされた識別情報は、追加の構成を必要とし、のみ 1 回サインインすることができます。詳細については、 [Office 365 の Id を理解して Azure Active Directory](about-office-365-identity.md)を読み取る。
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Azure Active Directory に接続するのには、Windows Azure Active Directory 同期 (DirSync) からアップグレードする場合は、
ディレクトリ同期を現在使用してアップグレードする場合、ヘッドを[azure.com](https://azure.com)に[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)の。
  
## <a name="prerequisites-for-azure-ad-connect"></a>Azure AD の前提条件を接続します。
Azure AD に Office 365 サブスクリプションと無料サブスクリプションを取得します。、ディレクトリ同期をセットアップすると、Azure Active Directory の接続をインストール、オンプレミスのサーバーのいずれかにされます。
  
Office 365 用に必要になります。
  
- (手順に従って、この)、オンプレミス ドメインを確認します。
- [ビジネス向けの Office 365 の管理者の役割を割り当てる](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)アクセス許可を持つ、Office 365 テナントとオンプレミスの Active Directory です。 
    
Azure AD 接続をインストールする、設置型サーバーの次のソフトウェアが必要になります。
  
|**サーバ OS**|**その他のソフトウェア**|
|:-----|:-----|
|**Windows Server 2012 R2** | で PowerShell は、既定でインストール、操作する必要はありません。  <br/> Net 4.5.1 以降のリリースが Windows Update で提供されているとします。コントロール パネルの Windows サーバーに最新の更新プログラムがインストールされていることを確認します。 |
|**パック 1 (SP1) のサービスを Windows Server 2008 R2**または**Windows Server 2012** | -PowerShell の最新バージョンは、Windows Management Framework 4.0 で使用できます。[Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で検索します。<br/> -.Net 4.5.1 およびそれ以降のリリースでは、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能です。 |
|**Windows Server 2008** | -サポートされる最新バージョンの PowerShell は、Windows Management Framework 3.0 では、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能な時間があります。  <br/> -.Net 4.5.1 およびそれ以降のリリースでは、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能です。 |
   
> [!NOTE]
> Azure Active Directory のディレクトリ同期を使用している場合は、Azure Active Directory に、オンプレミスの Active Directory から同期することができる配布グループのメンバーの最大数が 15,000 です。Azure AD 接続では、その番号は 50,000 です。 
  
Azure AD 接続のハードウェア、ソフトウェア、アカウントとアクセス許可の要件、SSL 証明書の要件、およびオブジェクトの制限をより慎重に確認、 [Azure Active Directory に接続するための前提条件](https://go.microsoft.com/fwlink/p/?LinkId=716896)を参照してください。
  
Azure AD 接続[リリースのバージョン履歴](https://go.microsoft.com/fwlink/p/?LinkId=733238)に含まれており、各リリースでの修正内容を参照してくださいかを確認することもできます。 

## <a name="to-set-up-directory-synchronization"></a>ディレクトリ同期を設定するには
1. Office 365 の管理センターにサインインし、**ユーザー**の選択\>左のナビゲーションには、**アクティブなユーザー**です。 
2. Office 365 管理センターで、[**アクティブ ユーザ**] ページで選択 * * より * * \> **ディレクトリ同期**します。
    
    ![[詳細] メニューの [ディレクトリ同期を選択します](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. * * は、ディレクトリ同期に最適ですか?* * ページの 2 つの最初の選択肢の**1 ~ 10** **11-50**で「組織の規模に基づいてことをお勧めを作成しクラウドでユーザーを管理します。ディレクトリ同期を使用すると、あなたの設定をより複雑ななります。クリックして、ユーザーを追加するのにはアクティブなユーザーをください。 
    
    - ただし、続行できますディレクトリ同期の設定によって、ページの一番下の**続行には、ここ**をクリックします。 
    
    - **51 250** ] または [ **251 またはそれ以上**の 2 つの後者選択肢を選択した場合、同期の設定はディレクトリ同期処理をお勧めします。**次**へを選択します。 
    
    ![次へを選択すると、ディレクトリ同期の設定を続行するのには](media/359a1eb9-99ae-4b5b-a413-4de53037cceb.png)
  
4. **クラウドとローカルのディレクトリの同期**では、情報を読みし、詳細情報を表示する場合、学習に移動する複数のリンク: [Office 365 ディレクトリ同期によってユーザーを提供する準備](prepare-for-directory-synchronization.md)をし、次の**を選択**. 
    
5. **では、ディレクトリを確認**] ページで、ディレクトリを自動的にチェックするための要件を確認します。要件に合致する場合は**次へ**を選択\>**スキャンを開始**します。要件を満たさない場合にも**手動で続行**を選択して続行できます。
    
    ![[次へ] または [手動で続行します、[ディレクトリ] ページを確認しましょう](media/af4a6bd5-13aa-4bfa-9751-4464a32ca8db.png)
  
6. ディレクトリをスキャンすることを選択した場合は、[**ディレクトリ同期の設定を評価する**] ページでは、**スキャンの開始**をクリックします。 
    
    ダウンロードしてスキャンを実行する指示に従います。
    
7. スキャンが完了した後、セットアップ ウィザードに戻ります、**次**のスキャン結果を表示する」を選択します。 
    
8. [**ドメインの所有権を確認**] ページの指示に従って、ドメインを確認します。詳細については、 [Office 365 の DNS レコードを管理するときに作成する DNS レコード](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)を参照してください。
    
    > [!IMPORTANT]
    > 自分のドメインを所有していることを確認するのには、TXT レコードを追加した後は、ドメイン ウィザードでユーザーを追加する次の手順に説明しないでください。ディレクトリ同期では、ユーザーを追加できます。 
  
    **Office 365 のセットアップ**・ ページに戻るし、**更新**を選択します。
    
    ![確認後、ドメイン、更新] を選択します。](media/9b5fb593-5ff7-49f0-80d0-18e36d39d669.png)
  
9. **自分のドメインが準備完了**] ページで、[**次**] を選択します。
    
10. **お客様の環境をクリーンアップする**] ページで、必要に応じて指示に従って、Active Directory をチェックするのには IDFix をダウンロードするします。**次**へを選択します。 
    
11. * * Azure Active Directory 接続を実行 * * ページで、Azure AD 接続ウィザードをインストールするのには**ダウンロード**を選択します。 
    
    > [!NOTE]
    > この時点で、Azure AD 接続ウィザードができます。ディレクトリ同期ウィザードのページが最後にお使いのブラウザーで Azure AD 接続手順が完了した後に戻れるようにしておくことを確認します。 
  
    Azure AD 接続ウィザードがインストール後に自動的に開きます。デスクトップのデフォルトのインストール ・ サイト、それを開くことができます。シナリオに応じて、ウィザードの指示に従います。
    
  - パスワード ハッシュの同期とのディレクトリ同期、[高速の設定を使用して、Azure の AD 接続](https://go.microsoft.com/fwlink/p/?LinkID=698537)を使用します。
    
  - 複数のフォレスト、パススルー認証、フェデレートされた識別情報および SSO オプション、[カスタム インストールの Azure AD 接続](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。
    
    これらのオプションを使用する**高速の設定**] ページで **[ユーザー設定**を選択します。 
    
12. Azure AD 接続ウィザードが完了したら、 **Office 365 のセットアップ**ウィザードに戻るし、**予期されたページとして勤務していることを確認の同期を行う**] の指示に従って。**次**へを選択します。 
    
13. 上の指示を読み、* * ユーザーをアクティブにする * * ページし、し、[**次**] を選択します。
    
14. **あなたはすべてのセットアップ**] ページの [**完了**] を選択します。 
    
## <a name="assign-licences-to-synchronized-users"></a>同期のユーザーにライセンスを割り当てる
同期したら、ユーザーが Office 365 は、作成されるが、メールなど、Office 365 の機能を使用するためにライセンスを割り当てる必要があります。手順については、[ビジネス向けの Office 365 のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)を参照してください。
    
## <a name="finish-setting-up-domains"></a>ドメインのセットアップを完了します。
自分のドメインの設定を完了するのには[Office 365 の DNS レコードを管理するときに作成する DNS レコード](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)の手順を実行します。