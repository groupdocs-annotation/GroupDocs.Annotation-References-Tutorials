---
title: テキストの上に画像の注釈を配置する
linktitle: テキストの上に画像の注釈を配置する
second_title: GroupDocs.Annotation .NET API
description: 効率的なドキュメント管理とコラボレーションのために、GroupDocs.Annotation を使用して .NET のテキストに画像注釈を追加する方法を学びます。
weight: 21
url: /ja/net/advanced-usage/put-image-annotation-over-text/
---
## 導入
.NET 開発の世界では、GroupDocs.Annotation はドキュメントに注釈を追加し、コラボレーションとドキュメント管理をより効率的にするための強力なソリューションを提供します。一般的な要件の 1 つは、テキストの上に画像の注釈を配置することです。これは、GroupDocs.Annotation for .NET を使用してシームレスに実現できます。
## 前提条件
GroupDocs.Annotation for .NET を使用してテキスト上に画像注釈を配置するプロセスに入る前に、次のものが揃っていることを確認してください。
1.  GroupDocs.Annotation for .NET Library: からライブラリをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/annotation/net/).
2. 開発環境: Visual Studio やその他の .NET IDE などの適切な開発環境をセットアップします。
3. 文書ファイルと画像ファイル: 注釈に使用する文書ファイル (PDF、DOCX など) と画像ファイルを準備します。
4. C# の基本的な理解: このチュートリアルで提供されるコード スニペットを実装するには、C# プログラミング言語に精通している必要があります。

## 名前空間のインポート
注釈プロセスに進む前に、必要な名前空間を C# プロジェクトにインポートしていることを確認してください。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## ステップ 1: 出力パスを定義する
まず、注釈付きドキュメントが保存される出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## ステップ 2: アノテーターを初期化する
を初期化します`Annotator`入力ドキュメントのパスを指定してオブジェクトを作成します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注釈コードがここに挿入されます
}
```
## ステップ 3: 画像注釈を作成する
を作成します`ImageAnnotation`ボックスの寸法、不透明度、ページ番号、画像パス、Z インデックスなどの必要なプロパティを持つオブジェクト:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## ステップ 4: 注釈を追加する
画像注釈をドキュメントに追加するには、`Add`の方法`Annotator`物体：
```csharp
annotator.Add(image);
```
## ステップ 5: 注釈付きドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ 6: 成功メッセージを表示する
注釈付きドキュメントへのパスを含む成功メッセージを表示します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
結論として、GroupDocs.Annotation を使用して .NET アプリケーションのテキストに画像注釈を追加するのは簡単なプロセスです。このチュートリアルで提供されるステップバイステップのガイドに従うことで、ドキュメントに効率的に注釈を付け、.NET プロジェクトでのコラボレーション機能とドキュメント管理機能を強化できます。
## よくある質問
### PDF 以外のドキュメントに注釈を付けることはできますか?
はい、GroupDocs.Annotation は、DOCX、XLSX、PPTX などのさまざまなドキュメント形式をサポートしています。
### GroupDocs.Annotation に利用できる無料トライアルはありますか?
はい、無料試用版を次からダウンロードできます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Annotation のサポートを受けるにはどうすればよいですか?
 GroupDocs.Annotation コミュニティ フォーラムからサポートを受けることができます。[ここ](https://forum.groupdocs.com/c/annotation/10).
### テスト目的で一時ライセンスが必要ですか?
はい、次から一時ライセンスを取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/)テスト目的のため。
### 注釈の外観をカスタマイズできますか?
はい。GroupDocs.Annotation には、色、不透明度、フォント サイズなど、注釈の外観をカスタマイズするためのさまざまなオプションが用意されています。