---
title: カスタムフォントのロード
linktitle: カスタムフォントのロード
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET にカスタム フォントをシームレスにロードしてドキュメントの注釈を強化する方法を学びます。簡単に統合するには、ステップバイステップに従ってください。
type: docs
weight: 20
url: /ja/net/advanced-usage/loading-custom-fonts/
---
## 導入
GroupDocs.Annotation for .NET は、開発者が注釈機能を .NET アプリケーションに簡単に追加できるようにする強力なライブラリです。これが提供する重要な機能の 1 つは、カスタム フォントを読み込む機能であり、これにより、ドキュメントの注釈のカスタマイズと柔軟性が強化されます。
## 前提条件
チュートリアルに進む前に、次の前提条件を満たしていることを確認してください。
1.  GroupDocs.Annotation for .NET Library: からライブラリをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/annotation/net/).
2. .NET 開発環境: .NET 開発用に作業環境がセットアップされていることを確認してください。
3. カスタム フォントへのアクセス: アプリケーションにロードするカスタム フォントを準備します。

## 名前空間のインポート
.NET プロジェクトで、GroupDocs.Annotation を利用するために必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## ステップ 1: アノテーター オブジェクトをインスタンス化する
のインスタンスを作成します。`Annotator`カスタム フォント ディレクトリとともに入力 PDF ドキュメントへのパスを指定してクラスを作成します。
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    //さらなる操作のためのコードはここに置かれます
}
```
## ステップ 2: プレビュー オプションを構成する
プレビュー オプションを定義して、ドキュメント プレビューの生成方法を指定します。プレビュー形式、ページ番号などのオプションを設定できます。
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## ステップ 3: ドキュメントのプレビューを生成する
を活用してください。`GeneratePreview`の方法`Document`カスタム フォントを使用してプレビューを生成するプロパティ:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## ステップ 4: 出力パスを表示する
最後に、ドキュメント プレビューが正常に生成されたことを示すメッセージと出力ディレクトリ パスを表示します。
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## 結論
結論として、GroupDocs.Annotation for .NET にカスタム フォントを読み込むことで、開発者は要件に応じてドキュメントの注釈を柔軟にカスタマイズできるようになります。このチュートリアルで概説されている手順に従うことで、カスタム フォントを .NET アプリケーションにシームレスに統合し、ユーザーの注釈エクスペリエンスを向上させることができます。
## よくある質問
### 複数のカスタム フォントを同時にロードできますか?
はい、インスタンス化するときに複数のフォント ディレクトリを指定できます。`Annotator`物体。
### サポートされているフォントの種類に制限はありますか?
GroupDocs.Annotation for .NET は、TrueType (.ttf) フォントや OpenType (.otf) フォントを含む幅広いフォント タイプをサポートします。
### ロードされたフォントを実行時に動的に変更できますか?
はい、必要に応じてフォント ディレクトリを動的に変更し、ドキュメントの注釈を再ロードできます。
### GroupDocs.Annotation は出力ドキュメントへのフォント埋め込みをサポートしていますか?
はい、出力ドキュメントにカスタム フォントを埋め込んで、さまざまなプラットフォーム間で一貫したレンダリングを確保できます。
### アプリケーション内でフォントのライセンスを処理する方法はありますか?
GroupDocs.Annotation は、評価目的の一時ライセンスを含む、フォント ライセンスを管理するためのオプションを提供します。