---
"description": "GroupDocs.Annotation でシームレスなドキュメント注釈を作成し、.NET アプリケーションを強化しましょう。ステップバイステップのチュートリアルも含まれています。"
"linktitle": "FTPからドキュメントを読み込む"
"second_title": "GroupDocs.Annotation .NET API"
"title": "FTPからドキュメントを読み込む"
"url": "/ja/net/document-loading-essentials/load-document-from-ftp/"
type: docs
"weight": 12
---

# FTPからドキュメントを読み込む

## 導入
GroupDocs.Annotation for .NETは、.NETアプリケーション内でドキュメントへの注釈機能を容易に利用できるように設計された多用途ライブラリです。PDF、Microsoft Officeドキュメント、画像、その他の形式を扱う場合でも、このライブラリはコメント、ハイライト、図形などの注釈を追加するための統合ソリューションを提供し、共同作業とドキュメント管理を強化します。
## 前提条件
チュートリアルに進む前に、次の前提条件が満たされていることを確認してください。
1. C# の知識: このチュートリアルで提供されるコード例を理解して実装するには、C# プログラミング言語の熟練度が不可欠です。
2. GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NETを以下のサイトからダウンロードしてインストールしてください。 [ダウンロードリンク](https://releases.groupdocs.com/annotation/net/)インストール手順に従って、ライブラリを .NET プロジェクトに正常に統合します。
## 名前空間のインポート
GroupDocs.Annotation for .NET の機能を利用するには、必要な名前空間を C# プロジェクトにインポートする必要があります。以下の手順に従ってください。

C# プロジェクト内で、コード ファイルの先頭に必要な名前空間を含めます。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

ここで、GroupDocs.Annotation for .NET を使用して FTP からドキュメントを読み込み、それに注釈を追加するプロセスを詳しく見ていきましょう。
## ステップ1: 出力パスを定義する
注釈付きドキュメントを保存する出力パスを指定します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ2: FTPからドキュメントを読み込む
指定されたファイル パスを使用して FTP サーバーからドキュメントを取得します。
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // 注釈コードはここに追加されます
}
```
## ステップ3: 注釈を追加する
領域注釈などの必要な注釈を定義してドキュメントに追加します。
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## ステップ4: 注釈付きドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## ステップ5: FTPからファイルを取得する
FTP サーバーからファイルを取得するメソッドを実装します。
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## ステップ6: FTPリクエストを作成する
ファイルをダウンロードするための FTP リクエストを生成します。
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## ステップ7: ファイルストリームを取得する
FTP 応答からファイル ストリームを取得します。
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## 結論
結論として、GroupDocs.Annotation for .NET は、開発者がドキュメント注釈機能を .NET アプリケーションにシームレスに統合することを可能にします。このチュートリアルで概説されているステップバイステップのガイドに従うことで、FTP からドキュメントを効率的に読み込み、簡単に注釈を追加できるため、アプリケーション内でのコラボレーションとドキュメント管理が強化されます。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
はい、GroupDocs.Annotation for .NET は、PDF、Microsoft Office ドキュメント、画像など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Annotation for .NET を使用して追加された注釈の外観をカスタマイズできますか?
はい、GroupDocs.Annotation for .NET では、色、スタイル、形状など、注釈の外観をカスタマイズする幅広いオプションが提供されています。
### GroupDocs.Annotation for .NET はクラウド ストレージ サービスをサポートしていますか?
はい、GroupDocs.Annotation for .NET は一般的なクラウド ストレージ サービスとシームレスに統合され、Dropbox、Google Drive、OneDrive などのサービスからドキュメントを読み込んで保存できます。
### GroupDocs.Annotation for .NET の試用版はありますか?
はい、GroupDocs.Annotation for .NETの機能を試すには、以下のサイトから無料トライアル版をダウンロードしてください。 [リリースページ](https://releases。groupdocs.com/).
### GroupDocs.Annotation for .NET の技術支援やサポートを受けるにはどうすればよいですか?
技術的なサポート、トラブルシューティング、または一般的な質問については、GroupDocs.Annotation for .NET にアクセスしてください。 [サポートフォーラム](https://forum。groupdocs.com/c/annotation/10).