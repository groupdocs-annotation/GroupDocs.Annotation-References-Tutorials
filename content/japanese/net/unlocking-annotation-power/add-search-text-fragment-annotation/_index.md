---
"description": "GroupDocs.Annotation for .NET のパワーを活用し、アプリケーションにドキュメント注釈機能を簡単に追加します。"
"linktitle": "ドキュメントに検索テキストフラグメント注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントに検索テキストフラグメント注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
"weight": 20
---

# ドキュメントに検索テキストフラグメント注釈を追加する

## 導入
.NET開発において、GroupDocs.Annotationはドキュメントにシームレスに注釈を付ける強力なツールとして際立っています。経験豊富な開発者の方でも、.NETの世界に足を踏み入れたばかりの方でも、この包括的なチュートリアルでは、名前空間のインポートからドキュメントに検索テキストフラグメント注釈を追加する複雑な操作の習得まで、GroupDocs.Annotation for .NETの基本を網羅的に解説します。
## 導入
GroupDocs.Annotation for .NET は、開発者がアプリケーションにドキュメント注釈機能を簡単に組み込むことを可能にします。直感的な API と強力な機能により、PDF、Microsoft Office ドキュメント、画像など、さまざまな形式のドキュメントに注釈を付けることができます。
## 前提条件
GroupDocs.Annotation for .NET を使用する前に、次の前提条件が満たされていることを確認してください。

## 名前空間のインポート
まず、.NET プロジェクトで GroupDocs.Annotation クラスとメソッドにアクセスするために必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ステップ1: 出力パスを定義する
まず、注釈付きドキュメントを保存する出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ2: アノテーターを初期化する
次に、 `Annotator` 注釈を付けるドキュメントへのパスを指定してクラスを作成します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## ステップ3: 検索テキストフラグメント注釈を作成する
作成する `SearchTextFragment` 検索するテキスト、フォント サイズ、フォント ファミリ、フォント カラー、背景色などの必要なプロパティを持つオブジェクト:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## ステップ4: 注釈を追加する
作成した検索テキストフラグメント注釈を、 `Add` 注釈者の方法:
```csharp
annotator.Add(searchText);
```
## ステップ5: 注釈付きドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ6: 成功メッセージを表示する
ドキュメントが正常に保存されたことをユーザーに通知します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
結論として、GroupDocs.Annotation for .NETはドキュメントへの注釈追加プロセスを簡素化し、共同作業とドキュメントレビュープロセスを強化します。このガイドで概説されている手順に従うことで、ドキュメント注釈機能を.NETアプリケーションにシームレスに統合できます。
## よくある質問
### GroupDocs.Annotation はすべてのドキュメント形式と互換性がありますか?
はい、GroupDocs.Annotation は、PDF、Microsoft Office ドキュメント、画像など、幅広いドキュメント形式をサポートしています。
### 注釈の外観をカスタマイズできますか?
もちろんです! GroupDocs.Annotation では、注釈の幅広いカスタマイズ オプションが提供されており、フォント サイズ、色、スタイルなどのプロパティを調整できます。
### GroupDocs.Annotation の無料トライアルはありますか?
はい、GroupDocs.Annotation の無料トライアルにアクセスして、購入前にその機能や性能を確認することができます。 [ここ](https://releases.groupdocs.com/)..
### GroupDocs.Annotation のサポートはどこで見つかりますか?
GroupDocs.Annotationに関するサポートと支援については、GroupDocsをご覧ください。 [フォーラム](https://forum.groupdocs.com/c/annotation/10) 注釈関連の質問と議論専用です。
### GroupDocs.Annotation の一時ライセンスを取得するにはどうすればよいですか?
GroupDocs.Annotationの一時ライセンスはGroupDocsを通じて取得できます。 [Webサイト](https://purchase.groupdocs.com/temporary-license/)製品を十分に評価することができます。