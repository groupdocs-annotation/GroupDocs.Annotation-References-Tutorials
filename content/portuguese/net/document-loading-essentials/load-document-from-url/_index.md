---
"description": "Aprenda a anotar documentos PDF programaticamente usando o GroupDocs.Annotation para .NET. Tutorial passo a passo com exemplos de código."
"linktitle": "Carregar documento da URL"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Carregar documento da URL"
"url": "/pt/net/document-loading-essentials/load-document-from-url/"
"weight": 15
---

# Carregar documento da URL

## Introdução
O GroupDocs.Annotation para .NET é uma biblioteca rica em recursos que permite aos desenvolvedores adicionar recursos de anotação aos seus aplicativos .NET sem esforço. Com o GroupDocs.Annotation, você pode anotar documentos PDF programaticamente, permitindo aos usuários destacar texto, adicionar comentários, desenhar formas e muito mais. Este tutorial o guiará pelas etapas de carregamento de um documento a partir de uma URL, adição de anotações e salvamento do documento anotado usando o GroupDocs.Annotation para .NET.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos:
1. Visual Studio: certifique-se de ter o Visual Studio instalado na sua máquina de desenvolvimento.
2. GroupDocs.Annotation para .NET: Baixe e instale o GroupDocs.Annotation para .NET do [site](https://releases.groupdocs.com/annotation/net/).
3. Conhecimento básico de C#: familiarize-se com a linguagem de programação C#.
4. Conexão com a Internet: você precisará de uma conexão com a Internet para acessar recursos externos e baixar arquivos de amostra.

## Importar namespaces
Primeiro, vamos importar os namespaces necessários no seu projeto C#:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Etapa 1: Carregar documento da URL
Para anotar um documento PDF a partir de um URL, siga estas etapas:
### Etapa 1.1: Definir o caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Etapa 1.2: Especificar URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Etapa 1.3: Carregar documento
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Adicione anotações aqui
    annotator.Save(outputPath);
}
```
## Etapa 2: Adicionar anotações
Agora, vamos adicionar anotações ao documento carregado. Neste exemplo, adicionaremos uma anotação de área:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Etapa 3: Salvar documento anotado
Por fim, salve o documento anotado no caminho de saída especificado:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Neste tutorial, aprendemos como anotar documentos PDF usando o GroupDocs.Annotation para .NET. Seguindo o guia passo a passo, você pode integrar perfeitamente a funcionalidade de anotação aos seus aplicativos .NET, permitindo que os usuários colaborem efetivamente em arquivos PDF.

## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os frameworks .NET?
Sim, o GroupDocs.Annotation para .NET é compatível com vários frameworks .NET, incluindo .NET Framework, .NET Core e .NET Standard.
### Posso personalizar a aparência das anotações?
Com certeza! O GroupDocs.Annotation para .NET oferece amplas opções de personalização, permitindo que você modifique a aparência e o comportamento das anotações de acordo com suas necessidades.
### Existe uma avaliação gratuita disponível para o GroupDocs.Annotation para .NET?
Sim, você pode baixar uma versão de avaliação gratuita do GroupDocs.Annotation para .NET no [site](https://releases.groupdocs.com/).
### Como posso obter suporte técnico para o GroupDocs.Annotation para .NET?
Se você encontrar algum problema técnico ou tiver dúvidas sobre o GroupDocs.Annotation para .NET, você pode buscar assistência no [fórum de suporte](https://forum.groupdocs.com/c/annotation/10).
### Onde posso comprar uma licença para o GroupDocs.Annotation para .NET?
Você pode adquirir uma licença para GroupDocs.Annotation para .NET no [página de compra](https://purchase.groupdocs.com/buy).