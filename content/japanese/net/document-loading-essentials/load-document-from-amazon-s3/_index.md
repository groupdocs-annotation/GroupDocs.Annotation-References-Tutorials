---
categories:
- Document Management
date: '2026-07-06'
description: C# を使用して AWS 資格情報を設定し、GroupDocs Annotation を Amazon S3 と統合する方法を学びます。ドキュメントの読み込み、注釈付け、管理のステップバイステップ
  ガイド。
keywords:
- configure aws credentials
- document management s3
- read file s3 c#
lastmod: '2026-07-06'
linktitle: Amazon S3 からドキュメントをロード
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  headline: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  type: TechArticle
- description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  name: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  steps:
  - name: Define Output Path
    text: 'This creates a local path where your annotated document will be saved.
      The `Path.Combine` method ensures cross‑platform compatibility, and we''re preserving
      the original file extension to maintain document type integrity. **Pro Tip**:
      Consider using a timestamp in your output filename to avoid overwr'
  - name: Specify Document Key
    text: This is your document's unique identifier in the S3 bucket. In real‑world
      scenarios, you'll typically get this from user input, a database record, or
      an API parameter. Make sure the key exactly matches the S3 object name, including
      any folder prefixes (e.g., `documents/2025/sample.pdf`).
  - name: Initialize Annotator
    text: '`Annotator` is the core class in GroupDocs.Annotation that represents an
      editable document session. It provides methods to add, modify, and delete annotations.
      By wrapping the S3 download stream in a `using` block, we ensure proper disposal
      of both the stream and the annotator instance.'
  - name: Create Area Annotation
    text: This creates a rectangular annotation on your document. The `Rectangle(100,
      100, 100, 100)` parameters represent X‑position, Y‑position, width, and height
      respectively. The `BackgroundColor` value `65535` creates a yellow highlight
      – you can customize this using standard RGB color codes. **Common Us
  - name: Add Annotation to Document
    text: This method adds our area annotation to the document. You can call `Add()`
      multiple times to include different annotation types such as text comments,
      arrows, or stamps. The annotations exist in memory until you explicitly save
      the document.
  - name: Save Annotated Document
    text: Now we're saving the annotated document to our specified output path. This
      creates a new file with all annotations embedded. If you need to store the result
      back in S3—a common production scenario—simply upload the file using the S3
      SDK after this step.
  - name: Display Success Message
    text: A simple confirmation message that helps with debugging and provides user
      feedback. In a real application you would replace this with proper logging or
      UI notification.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports 50+ input and output formats—including PDF,
      DOCX, PPTX, and HTML—though annotation types may vary by format.
    question: Is GroupDocs.Annotation for .NET compatible with all document formats?
  - answer: Yes, you can explore the features of GroupDocs.Annotation for .NET by
      accessing the free trial version available [here](https://releases.groupdocs.com/).
      This lets you test S3 integration and annotation capabilities risk‑free.
    question: Can I try GroupDocs.Annotation for .NET before purchasing?
  - answer: Comprehensive documentation for GroupDocs.Annotation for .NET is available
      [here](https://tutorials.groupdocs.com/annotation/net/). The docs include API
      references, advanced examples, and integration guides.
    question: Where can I find documentation for GroupDocs.Annotation for .NET?
  - answer: You can obtain a temporary license for evaluation purposes from [here](https://purchase.groupdocs.com/temporary-license/).
      This removes trial limitations and gives you full access to test production
      scenarios.
    question: Do I need a temporary license to evaluate GroupDocs.Annotation for .NET?
  - answer: For any queries or support‑related issues, you can visit the GroupDocs.Annotation
      forum [here](https://forum.groupdocs.com/c/annotation/10). The community and
      support team are active and helpful for troubleshooting integration problems.
    question: Where can I seek assistance or support for GroupDocs.Annotation for
      .NET?
  type: FAQPage
tags:
- groupdocs
- s3-integration
- document-annotation
- cloud-storage
title: GroupDocs Annotation の S3 統合用 AWS 資格情報の設定
type: docs
url: /ja/net/document-loading-essentials/load-document-from-amazon-s3/
weight: 10
---

# AWS資格情報の設定 - GroupDocs Annotation S3 統合

## クイック回答
- **AWS 資格情報はどのように設定しますか？** `AmazonS3Client` コンストラクタに `BasicAWSCredentials` を使用するか、IAM ロールに依存して自動的に資格情報を解決します。  
- **必要な NuGet パッケージは何ですか？** `GroupDocs.Annotation` と `AWSSDK.S3`。  
- **100 MB を超える PDF に注釈を付けられますか？** はい – ストリーミングと非同期 API を使用して、ファイル全体をメモリに読み込むのを回避します。  
- **統合はスレッドセーフですか？** リクエストごとに別々の `Annotator` インスタンスを作成してください；SDK 自体はステートレスです。  
- **S3 のドキュメントを暗号化する必要がありますか？** コンプライアンスとデータ保護のためにサーバーサイド暗号化 (SSE‑S3 または SSE‑KMS) を有効にしてください。

## なぜ S3 を文書注釈に使用するのか？

S3 を文書注釈に使用すると、スケーラブルでコスト効果が高く、グローバルにアクセス可能なストレージソリューションを提供しながら、ファイルのセキュリティも確保できます。  
- **スケーラビリティ**: S3 は実質的に無制限のオブジェクトを扱い、1 ファイルあたり最大 5 TB、秒間数百万件のリクエストをサポートします。  
- **コスト効果**: 使用したストレージ分だけ支払うモデルで、低コストクラスへの自動階層化が可能です。  
- **グローバルアクセシビリティ**: 任意の AWS リージョンから低レイテンシでアクセスでき、注釈付きドキュメントは常に利用可能です。  
- **セキュリティ**: 組み込み暗号化 (SSE‑S3、SSE‑KMS) と細かい IAM ポリシーで機密データを保護します。  
- **統合**: CloudFront、Lambda、IAM など既存の AWS サービスとネイティブに連携します。

## 前提条件

開始する前に、以下の項目を準備してください：

1. **C# 開発環境** – Visual Studio または .NET 対応の VS Code。  
2. **GroupDocs.Annotation for .NET** – [公式サイト](https://releases.groupdocs.com/annotation/net/) からダウンロード。  
3. **AWS S3 アクセス** – 対象バケットに対する読み書き権限を持つ有効な AWS 資格情報。  
4. **基本的な C# 知識** – クラス、async/await、ストリームの理解。  
5. **Amazon S3 SDK** – NuGet (`AWSSDK.S3`) でインストール。  

## S3 アクセス用の AWS 資格情報の設定方法

`BasicAWSCredentials` は AWS アクセスキー ID とシークレットアクセスキーを保持するクラスです。  
`AmazonS3Client` は S3 サービスとやり取りするための AWS SDK クライアントです。

AWS キーを一度だけロードし、SDK がすべてのリクエストで再利用できるようにします。最もシンプルな方法は `BasicAWSCredentials` オブジェクトを作成し、`AmazonS3Client` コンストラクタに渡すことです。実運用では、シークレットをハードコーディングしないよう IAM ロールや環境変数を使用してください。

**プロのコツ:** EC2、ECS、Lambda 上で実行する場合は、明示的な資格情報を省略し、インスタンスプロファイルから自動的に一時的資格情報を取得させましょう。

## 名前空間のインポート

S3 統合に必要な名前空間をすべてインポートします：

```csharp
using Amazon.S3;
using Amazon.S3.Model;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
```

これらのインポートにより、AWS S3 操作と GroupDocs の注釈機能にアクセスできます。`Amazon.S3` 名前空間はクラウドストレージとのやり取りを担当し、`GroupDocs.Annotation.Models` は注釈フレームワークを提供します。

## ステップバイステップ実装

以下では、S3 からドキュメントをロードし、注釈を追加する一連の手順を示します。各ステップは独立して実行できるように分割しています。

### ステップ 1: 出力パスの定義

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

ローカルに注釈付きドキュメントを保存するパスを作成します。`Path.Combine` メソッドによりクロスプラットフォーム互換性が確保され、元のファイル拡張子を保持してドキュメントタイプの整合性を保ちます。

**プロのヒント:** 出力ファイル名にタイムスタンプを付与して、過去の注釈が上書きされないようにしましょう: `"result_" + DateTime.Now.ToString("yyyyMMdd_HHmmss") + Path.GetExtension("input.pdf")`。

### ステップ 2: ドキュメントキーの指定

```csharp
string key = "sample.pdf";
```

これは S3 バケット内でのドキュメントの一意の識別子です。実際のシナリオでは、ユーザー入力、データベースレコード、または API パラメータから取得することが一般的です。キーは S3 オブジェクト名（フォルダプレフィックスを含む）と完全に一致させてください（例: `documents/2025/sample.pdf`）。

### ステップ 3: Annotator の初期化

`Annotator` は GroupDocs.Annotation のコアクラスで、編集可能なドキュメントセッションを表します。注釈の追加、変更、削除のメソッドを提供します。

```csharp
using (Annotator annotator = new Annotator(DownloadFile(key)))
{
```

S3 ダウンロードストリームを `using` ブロックでラップすることで、ストリームと Annotator インスタンスの両方が適切に破棄されます。

### ステップ 4: エリア注釈の作成

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
```

矩形のエリア注釈を作成します。`Rectangle(100, 100, 100, 100)` のパラメータはそれぞれ X 位置、Y 位置、幅、高さを表します。`BackgroundColor` 値 `65535` は黄色のハイライトを生成します – 標準の RGB カラーコードでカスタマイズ可能です。

**エリア注釈の一般的な使用例**:
- 契約書の重要箇所のハイライト  
- 技術仕様書のレビュー領域のマーキング  
- プレゼンテーションスライドへのビジュアルコールアウト  

### ステップ 5: ドキュメントへの注釈追加

```csharp
annotator.Add(area);
```

このメソッドでエリア注釈をドキュメントに追加します。`Add()` を複数回呼び出すことで、テキストコメント、矢印、スタンプなど他の注釈タイプも追加可能です。注釈は明示的に保存するまでメモリ上に保持されます。

### ステップ 6: 注釈付きドキュメントの保存

```csharp
annotator.Save(outputPath);
```

指定した出力パスに注釈付きドキュメントを保存します。これにより、すべての注釈が埋め込まれた新しいファイルが作成されます。実運用で結果を再度 S3 に保存したい場合は、このステップの後に S3 SDK を使用してアップロードしてください。

### ステップ 7: 成功メッセージの表示

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

デバッグやユーザーへのフィードバックに役立つシンプルな確認メッセージです。実際のアプリケーションでは、適切なロギングや UI 通知に置き換えることを推奨します。

## S3 ダウンロードメソッドの実装

まだ実装していない `DownloadFile(key)` メソッドを作成します。以下が必須ヘルパーの例です：

```csharp
private static Stream DownloadFile(string key)
{
    var client = new AmazonS3Client("your-access-key", "your-secret-key", Amazon.RegionEndpoint.USEast1);
    var request = new GetObjectRequest
    {
        BucketName = "your-bucket-name",
        Key = key
    };
    
    var response = client.GetObjectAsync(request).Result;
    return response.ResponseStream;
}
```

**セキュリティ注意:** 本番コードに AWS 資格情報をハードコーディングしないでください。IAM ロール、環境変数、または共有資格情報ファイルを使用してシークレットをソース管理から除外しましょう。

## Amazon S3 からドキュメントをロードする方法

`GetObjectAsync` は S3 からオブジェクトを取得し、ストリームを含むレスポンスを返す非同期メソッドです。  
`MemoryStream` はディスク I/O を伴わずに高速な読み書きが可能な .NET ストリームです。  
前述の `Annotator` は注釈対象のドキュメントをロードするクラスです。

`GetObjectAsync` で PDF を直接 S3 から取得し、レスポンスストリームを `MemoryStream` でラップして `Annotator` コンストラクタに渡します。この方法により、元ファイルをディスクに書き出す必要がなくなり、I/O オーバーヘッドが削減され、大容量ファイルでもメモリ使用量を抑えて処理できます。

```csharp
using (var response = await s3Client.GetObjectAsync(bucketName, key))
using (var memoryStream = new MemoryStream())
{
    await response.ResponseStream.CopyToAsync(memoryStream);
    memoryStream.Position = 0;
    using (var annotator = new Annotator(memoryStream))
    {
        // Add annotations here
    }
}
```

## 一般的な統合問題と解決策

実装経験に基づく頻出問題とその対処法をまとめました：

### 問題 1: 「Access Denied」エラー
**問題**: アプリケーションが S3 オブジェクトにアクセスできない。  
**解決策**: 対象バケットとオブジェクトに対して `s3:GetObject` 権限が付与されていることを確認してください。

### 問題 2: 大きなファイルのタイムアウト
**問題**: 50 MB 超のドキュメントでタイムアウトが発生する。  
**解決策**: 非同期操作を実装し、タイムアウト値を増加させます：

```csharp
var client = new AmazonS3Client();
client.Config.Timeout = TimeSpan.FromMinutes(10);
```

### 問題 3: 複数ドキュメントのメモリ問題
**問題**: 多数のドキュメントを処理するとメモリ不足例外が発生する。  
**解決策**: ストリームを速やかに破棄し、バッチ処理でドキュメントを分割して処理してください。

### 問題 4: リージョン不一致エラー
**問題**: S3 クライアントがバケットを見つけられない。  
**解決策**: `RegionEndpoint` がバケットの実際のリージョンと一致していることを確認してください。

## パフォーマンスとセキュリティのベストプラクティス

### パフォーマンス最適化
- **非同期メソッドの使用**: 同期呼び出しより `GetObjectAsync()` を優先。  
- **キャッシュの実装**: 頻繁にアクセスするドキュメントを短期間ローカルに保存。  
- **バッチ処理**: 適切な場合は複数ファイルを並列で処理。  
- **ストリーム処理**: 大容量ドキュメント全体をメモリに読み込まず、ストリームで処理。

### セキュリティ考慮事項
- **IAM ロールの使用**: ハードコーディングされた資格情報を排除。  
- **S3 暗号化の有効化**: サーバーサイド暗号化 (SSE‑S3 または SSE‑KMS) を設定。  
- **アクセスログの実装**: 誰がどのドキュメントにアクセスしたかを追跡。  
- **ファイルタイプの検証**: 処理前に拡張子と MIME タイプをチェック。

## 実際のユースケース

この S3 統合パターンはさまざまな業界で活躍します：

1. **法務文書レビュー** – 法律事務所が S3 に保存された契約書に注釈を付与。  
2. **教育プラットフォーム** – 教師がクラウド上の学生提出物にマークアップ。  
3. **建設管理** – 建築家が地域を超えて設計図に注釈。  
4. **医療記録** – 医療機関が患者文書に安全にメモを追加。  
5. **金融サービス** – 監査人がコンプライアンス文書に共同作業で注釈。

## トラブルシューティングガイド

**S3 からドキュメントをロードできない**  
- AWS 資格情報とバケット権限を確認。  
- バケット名とオブジェクトキーのスペルを再確認。  
- ドキュメントが S3 上で破損していないか確認。

**注釈が表示されない**  
- 注釈追加後に `annotator.Save()` を呼び出したか確認。  
- 使用したドキュメント形式が注釈タイプに対応しているか確認。  
- 注釈座標がページ範囲内に収まっているか確認。

**パフォーマンス問題**  
- S3 リクエストレートを監視し、指数バックオフを実装。  
- 頻繁にアクセスするファイルは CloudFront CDN を利用。  
- グローバルアプリケーションでは S3 Transfer Acceleration を検討。

## よくある質問

**Q: GroupDocs.Annotation for .NET はすべてのドキュメント形式に対応していますか？**  
A: GroupDocs.Annotation は PDF、DOCX、PPTX、HTML など 50 以上の入力・出力形式をサポートしていますが、注釈タイプは形式により異なる場合があります。

**Q: GroupDocs.Annotation for .NET の無料トライアルはありますか？**  
A: はい、[こちら](https://releases.groupdocs.com/) から無料トライアル版を入手でき、S3 統合や注釈機能をリスクなくテストできます。

**Q: GroupDocs.Annotation for .NET のドキュメントはどこで確認できますか？**  
A: 詳細なドキュメントは [こちら](https://tutorials.groupdocs.com/annotation/net/) にあります。API リファレンス、高度なサンプル、統合ガイドが含まれています。

**Q: 評価目的で一時ライセンスは必要ですか？**  
A: 評価用の一時ライセンスは [こちら](https://purchase.groupdocs.com/temporary-license/) から取得できます。これによりトライアル制限が解除され、実運用シナリオをフルにテストできます。

**Q: GroupDocs.Annotation for .NET のサポートはどこで受けられますか？**  
A: 質問やサポートが必要な場合は、GroupDocs.Annotation フォーラム [こちら](https://forum.groupdocs.com/c/annotation/10) へアクセスしてください。コミュニティとサポートチームが統合問題の解決を支援します。

**Q: 注釈付きドキュメントをローカルではなく S3 に保存できますか？**  
A: もちろん可能です！`annotator.Save(localPath)` 後に `PutObjectAsync()` を使用して S3 にアップロードすれば、完全なクラウド‑ツー‑クラウドワークフローが実現します。

**Q: S3 ドキュメント注釈の最大ファイルサイズはどれくらいですか？**  
A: GroupDocs.Annotation は大容量ファイルを処理できますが、実際の上限はサーバーメモリと S3 転送タイムアウトに依存します。100 MB 超のファイルの場合は、ストリーミングまたはチャンク処理を導入してメモリ枯渇を防止してください。

**最終更新:** 2026-07-06  
**テスト環境:** GroupDocs.Annotation 23.12 for .NET  
**作成者:** GroupDocs  

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

```csharp
var credentials = new BasicAWSCredentials("YOUR_ACCESS_KEY", "YOUR_SECRET_KEY");
var s3Client = new AmazonS3Client(credentials, RegionEndpoint.USEast1);
```

## 関連チュートリアル

- [GroupDocs.Annotation .NET ドキュメントロード](/annotation/net/document-loading-essentials/)
- [GroupDocs.Annotation .NET で FTP からドキュメントをロードする方法 - 完全ガイド](/annotation/net/document-loading/groupdocs-annotation-net-load-from-ftp/)
- [GroupDocs.Annotation .NET ドキュメントプレビュー - 完全ガイド](/annotation/net/document-preview/)