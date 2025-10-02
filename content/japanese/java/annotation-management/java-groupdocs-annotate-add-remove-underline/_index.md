---
"date": "2025-05-06"
"description": "GroupDocs.Annotationを使用してJavaドキュメントに下線注釈を追加および削除する方法を学びましょう。この詳細なガイドでドキュメント管理を強化しましょう。"
"title": "GroupDocs を使用して Java で下線注釈を追加および削除する包括的なガイド"
"url": "/ja/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# Javaの実装方法: GroupDocsで下線注釈を追加および削除する

## 導入

プログラムで注釈を追加または削除して、ドキュメント管理システムを強化したいですか? このチュートリアルでは、Java の強力な GroupDocs.Annotation ライブラリを使用して、PDF などのドキュメントに下線注釈を追加したり削除したりする方法について説明します。

**学習内容:**
- Annotator クラスを初期化します。
- GroupDocs.Annotation for Java を使用して、コメント付きの下線注釈を追加します。
- ドキュメントからすべての注釈を削除します。
- GroupDocs.Annotation を効率的に使用できるように環境を構成します。

これらの機能をプロジェクトでどのように活用できるか見ていきましょう。始める前に、必要な前提条件を満たしていることを確認してください。

## 前提条件

### 必要なライブラリと依存関係
このチュートリアルを効果的に実行するには、次のものを用意してください。
- **GroupDocs.Annotation for Java**: バージョン25.2以降を推奨します。
- **Java開発キット（JDK）**: バージョン 8 以上が必要です。

### 環境設定要件
開発環境に IntelliJ IDEA や Eclipse などの IDE と Maven などのビルド ツールが含まれていることを確認します。

### 知識の前提条件
Java プログラミングの基本的な理解、特に Maven 経由のライブラリの操作が役に立ちます。

## Java 用の GroupDocs.Annotation の設定

Java プロジェクトで GroupDocs.Annotation の使用を開始するには、次の設定手順に従います。

**Maven 構成:**
次の設定を `pom.xml` GroupDocs.Annotation をダウンロードして統合するためのファイル。

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

**ライセンス取得:**
まずはGroupDocsから無料トライアルをダウンロードするか、一時ライセンスを取得して、ライブラリの全機能をお試しください。本番環境での使用には、ライセンスのご購入が必要です。

## 実装ガイド

### 機能1: アノテーターを初期化し、下線注釈を追加する

このセクションでは、 `Annotator` クラスを作成し、ドキュメントに下線注釈を追加します。

#### 概要
注釈を追加すると、ドキュメントの特定の部分を強調表示するのに役立ちます。ここでは、説明やフィードバックのためにコメント付きのテキストに下線を引くことに焦点を当てます。

#### ステップバイステップの実装

**1. アノテーターを初期化する**
作成する `Annotator` オブジェクトを選択して PDF ファイルを読み込みます。

```java
import com.groupdocs.annotation.Annotator;

// 注釈を付けたい文書を読み込みます
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. 返信付きのコメントを作成する**
下線注釈に関連付けられたコメントを定義します。

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

**3. 下線注釈のポイントを定義する**
下線が表示される場所を決定する座標を設定します。

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

**4. 下線注釈の作成と設定**
下線注釈を作成し、色、不透明度、コメントなどのプロパティを設定します。

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // ARGB形式の黄色
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. 注釈を付けた文書を保存する**
変更を新しいファイルに保存します。

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### トラブルシューティングのヒント
- すべてのポイントの座標がドキュメントの境界内にあることを確認します。
- 確認するには `outputPath` ディレクトリが存在し、書き込み可能です。

### 機能2: 注釈なしでドキュメントを保存する

このセクションでは、以前に注釈を付けたドキュメントからすべての注釈を削除する方法について説明します。

#### 概要
共有やアーカイブのために、注釈のないドキュメントのクリーンなバージョンを保存する必要がある場合があります。

#### ステップバイステップの実装

**1. 注釈付きドキュメントで Annotator を初期化する**
既存の注釈があるドキュメントを読み込みます。

```java
Annotator annotator = new Annotator(outputPath);
```

**2. 保存オプションを設定して注釈を削除する**
出力ファイルに注釈を保存しないことを指定します。

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. 注釈なしでドキュメントを保存する**
クリーンアップされたドキュメントのパスを定義して保存します。

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## 実用的な応用

これらの機能が役立つ実際のシナリオをいくつか紹介します。
1. **文書レビュー**レビューのために契約書またはレポートのセクションを強調表示してコメントを追加します。
2. **教育ツール**生徒のために教科書にメモや訂正を書き加えます。
3. **共同編集**フィードバックを得るために、注釈付きのドラフトをチームメンバー間で共有します。
4. **法的文書**議論中に法律文書の重要な条項に下線を引く。
5. **マーケティング資料**配布前にパンフレットで重要な情報を強調表示します。

## パフォーマンスに関する考慮事項
GroupDocs.Annotation を使用する場合は、パフォーマンスを最適化するために次のヒントを考慮してください。
- **メモリ管理**：適切に処分する `Annotator` リソースを解放するためのオブジェクト。
- **バッチ処理**複数のドキュメントに注釈を付ける場合は、システム負荷を効率的に管理するために、それらをバッチで処理します。
- **リソースの割り当て**大きなファイルを処理するために十分なメモリと処理能力が環境にあることを確認してください。

## 結論
GroupDocs.Annotation for Javaを使用して下線付きの注釈を追加および削除する方法を学びました。このチュートリアルでは、Annotatorクラスの初期化、コメント付きの注釈の設定、注釈なしのドキュメントの保存について説明しました。 

さらに詳しく調べるには、これらの機能を既存のドキュメント管理システムに統合するか、GroupDocs が提供する他の注釈タイプを試してみることを検討してください。

## FAQセクション
1. **回の実行で複数の下線注釈を構成するにはどうすればよいですか?**
   - 複数の `UnderlineAnnotation` オブジェクトを順番に追加し、 `annotator.add()` 方法。
2. **このライブラリを使用して PDF 内の画像に注釈を付けることはできますか?**
   - はい、GroupDocs.Annotation は PDF などのドキュメント内の画像への注釈付けをサポートしています。
3. **GroupDocs.Annotation はどのようなファイル形式をサポートしていますか?**
   - PDF、Word、Excel など、さまざまなドキュメント形式をサポートしています。