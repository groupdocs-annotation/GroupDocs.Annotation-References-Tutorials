---
categories:
- Document Management
date: '2026-08-04'
description: Azure blob 接続文字列を .NET の GroupDocs.Annotation と共に使用する方法と、ドキュメントを安全に読み込むための
  blob セキュリティベストプラクティスをご紹介します。
keywords:
- azure blob connection string
- blob security best practices
- GroupDocs.Annotation Azure integration
- .NET document loading from Azure
- cloud storage annotation tutorial
lastmod: '2026-08-04'
linktitle: GroupDocs Azure 統合チュートリアル
og_description: Azure blob 接続文字列を .NET の GroupDocs.Annotation と共に使用する方法と、ドキュメントを安全に読み込むための
  blob セキュリティベストプラクティスをご紹介します。
og_image_alt: Step‑by‑step guide showing Azure blob connection string usage with GroupDocs.Annotation
  in a .NET app
og_title: Azure blob 接続文字列（GroupDocs.Annotation 用） – .NET ガイド
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Learn how to use the azure blob connection string with GroupDocs.Annotation
    in .NET, plus blob security best practices for safe document loading.
  headline: Azure blob connection string for GroupDocs.Annotation .NET
  type: TechArticle
- description: Learn how to use the azure blob connection string with GroupDocs.Annotation
    in .NET, plus blob security best practices for safe document loading.
  name: Azure blob connection string for GroupDocs.Annotation .NET
  steps:
  - name: Verify the **azure blob connection string** in Azure Key Vault matches the
      storage account.
    text: Verify the **azure blob connection string** in Azure Key Vault matches the
      storage account.
  - name: Test the connection with Azure Storage Explorer.
    text: Test the connection with Azure Storage Explorer.
  - name: Ensure your firewall allows outbound traffic on port 443 to `*.blob.core.windows.net`.
    text: Ensure your firewall allows outbound traffic on port 443 to `*.blob.core.windows.net`.
  - name: '**Create a test container** and upload a PDF.'
    text: '**Create a test container** and upload a PDF.'
  - name: '**Add the connection string** to Azure Key Vault and update the sample
      code.'
    text: '**Add the connection string** to Azure Key Vault and update the sample
      code.'
  - name: '**Run the async loading example** and verify the annotation UI appears.'
    text: '**Run the async loading example** and verify the annotation UI appears.'
  - name: '**Introduce caching** for your most‑used documents.'
    text: '**Introduce caching** for your most‑used documents.'
  - name: '**Scale up** by adding monitoring, logging, and production‑grade error
      handling.'
    text: '**Scale up** by adding monitoring, logging, and production‑grade error
      handling.'
  type: HowTo
- questions:
  - answer: Authentication errors usually mean the stored connection string is outdated
      or the account key was regenerated. Retrieve the latest secret from Azure Key
      Vault, test it with Azure Storage Explorer, and consider switching to Azure
      AD‑based authentication for production.
    question: How do I handle authentication errors with Azure Blob Storage?
  - answer: Yes – it streams PDFs directly from a `MemoryStream`, avoiding full‑file
      loading. For files over 200 MB, enable `DocStreamOptions` with a 64 KB buffer
      and monitor memory usage; you’ll typically stay under 500 MB of RAM even with
      300‑page PDFs.
    question: Can GroupDocs.Annotation handle large documents efficiently from Azure?
  - answer: Set a reasonable `HttpClient.Timeout` (e.g., 30 seconds), wrap the download
      in a Polly retry policy with exponential back‑off, and surface a progress indicator
      so users know the operation is still in progress.
    question: What’s the best way to handle network timeouts when loading documents?
  - answer: Use per‑tenant containers or blob‑level ACLs, generate short‑lived SAS
      tokens for each request, and always validate the tenant’s identity before issuing
      a token. Never rely on obscurity – enforce strict server‑side checks.
    question: How do I secure document access in a multi‑tenant application?
  - answer: Absolutely. GroupDocs.Annotation works with any `Stream`. Replace the
      Azure download code with the equivalent AWS S3 or Google Cloud Storage SDK call,
      return a `MemoryStream`, and the rest of the annotation pipeline remains unchanged.
    question: Is it possible to integrate this with other cloud storage providers?
  type: FAQPage
tags:
- azure blob connection string
- GroupDocs.Annotation
- .NET
- Azure Blob Storage
- document loading
title: GroupDocs.Annotation .NET 用 Azure blob 接続文字列
type: docs
url: /ja/net/document-loading/load-documents-azure-blob-groupdocs-annotation-dotnet/
weight: 1
---

# GroupDocs.Annotation .NET 用 Azure Blob 接続文字列

クラウドで PDF に注釈を付けながら **azure blob connection string** を使用する必要がある場合、ここが適切な場所です。このチュートリアルでは、GroupDocs.Annotation を使用して .NET アプリケーションから直接 Azure Blob Storage に保存されたドキュメントをロード、注釈付け、管理する方法を示します。また、堅牢な **blob security best practices**、パフォーマンスのヒント、トラブルシューティングチェックリストも提供し、予期せぬ問題なく本番環境向けソリューションを提供できます。

## クイック回答
- **azure blob connection string とは何ですか？** ストレージ アカウント名とキーを含む文字列で、アプリが Azure Blob Storage に認証できるようにします。
- **GroupDocs.Annotation のライセンスは必要ですか？** はい—本番環境でのデプロイには有効なライセンスが必要です。開発用にはトライアルが利用できます。
- **200 MB を超える PDF をロードできますか？** はい、ただしストリーミング（`MemoryStream`）と非同期 I/O を使用してメモリ圧迫を回避してください。
- **Azure Key Vault は必須ですか？** 必須ではありませんが、接続文字列を安全に保存する推奨方法です。
- **サポートされている .NET バージョンは？** .NET Core 3.1+、.NET 5、.NET 6、.NET 7 はすべて最新の GroupDocs.Annotation パッケージで動作します。

## Azure Blob 接続文字列とは？

**azure blob connection string** は、ストレージ アカウント名、キー、エンドポイントを組み合わせた単一のテキスト値で、.NET コードが Azure Blob Storage に対して認証できるようにします。この文字列を使用すると、追加の認証手順なしでブロブの読み書きを行う `CloudBlobClient` オブジェクトを作成できます。

## Azure Blob Storage と GroupDocs.Annotation を組み合わせて使用する理由

GroupDocs.Annotation は **50 以上** の入力・出力フォーマットをサポートし、典型的なサーバー上で数百ページの PDF に対して 2 秒未満で注釈を付けられ、ドキュメントをストリームから直接処理するため、一時的なファイルをディスクに書き込む必要がありません。これを Azure Blob Storage と組み合わせることで、水平スケーリングが可能な完全なクラウドネイティブワークフローを実現し、コンプライアンス要件も満たします。

## 前提条件 – 開始前に必要なもの

- **開発環境** – .NET Core 3.1+ または .NET Framework 4.6.1+、Visual Studio 2019+（または C# 拡張機能付き VS Code）。
- **Azure の設定** – 有効な Azure サブスクリプション、ストレージ アカウント、少なくとも 1 つのコンテナ。**azure blob connection string** を手元に用意しておき、後で Azure Key Vault に移行します。
- **GroupDocs.Annotation** – NuGet パッケージ（v25.4.0）と本番用の有効なライセンス。
- **基本的な C# 知識** – async/await、`using` ステートメント、ストリームの取り扱いに慣れていること。

> **プロのコツ:** `sample-docs` というテストコンテナを作成し、PDF（例: `sample.pdf`）をアップロードしてからコーディングを開始してください。

## .NET 用 GroupDocs.Annotation の設定

### パッケージのインストール

NuGet パッケージ マネージャ コンソールからライブラリをインストールします:

```  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  
```

または .NET CLI を使用します:

```  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  
```

バージョン **25.4.0** は、クラウドベースのドキュメント読み込みで 30 % の速度向上をもたらし、メモリ使用量を最大 40 % 削減するため、推奨されています。

### ライセンス（この部分は省略しないでください）

- **開発 / テスト** – [GroupDocs Downloads](https://releases.groupdocs.com/annotation/net/) から無料トライアルをダウンロード（評価用の透かしが適用されます）または、[Temporary License Page](https://purchase.groupdocs.com/temporary-license/) で一時ライセンスを取得し、透かしなしでテストできます。
- **本番** – [GroupDocs Purchase](https://purchase.groupdocs.com/buy) でフルライセンスを購入します。ライセンス ファイルは、いずれの注釈操作よりも先にロードする必要があります。

### 基本的な初期化パターン

以下のスニペットは、ローカル PDF 用に `Annotator` を作成する最小限のコードを示しています。次のセクションでは、ファイルシステムのパスを Azure からのストリームに置き換えます。

```  
```csharp
using GroupDocs.Annotation;

// Basic initialization - we'll improve this for cloud documents
Annotator annotator = new Annotator("path/to/your/document.pdf");
```  
```

**定義アンカー:** `Annotator` は GroupDocs.Annotation の主要クラスで、ドキュメント ストリームをロードし、注釈の追加、編集、取得のメソッドを提供します。

## 完全な Azure 統合実装

### Azure Blob Storage へ安全に認証する方法は？

StorageSharedKeyCredential は、Azure Blob Storage へのリクエスト認証に使用されるストレージ アカウント名とキーを表します。  
資格情報を安全に保つため、実行時に Azure Key Vault から接続文字列を取得し、StorageSharedKeyCredential を作成します。この資格情報はアカウント名とキーを Blob サービス クライアントに提供し、ソースコードにシークレットを露出させずに認証済み操作を可能にします。以下のコードがこのパターンを示しています。

```  
```csharp
using System;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;

// Replace these with your actual values
string accountName = "***";
string accountKey = "***";
string containerName = "***";

public static CloudBlobContainer GetContainer()
{
    // Define the endpoint URL for Azure Blob Storage
    string endpoint = $"https://{accountName}.blob.core.windows.net/";

    // Authenticate with the storage account using credentials
    StorageCredentials storageCredentials = new StorageCredentials(accountName, accountKey);
    CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(
        storageCredentials, new Uri(endpoint), null, null, null);

    // Create a blob client to interact with the Blob service
    CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();

    // Retrieve a reference to the specified container
    CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);

    // Ensure that the container exists, creating it if necessary
    container.CreateIfNotExists();
    
    return container;
}
```  
```

**説明:**  
- `StorageSharedKeyCredential` はアカウント名とキーを検証します。  
- `CloudBlobContainer` は Azure ストレージ アカウント内の特定のコンテナを表します。  
- `CreateIfNotExistsAsync()` は、既に存在していても例外をスローせずにコンテナが存在することを保証します。

### Azure からドキュメントを MemoryStream にロードして注釈を付ける方法は？

MemoryStream はデータをメモリ内に保存する .NET ストリームで、ディスク I/O なしで高速な読み書きが可能です。  
CloudBlockBlob はブロック ブロブ用のクライアントオブジェクトで、ダウンロードとアップロード操作を行えます。  
認証後、対象ブロブを MemoryStream にダウンロードします。ストリームを GroupDocs.Annotation に渡す前に位置を先頭にリセットし、ライブラリがドキュメントの先頭から読み取れるようにします。MemoryStream を使用すると、一時ファイルを書き込む必要がなくなり、特に大きな PDF のパフォーマンスが向上します。

```  
```csharp
public static Stream LoadDocumentFromAzure(CloudBlobContainer container, string blobName)
{
    // Retrieve a reference to the desired blob
    CloudBlockBlob blockBlob = container.GetBlockBlobReference(blobName);

    // Download the blob content into a memory stream
    using (var memoryStream = new MemoryStream())
    {
        blockBlob.DownloadToStream(memoryStream);
        memoryStream.Position = 0; // Reset stream position for reading
        return memoryStream;
    }
}
```  
```

**重要ポイント:**  
- `CloudBlockBlob` は大容量ファイルに最適化されており、並列ダウンロードをサポートします。  
- `DownloadToStreamAsync` 後はストリームのカーソルが末尾にあるため、`0` にリセットすることが必須で、GroupDocs が先頭から読み取れます。  
- ストリームを `using` ブロックでラップすることで、確実に破棄されメモリリークを防止します。

## 無視できないセキュリティベストプラクティス

### Azure Key Vault で資格情報を安全に保存する方法は？

**azure blob connection string** をソースコードに埋め込まないでください。Azure SDK を使用して実行時に Azure Key Vault から取得します。これによりシークレット管理が集中化され、自動ローテーションがサポートされ、資格情報がソース管理やログに露出しないようにできます。

```  
```csharp
// Example pattern (you'll need Azure.Security.KeyVault.Secrets package)
var keyVaultClient = new SecretClient(new Uri("https://your-keyvault.vault.azure.net/"), new DefaultAzureCredential());
var storageKey = await keyVaultClient.GetSecretAsync("storage-account-key");
```  
```

### コンテナへの適切なアクセス制御を実施する方法は？

コンテナのアクセスレベルを Private に設定し、ブロブが公開されないようにし、Shared Access Signatures (SAS) を使用して特定の操作に対して限定的かつ時間制限付きの権限を付与します。さらに、ネットワーク ルールを構成してトラフィックを信頼できる IP 範囲に制限し、攻撃対象を減らします。

- コンテナの公開アクセスレベルを **Private** に設定します。
- アカウントキーを公開せず、**Shared Access Signatures (SAS)** を生成して一時的かつスコープ限定のアクセスを付与します。
- ネットワーク ルールを適用し、アプリケーションの IP 範囲からのトラフィックのみを許可します。

### 処理前にドキュメントを検証する方法は？

GroupDocs.Annotation にファイルをロードする前に、セキュリティおよびサイズポリシーを満たしているか確認します。MIME タイプがサポート対象か確認し、最大ファイルサイズを強制し、ファイルヘッダーが期待される形式（例: `%PDF`）と一致するかなどの簡易チェックを行います。

```  
```csharp
// Check file size, type, and content before processing
private static bool IsValidDocument(Stream documentStream)
{
    // Implement your validation logic here
    return documentStream.Length > 0 && documentStream.Length < MaxAllowedFileSize;
}
```  
```

## 効果的なパフォーマンス最適化戦略

### すべての I/O 操作を非同期にする方法は？

Azure Storage SDK と .NET が提供する非同期メソッドを使用して、ネットワーク呼び出し中にスレッドがブロックされないようにします。非同期 I/O は、スレッドプールが I/O 完了を待つ間に他のリクエストを処理できるようにし、スケーラビリティを向上させます。これは高同時実行シナリオで不可欠です。

```  
```csharp
public static async Task<Stream> LoadDocumentFromAzureAsync(CloudBlobContainer container, string blobName)
{
    var blockBlob = container.GetBlockBlobReference(blobName);
    var memoryStream = new MemoryStream();
    
    await blockBlob.DownloadToStreamAsync(memoryStream);
    memoryStream.Position = 0;
    
    return memoryStream;
}
```  
```

### 頻繁にアクセスされるドキュメントのスマートキャッシュを実装する方法は？

ダウンロードした MemoryStream を Azure Redis などの分散キャッシュに保存し、ブロブ名とバージョン識別子を組み合わせたキーを使用します。これにより、繰り返しのダウンロードが減少し、レイテンシが低下し、頻繁にアクセスされるホットドキュメントのストレージアウトバウンドコストが削減されます。

```  
```csharp
private static readonly Dictionary<string, byte[]> DocumentCache = new();

public static Stream GetCachedOrLoadDocument(CloudBlobContainer container, string blobName)
{
    if (DocumentCache.TryGetValue(blobName, out var cachedBytes))
    {
        return new MemoryStream(cachedBytes);
    }
    
    // Load from Azure and cache for next time
    var stream = LoadDocumentFromAzure(container, blobName);
    var bytes = ((MemoryStream)stream).ToArray();
    DocumentCache[blobName] = bytes;
    
    return new MemoryStream(bytes);
}
```  
```

### ネットワーク使用量を監視・最適化する方法は？

ブロブのアクセスパターンを監視し、ストレージ層やリクエストのバッチングを調整してネットワークトラフィックを最適化します。読み取りをグループ化し、適切な層を選択し、アウトバウンドメトリクスを追跡することで、コストを管理しパフォーマンスを向上させられます。

- 可能な限り複数のブロブ読み取りを単一リクエストにバッチ化します。
- 適切なブロブ層を選択します（頻繁な読み取りは Hot、アクセスが少ない場合は Cool）。
- Azure Monitor でアウトバウンドメトリクスを追跡し、予期しないコストを防止します。

## よくある落とし穴と回避策

### 大容量 PDF を扱う際にメモリリークを防止する方法は？

ストリームやその他の I/O オブジェクトは常に速やかに破棄し、注釈処理中のアプリケーションのプライベートメモリ使用量を監視してください。適切に破棄することで、ハンドルが残ってメモリ圧迫を引き起こすのを防げます。特に高スループット環境で大容量 PDF を処理する場合に重要です。

```  
```csharp
public static void ProcessDocumentSafely(CloudBlobContainer container, string blobName)
{
    using var documentStream = LoadDocumentFromAzure(container, blobName);
    using var annotator = new Annotator(documentStream);
    
    // Process your annotations here
    // Both streams will be properly disposed
}
```  
```

### Azure のレートリミットエラーを優雅に処理する方法は？

Azure が 429 Too Many Requests 応答を返した場合、指数バックオフを実装し、Retry-After ヘッダーを尊重します。この戦略によりリトライ試行が時間的に分散され、連続的なスロットリングの可能性が減少し、全体的な信頼性が向上します。

```  
```csharp
private static async Task<T> ExecuteWithRetry<T>(Func<Task<T>> operation, int maxRetries = 3)
{
    for (int i = 0; i < maxRetries; i++)
    {
        try
        {
            return await operation();
        }
        catch (StorageException ex) when (ex.RequestInformation.HttpStatusCode == 429)
        {
            // Rate limited - wait before retry
            await Task.Delay(TimeSpan.FromSeconds(Math.Pow(2, i)));
        }
    }
    
    throw new Exception("Max retries exceeded");
}
```  
```

### ネットワーク障害に対するレジリエンスを構築する方法は？

回路ブレーカライブラリ（例: Polly）を使用してキャッシュされたコピーにフォールバックするか、ユーザーフレンドリーなエラーメッセージを表示し、バックグラウンドでリトライします。

## 実際のユースケースとアプリケーション

### 典型的な文書レビューのワークフローは？

法務チームは契約書をプライベートな Azure コンテナに保存し、レビュー担当者が GroupDocs.Annotation を通じて注釈を付け、すべてのバージョンを Azure Blob Storage に保持して監査コンプライアンスを確保できます。

### 教育コンテンツ管理にどのように役立ちますか？

講師は講義スライドを Azure にアップロードし、学生は同じ注釈付き PDF に即座にアクセスでき、プラットフォームは Azure のストレージ層に応じて自動的にスケールします。

### コンプライアンス文書にとって有用な理由は？

Azure は組み込みの不変性と保持ポリシーを提供し、GroupDocs はすべての注釈変更を追跡するため、完全で改ざん防止の監査トレイルが得られます。

## このアプローチを使用すべきでないケース

- 注釈が不要なシンプルなファイル閲覧アプリ – 軽量ビューアの方がコストが低くなります。
- オフライン優先のシナリオ – この統合は Azure へのネットワーク接続が必要です。
- 予算が極端に限られるプロジェクト – Azure ストレージと GroupDocs のライセンスは継続的なコストがかかります。
- リアルタイム共同編集（Google Docs スタイル） – GroupDocs.Annotation は同時・ライブ編集向けに設計されていません。

## トラブルシューティングガイド

### Azure Blob Storage の接続問題を解決する方法は？

接続できない場合、まず Key Vault に保存されている接続文字列がストレージ アカウントの資格情報と一致しているか確認してください。Azure Storage Explorer で接続をテストし、ファイアウォールでポート 443 のアウトバウンドトラフィックが `*.blob.core.windows.net` へ許可されていることを確認します。

1. Azure Key Vault の **azure blob connection string** がストレージ アカウントと一致していることを確認します。
2. Azure Storage Explorer で接続をテストします。
3. ファイアウォールがポート 443 のアウトバウンドトラフィックを `*.blob.core.windows.net` へ許可していることを確認します。

### メモリ不足例外を診断する方法は？

メモリ不足エラーは、破棄されていないストリームやファイル全体をメモリに読み込むことが原因であることが多いです。.NET のメモリ診断を有効にし、ストリームの寿命をログに記録し、最大ドキュメントサイズを強制して過剰なメモリ使用を防止してください。

- .NET メモリ診断 (`dotnet-counters`) を有効にします。
- ストリームの作成と破棄のタイムスタンプをログに記録します。
- 最大ドキュメントサイズ（例: 300 MB）を設定し、超過するアップロードは明確なエラーで拒否します。

### ドキュメント読み込みが遅い場合の改善方法は？

読み込み速度を上げるには、非同期ブロブダウンロードに切り替え、頻繁にアクセスされるファイルのキャッシュを有効にし、ホットドキュメントは Hot 層に、使用頻度の低いファイルは Cool 層に移動します。これらの手順でレイテンシが低減し、スループットが向上します。

- 非同期ダウンロード (`DownloadToStreamAsync`) に切り替えます。
- ホットドキュメントのキャッシュ（Redis またはインメモリ）を有効にします。
- 頻繁にアクセスされるブロブは Hot 層、アーカイブファイルは Cool 層を使用します。

## 結論

**azure blob connection string** に基づく認証と GroupDocs.Annotation のストリーミング API を組み合わせることで、セキュアで高性能なクラウドネイティブの注釈ソリューションが実現します。以下を忘れずに行ってください:

- シークレットは Azure Key Vault に保存（ハードコードしない）。  
- 速度向上のために非同期 I/O とキャッシュを使用。  
- レジリエンスのためにリトライと回路ブレーカーパターンを実装。  
- コストとパフォーマンスを管理するために Azure メトリクスを監視。

### 次のステップ

1. **テストコンテナを作成**し、PDF をアップロードします。
2. **接続文字列を Azure Key Vault に追加**し、サンプルコードを更新します。
3. **非同期ロードの例を実行**し、注釈 UI が表示されることを確認します。
4. **最も使用頻度の高いドキュメントにキャッシュを導入**します。
5. **監視、ロギング、本番レベルのエラーハンドリングを追加**してスケールアップします。

素晴らしいものを作る準備はできましたか？上記の認証スニペットから始め、最初のドキュメントをロードし、残りは GroupDocs.Annotation に任せましょう。

## よくある質問

**Q: Azure Blob Storage の認証エラーはどう対処すべきですか？**  
A: 認証エラーは、保存された接続文字列が古いか、アカウントキーが再生成されたことが原因です。最新のシークレットを Azure Key Vault から取得し、Azure Storage Explorer でテストし、本番環境では Azure AD ベースの認証への切り替えを検討してください。

**Q: GroupDocs.Annotation は Azure から大容量ドキュメントを効率的に処理できますか？**  
A: はい – `MemoryStream` から直接 PDF をストリーミングするため、ファイル全体のロードを回避します。200 MB 超のファイルの場合、64 KB バッファの `DocStreamOptions` を有効にし、メモリ使用量を監視してください。300 ページの PDF でも通常は 500 MB 未満の RAM で済みます。

**Q: ドキュメント読み込み時のネットワークタイムアウトはどう対処すべきですか？**  
A: 適切な `HttpClient.Timeout`（例: 30 秒）を設定し、Polly の指数バックオフ付きリトライポリシーでダウンロードをラップし、進行状況インジケータを表示してユーザーに処理が継続中であることを知らせます。

**Q: マルチテナントアプリケーションでドキュメントアクセスを安全にするには？**  
A: テナントごとのコンテナまたはブロブレベルの ACL を使用し、各リクエストに対して短期間有効な SAS トークンを生成し、トークン発行前に必ずテナントの身元を検証します。隠蔽に頼らず、厳格なサーバー側チェックを実施してください。

**Q: 他のクラウドストレージプロバイダーと統合できますか？**  
A: もちろん可能です。GroupDocs.Annotation は任意の `Stream` と連携します。Azure のダウンロードコードを AWS S3 や Google Cloud Storage の SDK 呼び出しに置き換え、`MemoryStream` を返せば、注釈パイプラインの残りは変更不要です。

---

**最終更新日:** 2026-08-04  
**テスト済み:** GroupDocs.Annotation 25.4.0 for .NET  
**作者:** GroupDocs

## 関連チュートリアル

- [Azure Blob Storage からドキュメントをロードする .NET](/annotation/net/document-loading-essentials/load-document-from-azure/)
- [GroupDocs.Annotation .NET ドキュメントロード](/annotation/net/document-loading-essentials/)
- [GroupDocs.Annotation を使用したドキュメントプレビュー生成 .NET 完全ガイド](/annotation/net/advanced-usage/generate-document-pages-preview/)