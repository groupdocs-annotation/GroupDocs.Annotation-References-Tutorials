---
"description": "GroupDocs.Annotation for .NET を使用してドキュメントに画像注釈を追加する方法を学びます。ドキュメント処理機能を簡単に強化できます。"
"linktitle": "ドキュメントに画像注釈を追加する（ローカルパス）"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントに画像注釈を追加する（ローカルパス）"
"url": "/ja/net/unlocking-annotation-power/add-image-annotation-local-path/"
"weight": 14
---

# ドキュメントに画像注釈を追加する（ローカルパス）

## 導入
GroupDocs.Annotation for .NETは、開発者がプログラム的にドキュメントに様々な種類の注釈を追加できる強力なライブラリです。このチュートリアルでは、ローカルパスを使用してドキュメントに画像注釈を追加する方法を学びます。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1. C# プログラミング言語の基礎知識。
2. Visual Studio がシステムにインストールされています。
3. GroupDocs.Annotation for .NET ライブラリがプロジェクトにインストールされているか、チュートリアルが組み込まれています。
4. 入力ドキュメント (例: PDF) と注釈用の画像ファイル。
## 名前空間のインポート
まず、C#ファイルに必要な名前空間をインポートする必要があります。これらの名前空間は、GroupDocs.Annotation の操作に必要なクラスとメソッドへのアクセスを提供します。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## ステップ1: 出力パスを定義する
注釈付きドキュメントを保存する出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ2: アノテーターを初期化する
入力ドキュメントへのパスを指定してアノテーターを初期化します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注釈コードはここに記入します
}
```
## ステップ3: 画像注釈を作成する
インスタンスを作成する `ImageAnnotation` クラスを作成し、位置、不透明度、ページ番号、画像パスなどのプロパティを指定します。
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## ステップ4: 注釈を追加する
作成した画像注釈をドキュメントに追加するには、 `Add` 注釈者の方法。
```csharp
annotator.Add(image);
```
## ステップ5: ドキュメントを保存する
注釈を付けたドキュメントを出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ6: 出力パスを表示する
ドキュメントの保存が成功したことと出力ファイルの場所を示すメッセージを表示します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに画像注釈を追加する方法を学習しました。これらの簡単な手順に従うだけで、強力な注釈機能を活用してドキュメント処理能力を強化できます。
## よくある質問
### PDF以外の文書に注釈を付けることはできますか?
はい、GroupDocs.Annotation は、Word、Excel、PowerPoint など、さまざまなドキュメント形式をサポートしています。
### GroupDocs.Annotation は .NET Core と互換性がありますか?
はい、GroupDocs.Annotation は .NET Framework と .NET Core の両方と互換性があります。
### 注釈の外観をカスタマイズできますか?
もちろん、要件に応じて注釈の外観、サイズ、色、その他のプロパティをカスタマイズできます。
### GroupDocs.Annotation は共同注釈のサポートを提供しますか?
はい、GroupDocs.Annotation は、複数のユーザーが同時にドキュメントに注釈を付けることができる共同注釈機能を提供します。
### 追加のヘルプやサポートはどこで受けられますか?
コミュニティから援助やサポートを受けるには、GroupDocs.Annotation フォーラムにアクセスしてください。