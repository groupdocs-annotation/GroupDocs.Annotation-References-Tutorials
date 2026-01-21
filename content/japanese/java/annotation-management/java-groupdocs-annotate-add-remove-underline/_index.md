---
categories:
- Java Development
date: '2025-12-21'
description: GroupDocs.Annotation を使用して、クリーンな PDF Java ファイルの作成方法と Java で PDF に注釈を付ける方法を、完全なコード例とトラブルシューティングのヒントとともに学びましょう。
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'クリーンなPDFをJavaで作成 - GroupDocsで下線アノテーション'
type: docs
url: /ja/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Clean PDF Java を作成する: GroupDocs で下線アノテーション

## Introduction

Java アプリケーションでのドキュメント管理やコラボレーションに苦労していますか？ あなたは一人ではありません。多くの開発者が、さまざまなファイル形式で確実に動作する堅牢なドキュメントアノテーション機能の実装に課題を抱えています。

このガイドでは **clean PDF Java** ファイルを作成し、GroupDocs.Annotation を使用して **annotate PDF in Java** する方法を学びます。チュートリアルの最後までに、コメント付きの下線アノテーションの追加方法、既存のアノテーションの削除方法、そしてこれらの機能をプロジェクトにシームレスに統合する方法が正確に分かります。

**このガイドで習得できること:**
- Java プロジェクトに GroupDocs.Annotation を正しく設定する方法  
- カスタムコメントとスタイリングを持つ下線アノテーションの追加  
- すべてのアノテーションを削除してクリーンなドキュメントバージョンを作成する方法  
- 開発者が直面しやすい一般的な問題のトラブルシューティング  
- 本番環境向けのパフォーマンス最適化  

ドキュメントレビューシステム、教育プラットフォーム、共同編集ツールのいずれを構築していても、実践的で検証済みのコード例がこのチュートリアルで網羅されています。

## クイック アンサー
- **下線注釈を追加するにはどうすればよいですか？** `UnderlineAnnotation` と `annotator.add()` を使用してドキュメントを保存します。
- **クリーンな PDF Java ファイルを作成するにはどうすればよいですか？** 注釈付きファイルを読み込み、`SaveOptions` で `AnnotationType.NONE` を設定して、新しいコピーを保存します。
- **必要なライブラリは何ですか？** GroupDocs.Annotationv25.2 以降とその Maven リポジトリ。
- **本番環境ではライセンスが必要ですか？** はい。透かしを回避するには、有効な GroupDocs ライセンスを適用してください。
- **複数のドキュメントを効率的に処理できますか？** 各 `Annotator` を try‑with‑resources ブロックでラップし、各ファイルの処理後に破棄します。

## クリーンな PDF Java ファイルを作成する方法
クリーンな PDF Java ファイルを作成するということは、元のコンテンツを保持しながら、**注釈なし** のドキュメントのバージョンを生成することを意味します。これは、最終的な配布、アーカイブ、またはレビューサイクル後に「クリーン」なコピーを共有する必要がある場合に便利です。

GroupDocs.Annotation を使えば、注釈付きファイルを読み込み、`SaveOptions` ですべての注釈タイプを除外するように設定し、結果を保存するだけで簡単に実行できます。手順については、後述の **注釈の削除** セクションで説明します。

## GroupDocs を使用して Java で PDF に注釈を付ける方法
GroupDocs.Annotation は、**Java で PDF に注釈を付ける** ための豊富な API を提供します。ハイライト、スタンプ、下線など、幅広い注釈タイプをサポートしています。このチュートリアルでは、テキストを強調表示しながらスレッド形式のコメントを可能にするためによく使用される下線注釈に焦点を当てます。

## 前提条件と環境設定

### 開始前に必要なもの

**開発環境要件:**
- Java Development Kit (JDK)8 以上 (JDK11 以上を推奨)
- 依存関係管理用の Maven3.6 以上または Gradle6.0 以上
- Java 拡張機能を備えた IntelliJ IDEA、Eclipse、VSCode などの IDE
- 2GB 以上の RAM (ドキュメント処理はメモリを大量に消費する場合があります)

**必要な知識:**
オブジェクトの初期化、メソッド呼び出し、Maven の依存関係といった Java の基本概念を理解している必要があります。サードパーティ製ライブラリの使用経験があれば、導入がスムーズに進みます。

**ドキュメントのテスト:**
サンプル PDF をいくつか用意しておいてください。テキストベースの PDF が最適です。スキャンした画像の場合は、注釈を付ける前に OCR が必要になる場合があります。

### Maven の設定: GroupDocs をプロジェクトに組み込む

Maven プロジェクトを適切に設定する方法は次のとおりです (多くの開発者が初めて試す際に、この設定につまずきます)。

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

**重要:** バージョン25.2は、この記事の執筆時点での最新の安定版リリースです。バグ修正やパフォーマンス向上を含む新しいバージョンについては、GroupDocsリポジトリを定期的にご確認ください。

### ライセンス設定（必ずお読みください）

**開発/テスト環境向け:**
GroupDocsウェブサイトから無料トライアル版をダウンロードしてください。トライアル版にはすべての機能が含まれていますが、処理済みのドキュメントには透かしが追加されます。

**本番環境向け:**
ライセンスを購入し、アプリケーションの起動時に適用してください。有効なライセンスがない場合、本番環境ビルドは制限されます。

## 実装ガイド: 下線注釈の追加

### 注釈ワークフローの理解

コードの説明に入る前に、**JavaでPDFに注釈を付ける**際に実行される4つのステップのワークフローを確認しましょう。

1. **ドキュメントの読み込み** – `Annotator`がファイルをメモリに読み込みます。
2. **注釈の作成** – 位置、スタイル、コメントなどのプロパティを定義します。
3. **注釈アプリケーション** – ライブラリが注釈をPDFの構造に挿入します。
4. **ドキュメントの保存** – 変更されたファイルを永続化し、オプションで元のファイルも保存します。

このプロセスは非破壊的です。上書きしない限り、ソースファイルはそのまま残ります。

### ステップ1: アノテーターを初期化し、ドキュメントを読み込む

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**プロのヒント:** 開発中は「ファイルが見つかりません」エラーを回避するため、絶対パスを使用してください。本番環境では、クラスパスまたはクラウドストレージバケットからリソースを読み込むことを検討してください。

### ステップ2: コメントと返信の作成（共同作業）

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**実用例:** レビュアーはスレッド形式の返信を追加することで特定の条項について議論することができ、会話を正確な注釈に結び付けることができます。

### ステップ3: 注釈の座標の定義（正しい位置の取得）

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**座標系:**
- ポイント1と2は下線の上端を定義します。
- ポイント3と4は下端を定義します。
- Y軸の差（730対650）は太さを制御します。

### ステップ4：下線注釈の作成と設定

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**色と不透明度に関するヒント:**
- `FontColor` は ARGB を使用します。`65535` (0x00FFFF) は明るい黄色になります。
- 赤の場合は `16711680` (0xFF0000)、青の場合は `255` (0x0000FF) を使用します。
- 不透明度を 0.5 から 0.8 にすると、テキストが見えにくくなることなく読みやすくなります。

### ステップ 5: 注釈付きドキュメントを保存する

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**メモリ管理:** `dispose()` 呼び出しはネイティブリソースを解放し、メモリリークを防ぎます。これは、多数のファイルを一括処理する際に非常に重要です。

## 注釈の削除: クリーンなドキュメントバージョンの作成

最終承認済みの契約書を配布する場合など、注釈のない PDF バージョンが必要になることがあります。GroupDocs を使えば、簡単に作成できます。

### 注釈削除オプションについて

以下の操作が可能です。
- すべての注釈を削除（最も一般的）
- 特定の種類の注釈を削除（例：ハイライトのみ）
- 著者またはページ別に注釈を削除

### 注釈削除の手順

**ステップ1: 以前に注釈を付けたドキュメントを読み込む**

```java
Annotator annotator = new Annotator(outputPath);
```

**ステップ2: クリーンな出力のための保存オプションを設定する**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**ステップ3: クリーンなバージョンを保存する**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

これにより、注釈オブジェクトを含まない、最終配布に最適な**クリーンなPDF Java**ファイルが生成されます。

## よくある問題と解決策

### 問題1: 「ドキュメントが見つかりません」エラー

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### 問題2: 注釈が間違った場所に表示される

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### 問題3: 大きなドキュメントでのメモリ問題

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### 問題4: 本番環境でのライセンス問題

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

## 本番環境アプリケーションのパフォーマンスに関するベストプラクティス

### メモリ管理戦略

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### スレッド処理に関する考慮事項

GroupDocs.Annotation はデフォルトでは**スレッドセーフではありません**。アプリケーションがドキュメントを並行処理する場合、以下の点に注意してください。

- `Annotator` インスタンスをスレッド間で**共有しないでください**。
- ファイルアクセスを**同期**するか、ロックメカニズムを使用してください。
- 高いスループットが必要な場合は、`Annotator` オブジェクトの**プール**を検討してください。

### キャッシュ戦略

- 頻繁に使用する注釈テンプレートをキャッシュします。
- 共通の座標セットには `Point` コレクションを再利用します。
- 同じベースドキュメントに繰り返し注釈を付ける場合は、**テンプレート PDF** をメモリ内に保持します。

## 実際のアプリケーションとユースケース

### ドキュメントレビューシステム

- **法務レビュー:** 契約条項に下線を引いて、リスクに関するコメントを追加します。
- **コンプライアンス監査:** 財務諸表の問題のあるセクションを強調表示します。
- **学術ピアレビュー:** 教授は説明が必要な箇所に下線を引いています。

### 教育プラットフォーム

- **学生用注釈ツール:** 学習者が電子書籍の重要な概念に下線を引けるようにしています。
- **教師からのフィードバック:** 提出された課題に直接インラインコメントを追加できます。

### 品質保証ワークフロー

- **技術文書レビュー:** エンジニアは更新が必要なセクションに下線を引いています。
- **標準操作手順:** 安全担当者は重要な手順を強調表示しています。

### コンテンツ管理システム

- **編集ワークフロー:** 編集者は事実確認が必要なテキストに下線を引いています。
- **バージョン管理:** ドキュメントのリビジョン間で注釈の履歴を追跡できます。

## プロフェッショナルな実装のための高度なヒント

### カスタム注釈スタイル

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### トラッキング用アノテーションメタデータ

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### ユーザー管理システムとの統合

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## 本番環境における問題のトラブルシューティング

### パフォーマンス監視

本番環境では、以下のメトリクスを確認してください。
- **ヒープ使用量** – `dispose()` が呼び出されていることを確認してください。
- **ドキュメントあたりの処理時間** – `annotator.save()` の前後のタイムスタンプを記録してください。
- **エラー率** – 例外をキャプチャして分類してください。

### 本番環境でよくある落とし穴

- **ファイルロック** – アノテーションを付ける前に、アップロードされたファイルが閉じられていることを確認してください。
- **同時編集** – 楽観的ロックまたはバージョンチェックを実装してください。
- **大きなファイル (50MB 以上)** – JVM タイムアウトを増やし、ストリーミング API の使用を検討してください。

### エラー処理のベストプラクティス

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## まとめ

これで、**クリーンな PDF Java** ファイルを作成し、GroupDocs.Annotation を使用して **Java で PDF に下線注釈を付ける** ために必要なものがすべて揃いました。以下の点にご注意ください。

- リソースは、try‑with‑resources または明示的な `dispose()` を使用して管理します。
- 下線の位置がずれないように、座標を早期に検証します。
- 運用環境の安定性を確保するために、堅牢なエラー処理を実装します。
- ワークフローに合わせて、ロールベースのスタイル設定とメタデータを活用します。

次のステップは？ ハイライト、スタンプ、テキスト置換など、他の注釈タイプを追加して、フル機能のドキュメントレビューソリューションを構築してみましょう。

## よくある質問

**Q: 1 回の操作で複数のテキスト領域に注釈を付けるにはどうすればよいですか？**
A: 異なる座標を持つ複数の `UnderlineAnnotation` オブジェクトを作成し、`annotator.add()` を使用して順番に追加します。

**Q: PDF ドキュメント内の画像に注釈を付けることはできますか？**
A: はい。同じ座標系を使用し、点が画像の境界内に収まるようにしてください。

**Q: GroupDocs.Annotation は PDF 以外にどのようなファイル形式をサポートしていますか？**
A: Word (DOC/DOCX)、Excel (XLS/XLSX)、PowerPoint (PPT/PPTX)、および JPEG、PNG、TIFF などの画像形式です。

**Q: メモリ不足に陥ることなく、非常に大きなドキュメントを処理するにはどうすればよいですか？**
A: ドキュメントを 1 つずつ処理し、JVM ヒープ (`-Xmx`) を増やし、`Annotator` インスタンスを常に速やかに破棄してください。

**Q: ドキュメントから既存の注釈を抽出することはできますか？**
A: はい。`annotator.get()` を使用してすべての注釈を取得し、必要に応じて種類、作成者、またはページでフィルタリングしてください。

---

**最終更新日:** 2025年12月21日
**テスト環境:** GroupDocs.Annotation25.2
**作成者:** GroupDocs