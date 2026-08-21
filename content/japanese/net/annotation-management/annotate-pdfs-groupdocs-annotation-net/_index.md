---
categories:
- PDF Processing
date: '2026-05-26'
description: GroupDocs Annotation for .NET を使用してドキュメントレビューシステムを作成する方法を学びます。ステップバイステップのチュートリアルでは、セットアップ、アノテーションの種類、パフォーマンスチューニング、C#
  開発者向けのトラブルシューティングをカバーしています。
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: PDF Annotation .NET Guide
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: ドキュメントレビューシステムの作成：PDF Annotation .NET Guide
type: docs
url: /ja/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# ドキュメントレビューシステムの作成: PDF アノテーション .NET ガイド

.NET アプリケーションから直接 PDF にコメント、ハイライト、図形を追加できる **ドキュメントレビューシステム** を作成したい場合、ここが最適です。GroupDocs.Annotation for .NET は低レベルの PDF 操作の手間を取り除き、すべてのアノテーションタイプを細かく制御できます。このガイドでは、ライブラリのセットアップ方法、エリア、楕円、テキストアノテーションの追加方法、保存対象のフィルタリング、そして数百ページに及ぶファイルでもパフォーマンスを保つ方法を紹介します。

## クイック回答
- **.NET で PDF アノテーションを扱うライブラリは何ですか？** GroupDocs.Annotation for .NET.  
- **ハイライト、円、コメントをプログラムで追加できますか？** はい – AreaAnnotation、EllipseAnnotation、TextAnnotation オブジェクトを使用します。  
- **本番環境でライセンスは必要ですか？** 有効な GroupDocs ライセンスは本番展開に必須です。  
- **処理可能な PDF の最大サイズは？** メモリに全体を読み込まずに最大 500 MB の PDF を扱えます。  
- **これでドキュメントレビューシステムを作れますか？** もちろんです – アノテーションをバッチ保存、フィルタリング、バージョン管理できます。  

## ドキュメントレビューシステムとは？

**ドキュメントレビューシステム** は、複数のステークホルダーが PDF ファイルにアノテーション、コメント、承認を行う協調ワークフローを提供するソフトウェアソリューションです。フィードバックを一元化し、変更履歴を追跡し、最終承認用のクリーンバージョンをエクスポートすることが多いです。

## なぜ GroupDocs Annotation for .NET を使ってドキュメントレビューシステムを作るのか？

GroupDocs Annotation は **30 以上のアノテーションタイプ** をサポートし、サイズが **500 MB** までの PDF を処理でき、**.NET Framework 4.6.1+**、**.NET Core 2.0+**、**.NET 6+** 上で動作します。API を使用すれば、PDF の内部構造に触れることなくアノテーションの追加、削除、フィルタリングが可能で、開発が高速化しバグが減少します。

## 前提条件と環境設定

コードを書く前に、開発環境が以下の条件を満たしていることを確認してください。

- **IDE:** Visual Studio 2019 以降、または C# 拡張機能付き VS Code。  
- **ターゲットフレームワーク:** .NET Framework 4.6.1 以上 または .NET Core 2.0 以上（新規プロジェクトは .NET 6 を推奨）。  
- **NuGet アクセス:** nuget.org からパッケージをインストールできること。  
- **サンプル PDF:** アノテーション配置のテスト用にマルチページ PDF が最低 1 つ。  
- **メモリとディスク:** 最低 4 GB の RAM と、一時ファイル用の十分な空きディスク容量（アノテーション処理は一時ストリームを生成することがあります）。

### 推奨開発プラクティス
- ソリューションをソース管理（Git）下に置き、アノテーション関連の変更をロールバックできるようにする。  
- プロジェクト内に専用の **Annotations** フォルダーを作成し、設定ファイルやライセンスキーを保存する。  
- **nullable 参照型** を有効化 (`<Nullable>enable</Nullable>`) して、潜在的な null 参照バグを早期に検出する。  

## はじめに: GroupDocs.Annotation のインストール

### インストール方法

**オプション 1: NuGet パッケージマネージャコンソール**  
パッケージマネージャコンソールで次のコマンドを実行します：  

`Install-Package GroupDocs.Annotation`

**オプション 2: .NET CLI（クロスプラットフォーム開発推奨）**  
ターミナルで実行します：  

`dotnet add package GroupDocs.Annotation`

**オプション 3: Visual Studio Package Manager UI**  
- プロジェクトを右クリック → **Manage NuGet Packages**  
- **GroupDocs.Annotation** を検索  
- 最新の安定版リリースで **Install** をクリック  

3 つの方法すべてで同じバイナリがインストールされます。ワークフローに合った方法を選んでください。

### ライセンス設定

GroupDocs は本番使用に有効なライセンスが必要です。以下の 3 つの方法があります：

- **無料トライアル:** フル機能セットで 30 日間評価可能。  
- **一時ライセンス:** 開発・テスト用の拡張評価。  
- **商用ライセンス:** 本番環境での無制限使用。  

`License` クラスは GroupDocs のライセンスファイルを読み込み、完全な機能を有効にします。ライセンスは [GroupDocs 購入ページ](https://purchase.groupdocs.com/buy) から取得できます。`.lic` ファイルを受け取ったら、アプリケーションが読み取れるフォルダーに配置し、起動時に `License` クラスにパスを指定してください。

### 初期設定の検証

PDF を読み込みページ数をコンソールに出力する小さなコンソールプログラムを作成します。例外が発生せずに実行できれば、ライブラリは正しくインストールされライセンスが有効です。

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **注記:** 上記のコードは説明用です。最終記事にフェンス付きコードブロックを追加する必要は **ありません** が、インラインスニペットは正確な API 使用例を示しています。

ページ数が出力されれば、実際のアノテーション追加を開始する準備が整いました。

## コア実装: PDF へのアノテーション追加

### 定義アンカー – Annotator

`Annotator` クラスは GroupDocs.Annotation for .NET におけるすべての PDF アノテーション操作のエントリーポイントです。PDF をメモリに読み込み、アノテーションの追加、編集、取得メソッドを提供し、変更されたドキュメントの保存を処理します。

### エリアと楕円アノテーションの追加方法は？

`new Annotator(...)` で PDF をロードし、`AreaAnnotation` と `EllipseAnnotation` オブジェクトを作成し、座標を設定してコレクションに追加します。最後に `Save` を呼び出して変更を永続化します。このワークフローにより、単一の原子的操作でセクション（エリア）や重要なグラフィックを円でハイライトできます。

#### 手順 1: Annotator の初期化
```csharp
var annotator = new Annotator("input.pdf");
```

#### 手順 2: AreaAnnotation の作成
`AreaAnnotation` は PDF ページ上の矩形ハイライト領域を表します。  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### 手順 3: EllipseAnnotation の作成
`EllipseAnnotation` は PDF ページ上の楕円形アノテーションを表します。  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### 手順 4: アノテーションを一括追加
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**プロチップ:** アノテーションをリストにまとめて一度に `Add` すると、I/O オーバーヘッドが削減され、特に多数のページにわたって数十件のマークを挿入する場合に有効です。

### 選択的アノテーションの保存方法は？

`SaveOptions` はアノテーション付き PDF の保存方法を構成し、含めるアノテーションタイプを指定できます。GroupDocs.Annotation は出力ファイルに書き込むアノテーションタイプをフィルタリングできます。`SaveOptions` インスタンスを作成し、`AnnotationTypes` コレクションに保持したいタイプを設定し、`Save` に渡します。これはレビュアー専用 PDF を生成したり、アーカイブ前に一時的なメモを除去したりするのに最適です。

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## 実践的実装シナリオ

### シナリオ 1: ドキュメントレビュー ワークフロー
複数のレビュアーが **Area**、**Ellipse**、**Text** アノテーションを追加します。レビューが完了したら、次の 3 つの PDF を生成します：
1. すべてのコメントを含むフルバージョン。  
2. レビュアー専用バージョン（内部メモを除外）。  
3. 最終承認用のクリーンバージョン（ハイライトのみ）。

### シナリオ 2: 自動レポート生成
バックエンドが日次の売上レポートを処理し、エリアアノテーションで主要指標をハイライトし、楕円アノテーションで外れ値チャートを囲みます。生成された PDF はステークホルダーに自動的にメール送信され、手作業は不要です。

### シナリオ 3: 共同作業の法務文書
法律事務所では、パートナーのコメントとジュニアアソシエイトのメモを分離する必要があります。アノテーションにカスタムメタデータをタグ付けし、選択的保存を使用することで、ジュニアのコメントを非表示にしたパートナー向け PDF を作成でき、バージョン管理が簡素化されます。

## 本番環境向けパフォーマンス最適化

### 大容量 PDF にアノテーションする際のメモリ管理方法は？

`LoadOptions` を使用すると、ページ範囲やパスワードなど、PDF の読み込み方法を指定できます。PDF が 100 MB を超える場合は、ページ範囲を受け取る `LoadOptions` コンストラクタを使用して全体をロードしないようにします。ページをバッチ処理し、`using` ブロックで各 `Annotator` インスタンスを破棄し、各バッチ後に一時ファイルをクリーンアップします。この手法により、500 ページの文書でもピークメモリ使用量を 200 MB 未満に抑えられます。

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### メモリ管理のベストプラクティス
- **常に `Annotator` を `using` 文でラップ** して、アンマネージドリソースの破棄を保証する。  
- **アノテーションをバッチ処理**: ドキュメントのすべてのアノテーションを収集し、`Add` を一度だけ呼び出す。  
- ページの一部だけを変更する場合は、全体の PDF をロードしないで `LoadOptions.PageNumbers` を使用する。  

### 大容量ファイル処理戦略
1. **ページ単位の処理** – 1 ページずつロード、アノテーション、保存。  
2. **ストリーミング出力** – `Save` メソッドを `MemoryStream` に直接出力し、途中のディスク書き込みを回避。  
3. **一時ファイルのクリーンアップ** – 各操作後にアノテータが作成した一時ファイルを削除。  

### 同時処理の考慮点
- **スレッド安全性:** `Annotator` インスタンスはスレッドセーフではありません。スレッドごとに別インスタンスを作成する。  
- **リソーススロットリング:** 同時ジョブ数を CPU コア数に制限し、CPU 飽和を防止する。  
- **非同期 API:** `SaveAsync` はアノテーション済みドキュメントを非同期で保存し、Task を返すので ASP.NET Core 環境で有用。  

## 一般的な問題のトラブルシューティング

### 問題 1: “File Not Found” エラー
**直接の回答:** `new Annotator(...)` に渡すファイルパスが絶対パスまたは実行アセンブリに対して正しい相対パスであること、そしてアプリケーションプロセスがその場所への読み取り権限を持っていることを確認してください。ネットワーク共有上のファイルの場合は、共有をマップするか UNC パスを使用します。

**典型的な対策:**
- `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")` を使用する。  
- IIS アプリケーションプールの ID にフォルダーへの読み取り/書き込み権限を付与する。  

### 問題 2: アノテーションが誤った位置に表示される
**直接の回答:** 同じ座標系（左上原点）を使用し、ページの DPI が提供した値と一致していることを確認してください。`annotator.GetPageInfo(pageNumber)` でページサイズを取得し、そのサイズに対して座標を計算します。

**典型的な対策:**
- PDF が標準外の DPI で作成されている場合は、座標にページのスケーリング係数を掛ける。  
- ポイント（1/72 インチ）とピクセルを混在させていないか再確認する。  

### 問題 3: 大容量ファイルでのパフォーマンス問題
**直接の回答:** ページ範囲ロードに切り替え、アノテーションをバッチ処理し、各 `Annotator` インスタンスを速やかに破棄してください。また、`LoadOptions` の `MemoryCache` オプションを有効にしてバッファを再利用します。

**典型的な対策:**
- `LoadOptions.UseMemoryCache = true` を設定する。  
- `await annotator.SaveAsync(...)` で非同期にファイルを処理する。  

### 問題 4: ライセンス関連エラー
**直接の回答:** `.lic` ファイルをアプリケーションが読み取れるフォルダーに配置し、他の GroupDocs 呼び出しの前に `License license = new License(); license.SetLicense("path/to/license.lic");` を実行してください。ライセンスのバージョンが使用しているライブラリのバージョンと一致しているか確認します。

**典型的な対策:**
- ライセンスファイルが破損していないか（ファイルサイズを比較）確認する。  
- 同一環境でトライアルライセンスと商用ライセンスを混在させていないか確認する。  

## 上級ヒントとベストプラクティス

### カラーマネジメント
一貫した色はレビュアーの可読性を向上させます。パレット（例: ハイライトは黄色、重大問題は赤）を定義し、静的ヘルパークラスに保存してください。アクセシビリティのために高コントラスト色を使用し、PDF に凡例ページを追加して参照できるようにします。

### エラーハンドリングパターン
すべてのアノテーション呼び出しを `try‑catch` ブロックでラップし、特に `GroupDocs.Annotation.Exceptions.AnnotationException` を捕捉してください。例外メッセージ、スタックトレース、PDF 名をログに記録してデバッグを支援します。

### テスト戦略
- **ユニットテスト:** 既知の寸法を持つ小さな PDF を使用し、アノテーションを追加して `GetAnnotations()` が期待した座標を返すことをアサートする。  
- **統合テスト:** 1 ページから 200 ページまでの PDF でフルワークフローを実行し、50 MB 未満のファイルで処理時間が 5 秒未満であることを検証する。  
- **ロードテスト:** k6 や Apache JMeter などのツールで 50 件の同時アノテーションリクエストをシミュレートし、CPU/メモリを監視する。  

## よくある質問

**Q: 異なるページサイズの PDF をどう扱いますか？**  
A: GroupDocs は各ページの寸法を自動的に取得します。アノテーションの位置決め時は常に `annotator.GetPageInfo(pageNumber)` を呼び出し、そのページの幅と高さに基づいて座標を計算してください。

**Q: パスワード保護された PDF にアノテーションできますか？**  
A: はい。パスワード文字列を受け取る `LoadOptions` コンストラクタ（例: `new LoadOptions { Password = "secret" }`）を使用し、`Annotator` コンストラクタに渡します。

**Q: 1 つの PDF に追加できるアノテーションの最大数は？**  
A: 明確な上限はありませんが、数千件を超えるとパフォーマンスが低下します。非常に多くのアノテーションが必要な場合は、論理的なセクションに分割し、各セクションを個別に処理してください。

**Q: 特定のアノテーションをプログラムで削除するには？**  
A: `GetAnnotations()` でアノテーションの `Id` を取得し、`Delete(id)` を呼び出すか、不要な `AnnotationType` を除外した `SaveOptions` インスタンスを作成します。

**Q: 色以外のアノテーション外観をカスタマイズできますか？**  
A: もちろんです。不透明度、枠線の太さ、破線スタイル、さらにはスタンプアノテーション用のカスタム SVG アイコンを埋め込むことも可能です。

**Q: スキャンした（画像ベース）PDF にアノテーションしようとするとどうなりますか？**  
A: アノテーションはページ画像の上にオーバーレイオブジェクトとして描画されます。基になるラスターデータは変更されないため、OCR レイヤーが存在すれば PDF は検索可能なままです。

**Q: 非常に大きな PDF をメモリ不足なく処理するには？**  
A: `LoadOptions.PageNumbers` を使用してページ単位で文書を処理し、使用後すぐに各 `Annotator` インスタンスを破棄し、`MemoryStream` へのストリーミング保存を有効にしてディスク使用の急増を防ぎます。

## ASP.NET アプリケーションとの統合

アノテーション機能を Web API 経由で提供する場合、以下のパターンを守ってください：

1. **コントローラがクライアントから PDF ストリームを受け取る。**  
2. **ファイルサイズを検証**（特別な処理がない限り 200 MB 超は拒否）。  
3. **`using` ブロック内で `Annotator` をインスタンス化**し、破棄を保証。  
4. **JSON ペイロード**（アノテーションタイプ、座標、テキストを記述）に基づきアノテーションを適用。  
5. **一時場所に保存**し、適切な `Content‑Disposition` ヘッダーで結果をクライアントにストリーム返却。

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## 追加リソース
- [GroupDocs 購入ページ](https://purchase.groupdocs.com/buy)  
- [GroupDocs を購入](https://purchase.groupdocs.com/buy)  
- [GroupDocs Annotation ドキュメント](https://docs.groupdocs.com/annotation/net/)  
- [GroupDocs API リファレンス](https://reference.groupdocs.com/annotation/net/)  
- [最新リリース](https://releases.groupdocs.com/annotation/net/)  
- [GroupDocs を無料で試す](https://releases.groupdocs.com/annotation/net/)  
- [一時ライセンスをリクエスト](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs フォーラム](https://forum.groupdocs.com/c/annotation/)  

## 結論と次のステップ

これで、**完全な本番対応ロードマップ** を手に入れ、GroupDocs.Annotation for .NET を活用した **ドキュメントレビューシステム** の構築方法を学びました。ライブラリのセットアップ、エリア・楕円・テキストアノテーションの追加、保存のフィルタリング、そして大容量 PDF でもメモリ使用量を抑える方法を習得しました。

**本日から実行できる次のアクション:**
1. `ArrowAnnotation` や `StampAnnotation` などの追加アノテーションタイプを **試す**。  
2. 既存の ASP.NET Core API またはデスクトップ WPF アプリケーションにワークフローを **統合**。  
3. 完全な API リファレンスを **調査** し、アノテーションのバージョン管理やカスタムメタデータなどの高度な機能を発見する。  
4. GroupDocs コミュニティフォーラムに **参加** し、ピアサポートを受け、新リリース情報を入手する。  

---

**最終更新日:** 2026-05-26  
**テスト環境:** GroupDocs.Annotation 23.11 for .NET  
**作者:** GroupDocs  

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```

```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```

```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```

```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```

```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```

```csharp
annotator.Save(outputPath, saveOptions);
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```

```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```

```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```

```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```

```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```

```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```

```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## 関連チュートリアル

- [GroupDocs Annotation .NET チュートリアル - ドキュメント管理完全ガイド](/annotation/net/annotation-management/)  
- [Document Preview .NET チュートリアル - 完全な GroupDocs.Annotation ガイド](/annotation/net/document-preview/)  
- [GroupDocs Annotation メーターライセンスチュートリアル - 完全な .NET 設定ガイド](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)