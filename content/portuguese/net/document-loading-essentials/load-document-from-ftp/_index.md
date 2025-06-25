---
"description": "Aprimore seus aplicativos .NET com o GroupDocs.Annotation para anotações perfeitas em documentos. Tutorial passo a passo incluído."
"linktitle": "Carregar documento do FTP"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Carregar documento do FTP"
"url": "/pt/net/document-loading-essentials/load-document-from-ftp/"
"weight": 12
---

# Carregar documento do FTP

## Introdução
GroupDocs.Annotation para .NET é uma biblioteca versátil projetada para facilitar a anotação de documentos em aplicativos .NET sem esforço. Seja com PDFs, documentos do Microsoft Office, imagens ou outros formatos, esta biblioteca oferece uma solução unificada para adicionar anotações, como comentários, destaques e formas, aprimorando a colaboração e o gerenciamento de documentos.
## Pré-requisitos
Antes de começar o tutorial, certifique-se de ter os seguintes pré-requisitos:
1. Conhecimento de C#: Proficiência na linguagem de programação C# é essencial para entender e implementar os exemplos de código fornecidos neste tutorial.
2. GroupDocs.Annotation para .NET: Certifique-se de baixar e instalar o GroupDocs.Annotation para .NET do [link para download](https://releases.groupdocs.com/annotation/net/). Siga as instruções de instalação para integrar a biblioteca ao seu projeto .NET com sucesso.
## Importar namespaces
Para utilizar as funcionalidades do GroupDocs.Annotation para .NET, você precisa importar os namespaces necessários para o seu projeto C#. Siga estes passos:

No seu projeto C#, inclua os namespaces necessários no início do seu arquivo de código:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Agora, vamos nos aprofundar no processo de carregar um documento do FTP e adicionar anotações a ele usando o GroupDocs.Annotation para .NET.
## Etapa 1: Definir o caminho de saída
Especifique o caminho de saída onde o documento anotado será salvo.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: Carregar documento do FTP
Recupere o documento do servidor FTP usando o caminho de arquivo fornecido.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // O código de anotação será adicionado aqui
}
```
## Etapa 3: Adicionar anotação
Defina e adicione a anotação desejada, como uma anotação de área, ao documento.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Etapa 4: Salvar documento anotado
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
## Etapa 6: Criar solicitação de FTP
Gere uma solicitação FTP para baixar o arquivo.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Etapa 7: Obter fluxo de arquivos
Recupere o fluxo de arquivos da resposta FTP.
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
Concluindo, o GroupDocs.Annotation para .NET capacita os desenvolvedores a integrar perfeitamente funcionalidades de anotação de documentos em seus aplicativos .NET. Seguindo o guia passo a passo descrito neste tutorial, você pode carregar documentos de FTP com eficiência e adicionar anotações com facilidade, aprimorando a colaboração e o gerenciamento de documentos em seus aplicativos.
## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documento?
Sim, o GroupDocs.Annotation for .NET suporta uma ampla variedade de formatos de documentos, incluindo PDF, documentos do Microsoft Office, imagens e muito mais.
### Posso personalizar a aparência das anotações adicionadas usando o GroupDocs.Annotation for .NET?
Com certeza, o GroupDocs.Annotation para .NET oferece amplas opções de personalização para a aparência das anotações, incluindo cores, estilos e formas.
### GroupDocs.Annotation for .NET oferece suporte para serviços de armazenamento em nuvem?
Sim, o GroupDocs.Annotation para .NET integra-se perfeitamente com serviços populares de armazenamento em nuvem, permitindo que você carregue e salve documentos de serviços como Dropbox, Google Drive e OneDrive.
### Existe uma versão de teste disponível para o GroupDocs.Annotation para .NET?
Sim, você pode explorar os recursos do GroupDocs.Annotation para .NET baixando a versão de teste gratuita do [página de lançamento](https://releases.groupdocs.com/).
### Como posso obter assistência técnica ou suporte para o GroupDocs.Annotation para .NET?
Para assistência técnica, solução de problemas ou dúvidas gerais, você pode visitar o GroupDocs.Annotation para .NET [fórum de suporte](https://forum.groupdocs.com/c/annotation/10).