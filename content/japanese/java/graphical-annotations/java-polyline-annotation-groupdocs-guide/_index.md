---
categories:
- Java Development
date: '2026-09-10'
description: pdf annotation library java を使用してインタラクティブなポリライン注釈を追加し、spring boot pdf
  annotation services と統合し、Java で SVG パスを生成する方法を学びます。
keywords:
- pdf annotation library java
- spring boot pdf annotation
- generate svg path java
- polyline annotation java
- groupdocs annotation java
lastmod: '2026-09-10'
linktitle: Java ポリライン注釈ガイド
og_description: pdf annotation library java を使用してインタラクティブなポリライン注釈を追加し、spring boot
  pdf annotation services と統合し、Java で SVG パスを生成する方法を学びます。
og_image_alt: Guide to adding interactive polyline annotations using a pdf annotation
  library java
og_title: pdf annotation library java を使用してポリライン PDF を扱う方法
schemas:
- author: GroupDocs
  dateModified: '2026-09-10'
  description: Learn how to use a pdf annotation library java to add interactive polyline
    annotations, integrate with spring boot pdf annotation services, and generate
    SVG paths in Java.
  headline: How to use a pdf annotation library java for polyline PDFs
  type: TechArticle
- description: Learn how to use a pdf annotation library java to add interactive polyline
    annotations, integrate with spring boot pdf annotation services, and generate
    SVG paths in Java.
  name: How to use a pdf annotation library java for polyline PDFs
  steps:
  - name: '**Create the annotation replies collection** – this gives reviewers a place
      to add comments.'
    text: '**Create the annotation replies collection** – this gives reviewers a place
      to add comments.'
  - name: '**Organize the replies** into a list that the annotation will reference.'
    text: '**Organize the replies** into a list that the annotation will reference.'
  - name: '**Configure the polyline** – set the bounding box, pen color, opacity,
      and most importantly the `SVGPath` that draws the line.'
    text: '**Configure the polyline** – set the bounding box, pen color, opacity,
      and most importantly the `SVGPath` that draws the line.'
  - name: '**Add the annotation to the document** via `annotator.addAnnotation(polyline)`.'
    text: '**Add the annotation to the document** via `annotator.addAnnotation(polyline)`.'
  - name: '**Save and clean up** – persist the PDF and dispose of the `Annotator`
      instance.'
    text: '**Save and clean up** – persist the PDF and dispose of the `Annotator`
      instance.'
  - name: '**Trim coordinate precision** – round to two decimal places.'
    text: '**Trim coordinate precision** – round to two decimal places.'
  - name: '**Prefer relative commands (`l`)** – they reduce string length by up to
      30 %.'
    text: '**Prefer relative commands (`l`)** – they reduce string length by up to
      30 %.'
  - name: '**Group similar annotations** – apply the same style to multiple polylines
      to reuse resources.'
    text: '**Group similar annotations** – apply the same style to multiple polylines
      to reuse resources.'
  type: HowTo
- questions:
  - answer: It connects multiple points to form complex, interactive paths in a PDF.
    question: What is the primary purpose of a polyline annotation?
  - answer: GroupDocs.Annotation for Java, a leading pdf annotation library java.
    question: Which library makes this easiest in Java?
  - answer: Yes – see the Spring Boot integration section.
    question: Can I use it with Spring Boot?
  - answer: By providing an SVG path string (e.g., using `generate svg path java`).
    question: How do I define the line shape?
  - answer: A trial license works for development; a production license is required
      for deployment.
    question: Do I need a license?
  type: FAQPage
tags:
- pdf annotation
- java
- groupdocs
- spring boot
title: pdf annotation library java を使用してポリライン PDF を扱う方法
type: docs
---

# pdf annotation library java を使用してポリライン PDF を扱う方法

この包括的なチュートリアルでは、**use a pdf annotation library java** を使用してインタラクティブなポリラインアノテーションを作成し、Spring Boot サービスに組み込み、SVG パス文字列をプログラムで生成する方法を学びます。ドキュメントレビュー プラットフォーム、eラーニングツール、または技術図表ジェネレータを構築する場合でも、以下の手順はスケーラブルな本番環境向けソリューションを提供します。

## クイック回答
- **ポリラインアノテーションの主な目的は何ですか？** PDF 内で複数の点を結び、複雑でインタラクティブなパスを形成します。  
- **Java でこれを最も簡単に実現できるライブラリはどれですか？** GroupDocs.Annotation for Java、主要な pdf annotation library java です。  
- **Spring Boot で使用できますか？** はい – Spring Boot 統合セクションをご覧ください。  
- **ライン形状はどのように定義しますか？** SVG パス文字列を提供します（例: `generate svg path java` を使用）。  
- **ライセンスは必要ですか？** 開発にはトライアルライセンスで動作しますが、デプロイには本番ライセンスが必要です。

## なぜ GroupDocs.Annotation for Java を選ぶのか？
GroupDocs.Annotation は、PDF アノテーション開発を簡素化する包括的な機能セットを提供します。高性能処理、広範なフォーマットサポート、組み込みのインタラクティブアノテーションタイプを備え、コードの複雑さとメモリ使用量を最小限に抑えます。これにより、多様な環境で信頼性とスケーラビリティの高い文書処理が求められるエンタープライズアプリケーションに最適です。

GroupDocs.Annotation は、汎用 PDF ツールキットを上回る **pdf annotation library java** です。以下を提供します：

- **50 以上の入力および出力フォーマット** – DOCX、XLSX、PPTX、HTML、一般的な画像形式を含み、ファイル全体をメモリにロードせずに数百ページの PDF を処理します。  
- **組み込みのアノテーションタイプ**（ポリライン、ハイライト、コメントなど）で、主要な PDF ビューアすべてで一貫した表示が可能です。  
- **サーバーサイド処理**により、クライアント側のセキュリティ問題を排除し、すべてのプラットフォームで同一のレンダリングを保証します。  
- **エンタープライズレベルのパフォーマンス** – 標準的なクラウド VM で 300 ページの PDF に対して 2 秒未満でアノテーションを付与できます。

iText や PDFBox と比較すると、ボイラープレートコードが大幅に減ります。クライアント側の JavaScript ソリューションと比較しても、ライセンスとリソース使用を完全に管理できるサーバー側で重い処理を行うため、柔軟性が向上します。

## 本ガイドで学べること
このガイドを終える頃には、以下ができるようになります：

- Maven または Gradle プロジェクトで pdf annotation library java をインストールおよび設定する。  
- カスタムカラー、透明度、SVG で定義されたジオメトリを使用したインタラクティブなポリライン PDF アノテーションを作成する。  
- コラボレーティブなレビュー ワークフローのために、アノテーションにコメント返信を添付する。  
- メモリ使用量を最適化し、大規模な文書コレクションをバッチ処理する。  
- Spring Boot REST API を通じてアノテーション作成を公開する。

## 前提条件と環境設定
**必須要件**
- JDK 8 以上（JDK 11+ 推奨）  
- Maven 3.6+ または Gradle 6+  
- IntelliJ IDEA や Eclipse などの IDE  
- Java と Maven の依存関係管理に関する基本的な知識  

**あると望ましい**
- PDF ページ座標系の理解  
- SVG パス構文の経験（`generate svg path java` に有用）

### Maven 設定
pom.xml に GroupDocs.Annotation の依存関係を追加します:

```xml
<!-- placeholder for Maven dependency -->
```

**Pro tip**: 常に GroupDocs のウェブサイトで最新の安定版を使用していることを確認してください。バージョン 25.2 ではポリライン描画が 30% 高速化されました。

### ライセンス設定
GroupDocs.Annotation は本番利用にライセンスが必要です。

- **開発/テスト** – 30 日間フル機能を提供する [free trial license](https://releases.groupdocs.com/annotation/java/) で開始します。  
- **拡張評価** – さらに時間が必要な場合は [temporary license](https://purchase.groupdocs.com/temporary-license/) をリクエストしてください。  
- **本番** – [GroupDocs purchase page](https://purchase.groupdocs.com/buy) からサブスクリプションを購入します。ライセンスは導入規模（シングルアプリ vs. サイト全体）に応じて階層化されています。

### 基本的な環境初期化
`Annotator` クラスはすべてのアノテーション操作のエントリーポイントです:

```java
// placeholder for Annotator initialization
```

**Important**: 長時間稼働するサービスでは、メモリリークを防ぐために try‑with‑resources を使用するか、`Annotator` の `close()` を明示的に呼び出してください。

## pdf annotation library java を使用してポリラインアノテーションを作成する方法
`PolylineAnnotation` は、ジオメトリが SVG パス文字列で定義されたマルチセグメントのライン形状を表します。

対象の PDF をロードし、`PolylineAnnotation` をインスタンス化し、視覚プロパティを設定し、コメント返信を添付してからドキュメントを保存します。このエンドツーエンドのフローは API 呼び出しが 3 回だけで、典型的な 10 ページのファイルでは 1 秒未満で実行され、効率的に処理されます。

### 定義アンカー
`PolylineAnnotation` は、ジオメトリが SVG パス文字列で定義されたマルチセグメントライン形状を表す GroupDocs.Annotation クラスです。色、透明度、ページ位置などの共通アノテーションプロパティを継承します。

### 手順ごとのウォークスルー
1. **アノテーション返信コレクションを作成** – これによりレビュアーはコメントを追加できる場所が提供されます。  
2. **返信を整理**し、アノテーションが参照するリストにします。  
3. **ポリラインを設定** – バウンディングボックス、ペンカラー、透明度、そして最も重要な `SVGPath`（ラインを描画する）を設定します。  
4. `annotator.addAnnotation(polyline)` を使用してアノテーションをドキュメントに追加します。  
5. **保存とクリーンアップ** – PDF を永続化し、`Annotator` インスタンスを破棄します。

以下のプレースホルダーは、実際の Java スニペットを貼り付ける場所を示しています:

```text
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
```

```text
```java
import com.groupdocs.annotation.Annotator;

// Initialize Annotator with your document
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```
```

```text
```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;

// Create reply instances with comments
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());
```
```

```text
```java
import java.util.ArrayList;
import java.util.List;

// Add replies to a list
List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```
```

```text
```java
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.PolylineAnnotation;

// Initialize polyline annotation
PolylineAnnotation polyline = new PolylineAnnotation();
polyline.setBox(new Rectangle(250, 35, 102, 12)); // Position and size
polyline.setMessage("This is a polyline annotation"); // Annotation message
polyline.setOpacity(0.7); // Opacity (0-1)
polyline.setPageNumber(0); // Page index (0-based)
polyline.setPenColor(65535); // Color in ARGB format
polyline.setPenStyle(PenStyle.DOT); // Pen style options
polyline.setPenWidth((byte) 3); // Pen width in pixels

// Associate replies and define the path
polyline.setReplies(replies);
polyline.setSvgPath("M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793...");
```
```

```text
```java
// Add the annotation using Annotator
annotator.add(polyline);
```
```

```text
```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/Annotated.pdf";
annotator.save(outputPath); // Save annotated document

// Dispose of annotator resources
annotator.dispose();
```
```

## SVG パスの扱い方
SVG パス文字列はポリラインの正確な形状を定義します。pdf annotation library java が解釈してラインを描画する、コンパクトなコマンド言語を使用します。

### 基本的なパスコマンド
- **M** – 移動（開始点）  
- **L** – 線を引く（絶対座標）  
- **l** – 線を引く（相対座標）  

シンプルな L 字形のパスは次のようになります:

```text
```
M10,10 L50,10 L50,50
```
```

### プログラムでパスを生成する
ユーザー提供のポイントからパスを構築する必要がある場合、Java で SVG 文字列を生成します:

```text
```java
public String generatePolylinePath(Point[] points) {
    if (points.length == 0) return "";
    
    StringBuilder path = new StringBuilder();
    path.append("M").append(points[0].x).append(",").append(points[0].y);
    
    for (int i = 1; i < points.length; i++) {
        path.append("L").append(points[i].x).append(",").append(points[i].y);
    }
    
    return path.toString();
}
```
```

この手法は `generate svg path java` シナリオ（動的図表エディタなど）に最適です。

## 実務でのユースケースとアプリケーション

### 技術文書
```text
```java
// Create annotation for data flow path
PolylineAnnotation dataFlow = new PolylineAnnotation();
dataFlow.setMessage("Data flow from API to Database");
dataFlow.setPenColor(0xFF0000FF); // Blue for data flow
dataFlow.setPenStyle(PenStyle.SOLID);
dataFlow.setPenWidth((byte) 2);
// SVG path would show the actual route through your architecture
```
```

### 教育資料
```text
```java
// Highlight geometric proof steps
PolylineAnnotation proofStep = new PolylineAnnotation();
proofStep.setMessage("Proof step 3: Angle bisector construction");
proofStep.setPenColor(0xFF00FF00); // Green for completed steps
proofStep.setOpacity(0.8); // Slightly transparent to not obscure text
```
```

### 法務文書レビュー
```text
```java
// Connect related contract sections
PolylineAnnotation clauseConnection = new PolylineAnnotation();
clauseConnection.setMessage("This clause relates to section 4.2");
clauseConnection.setPenStyle(PenStyle.DASH); // Dashed for suggestions
clauseConnection.setPenColor(0xFFFF9900); // Orange for attention
```
```

## 人気のある Java フレームワークとの統合

### Spring Boot PDF アノテーション統合
Spring サービスを通じてアノテーション作成を公開します:

```text
```java
@Service
public class DocumentAnnotationService {
    
    public String addPolylineAnnotation(String documentPath, 
                                       PolylineConfig config) {
        try (Annotator annotator = new Annotator(documentPath)) {
            PolylineAnnotation polyline = createPolylineFromConfig(config);
            annotator.add(polyline);
            
            String outputPath = generateOutputPath(documentPath);
            annotator.save(outputPath);
            return outputPath;
        }
    }
    
    private PolylineAnnotation createPolylineFromConfig(PolylineConfig config) {
        // Implementation details based on your config structure
        // This pattern keeps your annotation logic organized and testable
    }
}
```
```

### REST API 統合
ポリライン座標を記述した JSON ペイロードを受け取るエンドポイントを定義します:

```text
```java
@RestController
@RequestMapping("/api/annotations")
public class AnnotationController {
    
    @Autowired
    private DocumentAnnotationService annotationService;
    
    @PostMapping("/polyline")
    public ResponseEntity<String> addPolylineAnnotation(
            @RequestBody PolylineRequest request) {
        
        try {
            String result = annotationService.addPolylineAnnotation(
                request.getDocumentPath(), 
                request.getConfig()
            );
            return ResponseEntity.ok(result);
        } catch (Exception e) {
            return ResponseEntity.badRequest()
                .body("Error adding annotation: " + e.getMessage());
        }
    }
}
```
```

## パフォーマンス最適化とベストプラクティス

### メモリ管理
高スループットシナリオでは、スレッドごとに単一の `Annotator` インスタンスを再利用し、速やかに閉じます:

```text
```java
// Use try-with-resources for automatic cleanup
public void processMultipleDocuments(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process document
            addPolylineAnnotations(annotator);
            annotator.save(generateOutputPath(path));
        } // Automatic disposal happens here
    }
}
```
```

### バッチ処理
数千の PDF を扱う場合、ヒープ使用量を抑えるためにバッチで処理します:

```text
```java
public void batchAddPolylines(String documentPath, 
                             List<PolylineConfig> configs) {
    try (Annotator annotator = new Annotator(documentPath)) {
        // Add all annotations before saving
        for (PolylineConfig config : configs) {
            PolylineAnnotation polyline = createFromConfig(config);
            annotator.add(polyline);
        }
        // Single save operation is more efficient
        annotator.save(generateOutputPath(documentPath));
    }
}
```
```

### SVG パスの最適化
複雑なパスは描画速度を低下させる可能性があります。以下のガイドラインに従ってください:

1. **座標精度を削減** – 小数点以下2桁に丸めます。  
2. **相対コマンド (`l`) を優先** – 文字列長を最大30%削減できます。  
3. **類似アノテーションをグループ化** – 複数のポリラインに同じスタイルを適用してリソースを再利用します。

```text
```java
// Optimize coordinate precision
public String optimizePath(String svgPath) {
    return svgPath.replaceAll("(\\d+\\.\\d{3})\\d+", "$1");
}
```
```

## よくある問題と解決策

### 問題 1: アノテーションが表示されない
典型的な原因は、ページインデックスが正しくない（ページはゼロベース）、SVG 座標がページ境界外、または透明度が低すぎることです。ページ番号を調整し、SVG パスがページ矩形内に収まっていることを確認してください。

```text
```java
// Debug your annotation placement
PolylineAnnotation polyline = new PolylineAnnotation();
polyline.setPageNumber(0); // Ensure correct page
polyline.setOpacity(1.0); // Full opacity for testing
polyline.setPenWidth((byte) 5); // Thicker line for visibility

// Log the bounding box to verify coordinates
Rectangle box = polyline.getBox();
System.out.println("Annotation bounds: " + box.getX() + "," + box.getY());
```
```

### 問題 2: 大規模文書での OutOfMemoryError
大規模な PDF はストリーミングモードで処理し、ドキュメント全体をメモリにロードしないようにします:

```text
```java
// Implement proper memory management
public void processLargeDocument(String documentPath) {
    // Process in smaller batches
    int maxAnnotationsPerBatch = 50;
    List<PolylineConfig> allConfigs = getAnnotationConfigs();
    
    for (int i = 0; i < allConfigs.size(); i += maxAnnotationsPerBatch) {
        try (Annotator annotator = new Annotator(documentPath)) {
            int end = Math.min(i + maxAnnotationsPerBatch, allConfigs.size());
            List<PolylineConfig> batch = allConfigs.subList(i, end);
            
            processBatch(annotator, batch);
            annotator.save(generateBatchOutputPath(documentPath, i));
        }
        // Force garbage collection between batches if needed
        System.gc();
    }
}
```
```

### 問題 3: 無効な SVG パス形式
パスが移動コマンド (`M`) で始まり、すべての数値が有効な double であることを確認してください。

```text
```java
// Validate SVG path before using
public boolean isValidSVGPath(String path) {
    // Basic validation - should start with M or m
    if (!path.matches("^[Mm]\\d+.*")) {
        return false;
    }
    
    // Additional validation logic here
    return true;
}

// Use validated paths only
if (isValidSVGPath(pathString)) {
    polyline.setSvgPath(pathString);
} else {
    throw new IllegalArgumentException("Invalid SVG path: " + pathString);
}
```
```

### 問題 4: ライセンス検証に失敗した
`GroupDocs.Annotation.lic` ファイルをクラスパスに配置するか、アプリケーション起動時にプログラムでライセンスを設定してください。

```text
```java
// Proper license initialization
public class AnnotationConfig {
    
    @PostConstruct
    public void initializeLicense() {
        try {
            // Load license from classpath or file system
            String licensePath = getClass().getClassLoader()
                .getResource("GroupDocs.Annotation.lic").getPath();
            
            License license = new License();
            license.setLicense(licensePath);
            
            System.out.println("GroupDocs.Annotation license loaded successfully");
        } catch (Exception e) {
            System.err.println("Failed to load license: " + e.getMessage());
            // Handle license failure appropriately
        }
    }
}
```
```

## 高度なカスタマイズ手法

### 動的カラー割り当て
`ColorHelper` は、アノテーションカテゴリを ARGB カラー値にマッピングするユーティリティメソッドを提供します。

```text
```java
public class ColorHelper {
    private static final Map<String, Integer> CATEGORY_COLORS = Map.of(
        "error", 0xFFFF0000,      // Red
        "warning", 0xFFFF9900,    // Orange  
        "info", 0xFF0099FF,       // Blue
        "success", 0xFF00FF00     // Green
    );
    
    public static int getColorForCategory(String category) {
        return CATEGORY_COLORS.getOrDefault(category, 0xFF000000); // Default black
    }
}
```
```

### カスタムプロパティを持つインタラクティブアノテーション
`authorId` や `timestamp` などのメタデータを追加して、アノテーションペイロードを充実させます:

```text
```java
// Create custom annotation with metadata
PolylineAnnotation polyline = new PolylineAnnotation();
polyline.setMessage("Process Flow: " + processName);

// Add custom properties (stored in message or replies)
Reply metadataReply = new Reply();
metadataReply.setComment("metadata:{\"processId\":\"12345\",\"priority\":\"high\"}");
polyline.setReplies(Arrays.asList(metadataReply));
```
```

## 実装のテスト

### ユニットテスト
`Annotator` をモックし、`addAnnotation` が正しく構成された `PolylineAnnotation` を受け取ることを検証します。

```text
```java
@Test
public void testPolylineAnnotationCreation() {
    // Arrange
    String documentPath = "test-documents/sample.pdf";
    PolylineConfig config = new PolylineConfig();
    config.setMessage("Test polyline");
    config.setPath("M10,10L50,50");
    
    // Act
    try (Annotator annotator = new Annotator(documentPath)) {
        PolylineAnnotation polyline = createPolylineFromConfig(config);
        annotator.add(polyline);
        
        // Assert
        assertNotNull(polyline);
        assertEquals("Test polyline", polyline.getMessage());
        assertEquals(0.7, polyline.getOpacity(), 0.01);
    }
}
```
```

### 統合テスト
実際の PDF ファイルに対してエンドツーエンドテストを実行し、ポリラインが複数のビューアで期待通りに表示されることを確認します。

```text
```java
@Test
public void testEndToEndAnnotationWorkflow() {
    // Test complete process from document input to annotated output
    String inputPath = "test-documents/input.pdf";
    String outputPath = "test-output/annotated.pdf";
    
    DocumentAnnotationService service = new DocumentAnnotationService();
    String result = service.addPolylineAnnotation(inputPath, createTestConfig());
    
    // Verify output file exists and contains annotations
    assertTrue(Files.exists(Paths.get(result)));
    
    // Additional verification logic
    verifyAnnotationExists(result);
}
```
```

## 結論
これで、**pdf annotation library java** を使用してインタラクティブなポリライン PDF を作成する、堅牢で本番対応のアプローチが手に入りました。このソリューションは単一文書のプロトタイプからエンタープライズ規模のバッチ処理までスケールし、Spring Boot とシームレスに統合され、SVG ベースのジオメトリを完全に制御できます。

## 次のステップ
- 不規則領域のハイライトに **area annotations** を検討してください。  
- 方向性を示すために **arrow annotations** を追加してください。  
- WebSocket エンドポイントでアノテーションメタデータを公開し、**real‑time editing** を実装してください。  
- より深い API 機能については、GroupDocs.Annotation の [documentation](https://docs.groupdocs.com/annotation/java/) を確認してください。

## リソースと追加リーディング
- **Documentation**: [GroupDocs.Annotation for Java Documentation](https://docs.groupdocs.com/annotation/java/)  
- **API reference**: [Complete API Reference](https://reference.groupdocs.com/annotation/java/)  
- **Sample projects**: 完全なサンプルアプリケーションは GroupDocs の GitHub リポジトリで閲覧できます。  
- **Support forum**: コミュニティや GroupDocs エキスパートに質問や解決策を共有してください。  
- **Purchase and licensing options**: 詳細は [Purchase and licensing options](https://purchase.groupdocs.com/buy) をご確認ください。

---

**Last Updated:** 2026-09-10  
**Tested With:** GroupDocs.Annotation 25.2 for Java  
**Author:** GroupDocs  

## 関連チュートリアル
- [PDF アノテーション Java の追加 – 完全な GroupDocs ガイド](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [GroupDocs Annotation を使用した PDF Java のロード: ドキュメントロードガイド](/annotation/java/document-loading/)  
- [GroupDocs Java ウォーターマークアノテーション PDF ガイド](/annotation/java/graphical-annotations/groupdocs-java-watermark-annotations-pdf-guide/)