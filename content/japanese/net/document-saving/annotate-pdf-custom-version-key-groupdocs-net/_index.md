---
"date": "2025-05-06"
"description": "強力な GroupDocs.Annotation for .NET ライブラリを使用して、カスタム バージョン キーで PDF に注釈を付けて保存し、各ドキュメントの反復が一意に識別できるようにする方法を学習します。"
"title": "GroupDocs.Annotation を使用して .NET でカスタム バージョン キーを使用して注釈付き PDF を保存する"
"url": "/ja/net/document-saving/annotate-pdf-custom-version-key-groupdocs-net/"
type: docs
"weight": 1
---

# GroupDocs.Annotation を使用して .NET でカスタム バージョン キーを使用して注釈付き PDF を保存する

## 導入
今日のデジタル世界では、共同プロジェクト全体にわたって正確性と説明責任を維持するために、ドキュメントのバージョン管理が不可欠です。各バージョンを一意に識別できるようにしながら、ドキュメントを効率的に管理し、注釈を付けるにはどうすればよいでしょうか？このチュートリアルでは、注釈付きPDFドキュメントをカスタムバージョンキーで保存する手順を説明します。 **.NET 用 GroupDocs.Annotation** ライブラリ。この強力なツールを活用することで、ワークフローを効率化し、ドキュメント管理業務を強化できます。

この記事では、ドキュメント注釈を実装し、特定のバージョンキーで保存することで、すべてのイテレーションが追跡可能かつ明確に区別できるようにする方法を説明します。学習内容は以下のとおりです。
- 使い方 **.NET 用 GroupDocs.Annotation** PDF ドキュメントに注釈を付けます。
- カスタム キーを使用してドキュメントの注釈付きバージョンを保存するテクニック。
- 現実のシナリオにおける実践的なアプリケーション。

この機能を実装する前に、前提条件について詳しく見ていきましょう。

## 前提条件
このチュートリアルを実行するには、次のものが必要です。

### 必要なライブラリとバージョン
- **GroupDocs.注釈** ライブラリ（バージョン25.4.0以降）
- .NET Framework または .NET Core 環境がマシンにセットアップされている

### 環境設定要件
開発環境に以下のものが備わっていることを確認してください。
- Visual Studio または C# をサポートする同様の IDE
- アクセス可能なディレクトリに保存された、注釈を付けられるPDF文書

### 知識の前提条件
C#プログラミングの基本的な概念と.NET環境の理解があれば有利です。ドキュメント処理ライブラリの使用経験があれば有利ですが、必須ではありません。

## GroupDocs.Annotation を .NET 用にセットアップする
まず、 **GroupDocs.注釈** プロジェクトにライブラリを追加します。このパッケージをインストールするには、主に2つの方法があります。

### NuGet パッケージ マネージャー コンソール
NuGet パッケージ マネージャー コンソールで次のコマンドを実行します。
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### .NET CLI
または、.NET コマンド ライン インターフェイス (CLI) を使用することもできます。
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

#### ライセンス取得手順
1. **無料トライアル**無料試用版は以下からダウンロードできます [GroupDocs リリース](https://releases.groupdocs.com/annotation/net/) ライブラリの機能をテストします。
2. **一時ライセンス**より詳細なテストが必要な場合は、 [GroupDocs 一時ライセンスページ](https://purchase。groupdocs.com/temporary-license/).
3. **購入**長期使用の場合は、ライセンスを [GroupDocs 購入ページ](https://purchase。groupdocs.com/buy).

#### C# による基本的な初期化とセットアップ
GroupDocs.Annotation for .NETを使用してドキュメントに注釈を付け始めるには、まず `Annotator` ドキュメントへのパスを持つインスタンス:
```csharp
using GroupDocs.Annotation;
// 入力ディレクトリと出力ディレクトリの定数を定義する
const string INPUT_PDF = "YOUR_DOCUMENT_DIRECTORY/document.pdf";
const string OUTPUT_PATH = Path.Combine("YOUR_OUTPUT_DIRECTORY", "result.pdf");

using (Annotator annotator = new Annotator(INPUT_PDF))
{
    // さらなる注釈手順はここに追加されます
}
```
これにより、注釈を追加し、カスタム バージョン キーを使用してドキュメントを保存するための準備が整います。

## 実装ガイド
### ドキュメントに注釈を追加する
#### 概要
このセクションでは、2 種類の注釈を使用して PDF ドキュメントに注釈を付ける方法を説明します。 `AreaAnnotation` そして `EllipseAnnotation`これらは、ドキュメント内の特定の領域を強調表示するのに役立ちます。

#### ステップ1: アノテーターを初期化する
まず、 `Annotator` 入力 PDF へのパスを持つクラス:
```csharp
using (Annotator annotator = new Annotator(INPUT_PDF))
{
    // 注釈の手順は以下のとおりです
}
```
その `Annotator` オブジェクトを使用すると、注釈を効果的に管理および適用できます。

#### ステップ2: AreaAnnotationオブジェクトを作成する
位置や色など、エリア注釈のプロパティを定義します。
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 位置（x、y）とサイズ（幅、高さ）を定義します
    BackgroundColor = 65535,                // 背景色のARGB形式を設定します
    PageNumber = 1                          // 注釈を付けるページ番号を指定します
};
```

#### ステップ3: EllipseAnnotationオブジェクトを作成する
同様に、必要なプロパティを使用して楕円注釈を設定します。
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 位置（x、y）とサイズ（幅、高さ）を定義します
    BackgroundColor = 123456,                // 背景色のARGB形式を設定します
    PageNumber = 1                          // 注釈を付けるページ番号を指定します
};
```

#### ステップ4: 注釈を追加する
両方の注釈を `Annotator` 実例：
```csharp
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```
この手順では、カスタム注釈をドキュメントに登録します。

#### ステップ5: カスタムバージョンキーを使用して注釈付きドキュメントを保存する
最後に、注釈を付けたドキュメントを保存し、 `SaveOptions` クラス：
```csharp
annotator.Save(OUTPUT_PATH, new SaveOptions { Version = "SECOND" });
```
その `Version` 不動産の `SaveOptions` ドキュメントの各バージョンに意味のある識別子を割り当てることができます。

### トラブルシューティングのヒント
- 入力ディレクトリと出力ディレクトリのパスが正しいことを確認します。
- 注釈を続行する前に、NuGet または CLI 経由で GroupDocs.Annotation がインストールされていることを確認してください。
- 権限の問題が発生した場合は、環境内のファイル アクセス権を確認してください。

## 実用的な応用
GroupDocs.Annotation は汎用性が高く、さまざまな実際のシナリオに統合できます。
1. **法的文書レビュー**契約書に注釈を付けて、レビュー プロセス中に注意が必要な条件を強調表示します。
2. **学術フィードバック**PDF にコメントや訂正を記入して、生徒の提出物に対するフィードバックを提供します。
3. **デザインコラボレーション**注釈を使用して共同設計レビューを行い、設計変更のドキュメントをマークアップします。

統合の可能性は .NET システムとフレームワーク全体に広がり、エンタープライズ アプリケーションのドキュメント処理機能が強化されます。

## パフォーマンスに関する考慮事項
GroupDocs.Annotation を使用する場合は、次のパフォーマンス最適化のヒントを考慮してください。
- 破棄することでメモリ使用量を最適化します `Annotator` 使用後のインスタンス。
- リソースの割り当てを効率的に管理し、大規模なドキュメントをスムーズに処理します。
- .NET メモリ管理のベスト プラクティスを適用して、アプリケーションの安定性と応答性を確保します。

## 結論
PDFに注釈を付ける方法を学習しました。 **.NET 用 GroupDocs.Annotation** カスタムバージョンキーを使用して保存できます。この機能により、注釈付きバージョンを一意に識別できるため、ドキュメント管理ワークフローが大幅に改善されます。

次のステップとして、GroupDocs.Annotation のさらなる機能を調べたり、この機能をより大規模なアプリケーションに統合したりします。

## FAQセクション
1. **GroupDocs.Annotation for .NET とは何ですか?**
   - .NET アプリケーションでプログラムによってドキュメントに注釈を付けるライブラリ。さまざまな注釈タイプとカスタマイズ オプションを提供します。
2. **ドキュメントに複数の注釈を追加するにはどうすればよいですか?**
   - 使用 `Add` 方法 `Annotator` 注釈オブジェクトのリストを含むインスタンス。
3. **注釈付きバージョンを異なる識別子で保存できますか?**
   - はい、カスタムバージョンキーを指定することで `SaveOptions`。
4. **GroupDocs.Annotation を使用して注釈を付けることができるドキュメントの種類は何ですか?**
   - PDF、Word ファイル、画像など、さまざまなドキュメント形式をサポートしています。
5. **GroupDocs.Annotation のライセンスを取得するにはどうすればよいですか?**
   - ライセンスを取得するには [GroupDocs 購入ページ](https://purchase。groupdocs.com).