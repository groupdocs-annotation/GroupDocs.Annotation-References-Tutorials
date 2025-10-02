---
"description": "GroupDocs.Annotation を使用して .NET でドキュメントに注釈を付ける方法を学びます。Azure Blob Storage とのシームレスな統合のためのステップバイステップのチュートリアルです。"
"linktitle": "Azureからドキュメントを読み込む"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Azureからドキュメントを読み込む"
"url": "/ja/net/document-loading-essentials/load-document-from-azure/"
type: docs
"weight": 11
---

# Azureからドキュメントを読み込む

## 導入
ドキュメント管理とコラボレーションの分野において、GroupDocs.Annotation for .NETは、.NETアプリケーション内でシームレスな注釈とマークアップ機能を実現する堅牢なソリューションとして登場しました。このチュートリアルでは、GroupDocs.Annotation for .NETを活用してドキュメントに注釈を付ける複雑な手順を詳しく説明し、前提条件から高度な使用方法まで、ステップバイステップで解説します。
## 前提条件
GroupDocs.Annotation for .NET を使用する前に、次の前提条件が満たされていることを確認してください。
1. .NET Framework のインストール: GroupDocs.Annotation for .NET には、互換性のある .NET ランタイム環境が必要です。システムに .NET Framework がインストールされていることを確認してください。
2. GroupDocs.Annotation ライブラリへのアクセス: Web サイトからダウンロードするか、NuGet などのパッケージ マネージャーを介して、GroupDocs.Annotation for .NET ライブラリへのアクセスを取得します。
3. 注釈を付けるドキュメント: 注釈を付けるドキュメント（例: PDF）を準備します。ドキュメントがローカルまたはAzure Blob Storageなどのクラウドストレージサービス経由でアクセスできることを確認してください。

## 名前空間のインポート
GroupDocs.Annotation for .NET を使用してドキュメントに注釈を付けるには、必要な名前空間をプロジェクトにインポートします。この手順により、必要なクラスと機能にアクセスできるようになります。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Azureからドキュメントを読み込む
Azure Blob Storage に保存されているドキュメントに注釈を付けるには、次の手順に従います。
### ステップ1: 出力パスを設定する
注釈付きドキュメントを保存する出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### ステップ2: ドキュメントをダウンロードする
Azure Blob Storageからドキュメントを取得するには、 `DownloadFile` 方法。
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // 注釈ロジック
    annotator.Save(outputPath);
}
```
## Azure Blob Storage からファイルをダウンロードする
Azure Blob Storageからドキュメントをダウンロードするには、 `DownloadFile` 方法。
### ステップ1: BLOBを取得する
Azure Blob Storage コンテナーにアクセスし、目的の BLOB を取得します。
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### ステップ2: BLOBコンテンツをダウンロードする
BLOB コンテンツをメモリ ストリームにダウンロードします。
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Azure Blob ストレージ コンテナーを取得する
Azure Blob Storageとやりとりするには、 `GetContainer` 方法。
### ステップ1: ストレージ資格情報を初期化する
必要なアカウント資格情報とエンドポイント情報を提供します。
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{アカウント名}.blob.core.windows.net/";
```
### ステップ2: BLOBクライアントを作成する
Azure Blob Storage と対話するためのクライアントを作成します。
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### ステップ3: コンテナ参照を取得する
指定されたコンテナへのチュートリアルを取得します。
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### ステップ4: コンテナが存在しない場合は作成する
コンテナが存在することを確認し、存在しない場合は作成します。
```csharp
container.CreateIfNotExists();
```

## 結論
GroupDocs.Annotation for .NET は、.NET アプリケーションにシームレスに統合された強力なドキュメント注釈機能により、開発者を支援します。このチュートリアルで説明する手順に従うことで、GroupDocs.Annotation の機能を効果的に活用し、Azure Blob Storage に保存されているドキュメントに注釈を付けることができます。
#### よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation は、PDF、DOCX、PPTX など、幅広いドキュメント形式をサポートしています。
### 特定の要件に応じて注釈をカスタマイズできますか?
はい、GroupDocs.Annotation では注釈の広範なカスタマイズ オプションが提供されており、ユーザーは外観、動作、メタデータを変更できます。
### GroupDocs.Annotation は共同ドキュメント注釈付けに適していますか?
もちろんです! GroupDocs.Annotation は、複数のユーザーが同時に注釈を追加、編集、確認できるようにすることで、共同ドキュメント注釈付けを容易にします。
### GroupDocs.Annotation はクロスプラットフォームの互換性を提供しますか?
はい、GroupDocs.Annotation は、Windows、Linux、macOS など、さまざまなプラットフォームでシームレスに動作するように設計されています。
### GroupDocs.Annotation ユーザー向けのテクニカル サポートは提供されますか?
はい、GroupDocs はフォーラムと専用のサポート チャネルを通じて包括的な技術サポートを提供します。