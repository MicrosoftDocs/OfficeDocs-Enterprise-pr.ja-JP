---
title: Office 365 IdFix ツールをダウンロードして実行する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Office 365 IdFix ツールをダウンロードして実行し、Active Directory ドメインサービス (AD DS) をクリーンアップしてから Office 365 に同期する方法。
ms.openlocfilehash: 4a402cf245ebd20fbc5846908d521469ebfb90c1
ms.sourcegitcommit: 10ae1163f8443c53f19dfad6b7c2b2bb952bf759
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2019
ms.locfileid: "34490756"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a>Office 365 IdFix ツールをダウンロードして実行する


IdFix Office 365 と同期する前に、Active Directory ドメインサービス (AD DS) ドメイン内の重複や書式の問題などのエラーを識別します。 
  
このタスクを正常に完了するには、AD DS 内のユーザー、グループ、および連絡先オブジェクトに慣れている必要があります。
  
このタスクを完了できない場合は、他にもいくつかの操作を実行できます。 これらのメソッドは簡単になる場合もありますが、時間がかかる場合や他の欠点がある場合もあります。 以下にその例を示します。
  
- **IdFix を実行せずにディレクトリ同期を実行する** 

  IdFix ツールを使用せずにディレクトリを同期することはできますが、お勧めしません。 同期の前にエラーを修正するには時間がかかり、多くの場合、クラウドへの移行がよりスムーズになります。 

- **コンサルタントの雇用** 

  専門家のヘルプを利用することで、ユーザーの作業を迅速に行い、ディレクトリを同期させることができます。 
    
## <a name="what-you-need-to-run-idfix"></a>IdFix を実行するために必要なこと

IdFix を入手して実行する最も簡単な方法は、AD DS ドメインに参加しているコンピューターにダウンロードすることです。 必要であれば、ドメインコントローラー上で実行できますが、これは必須ではありません。
  
### <a name="idfix-hardware-requirements"></a>IdFix のハードウェア要件

IdFix をダウンロードするコンピューターは、以下の最小ハードウェア要件を満たす必要があります。
  
- 4 GB の RAM
- 2 GB のハードディスク容量
   
### <a name="idfix-software-requirements"></a>IdFix ソフトウェアの要件

IdFix をダウンロードしたコンピューターは、ユーザーを Office 365 に同期するのと同じ AD DS ドメインに参加させる必要があります。 

また、コンピューターには .NET Framework 4.0 がインストールされている必要があります。 Windows Server 2008 以降を実行している場合は、.NET Framework が既にインストールされている可能性があります。 それ以外の場合は、ダウンロードセンターまたは Windows Update[から .net 4.0 をダウンロード](https://go.microsoft.com/fwlink/p/?LinkId=400475)することができます。 
  
### <a name="idfix-permissions-requirements"></a>IdFix 権限の要件

IdFix を実行するために使用するユーザーアカウントには、AD DS ドメインに対する読み取りおよび書き込みアクセス権が必要です。
  
ユーザーアカウントがこれらの要件を満たしているかどうかがわからず、確認する方法がわからない場合でも、IdFix をダウンロードして実行することができます。 ユーザーアカウントが適切なアクセス許可を持っていない場合、IdFix は、実行しようとしたときにエラーを表示するだけです。
  
## <a name="download-and-extract-idfix"></a>IdFix のダウンロードと抽出

次の手順に従います。 
  
1. IdFix ツールを実行するコンピューターにサインインします。
    
2. [Idfix DirSync エラー修復ツール](https://go.microsoft.com/fwlink/?linkid=867219)の Microsoft ダウンロードサイトに移動します。
    
3. Zip ファイルをダウンロードして開きます。
    
3. **Idfix**ウィンドウで、[**抽出**] を選択し、[**すべて抽出**] を選択します。 既定では、IdFix はに`C:\Users\<your user name>\Documents\IdFix`展開されます。 
    
6. [**抽出**] を選びます。

これらの手順は、Windows Server 2016 を実行しているサーバー上で Internet Explorer を使用して行いました。 異なるバージョンの Windows または別のブラウザーを使用している場合は、手順が異なることがあります。
    
## <a name="run-the-idfix-tool"></a>IdFix ツールを実行する

IdFix をダウンロードして抽出した後、それを実行して AD DS ドメインの問題を検索します。
  
1. AD DS ドメインに対する読み取り/書き込みアクセス権を持つアカウントを使用して、IdFix をダウンロードしたコンピューターにサインインします。
    
2. エクスプローラーで、IdFix を抽出した場所に移動します。 抽出中に既定のフォルダーを選択した場合`C:\Users\<your user name>\Documents\IdFix`は、に移動します。 
    
3. [ **Idfix**] をダブルクリックします。 
  
4. 既定では、IdFix はマルチテナントルールセットを使用して、ディレクトリ内のエントリをテストします。 これは、ほとんどの Office 365 お客様のための適切なルールセットです。 ただし、事務規制 (ITAR) のお客様のために、Office 365 の専用または国際トラフィックの場合、IdFix を構成して、代わりに専用のルールセットを使用することができます。 お客様の種類がわからない場合は、この手順を省略しても問題ありません。 ルールセットを専用に設定するには、メニューバーの歯車アイコンをクリックして、[**専用**] を選択します。
    
5. [**クエリ**] を選択します。
    
    ![IdFix で [クエリ] を選択します。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. 既定では、IdFix はディレクトリ全体を検索してエラーを検出します。
    
    ディレクトリのサイズによっては、クエリの実行に時間がかかることがあります。 ツールのメインウィンドウの下部にある進捗状況を確認できます。 [**キャンセル**] をクリックした場合は、最初から再起動する必要があります。
  
7. IdFix がクエリを完了した後、エラーがない場合はディレクトリを同期することができます。 ディレクトリにエラーがある場合は、同期する前にそれらを修正することをお勧めします。 詳細については、「 [Office 365 と同期するディレクトリ属性の準備](prepare-directory-attributes-for-synch-with-idfix.md)」を参照してください。
    
    同期する前にエラーを修正することは必須ではありませんが、IdFix から返されたすべてのエラーを少なくとも確認することを強くお勧めします。
    
    各エラーは、ツールのメインウィンドウの独立した行に表示されます。 
    
8. [**更新**] 列の提案された変更に同意する場合は、[**アクション**] 列で、変更を実装するために idfix を実行する対象を選択し、[**適用**] をクリックします。 [**適用**] をクリックすると、ツールによってディレクトリ内の変更が行われます。
    
    更新のたびに [**適用**] をクリックする必要はありません。 その代わりに、[**適用**] をクリックする前にいくつかのエラーを修正し、idfix によってすべて同時に変更することができます。 エラーの種類を一覧表示する列の上部にある [**エラー** ] をクリックすると、エラーの種類別にエラーを並べ替えることができます。 
    
    1つの方法は、同じ種類のすべてのエラーを修正することです。たとえば、最初にすべての重複を修正して適用します。 次に、文字書式エラーなどを修正します。 変更を適用するたびに、IdFix ツールによって別のログファイルが作成されます。このファイルを使用すると、誤った変更を行った場合に、変更を元に戻すことができます。 [トランザクションログ](idfix-transaction-log.md)は、idfix を抽出したフォルダーに格納されます。これは、既定で_ユーザー名> \documents\idfix を C:\Users\<_ ます。 
    
    ![IdFix で修復エラーが発生しました。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. ディレクトリにすべての変更が加えられたら、IdFix を再度実行して、作成した修正プログラムで新しいエラーが発生していないことを確認してください。 必要な回数だけこれらの手順を繰り返すことができます。 同期する前に、このプロセスを何度か実行することをお勧めします。
    
## <a name="additional-resources-on-idfix"></a>IdFix に関するその他の技術情報 

- [IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Office 365 IdFix トランザクションログ](idfix-transaction-log.md)
    
## <a name="video-training"></a>ビデオ トレーニング

詳細については、レッスン「[インストールと使用](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US)」を参照してください。このツールは、LinkedIn Learning によって提供されています。
  

