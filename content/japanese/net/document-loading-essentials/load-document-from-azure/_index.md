---
title: Azureからドキュメントをロードする
linktitle: Azureからドキュメントをロードする
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation を使用して .NET でドキュメントに注釈を付ける方法を学びます。 Azure Blob Storage とのシームレスな統合のためのステップバイステップのチュートリアル。
type: docs
weight: 11
url: /ja/net/document-loading-essentials/load-document-from-azure/
---
## 導入
ドキュメント管理とコラボレーションの領域では、GroupDocs.Annotation for .NET が堅牢なソリューションとして登場し、.NET アプリケーション内でのシームレスな注釈およびマークアップ機能を促進します。このチュートリアルでは、GroupDocs.Annotation for .NET を活用してドキュメントに注釈を付ける方法の複雑さを掘り下げ、前提条件から高度な使用法まで段階的なガイダンスを提供します。
## 前提条件
GroupDocs.Annotation for .NET に入る前に、次の前提条件が満たされていることを確認してください。
1. .NET Framework のインストール: GroupDocs.Annotation for .NET には、互換性のある .NET ランタイム環境が必要です。システムに .NET Framework がインストールされていることを確認してください。
2. GroupDocs.Annotation ライブラリへのアクセス: Web サイトからダウンロードするか、NuGet などのパッケージ マネージャーを通じて、GroupDocs.Annotation for .NET ライブラリへのアクセスを取得します。
3. 注釈を付けるドキュメント: 注釈を付ける予定のドキュメント (PDF など) を準備します。ローカルで、または Azure Blob Storage などのクラウド ストレージ サービス経由でドキュメントにアクセスできることを確認してください。

## 名前空間のインポート
GroupDocs.Annotation for .NET を使用してドキュメントに注釈を付けるには、必要な名前空間をプロジェクトにインポートします。この手順により、必要なクラスと機能に確実にアクセスできるようになります。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Azureからドキュメントをロードする
Azure Blob Storage に保存されているドキュメントに注釈を付けるには、次の手順に従います。
### ステップ 1: 出力パスを設定する
注釈付きドキュメントが保存される出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### ステップ 2: ドキュメントをダウンロードする
次のコマンドを呼び出して、Azure Blob Storage からドキュメントを取得します。`DownloadFile`方法。
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    //注釈ロジック
    annotator.Save(outputPath);
}
```
## Azure Blob Storage からファイルをダウンロードする
Azure Blob Storage からドキュメントをダウンロードするには、`DownloadFile`方法。
### ステップ 1: BLOB を取得する
Azure Blob Storage コンテナーにアクセスし、目的の BLOB を取得します。
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### ステップ 2: BLOB コンテンツをダウンロードする
BLOB コンテンツをメモリ ストリームにダウンロードします。
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Azure Blob Storage コンテナーを取得する
Azure Blob Storage と対話するには、`GetContainer`方法。
### ステップ 1: ストレージ認証情報を初期化する
必要なアカウント認証情報とエンドポイント情報を入力します。
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{アカウント名}.blob.core.windows.net/";
```
### ステップ 2: BLOB クライアントを作成する
Azure Blob Storage と対話するためのクライアントを作成します。
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### ステップ 3: コンテナ参照の取得
指定されたコンテナへの参照を取得します。
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### ステップ 4: コンテナが存在しない場合は作成する
コンテナが存在することを確認し、存在しない場合は作成します。
```csharp
container.CreateIfNotExists();
```

## 結論
GroupDocs.Annotation for .NET は、開発者に強力なドキュメント注釈機能を提供し、.NET アプリケーションにシームレスに統合します。このチュートリアルで説明されている手順に従うことで、GroupDocs.Annotation の機能を効果的に利用して、Azure Blob Storage に保存されているドキュメントに注釈を付けることができます。
#### よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation は、PDF、DOCX、PPTX などを含む幅広いドキュメント形式をサポートしています。
### 特定の要件に応じて注釈をカスタマイズできますか?
はい、GroupDocs.Annotation は注釈の広範なカスタマイズ オプションを提供しており、ユーザーは外観、動作、メタデータを変更できます。
### GroupDocs.Annotation は共同ドキュメントの注釈付けに適していますか?
絶対に！ GroupDocs.Annotation は、複数のユーザーが同時に注釈を追加、編集、確認できるようにすることで、共同でのドキュメントへの注釈付けを容易にします。
### GroupDocs.Annotation はクロスプラットフォーム互換性を提供しますか?
はい。GroupDocs.Annotation は、Windows、Linux、macOS などのさまざまなプラットフォームでシームレスに動作するように設計されています。
### GroupDocs.Annotation ユーザーはテクニカル サポートを利用できますか?
はい。GroupDocs は、フォーラムと専用のサポート チャネルを通じて包括的な技術サポートを提供します。