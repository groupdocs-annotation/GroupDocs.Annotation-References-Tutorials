---
title: ローカルディスクからドキュメントをロード
linktitle: ローカルディスクからドキュメントをロード
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用して、ドキュメントの注釈の機能を解放します。注釈機能を .NET アプリケーションにシームレスに統合します。
weight: 13
url: /ja/net/document-loading-essentials/load-document-from-local-disk/
---
## 導入
GroupDocs.Annotation for .NET を使用すると、ドキュメント アノテーションの可能性を最大限に引き出すことがかつてないほど簡単になります。この強力なツールを使用すると、開発者は堅牢な注釈機能を .NET アプリケーションにシームレスに統合できます。この包括的なガイドでは、GroupDocs.Annotation for .NET を活用してドキュメントに注釈を付けるプロセスを段階的に説明します。経験豊富な開発者であっても、初心者であっても、このチュートリアルではドキュメントの共同作業を強化し、ワークフローを合理化するための知識を身につけることができます。
## 前提条件
GroupDocs.Annotation for .NET を使用したドキュメントの注釈を始める前に、次の前提条件を満たしていることを確認してください。
1. C# の基礎知識: C# プログラミング言語の基礎を理解していることが不可欠です。
2. GroupDocs.Annotation for .NET のインストール: GroupDocs.Annotation for .NET を次からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/annotation/net/).
3. 開発環境: Visual Studio または互換性のある IDE を使用して開発環境をセットアップします。

## 名前空間のインポート
GroupDocs.Annotation for .NET を使用してドキュメントに注釈を付けるには、必要な名前空間をプロジェクトにインポートします。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## ステップ 1: ローカル ディスクからドキュメントをロードする
まず、ローカル ディスクからドキュメントをロードする必要があります。次のコード スニペットを使用します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## ステップ 2: 注釈領域を定義する
次に、注釈領域を定義します。この例では、AreaAnnotation を作成します。
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## ステップ 3: 注釈を付けてドキュメントを保存する
ドキュメントに注釈を付けた後、注釈を付けて保存します。
```csharp
    annotator.Save(outputPath);
}
```
## ステップ 4: 成功メッセージを表示する
最後に、出力パスを含む成功メッセージを表示します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
結論として、GroupDocs.Annotation for .NET は、ドキュメントの注釈機能を .NET アプリケーションに統合するための堅牢なソリューションを提供します。このステップバイステップのガイドに従うことで、ドキュメントに簡単に注釈を付け、プロジェクトでのコラボレーションを強化することができます。
## よくある質問
### 購入する前に GroupDocs.Annotation for .NET を試すことはできますか?
はい、以下から無料試用版をダウンロードできます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET のドキュメントはどこで見つけられますか?
ドキュメントにアクセスできます[ここ](https://tutorials.groupdocs.com/annotation/net/).
### GroupDocs.Annotation for .NET の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスは次から取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Annotation for .NET のサポートは利用できますか?
はい、GroupDocs フォーラムでサポートを見つけることができます。[ここ](https://forum.groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET はどこで購入できますか?
 .NET 用の GroupDocs.Annotation を購入できます。[ここ](https://purchase.groupdocs.com/buy).