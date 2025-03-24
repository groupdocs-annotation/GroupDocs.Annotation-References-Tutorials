---
title: 画像注釈をドキュメントに追加 (ローカル パス)
linktitle: 画像注釈をドキュメントに追加 (ローカル パス)
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用してドキュメントに画像注釈を追加する方法を学びます。ドキュメント処理機能を簡単に強化します。
weight: 14
url: /ja/net/unlocking-annotation-power/add-image-annotation-local-path/
---

# 画像注釈をドキュメントに追加 (ローカル パス)

## 導入
GroupDocs.Annotation for .NET は、開発者がプログラムでドキュメントにさまざまな種類の注釈を追加できる強力なライブラリです。このチュートリアルでは、ローカル パスを使用してドキュメントに画像注釈を追加する方法を学びます。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1. C# プログラミング言語の基本的な知識。
2. Visual Studio がシステムにインストールされている。
3. プロジェクトにインストールまたは参照される .NET ライブラリの GroupDocs.Annotation。
4. 入力ドキュメント (PDF など) と注釈用の画像ファイル。
## 名前空間のインポート
まず、必要な名前空間を C# ファイルにインポートする必要があります。これらの名前空間は、GroupDocs.Annotation を操作するために必要なクラスとメソッドへのアクセスを提供します。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## ステップ 1: 出力パスを定義する
注釈付きドキュメントが保存される出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ 2: アノテーターを初期化する
入力ドキュメントへのパスを指定して、アノテーターを初期化します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注釈コードはここに記述されます
}
```
## ステップ 3: 画像注釈を作成する
のインスタンスを作成します。`ImageAnnotation`クラスを作成し、位置、不透明度、ページ番号、画像パスなどのプロパティを指定します。
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
## ステップ 4: 注釈を追加する
作成した画像注釈をドキュメントに追加するには、`Add`アノテーターのメソッド。
```csharp
annotator.Add(image);
```
## ステップ 5: ドキュメントを保存する
注釈付きドキュメントを出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ 6: 出力パスを表示する
ドキュメントが正常に保存されたことと出力ファイルの場所を示すメッセージを表示します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに画像注釈を追加する方法を学習しました。これらの簡単な手順に従うことで、強力な注釈機能を使用してドキュメント処理機能を強化できます。
## よくある質問
### PDF以外のドキュメントに注釈を付けることはできますか?
はい。GroupDocs.Annotation は、Word、Excel、PowerPoint などを含むさまざまなドキュメント形式をサポートしています。
### GroupDocs.Annotation は .NET Core と互換性がありますか?
はい、GroupDocs.Annotation は .NET Framework と .NET Core の両方と互換性があります。
### 注釈の外観をカスタマイズできますか?
もちろん、要件に応じて注釈の外観、サイズ、色、その他のプロパティをカスタマイズできます。
### GroupDocs.Annotation は共同アノテーションをサポートしますか?
はい、GroupDocs.Annotation は、複数のユーザーが同時にドキュメントに注釈を付けることができる共同注釈機能を提供します。
### 追加のヘルプやサポートはどこで入手できますか?
コミュニティからの支援やサポートについては、GroupDocs.Annotation フォーラムにアクセスしてください。