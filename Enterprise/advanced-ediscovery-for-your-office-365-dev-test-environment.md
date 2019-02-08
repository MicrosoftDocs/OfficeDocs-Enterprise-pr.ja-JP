---
title: Office 365 の開発/テスト環境のアドバンスト eDiscovery
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: '概要: Office 365 の開発/テスト環境で、サンプル データを使用して Office 365 アドバンスト eDiscovery を構成し、デモンストレーションします。'
ms.openlocfilehash: c93900e07b8b9adbe0f1120eca77019b9dcc1eda
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897510"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Office 365 の開発/テスト環境のアドバンスト eDiscovery

 **概要:** Office 365 の開発/テスト環境で、サンプル データを使用して Office 365 アドバンスト eDiscovery を構成し、デモンストレーションします。
  
Office 365 高度な電子的証拠開示では、簡単に検索したり、電子メールやドキュメントなど、Office 365 に格納されているデータの間で関連情報を分析することができます。訴訟の状況で特に膨大な時間と経費を節約できます。詳細については、[電子的証拠開示の Office 365 の詳細](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)を参照してください。
  
この記事の手順では、架空の契約問題に関するデータの小さなセットを作成し、そのデータをアドバンスト eDiscovery で分析します。
  
> [!TIP]
> [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>フェーズ 1: Office 365 の開発/テスト環境を作成する

最小要件、軽量化による高度な電子的証拠開示をテストする場合は、フェーズ 2 と[Office 365 の開発/テスト環境](office-365-dev-test-environment.md)の第 3 段階で指示します。
  
シミュレートされた企業で高度な電子的証拠開示をテストする場合は、 [Office 365 の開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)に指示します。
  
> [!NOTE]
> 高度な電子的証拠開示のテストは、シミュレートされたエンタープライズ環境には、シミュレートされたイントラネットをインターネットに接続されていると Windows サーバーの AD フォレストの場合、ディレクトリ同期します。ここでは、オプションを表す一般的な組織環境でのテストや実験を行うことができますように。 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>フェーズ 2:アドバンスト eDiscovery 用のサンプル データを作成する

この手順では、電子メール メッセージを作成します。このメッセージをアドバンスト eDiscovery のケースで分析することになります。
  
1. Internet Explorer を開き、サインイン[https://outlook.com](https://outlook.com)[の開発/テスト環境を Office 365](office-365-dev-test-environment.md)の第 2 フェーズで作成した Outlook のアカウントにします。
    
  - ライトウェイトの開発/テスト環境を使用している場合は、Internet Explorer のプライベート セッションを開いて、ローカル コンピューターからサインインします。
    
  - シミュレートされたエンタープライズ開発/テスト環境を使用する場合は、Azure ポータルを使用して ([https://portal.azure.com](https://portal.azure.com)) CLIENT1 バーチャル マシンに接続し、CLIENT1 からサインインします。
    
2. **[Outlook メール]** タブで、**[新規作成]** をクリックします。
    
3. 試用版サブスクリプションの User6 のアカウントの電子メール アドレスを入力**する**」( **user6 @** 。<organization name> **. onmicrosoft.com**)。
    
4. 件名に、「**Test email 1**」と入力します。
    
5. 本文に、「**Tailspin contract draft**」と入力して、**[送信]** をクリックします。
    
6. **[Outlook メール]** タブで、**[新規作成]** をクリックします。
    
7. **[宛先]** に、試用版サブスクリプションの User6 アカウントの電子メール アドレスを入力します。
    
8. 件名に、「**Test email 2**」と入力します。
    
9. 本文に、「**Tailspin lunch meeting**」と入力して、**[送信]** をクリックします。
    
10. **[Outlook メール]** タブで、**[新規作成]** をクリックします。
    
11. **[宛先]** に、試用版サブスクリプションの User6 アカウントの電子メール アドレスを入力します。
    
12. 件名に、「**Test email 3**」と入力します。
    
13. 本文に、「**Tailspin contract disagreement**」と入力して、**[送信]** をクリックします。
    
14. 右上隅で [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。
    
15. 新しいタブを開くし、Office 365 ポータルにサインイン ([https://portal.office.com](https://portal.office.com))、試用版サブスクリプションの User6 のアカウントのパスワードとアカウント名とします。
    
16. **[Office 365 ポータル]** タブで、**[メール]** をクリックします。
    
17. [場所] タブの [ **Outlook のメール - User6 -** User6 が Outlook の電子メール アカウントからすべての 3 つの電子メールを受信したことを確認してください。
    
18. User6 の **Office 365 ポータルのタブ**に戻ります。
    
19. 右上の隅にあるユーザー アイコンをクリックして、**[サインアウト]** をクリックします。
    
この手順では、2 つの Word 文書を作成します。この文書をアドバンスト eDiscovery のケースで分析することになります。
  
1. **[Office]** ページで **[サインイン]** をクリックし、グローバル管理者アカウントの認証情報でサインインします。
    
2. 新しいタブでは、本番環境の SharePoint サイトの URL へのアクセス: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. **[実稼働サイト コレクション]** タブの **[ドキュメント]** で **[新規] > [Word 文書]** をクリックします。
    
4. **[Word Online]** ページで、「**Tailspin draft contract**」と入力して、タイトルに **[保存済み]** と表示されるまで待ってから、**[Word Online]** ページのタブを閉じます。
    
5. **[実稼働サイト コレクション]** タブの **[ドキュメント]** で **[新規] > [Word 文書]** をクリックします。
    
6. **[Word Online]** タブで、「**Tailspin contract dispute notes**」と入力して、タイトルに **[保存済み]** と表示されるまで待ってから、**[Word Online]** タブを閉じます。
    
7. **[運用サイト コレクション]** タブのドキュメントの一覧に、**Document** および **Document1** が表示されます。
    
8. **[運用サイト コレクション]** タブを閉じます。
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>フェーズ 3: 使用して高度な電子的証拠開示の法的な争い

残念ながら、組織と Tailspin toys 社の契約紛争は、法的措置のポイントに達した。この手順で作成して構成する、高度な電子的証拠開示のケースを検索し、電子メールと「Tailspin 契約」のテキストを含むドキュメントを分析します。
  
アドバンスト eDiscovery を使用するためのプロセスは、次のとおりです。
  
- セキュリティで検索を作成する&amp;コンプライアンス センターが、その結果を分析し、高度な電子的証拠開示の結果を準備します。
    
- アドバンスト eDiscovery でケースを作成して構成し、検索結果を分析します。
    
この手順で、セキュリティで検索を作成する&amp;コンプライアンスの中央に「Tailspin 契約」では、検索結果を高度な電子的証拠開示の結果を準備します。
  
1. **Office 365 ポータル**のタブで、**[管理者]** をクリックします
    
2. 管理センターのタブにある左側のナビゲーションで、**[管理センター]、[コンプライアンス]** をクリックします。
    
3. 上の**セキュリティ&amp;準拠**] タブで、[**アクセス許可**] をクリックします。
    
4. **[アクセス許可]** リストで、**[Organization Management]** をダブルクリックします。
    
5. **[役割グループ]** ウィンドウで、**[メンバー]** のプラス記号をクリックします。
    
6. **[メンバーの選択]** ウィンドウで、管理者アカウントの名前をダブルクリックして、**[OK]** をクリックします。
    
7. **[役割グループ]** ウィンドウで、**[保存]** をクリックします。
    
8. **[アクセス許可]** リストで、**[電子情報開示マネージャー]** をダブルクリックします。
    
9. **[役割グループ]** ウィンドウで、**[電子情報開示の管理者]** のプラス記号のアイコンをクリックします。
    
10. **[メンバーの選択]** ウィンドウで、管理者アカウントの名前をダブルクリックして、**[OK]** をクリックします。
    
11. **[役割グループ]** ウィンドウで、**[保存]** をクリックします。
    
12. 左側のナビゲーションでをクリックして**検索&amp;調査 _gt のコンテンツの検索**。
    
13. プラス記号のアイコンをクリックして、検索を追加します。
    
14. **[新規検索]** ウィンドウで、**[名前]** に「**Tailspin contract search**」と入力します。
    
15. **[どこを調べますか?]** で、**[すべての場所の検索]** をクリックし、**[Exchange]**、**[SharePoint]**、および **[パブリック フォルダー]** を選択して、**[次へ]** をクリックします。
    
16. **[どこを調べますか?]** で、「**Tailspin contract**」と入力して、**[検索]** をクリックします。
    
17. 検索のリストで、名前 **[Tailspin contract search]** をクリックします。
    
18. **Tailspin 契約の検索**ウィンドウで、[**結果**] で、**検索結果のプレビュー**をクリックします。生産の SharePoint サイト (**ドキュメント****文書 1**) と User6 に**テスト ・ メール 1**と**3 のテスト メール**のメールの 2 つのドキュメントの一覧を示すウィンドウが表示されます。ウィンドウを閉じます。
    
19. **[コンテンツ検索]** ウィンドウで、**[アドバンスト eDiscovery による結果の分析]** の **[分析用の結果のプレビュー]** をクリックします。
    
20. **[Tailspin contract search の検索結果の準備]** ウィンドウで、**[準備]** をクリックして完了まで待機します。
    
この手順では、アドバンスト eDiscovery の新しケースを作成し、Tailspin contract search の結果を分析します。
  
1. 左側のナビゲーションでは、クリックしてで**電子的証拠開示****検索&amp;調査**。
    
2. **[電子情報開示]** ウィンドウで、**[アドバンスト eDiscovery に移動]** をクリックします。
    
3. **[アドバンスト eDiscovery]** タブで、プラス記号のアイコンをクリックして、新しいケースを追加します。
    
4. **[ケースの追加]** ウィンドウで、**[名前]** に「**Tailspin contract dispute**」と入力して **[OK]** をクリックします。ケースが作成されるまで待機します。
    
5. リスト内の **[Tailspin contract dispute]** ケースをダブルクリックします。 
    
6. **コンテナー** ] ボックスの一覧で**Tailspin 契約検索**コンテナーをクリックし、[**プロセス**] をクリックします。処理が完了するまで待機します。
    
7. ウィンドウの下側に **[処理: 完了]** が表示されたら、左側のナビゲーションで **[プロセスの概要]** をクリックして概要を確認します。
    
8. 上部のナビゲーションで、**[分析]** をクリックします。
    
9. **[セットアップ]** ページで、**[テーマ]** の **[最大テーマ数]** に「**3**」と入力します。
    
10. **分析**] をクリックし、分析を完了するまで待機します。ターゲット ・ カタログの作成、ドキュメント、電子メール、および添付ファイルの分析と円グラフの系列を参照してくださいする必要があります。詳細については、[結果の分析を表示する](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)を参照してください。
    
この環境を使用して、新しいコンテンツ、新しい検索およびケースを作成できるようになりました。また、Office 365 のアドバンスト eDiscovery の実験をさらに進めることができるようになりました。
  
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 開発/テスト環境の Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)

[Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


