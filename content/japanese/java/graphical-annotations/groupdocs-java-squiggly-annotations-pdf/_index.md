---
categories:
- Java Development
date: '2026-05-16'
description: GroupDocs.Annotation を使用して Java でアノテーション返信を作成する方法を学びましょう。実践的な例、パフォーマンス向上のヒント、ベストプラクティスを通じて、Java
  における PDF アノテーションをマスターできます。
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Java PDF アノテーション チュートリアル
schemas:
- author: GroupDocs
  dateModified: '2026-05-16'
  description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  headline: 'Java PDF Annotation Library: create annotation reply java'
  type: TechArticle
- description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  name: 'Java PDF Annotation Library: create annotation reply java'
  steps:
  - name: Import All Required Classes
    text: '- `Annotator` is the entry point for all document‑level operations. - `Point`
      represents a coordinate on a page (X and Y measured from the top‑left). - `SquigglyAnnotation`
      defines the wavy underline used to highlight errors. - `Reply` stores threaded
      comments attached to an annotation. - `SaveOptio'
  - name: Create and Configure Your Squiggly Annotation
    text: 'SquigglyAnnotation is a class that creates a wavy underline used to highlight
      errors in a PDF. - **Coordinate system**: Points start at the top‑left corner.
      The two points above draw a horizontal wavy line from (100, 200) to (300, 200).
      - **Opacity** 0.7 means the annotation is 70 % opaque, letting '
  - name: Add Interactive Replies (Optional but Powerful)
    text: Reply is a class representing a comment thread attached to an annotation.
      - Replies create a **threaded discussion** directly on the annotation, mirroring
      the experience of modern PDF reviewers. - Each reply stores author information
      and a timestamp, which you can later filter or display in a UI.
  - name: Apply Annotation and Save Document
    text: '- The **try‑with‑resources** construct automatically closes the `Annotator`,
      releasing file handles and native buffers. - `save` writes the modified PDF
      to `output.pdf`. > **Memory note:** The `Annotator` loads only the pages you
      touch. For multi‑hundred‑page PDFs, this approach keeps heap usage und'
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation focuses exclusively on annotation workflows, offering
      over 30 annotation types, threaded replies, and native support for 50 + file
      formats while keeping the memory footprint under 200 MB for 500‑page PDFs.
    question: What makes GroupDocs.Annotation better than other Java PDF libraries?
  - answer: Absolutely. Create a `@RestController` that injects the `Annotator` service,
      processes multipart uploads, and streams the annotated PDF back to the client.
      Remember to configure a thread‑pool for concurrent requests.
    question: Can I use this library with Spring Boot applications?
  - answer: Query each page’s dimensions via `annotator.getPageInfo(pageIndex)` and
      calculate relative coordinates (e.g., percentages) instead of hard‑coding point
      values. This ensures annotations appear correctly on A4, Letter, and custom‑size
      pages.
    question: How do I handle documents with different page sizes?
  - answer: Yes. Call `annotator.get()` to retrieve a collection of all annotations,
      then iterate to read properties such as author, comment, and geometry. This
      is useful for migration or analytics scenarios.
    question: Is there a way to extract existing annotations from PDFs?
  - answer: Implement authentication at the application layer, store the user ID with
      each `Reply`, and enforce business rules (e.g., only the author or an admin
      can edit or delete a reply). The API itself does not enforce permissions, giving
      you full flexibility.
    question: What's the best approach for handling annotation permissions in multi‑user
      systems?
  type: FAQPage
tags:
- pdf-annotations
- java-libraries
- document-processing
- groupdocs
title: 'Java PDF Annotation Library: アノテーション返信の作成 (java)'
type: docs
url: /ja/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Java PDF アノテーション ライブラリ: アノテーション返信の作成 (Java)

If you need to **create annotation reply java** for PDFs—whether you’re building a contract‑review portal, an e‑learning system, or a bulk‑processing pipeline—this guide shows you exactly how to do it with GroupDocs.Annotation for Java. We’ll walk through setup, squiggly annotation creation, reply threading, and performance tuning so you can ship a reliable solution in days, not weeks.

## クイック回答
- **GroupDocs.Annotation の主な目的は何ですか？** Java で PDF アノテーションのプログラムによる作成、変更、抽出を可能にします。  
- **スキューイィ（波線）アノテーションはどう追加しますか？** `SquigglyAnnotation` をインスタンス化し、ジオメトリとスタイルを設定してから `annotator.add(...)` を呼び出します。  
- **アノテーションに返信を添付できますか？** はい—`Reply` オブジェクトを作成し、作者とテキストを設定して親アノテーションに関連付けます。  
- **本番環境でライセンスが必要ですか？** 絶対に必要です。有効なライセンスがないと出力に透かしが入ります。  
- **バッチ処理に適していますか？** はい—`try‑with‑resources` を使用して各ドキュメントを開き、アノテーションを付け、閉じることでメモリ使用量を抑えます。  

## なぜ Java 開発者に PDF アノテーション ライブラリが必要なのか

PDF に手動でマークアップするのは時間がかかり、エラーが起きやすいです。特に何百もの契約書や試験用紙をレビューする必要がある場合はなおさらです。Java 用 PDF アノテーション ライブラリはこの作業を自動化し、ハイライト、スキューイィ（波線）下線、スレッド化されたコメントをファイルに直接埋め込むことができます。その結果、別のビューアを必要とせず、すべてのマークアップを保持した検索可能でポータブルなドキュメントが得られます。

**このガイドで習得できること**
- Maven プロジェクトへの GroupDocs.Annotation のインストールとライセンス設定  
- Word のネイティブ下線のように見えるスキューイィ（波線）アノテーションの作成  
- 共同レビューのために任意のアノテーションにスレッド化された返信を追加  
- 大容量 PDF を処理する際のメモリと CPU 使用率の最適化  
- Spring Boot、マイクロサービス、デスクトップアプリへのソリューションのデプロイ  

法務文書レビューシステム、教育用採点ツール、または自動品質管理パイプラインを構築する場合でも、以下の手法は本番環境に即した基盤を提供します。

## create annotation reply java とは何か

`create annotation reply java` は、Java を使用して既存の PDF アノテーションにコメントスレッド（Reply）を添付するプログラム的なプロセスです。返信により複数のレビュアーが文書を離れることなく特定のマークアップについて議論でき、シームレスなインプレース コラボレーションが実現します。この機能により、静的な PDF がインタラクティブなディスカッション プラットフォームに変わり、コンテキストと監査トレイルがファイル内に直接保存されます。

## 前提条件: 環境の準備

- **JDK** 8 以上（ガベージコレクション性能向上のため JDK 11 以上推奨）  
- **Maven** または **Gradle**（依存関係管理用、例は Maven 使用）  
- Maven 対応の IDE（IntelliJ IDEA、Eclipse、または VS Code）  
- IDE とテスト実行用に最低 **2 GB** の空き RAM  
- 実験用のサンプル PDF ファイル（任意の PDF エディタで簡単な PDF を生成可能）  

GroupDocs.Annotation は完全にプロセス内で動作し、外部の PDF ビューアやネイティブライブラリは不要です。

## GroupDocs.Annotation for Java の設定

ライブラリの統合は数ステップのプロセスですが、見落とすとランタイムエラーを引き起こす隠れた落とし穴がいくつかあります。

### Maven 依存関係の設定

`pom.xml` にリポジトリと依存関係を追加します。Maven がアーティファクトを解決できるように、`<repositories>` 要素を `<dependencies>` の **前** に配置してください。

```xml
<repositories>
    <repository>
        <id>groupdocs-repo</id>
        <url>https://repo.groupdocs.com/repo</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>25.2</version>
    </dependency>
</dependencies>
```

> **プロのコツ:** 最新バージョンは GroupDocs のリリースページで確認してください。新しいリリースには、最新の PDF 標準へのサポートやパフォーマンス向上が含まれることが多いです。

### ライセンス設定（これをスキップしないでください！）

GroupDocs.Annotation は本番使用にライセンスファイルが必要です。これがないと、生成されるすべての PDF に透かしが入ります。

1. **無料トライアル** – 30 日間フル機能、評価に最適。  
2. **一時ライセンス** – 開発および社内テストに適しています。  
3. **フルライセンス** – 商用展開には必須です。  

`GroupDocs.Annotation.lic` ファイルを resources フォルダに配置し、起動時にロードします:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **よくある落とし穴:** ライセンス手順を忘れると透かし入り PDF になり、API 呼び出しが黙って失敗します。起動時の早い段階で必ずライセンスを検証してください。

## 完全実装ガイド: スキューイィ（波線）アノテーションの追加

以下は、スキューイィ（波線）アノテーションを作成しながら **create annotation reply java** を行う手順ごとのウォークスルーです。各ステップには簡潔な説明が含まれており、各行の「なぜ」を理解できます。

### 手順 1: 必要なクラスすべてをインポート

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` はすべてのドキュメントレベル操作のエントリーポイントです。  
- `Point` はページ上の座標（左上基準の X と Y）を表します。  
- `SquigglyAnnotation` はエラーを強調する波線下線を定義します。  
- `Reply` はアノテーションに添付されたスレッド化されたコメントを保持します。  
- `SaveOptions` は出力形式と圧縮を制御できます。  

### 手順 2: スキューイィ（波線）アノテーションを作成し設定

```java
SquigglyAnnotation squiggly = new SquigglyAnnotation();
squiggly.setPageNumber(1);
squiggly.setColor(0xFFFF0000); // ARGB red
squiggly.setOpacity(0.7);
squiggly.setPoints(Arrays.asList(
    new Point(100, 200),
    new Point(300, 200)
));
```

SquigglyAnnotation は PDF のエラーを強調する波線下線を作成するクラスです。

- **座標系**: ポイントは左上隅から始まります。上記の 2 点は (100, 200) から (300, 200) までの水平な波線を描きます。  
- **不透明度** 0.7 はアノテーションが 70 % の不透明度で、下のテキストが読みやすいことを意味します。  

### 手順 3: インタラクティブな返信を追加（オプションだが強力）

```java
Reply reply1 = new Reply();
reply1.setComment("Please double‑check this clause.");
reply1.setAuthor("Alice");
reply1.setCreatedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("I think the wording is correct.");
reply2.setAuthor("Bob");
reply2.setCreatedOn(new Date());

squiggly.setReplies(Arrays.asList(reply1, reply2));
```

Reply はアノテーションに添付されたコメントスレッドを表すクラスです。

- 返信はアノテーション上に **スレッド化されたディスカッション** を作成し、最新の PDF レビューアの体験を再現します。  
- 各返信は作者情報とタイムスタンプを保持し、後で UI に表示したりフィルタリングしたりできます。  

### 手順 4: アノテーションを適用しドキュメントを保存

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- **try‑with‑resources** 構文は `Annotator` を自動的に閉じ、ファイルハンドルとネイティブバッファを解放します。  
- `save` は変更された PDF を `output.pdf` に書き込みます。  

> **メモリに関する注意:** `Annotator` は操作したページだけをロードします。数百ページの PDF でも、このアプローチにより典型的なサーバーでヒープ使用量を 150 MB 未満に抑えられます。

## 高度な構成オプション

### アノテーション外観のカスタマイズ

ブランドガイドラインに合わせて視覚スタイルを微調整できます:

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **ボーダー幅** は線の太さ（ポイント単位）を制御します。  
- **ARGB** フォーマットは透明度用のアルファチャンネルを含みます。  

### アノテーションの正確な位置決め

ページサイズが異なる PDF では座標を正確に取得するのは難しいことがあります。以下の体系的なアプローチに従ってください:

1. **PDF をビューアで開く**（例: Adobe Acrobat）し、対象領域の定規値をメモします。  
2. **定規値をポイントに変換**（1 ポイント = 1/72 インチ）。  
3. `annotator.getPageInfo(pageIndex)` を使用してページの幅と高さを取得し、相対位置を計算します。  

## よくある問題と解決策

### 問題: アノテーションが表示されない

**Most likely causes**
- ポイントがページ境界外にある  
- ライセンスがロードされていない（透かしがアノテーションを隠す）  
- ページ番号が間違っている（API ではページはゼロベース）  

**Solution checklist**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### 問題: 大容量ファイルでのパフォーマンス低下

Loading a 500‑page PDF into memory can stall your service. Mitigate this by:

- **1 ページずつ処理** – ドキュメントを開き、単一ページにアノテーションを付け、保存し、次へ進む。  
- **ストリーミング** – `Annotator` のストリーミング API を使用して全文書のバッファリングを回避。  
- **キャッシュ** – 頻繁にアクセスする PDF を高速キャッシュ（例: Redis）に保存し、キャッシュされたコピーにアノテーションを付ける。  

### 問題: カラー値が機能しない

GroupDocs は単純な RGB ではなく **ARGB**（アルファ、赤、緑、青）を期待します。ARGB 値 `0xFFFF0000` は完全に不透明な赤を意味します。`0xFF0000` を指定するとライブラリは誤って解釈し、黒いアノテーションになります。

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## パフォーマンスのベストプラクティス

### メモリ管理

バッチジョブで数十の PDF にアノテーションを付ける場合、各ファイルを個別の try‑with‑resources ブロックでラップします:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- このパターンにより各イテレーション後にネイティブバッファが解放され、長時間実行プロセスでの **OutOfMemoryError** を防止します。  

### バッチ処理の最適化

高スループット環境では、バウンドされたスレッドプールと組み合わせた並列ストリームを検討してください:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **バウンドプール** はスレッドの爆発を防ぎ、並列ストリームは CPU コアを活用し続けます。  

### ファイルサイズに関する考慮点

大容量 PDF（> 100 MB）はパフォーマンスを低下させます。以下の戦略を適用してください:

- **事前圧縮**: Ghostscript などのツールでアノテーション前に元 PDF を圧縮。  
- **必要なページのみアノテーション** – マークアップが不要なページはスキップ。  
- **分割**: 文書を論理的なセクション（例: 章ごと）に分割し、各チャンクを独立して処理。  

## 実際のユースケース

### 文書レビューシステム

法律事務所では問題のある条項にフラグを付ける必要があります。スキューイィ（波線）アノテーションとスレッド化された返信を組み合わせることで、複数の弁護士が PDF を離れることなく単一段落について議論できます:

- **弁護士 A** が条項の下に赤いスキューイィを追加し、「曖昧な表現」と記述。  
- **弁護士 B** が「‘material breach’ の定義を追加してください」と返信。  
- 全体の議論は埋め込まれたまま検索可能で監査可能です。  

### 既存システムとの統合

GroupDocs.Annotation は一般的な Java フレームワークとスムーズに連携します:

- **Spring Boot** – PDF のマルチパートアップロードを受け取り、アノテーションを付加し、結果をストリームで返す REST エンドポイント `/api/annotate` を公開。  
- **JSF** – アノテーション操作を UI コンポーネントにバインドし、ウェブビューでオンザフライのマークアップを実現。  
- **マイクロサービス** – ライブラリのフットプリントが小さく（< 15 MB）Docker でコンテナ化し、水平スケーリングが可能。  

### ワークフロー自動化

アノテーションを他の GroupDocs 製品（例: GroupDocs.Signature）と組み合わせてエンドツーエンドのパイプラインを構築します:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## スキューイィ（波線）アノテーションと代替手段の使い分け

| ユースケース | 推奨アノテーション |
|----------|------------------------|
| スペルや文法エラーのマーキング | **Squiggly** – ワードプロセッサに似た視覚的なヒント |
| エラーを示さず重要なセクションをハイライト | **Highlight** – 半透明オーバーレイ |
| 詳細なフィードバックの提供 | **Text** または **Comment** – フリーフォームのノートボックス |
| 文書の承認または却下 | **Stamp** – “Approved” または “Rejected” バッジ |

## 結論

これで GroupDocs.Annotation を使用した **create annotation reply java** の完全な本番対応レシピが手に入りました。API をマスターし、ライセンスを処理し、上記のパフォーマンスヒントを適用することで、以下が可能です:

- 数千の PDF に対するエラー・マーキングを自動化  
- ファイル内で共同作業のスレッド化されたディスカッションを実現  
- 大容量ドキュメントを処理してもメモリ使用量を低く抑制  

**次のステップ**
1. 他のアノテーションタイプ（ハイライト、スタンプ、テキスト）を試す。  
2. PDF を受け取り、アノテーションを付与し、結果を返す REST サービスを構築。  
3. 抽出 API (`annotator.get()`) を調査し、分析用に既存コメントを取得。  

プログラムによる PDF アノテーションの力は、手間のかかる手動マークアップを繰り返し可能で監査可能なコードに置き換える点にあります。ニッチな法務テック製品でも汎用的な文書ワークフローエンジンでも、このガイドの手法は前進するための確固たる基盤を提供します。

## よくある質問

**Q: GroupDocs.Annotation が他の Java PDF ライブラリより優れている点は何ですか？**  
A: GroupDocs.Annotation はアノテーションワークフローに特化しており、30 種類以上のアノテーション、スレッド化された返信、50 以上のファイル形式のネイティブサポートを提供し、500 ページの PDF でもメモリフットプリントを 200 MB 未満に抑えます。

**Q: このライブラリを Spring Boot アプリケーションで使用できますか？**  
A: もちろんです。`Annotator` サービスをインジェクトする `@RestController` を作成し、マルチパートアップロードを処理して、アノテーション済み PDF をクライアントにストリーム返却します。並行リクエスト用にスレッドプールを設定することを忘れずに。

**Q: 異なるページサイズのドキュメントをどう扱いますか？**  
A: `annotator.getPageInfo(pageIndex)` で各ページの寸法を取得し、ポイント値をハードコーディングする代わりに相対座標（例: パーセンテージ）を計算します。これにより A4、Letter、カスタムサイズのページでもアノテーションが正しく表示されます。

**Q: 既存の PDF からアノテーションを抽出する方法はありますか？**  
A: はい。`annotator.get()` を呼び出してすべてのアノテーションのコレクションを取得し、作者、コメント、ジオメトリなどのプロパティを読み取ります。移行や分析シナリオで有用です。

**Q: マルチユーザーシステムでアノテーション権限を扱う最適なアプローチは何ですか？**  
A: アプリケーション層で認証を実装し、各 `Reply` にユーザー ID を保存してビジネスルール（例: 作者または管理者のみが返信を編集・削除できる）を適用します。API 自体は権限を強制しないため、柔軟に対応できます。

**Q: 数百の PDF を処理する際のメモリ使用量を最適化するには？**  
A: 各ドキュメントで try‑with‑resources を使用し、ページを個別に処理し、同時メモリ消費を制限するバウンドスレッドプールを検討してください。VisualVM などのツールで JVM ヒープを監視し、`-Xmx` 設定を微調整すると効果的です。

**最終更新日:** 2026-05-16  
**テスト環境:** GroupDocs.Annotation 25.2 for Java  
**作者:** GroupDocs  

**追加リソース**
- [GroupDocs.Annotation for Java ドキュメント](https://docs.groupdocs.com/annotation/java/)
- [完全 API リファレンス](https://reference.groupdocs.com/annotation/java/)

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

```java
import com.groupdocs.annotation.Annotator;

// Initialize your annotator - this is your entry point to all annotation features
try (Annotator annotator = new Annotator("path/to/your/document.pdf")) {
    // All your annotation magic happens here
    System.out.println("Annotator initialized successfully!");
}
```

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.annotationmodels.SquigglyAnnotation;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
```

```java
// Create a new SquigglyAnnotation instance
SquigglyAnnotation squigglyAnnotation = new SquigglyAnnotation();

// Set the creation date of the annotation
squigglyAnnotation.setCreatedOn(new Date());

// Define font and background colors using RGB values
squigglyAnnotation.setFontColor(65535); // Yellow color in ARGB format
squigglyAnnotation.setBackgroundColor(16761035); // Light blue color in ARGB format

// Set a message to display with the annotation
squigglyAnnotation.setMessage("This is squiggly annotation");

// Define opacity (range 0.0 - 1.0)
squigglyAnnotation.setOpacity(0.7);

// Specify the page number for the annotation (zero-based index)
squigglyAnnotation.setPageNumber(0);

// Set squiggly line color specific to Word and PDF documents
squigglyAnnotation.setSquigglyColor(1422623); // Color code for squiggly lines

// Define points marking the start and end of the annotation on the page
List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));
points.add(new Point(240, 730));
points.add(new Point(80, 650));
points.add(new Point(240, 650));
squigglyAnnotation.setPoints(points);
```

```java
// Create replies to the annotation (optional)
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(new Date());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

// Associate replies with the annotation
squigglyAnnotation.setReplies(replies);
```

```java
try (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Add the prepared squiggly annotation to the document
    annotator.add(squigglyAnnotation);
    
    // Save the annotated document
    annotator.save("YOUR_OUTPUT_DIRECTORY/result_squiggly_annotation.pdf");
}
```

```java
// Custom color configurations
squigglyAnnotation.setFontColor(0xFF0000); // Red text
squigglyAnnotation.setBackgroundColor(0x00FF00); // Green background
squigglyAnnotation.setSquigglyColor(0x0000FF); // Blue squiggly line

// Transparency effects
squigglyAnnotation.setOpacity(0.3); // Very subtle
// or
squigglyAnnotation.setOpacity(0.9); // Almost opaque
```

```java
// Verify your points are within page boundaries
System.out.println("Page dimensions: " + annotator.getPageInfo(0));

// Check if your points make sense
List<Point> points = squigglyAnnotation.getPoints();
for (Point point : points) {
    System.out.println("Point: (" + point.getX() + ", " + point.getY() + ")");
}
```

```java
// Wrong: RGB format
int wrongColor = 0xFF0000; // This might not work as expected

// Right: ARGB format
int rightColor = 0xFFFF0000; // Full opacity red
```

```java
// Good practice: Use try-with-resources
try (Annotator annotator = new Annotator(inputPath)) {
    // Process annotations
    annotator.add(annotation);
    annotator.save(outputPath);
} // Automatic cleanup happens here

// Avoid: Manual resource management
Annotator annotator = new Annotator(inputPath); // Resources might leak
```

```java
public void processBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            addAnnotations(annotator);
            annotator.save(getOutputPath(path));
        } catch (Exception e) {
            // Handle individual document failures without stopping the batch
            System.err.println("Failed to process: " + path + " - " + e.getMessage());
        }
    }
}
```

```java
public class DocumentWorkflow {
    public void reviewDocument(String documentPath, ReviewLevel level) {
        try (Annotator annotator = new Annotator(documentPath)) {
            switch (level) {
                case GRAMMAR_CHECK:
                    addGrammarAnnotations(annotator);
                    break;
                case LEGAL_REVIEW:
                    addLegalAnnotations(annotator);
                    break;
                case FINAL_PROOF:
                    addProofreadingAnnotations(annotator);
                    break;
            }
            annotator.save(getReviewedPath(documentPath));
        }
    }
}
```

## 関連チュートリアル

- [Java PDF アノテーション ライブラリ チュートリアル](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [アノテーション返信の削除 Java - GroupDocs.Annotation で ID による返信管理](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [PDF アノテーションの編集 Java - 完全な GroupDocs チュートリアル](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)