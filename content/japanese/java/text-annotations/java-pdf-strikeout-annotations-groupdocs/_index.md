---
categories:
- Java PDF Processing
date: '2026-05-21'
description: GroupDocs を使用して Java で PDF に取り消し線注釈を追加する方法を学びます。このステップバイステップのチュートリアルでは、セットアップ、コード、トラブルシューティング、パフォーマンスのヒントをカバーしています。
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Java PDF Text Strikeout ガイド
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: JavaでPDFに取り消し線注釈を追加する方法 – 完全なGroupDocsガイド
type: docs
url: /ja/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# JavaでPDFに取り消し線アノテーションを追加する方法

PDFのテキストをプログラムで取り消し線を引く必要があったことはありませんか？ドキュメントレビューシステムを構築したり、編集ワークフローを作成したり、単に削除対象のテキストにマークを付けるだけでも、Javaで**取り消し線アノテーションを追加する方法**は、時間を節約し手作業を減らす実用的なスキルです。この包括的ガイドでは、プロジェクトのセットアップからパフォーマンスチューニングまで、GroupDocs.Annotation for Java を使用した取り消し線アノテーションの実装に必要なすべてを学べます。

## クイック回答
- **最初のステップは何ですか？** `pom.xml` に GroupDocs.Annotation の Maven 依存関係を追加します。  
- **取り消し線はどう作成しますか？** `Annotator` をインスタンス化し、ポイントで `StrikeoutAnnotation` を定義し、色/不透明度を設定してから `addAnnotation` を呼び出します。  
- **コメントを追加できますか？** はい、協働のために `Comment` オブジェクトをアノテーションに添付します。  
- **アノテーションがずれている場合は？** 座標ポイントを調整します。PDF は左下原点システムを使用します。  
- **ドキュメントサイズに制限はありますか？** GroupDocs は、ファイル全体をメモリに読み込まずに数百ページの PDF を処理します。

## PDFアノテーションにおける「取り消し線の追加」とは何ですか？
「取り消し線の追加」とは、アノテーション API を使用して PDF ドキュメント内の選択テキストにプログラムで線を引くプロセスを指します。Java では、GroupDocs.Annotation が専用の `StrikeoutAnnotation` クラスを提供し、取り消し線の描画、スタイリング、永続化を処理します。

## Java PDF取り消し線にGroupDocsを使用する理由
GroupDocs.Annotation は **50 以上の入力および出力フォーマット**（PDF、DOCX、XLSX、PPTX、HTML、一般的な画像形式など）をサポートしているため、特定のファイルタイプに縛られることはありません。低レベルの PDF 構造を抽象化したハイレベル API を提供し、フォント埋め込み、ページレンダリング、アノテーションの永続化を自動的に処理するため、開発者は PDF の内部構造ではなくビジネスロジックに集中できます。

## 前提条件とセットアップ要件

### 必須要件
- **Java Development Kit (JDK)：** バージョン 8 以上（最適なガベージコレクションのために JDK 11 以上を推奨）。  
- **GroupDocs.Annotation for Java：** Maven で統合（以下の Maven スニペット参照）。  
- **IDE：** IntelliJ IDEA、Eclipse、または任意の Java 対応エディタ。

### Maven依存関係の設定
`pom.xml` に以下の依存ブロックを追加します：

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

**プロ・ヒント：** 常に GroupDocs のリリースページで最新バージョンを確認してください。新しいリリースは機能追加やバグ修正が行われ、アノテーションのレンダリングに影響する可能性があります。

### ライセンス取得方法
GroupDocs.Annotation は本番使用のために有効なライセンスが必要です。以下の 3 つのオプションがあります：

- **無料トライアル：** [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/) からダウンロード  
- **一時ライセンス：** [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/) で開発キーをリクエスト  
- **フルライセンス：** [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy) で本番用に購入  

トライアル版は控えめな透かしが追加されるため、テスト計画をそれに合わせてください。

## ステップバイステップ実装ガイド

### コアコンポーネントの理解
以下の定義は、簡単な概念モデルを提供します：

- **Annotator：** PDF をロードし、アノテーションメソッドを提供する主要な API オブジェクト。  
- **StrikeoutAnnotation：** 取り消し線のビジュアルとスタイリングオプションを表す。  
- **Point：** ラインの開始点と終了点を示す座標ペア (X, Y)。  
- **Comment：** コラボレーション用にアノテーションに添付できる任意のテキスト。

### ステップ1：ファイルパスの設定
ソース PDF と出力ファイルの場所を定義します。パスが正しくないと「ファイルが見つかりません」エラーの一般的な原因になります。

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**一般的なミス警告：** 出力ディレクトリが存在し、書き込み可能であることを確認してください。GroupDocs は欠落したフォルダを自動作成しません。

### ステップ2：Annotatorの初期化
`Annotator` インスタンスを作成し、PDF をメモリにロードします。

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**ここで何が起こるか？** ライブラリは PDF 構造を解析し、内部表現を構築し、ページ単位のアノテーションキャンバスを準備します。数百ページのファイルの場合、このステップに数秒かかることがあります。

### ステップ3：コメントの追加（任意だが推奨）
`Comment` はアノテーションに添付できるテキストノートを表すクラスで、取り消し線の理由を説明するために使用します。

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**実務的なヒント：** コメントを使用してテキストが削除される理由を説明しましょう。これは法務や編集レビューのワークフローで特に有用です。

### ステップ4：アノテーション座標の定義
`Point` オブジェクトは、PDF ページ上のアノテーションの正確な位置を定義する X‑Y 座標ペアを保持します。

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**座標系の説明：** PDF の座標は左下隅 (0,0) から始まります。例では、対象ページの (80,730) から (240,730) までの水平線を作成しています。

**適切な座標の見つけ方：** 多くの開発者はページ幅/高さのパーセンテージを絶対ポイントに変換するヘルパーを作成し、異なるページサイズに対してコードを堅牢にします。

### ステップ5：取り消し線アノテーションの作成
`StrikeoutAnnotation` は、取り消し線のビジュアル、色や不透明度などのスタイルプロパティ、そして関連メタデータをカプセル化します。

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**カラー値：** `fontColor` は十進数の RGB 値を使用します（例：明るい黄色は 65535）。ブランド固有の色が必要な場合はオンラインコンバータを使用してください。

**不透明度の推奨：** `0.7`（70 %）の不透明度は、テキストを読みやすく保ちつつ明確な視覚的ヒントを提供します。

### ステップ6：アノテーションの適用
`addAnnotation` は `Annotator` のメソッドで、準備したアノテーションをドキュメントに登録し、レンダリングと保存が行われるようにします。

```java
annotator.add(strikeout);
```

### ステップ7：保存とクリーンアップ
`dispose()` は `Annotator` インスタンスが保持するネイティブリソースを解放し、処理完了後のメモリリークを防止します。

```java
annotator.save(outputPath);
annotator.dispose();
```

**メモリ管理の注意点：** `dispose()` を呼び出すことでネイティブリソースが解放され、大量の PDF をバッチ処理する際のメモリリークを防げます。

## 一般的な問題と解決策

### 問題1：「ファイルが見つかりません」エラー
**症状：** `Annotator` の構築中に例外がスローされます。  
**解決策：** 入出力パスの両方を確認し、アプリケーションに読み書き権限があることを確認してください。

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### 問題2：取り消し線が誤った位置に表示される
**症状：** 線が意図したテキストと合致しません。  
**解決策：** PDF の Y 座標は上方向に増加することを覚えておいてください。ビジュアルデバッグツールを使用するか、ページ寸法を出力してポイントを微調整します。

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### 問題3：アノテーションが表示されない
**症状：** 保存後に取り消し線が表示されません。  
**可能な原因と修正策：**
- **不透明度が低すぎる：** 一時的に不透明度を `1.0` に設定して可視性を確認してください。  
- **カラーのブレンド：** 赤 (`255`) などの高コントラスト色を使用してください。  
- **ページインデックスが間違っている：** ページ番号はゼロベースです。正しいページを対象にしているか確認してください。

### 問題4：大容量ファイルでのメモリ問題
**症状：** `OutOfMemoryError` が発生したり、パフォーマンスが低下したりします。  
**解決策：**
- ドキュメントを小さなバッチに分割して処理する。  
- 利用可能な場合はストリーミング API を使用する。  
- 各ドキュメント処理後に必ず `dispose()` を呼び出す。

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## 実際のアプリケーションとユースケース

### 法務文書レビュー
法律事務所は契約書に取り消し線を付けて削除された条項を示し、監査トレイルを保持します。

### 学術論文編集
教授はピアレビュー時に削除を提案するために取り消し線を使用し、文脈のために元のテキストを可視化したままにします。

### コンテンツ管理システム
出版プラットフォームは、手動モデレーション前にポリシー違反のセクションに自動的に取り消し線を付けてフラグ付けします。

### 文書のバージョン管理
企業は取り消し線アノテーションを、コードの差分に似た文書中心のバージョン管理ワークフローにおける「削除マーカー」として扱います。

## パフォーマンス最適化のヒント

### バッチ処理戦略
多数の PDF を処理する際は、可能な限り単一の `Annotator` インスタンスを再利用し、ファイルを並列スレッドで処理します。

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### メモリ管理のベストプラクティス
- すべての `Annotator` で `dispose()` を呼び出す。  
- ヒープ圧迫を防ぐために同時にロードするドキュメント数を制限する。  
- VisualVM などのツールで JVM のメモリ使用状況を監視する。

### 座標キャッシュ
同じアノテーションレイアウトを複数のファイルに適用する場合、`Point` オブジェクトをキャッシュして再計算を回避します。

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## 高度なカスタマイズオプション

### 動的カラー選択
ビジネスルールに基づき、実行時に色を選択します（例：重大な削除は赤、暫定的なものは黄色）。

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### 複数行取り消し線
複数行のテキストを横切るジグザグ線を描くために、`Point` ペアの系列を作成します。

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## トラブルシューティングチェックリスト
1. **ファイル権限：** 読み書きアクセスを確認する。  
2. **ライブラリバージョン：** サポートされている GroupDocs.Annotation のリリースを使用していることを確認する。  
3. **ライセンス状態：** ライセンスファイルが正しく参照されていることを確認する。  
4. **PDF 互換性：** PDF が破損しておらず、サポートされるサイズ制限内であることを確認する。  
5. **座標の検証：** すべてのポイントがページ境界内にあることを確認する。  
6. **ヒープ領域：** 非常に大きなファイルを処理する場合は JVM の `-Xmx` を増やす。

## よくある質問

**Q: 複数行にわたってテキストに取り消し線を引くことはできますか？**  
A: はい。目的のパスをたどる複数の `Point` オブジェクトを作成すれば、アノテーションは提供されたポリラインに従います。

**Q: ページ境界外の座標を指定した場合はどうなりますか？**  
A: アノテーションはクリップされ、見えなくなる可能性があります。常にページの幅と高さに対して座標を検証してください。

**Q: 追加した取り消し線アノテーションを削除できますか？**  
A: もちろんです。アノテーションの ID を使用するか、タイプでフィルタリングして `removeAnnotation` メソッドを呼び出し、プログラムで削除します。

**Q: 単一の PDF に追加できるアノテーション数に制限はありますか？**  
A: GroupDocs は厳密な上限を設けていませんが、数千件のアノテーションを追加するとパフォーマンスが低下する可能性があります。非常に多い場合はページ分割や要約を検討してください。

**Q: パスワード保護された PDF を扱うにはどうすればよいですか？**  
A: パスワードを `Annotator` コンストラクタに渡します。ライブラリはメモリ内でドキュメントを復号し、アノテーションを適用します。

**Q: ページサイズや向きが異なる PDF に対応するには？**  
A: `annotator.getPageInfo(pageNumber)` で各ページの寸法を取得し、それらの寸法に対して相対的に座標を計算して一貫した配置を確保します。

## 結論
これで、GroupDocs.Annotation を使用した Java で PDF に取り消し線アノテーションを **追加する方法** の完全な本番対応ソリューションが手に入りました。ファイルパスの取り扱い、座標計算、リソース管理をマスターすれば、この機能をドキュメントレビューツール、コンテンツパイプライン、または正確なビジュアルフィードバックが必要な任意の Java ベースのアプリケーションに組み込むことができます。

**次のステップ**
1. サンプルプロジェクトをクローンし、サンプル PDF で実行する。  
2. 異なる色、不透明度、コメントテキストで試す。  
3. 既存のドキュメント処理サービスにアノテーションワークフローを統合する。  
4. ハイライト、付箋、シェイプアノテーションなどの関連アノテーションタイプを調査し、PDF 操作ツールキットを拡充する。

もっと知りたいですか？公式ドキュメントで API の詳細な洞察を深めてください。

## 追加リソース
- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - GroupDocs ライブラリの一般的なドキュメント  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - 完全な API リファレンス  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - メソッドごとの詳細  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - ライブラリを最新に保つ  
- [Purchase License](https://purchase.groupdocs.com/buy) - 本番向けライセンス  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - 購入前に評価  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - 開発テスト用  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - コミュニティヘルプと公式サポート  

**最終更新日：** 2026-05-21  
**テスト環境：** GroupDocs.Annotation 23.12 for Java  
**作者：** GroupDocs

## 関連チュートリアル
- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)