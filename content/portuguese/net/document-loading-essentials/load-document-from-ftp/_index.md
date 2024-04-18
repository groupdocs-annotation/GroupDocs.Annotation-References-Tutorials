---
title: Carregar documento do FTP
linktitle: Carregar documento do FTP
second_title: API GroupDocs.Annotation .NET
description: Aprimore seus aplicativos .NET com GroupDocs.Annotation para anotações contínuas em documentos. Tutorial passo a passo incluído.
type: docs
weight: 12
url: /pt/net/document-loading-essentials/load-document-from-ftp/
---
## Introdução
GroupDocs.Annotation for .NET é uma biblioteca versátil projetada para facilitar os recursos de anotação de documentos em aplicativos .NET sem esforço. Esteja você lidando com PDFs, documentos do Microsoft Office, imagens ou outros formatos, esta biblioteca oferece uma solução unificada para adicionar anotações, como comentários, destaques e formas, para aprimorar a colaboração e o gerenciamento de documentos.
## Pré-requisitos
Antes de mergulhar no tutorial, certifique-se de ter os seguintes pré-requisitos em vigor:
1. Conhecimento de C#: Proficiência na linguagem de programação C# é essencial para compreender e implementar os exemplos de código fornecidos neste tutorial.
2.  GroupDocs.Annotation for .NET: certifique-se de baixar e instalar GroupDocs.Annotation for .NET do[Link para Download](https://releases.groupdocs.com/annotation/net/). Siga as instruções de instalação para integrar a biblioteca ao seu projeto .NET com sucesso.
## Importar namespaces
Para utilizar as funcionalidades do GroupDocs.Annotation for .NET, você precisa importar os namespaces necessários para o seu projeto C#. Siga esses passos:

Dentro do seu projeto C#, inclua os namespaces necessários no início do seu arquivo de código:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Agora, vamos nos aprofundar no processo de carregamento de um documento do FTP e adição de anotações a ele usando GroupDocs.Annotation for .NET.
## Etapa 1: definir o caminho de saída
Especifique o caminho de saída onde o documento anotado será salvo.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: carregar o documento do FTP
Recupere o documento do servidor FTP usando o caminho de arquivo fornecido.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // O código de anotação será adicionado aqui
}
```
## Etapa 3: adicionar anotação
Defina e adicione a anotação desejada, como uma anotação de área, ao documento.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Etapa 4: salvar o documento anotado
Salve o documento anotado no caminho de saída especificado.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Etapa 5: recuperar arquivo do FTP
Implemente o método para buscar o arquivo do servidor FTP.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Etapa 6: criar solicitação de FTP
Gere uma solicitação FTP para baixar o arquivo.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Etapa 7: obter fluxo de arquivos
Recuperar o fluxo de arquivos da resposta FTP.
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
## Conclusão
Concluindo, GroupDocs.Annotation for .NET capacita os desenvolvedores a integrar perfeitamente funcionalidades de anotação de documentos em seus aplicativos .NET. Seguindo o guia passo a passo descrito neste tutorial, você pode carregar documentos de FTP com eficiência e adicionar anotações com facilidade, melhorando a colaboração e o gerenciamento de documentos em seus aplicativos.
## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documentos?
Sim, GroupDocs.Annotation for .NET oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, documentos do Microsoft Office, imagens e muito mais.
### Posso personalizar a aparência das anotações adicionadas usando GroupDocs.Annotation for .NET?
Com certeza, GroupDocs.Annotation for .NET oferece amplas opções de personalização para a aparência das anotações, incluindo cores, estilos e formas.
### O GroupDocs.Annotation for .NET fornece suporte para serviços de armazenamento em nuvem?
Sim, o GroupDocs.Annotation for .NET integra-se perfeitamente com serviços populares de armazenamento em nuvem, permitindo carregar e salvar documentos de serviços como Dropbox, Google Drive e OneDrive.
### Existe uma versão de teste disponível para GroupDocs.Annotation for .NET?
 Sim, você pode explorar os recursos do GroupDocs.Annotation for .NET baixando a versão de avaliação gratuita no site[página de lançamento](https://releases.groupdocs.com/).
### Como posso obter assistência técnica ou suporte para GroupDocs.Annotation for .NET?
 Para assistência técnica, solução de problemas ou dúvidas gerais, você pode visitar GroupDocs.Annotation for .NET[Fórum de suporte](https://forum.groupdocs.com/c/annotation/10).