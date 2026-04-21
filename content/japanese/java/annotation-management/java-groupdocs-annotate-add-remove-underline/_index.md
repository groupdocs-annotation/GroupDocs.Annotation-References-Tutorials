---
categories:
- Java Development
date: '2026-03-24'
description: GroupDocs.Annotation を使用して、クリーンな PDF Java ファイルの作成方法、Java の PDF メモリ管理、PDF
  の注釈付けを学び、完全なコード例とトラブルシューティングのヒントを提供します。
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2026-03-24'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'JavaでクリーンなPDFを作成: GroupDocsで下線アノテーション'
type: docs
url: /ja/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# クリーンな PDF Java を作成: GroupDocs の下線アノテーション

もし **create clean PDF Java** ファイルを作成し、共同アノテーションを追加したいのであれば、ここが適切な場所です。Java アプリケーションでのドキュメント管理やコラボレーションに苦労していますか？あなたは一人ではありません。多くの開発者が、さまざまなファイル形式で信頼性の高いドキュメントアノテーション機能を実装する課題に直面しています。

このガイドでは、**create clean PDF Java** ファイルを作成し、GroupDocs.Annotation を使用して **annotate PDF in Java** の方法を学びます。チュートリアルの最後までに、コメント付きの下線アノテーションの追加方法、既存のアノテーションの削除方法、そしてこれらの機能をプロジェクトにシームレスに統合する方法が正確に分かります。

**このガイドで習得できること:**
- Java プロジェクトで GroupDocs.Annotation を正しく設定する  
- カスタムコメントとスタイリング付きの下線アノテーションを追加する  
- すべてのアノテーションを削除してクリーンなドキュメントバージョンを作成する  
- 開発者が直面する一般的な問題のトラブルシューティング  
- 本番アプリケーション向けのパフォーマンス最適化  

ドキュメントレビューシステム、教育プラットフォーム、または共同編集ツールを構築している場合でも、このチュートリアルは実用的でテスト済みのコード例で網羅しています。

## クイック回答
- **下線アノテーションはどう追加しますか？** `UnderlineAnnotation` と `annotator.add()` を使用し、ドキュメントを保存します。  
- **クリーンな PDF Java ファイルはどう作成しますか？** アノテーションが付いたファイルをロードし、`SaveOptions` で `AnnotationType.NONE` を設定して新しいコピーを保存します。  
- **必要なライブラリは何ですか？** GroupDocs.Annotation v25.2（またはそれ以降）とその Maven リポジトリ。  
- **本番環境でライセンスは必要ですか？** はい—有効な GroupDocs ライセンスを適用してウォーターマークを回避してください。  
- **複数のドキュメントを効率的に処理できますか？** 各 `Annotator` を try‑with‑resources ブロックでラップし、各ファイル処理後に破棄します。

## クリーンな PDF Java ファイルの作成方法
クリーンな PDF Java ファイルを作成するとは、元のコンテンツを保持しながら **アノテーションが全くない** バージョンのドキュメントを生成することです。最終配布、アーカイブ、またはレビューサイクル後に「クリーン」なコピーを共有する必要がある場合に便利です。

GroupDocs.Annotation を使用すれば簡単です。アノテーションが付いたファイルをロードし、`SaveOptions` で全てのアノテーションタイプを除外するよう設定し、結果を保存します。手順は後述の **Removing Annotations** セクションで示しています。

## なぜクリーンな PDF Java ファイルを作成するのか？
クリーンなバージョンはレビュアーのマーク、コメント、ハイライトを除去し、クライアントや規制当局、一般公開向けに仕上がった文書を提供します。また、ファイルサイズが削減され、内部メモの誤って公開されるリスクを防ぎます—法務やコンプライアンスのワークフローにとって重要です。

## GroupDocs を使用した Java での PDF アノテーション方法
GroupDocs.Annotation は **annotate PDF in Java** のための豊富な API を提供します。ハイライト、スタンプ、下線など、さまざまなアノテーションタイプをサポートしています。このチュートリアルでは、テキストを強調しつつスレッド化されたコメントを可能にする下線アノテーションに焦点を当てます。

## 前提条件と環境設定

### 開始前に必要なもの

**開発環境の要件:**
- Java Development Kit (JDK) 8 以上 (JDK 11+ 推奨)  
- 依存関係管理のための Maven 3.6+ または Gradle 6.0+  
- IntelliJ IDEA、Eclipse、または Java 拡張機能付き VS Code などの IDE  
- 少なくとも 2 GB の利用可能 RAM（ドキュメント処理はメモリ集中的になる可能性があります）

**知識の前提条件:** 基本的な Java の概念（オブジェクト初期化、メソッド呼び出し、Maven 依存関係）に慣れている必要があります。サードパーティライブラリの経験があると導入がスムーズです。

**テスト用ドキュメント:** サンプル PDF を数件用意してください。テキストベースの PDF が最適です。スキャン画像はアノテーション前に OCR が必要になる場合があります。

### Maven 設定: プロジェクトに GroupDocs を導入する

Maven プロジェクトを正しく設定する方法は以下の通りです（初めての方はよく躓きます）。

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

**重要:** 執筆時点での最新安定版はバージョン 25.2 です。バグ修正やパフォーマンス向上を含む新しいバージョンがあるか、定期的に GroupDocs リポジトリを確認してください。

### ライセンス設定（省略しないでください）

**開発/テスト用:** GroupDocs のウェブサイトから無料トライアルをダウンロードしてください。トライアルはすべての機能を含みますが、処理されたドキュメントにウォーターマークが追加されます。

**本番用:** ライセンスを購入し、アプリケーション起動時に適用してください。有効なライセンスがない場合、本番ビルドは機能が制限されます。

## 実装ガイド: 下線アノテーションの追加

### アノテーションワークフローの理解

コードに入る前に、**annotate PDF in Java** 時に発生する 4 ステップのワークフローを見てみましょう。

1. **ドキュメントのロード** – `Annotator` がファイルをメモリに読み込みます。  
2. **アノテーションの作成** – 位置、スタイル、コメントなどのプロパティを定義します。  
3. **アノテーションの適用** – ライブラリが PDF の構造にアノテーションを挿入します。  
4. **ドキュメントの保存** – 変更されたファイルを永続化し、必要に応じて元のファイルを保持します。

このプロセスは破壊的ではなく、上書きしない限り元のファイルは変更されません。

### 手順 1: Annotator を初期化し、ドキュメントをロードする

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**プロのコツ:** 開発時は絶対パスを使用して “file not found” エラーを回避してください。本番環境では、クラスパスやクラウドストレージバケットからリソースをロードすることを検討してください。

### 手順 2: コメントと返信の作成（コラボレーション部分）

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

**実務での使用例:** レビュアーはスレッド化された返信を追加して特定の条項について議論でき、会話が正確にそのアノテーションに紐付けられます。

### 手順 3: アノテーション座標の定義（位置合わせ）

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
- ポイント 1 と 2 が下線の上端を定義します。  
- ポイント 3 と 4 が下端を定義します。  
- Y の差 (730 対 650) が太さを制御します。

### 手順 4: 下線アノテーションの作成と設定

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

**色と不透明度のヒント:**  
- `FontColor` は ARGB を使用します。`65535` (0x00FFFF) は明るい黄色になります。  
- 赤は `16711680` (0xFF0000)、青は `255` (0x0000FF) を使用します。  
- 不透明度を 0.5〜0.8 の範囲に設定すると、テキストを隠さずに読みやすさが確保できます。

### 手順 5: アノテーション済みドキュメントの保存

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**メモリ管理:** `dispose()` 呼び出しはネイティブリソースを解放し、メモリリークを防止します—バッチで多数のファイルを処理する際に重要です。

## アノテーションの削除: クリーンなドキュメントバージョンの作成

場合によっては、PDF の **アノテーションが全くない** バージョンが必要になることがあります—例えば、最終承認済みの契約書を提供する際などです。GroupDocs なら簡単に実現できます。

### アノテーション削除オプションの理解

- **すべて** のアノテーションを削除（最も一般的）  
- 特定のタイプだけを削除（例: ハイライトのみ）  
- 作者またはページ単位でアノテーションを削除  

### 手順別 アノテーション削除

**Step 1: Load the Previously Annotated Document**

```java
Annotator annotator = new Annotator(outputPath);
```

**Step 2: Configure Save Options for a Clean Output**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Step 3: Save the Clean Version**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

これにより、アノテーションオブジェクトが一切含まれない **clean PDF Java** ファイルが生成され、最終配布に最適です。

## よくある問題と解決策

### 問題 1: “Document not found” エラー

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

### 問題 2: アノテーションが誤った位置に表示される

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### 問題 3: 大容量ドキュメントでのメモリ問題

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### 問題 4: 本番環境でのライセンス問題

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

## 本番アプリケーション向けパフォーマンスベストプラクティス

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

### スレッドに関する考慮点

GroupDocs.Annotation は **not thread‑safe** です。アプリケーションが同時にドキュメントを処理する場合:

- **決して** `Annotator` インスタンスをスレッド間で共有しない。  
- ファイルアクセスを **同期** させるか、ロック機構を使用する。  
- 高スループットが必要な場合は `Annotator` オブジェクトの **プール** を検討する。

### キャッシュ戦略

- 頻繁に使用するアノテーションテンプレートをキャッシュする。  
- 共通の座標セットには `Point` コレクションを再利用する。  
- 同じベースドキュメントに繰り返しアノテーションする場合は、**テンプレート PDF** をメモリに保持する。

## Java PDF メモリ管理のヒント

大容量 PDF を扱ったり、バッチで多数のファイルを処理する際には、効率的なメモリ使用が不可欠です。以下に実用的な推奨事項を示します。

- **try‑with‑resources** をすべての `Annotator` に使用して、確実に破棄する。  
- 必要に応じて **JVM ヒープ** (`-Xmx`) を増やし、プロファイリングツールで使用状況を監視する。  
- 可能な限り **ドキュメントを順次処理** し、各ファイル処理後にメモリを解放する。  
- **同じ PDF を複数回ロードしない**；繰り返し読む必要がある場合は同じストリームを再利用する。

これらの実践により、アプリケーションの応答性が保たれ、重いアノテーション作業中のメモリ不足クラッシュを防止できます。

## 実務での活用例とユースケース

### ドキュメントレビューシステム

- **法務レビュー:** 契約条項に下線を引き、リスクに関するコメントを追加。  
- **コンプライアンス監査:** 財務諸表の問題箇所をハイライト。  
- **学術ピアレビュー:** 教授が明確化が必要な箇所に下線を引く。

### 教育プラットフォーム

- **学生用アノテーションツール:** 学習者が電子書籍の重要概念に下線を引けるようにする。  
- **教師のフィードバック:** 提出された課題に直接インラインコメントを提供。

### 品質保証ワークフロー

- **技術文書レビュー:** エンジニアが更新が必要なセクションに下線を引く。  
- **標準作業手順:** 安全担当者が重要な手順をハイライト。

### コンテンツ管理システム

- **編集ワークフロー:** 編集者が事実確認が必要なテキストに下線を引く。  
- **バージョン管理:** ドキュメント改訂ごとのアノテーション履歴を追跡。

## プロフェッショナル実装のための高度なヒント

### Custom Annotation Styles

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Annotation Metadata for Tracking

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integration with User Management Systems

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

## 本番環境のトラブルシューティング

### パフォーマンス監視

本番で以下の指標を監視してください:
- **ヒープ使用量** – `dispose()` が呼び出されていることを確認。  
- **ドキュメントごとの処理時間** – `annotator.save()` 前後のタイムスタンプを記録。  
- **エラー率** – 例外を捕捉し、カテゴリ分けする。

### 本番での一般的な落とし穴

- **ファイルロック** – アノテーション前にアップロードされたファイルが閉じられていることを確認。  
- **同時編集** – 楽観的ロックまたはバージョンチェックを実装。  
- **大容量ファイル (> 50 MB)** – JVM のタイムアウトを延長し、ストリーミング API の使用を検討。

### Error Handling Best Practices

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

## 結論

これで、GroupDocs.Annotation を使用して **create clean PDF Java** ファイルを作成し、**annotate PDF in Java** で下線アノテーションを追加するために必要なすべてが揃いました。以下を忘れずに実施してください：

- try‑with‑resources または明示的な `dispose()` でリソースを管理する。  
- 下線の位置ずれを防ぐために座標を早期に検証する。  
- 本番環境の安定性のために堅牢なエラーハンドリングを実装する。  
- ワークフローに合わせてロールベースのスタイリングとメタデータを活用する。

次のステップは？ハイライト、スタンプ、テキスト置換など、他のアノテーションタイプを追加して、フル機能のドキュメントレビューソリューションを構築してみてください。

## よくある質問

**Q: 単一操作で複数のテキスト領域にアノテーションするには？**  
A: 異なる座標を持つ複数の `UnderlineAnnotation` オブジェクトを作成し、`annotator.add()` で順次追加します。

**Q: PDF 文書内の画像にアノテーションできますか？**  
A: はい。同じ座標系を使用し、ポイントが画像の境界内に収まっていることを確認してください。

**Q: PDF 以外に GroupDocs.Annotation がサポートするファイル形式は？**  
A: Word (DOC/DOCX)、Excel (XLS/XLSX)、PowerPoint (PPT/PPTX)、および JPEG、PNG、TIFF などの画像形式です。

**Q: メモリ不足にならずに非常に大きなドキュメントを処理するには？**  
A: ドキュメントを1つずつ処理し、JVM ヒープ (`-Xmx`) を増やし、`Annotator` インスタンスは常に速やかに破棄してください。

**Q: 既存のアノテーションをドキュメントから抽出できますか？**  
A: はい。`annotator.get()` を使用してすべてのアノテーションを取得し、必要に応じてタイプ、作者、ページでフィルタリングします。

---

**最終更新日:** 2026-03-24  
**テスト環境:** GroupDocs.Annotation 25.2  
**作者:** GroupDocs