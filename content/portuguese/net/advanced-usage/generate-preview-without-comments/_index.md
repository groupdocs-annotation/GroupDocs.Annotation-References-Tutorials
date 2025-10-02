---
"description": "Aprenda a integrar perfeitamente recursos de anotação de documentos em seus aplicativos .NET usando o GroupDocs.Annotation for .NET."
"linktitle": "Gerar visualização sem comentários"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Gerar visualização sem comentários"
"url": "/pt/net/advanced-usage/generate-preview-without-comments/"
type: docs
"weight": 14
---

# Gerar visualização sem comentários

## Introdução
GroupDocs.Annotation para .NET é uma ferramenta poderosa que permite aos desenvolvedores incorporar recursos de anotação em seus aplicativos .NET de forma integrada. Seja trabalhando em um sistema de gerenciamento de documentos, uma plataforma de colaboração ou qualquer outro aplicativo que exija recursos de anotação em documentos, o GroupDocs.Annotation oferece um conjunto abrangente de ferramentas para aprimorar a funcionalidade do seu aplicativo.
## Pré-requisitos
Antes de começar a usar o GroupDocs.Annotation para .NET, certifique-se de ter os seguintes pré-requisitos configurados:
### 1. Instale o GroupDocs.Annotation para .NET
Para começar, você precisa baixar e instalar o GroupDocs.Annotation para .NET. Você pode encontrar o link para download [aqui](https://releases.groupdocs.com/annotation/net/). Siga as instruções de instalação fornecidas na documentação para um processo de configuração tranquilo.
### 2. Obter licença
O GroupDocs.Annotation para .NET requer uma licença para uso comercial. Você pode adquirir uma licença em [aqui](https://purchase.groupdocs.com/buy) ou optar por uma licença temporária [aqui](https://purchase.groupdocs.com/temporary-license/) para fins de teste.
### 3. Familiaridade com o .NET Framework
Conhecimento básico do .NET Framework e da linguagem de programação C# é essencial para utilizar efetivamente o GroupDocs.Annotation para .NET.

## Importar namespaces
Agora que você configurou os pré-requisitos, vamos importar os namespaces necessários para seu aplicativo .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Siga estas instruções passo a passo para gerar uma visualização sem comentários usando o GroupDocs.Annotation para .NET:
## Etapa 1: Inicializar o Annotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Etapa 2: Configurar opções de visualização
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## Etapa 3: especifique o formato de visualização e os números de página
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## Etapa 4: desabilitar a renderização de comentários
```csharp
    previewOptions.RenderComments = false;
```
## Etapa 5: gerar visualização
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Depois de seguir essas etapas, seu aplicativo .NET poderá gerar uma visualização das páginas especificadas do documento sem renderizar comentários.

## Conclusão
Incorporar recursos de anotação em seus aplicativos .NET nunca foi tão fácil graças ao GroupDocs.Annotation para .NET. Seguindo os passos descritos neste tutorial, você pode integrar perfeitamente os recursos de anotação de documentos aos seus aplicativos, aprimorando a colaboração e o gerenciamento de documentos.
## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documento?
O GroupDocs.Annotation para .NET oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, DOCX, PPTX, XLSX e muito mais.
### Posso personalizar a aparência das anotações geradas usando o GroupDocs.Annotation for .NET?
Sim, o GroupDocs.Annotation para .NET oferece amplas opções de personalização, permitindo que você adapte a aparência das anotações para atender às necessidades do seu aplicativo.
### O GroupDocs.Annotation para .NET oferece suporte à colaboração multiusuário?
Sim, o GroupDocs.Annotation para .NET oferece recursos de anotação colaborativa, permitindo que vários usuários anotem documentos simultaneamente.
### Há suporte técnico disponível para o GroupDocs.Annotation para .NET?
Sim, o suporte técnico para GroupDocs.Annotation para .NET está disponível através do [fórum de suporte](https://forum.groupdocs.com/c/annotation/10).
### Posso testar o GroupDocs.Annotation para .NET gratuitamente antes de comprar?
Sim, você pode explorar os recursos do GroupDocs.Annotation para .NET baixando a versão de avaliação gratuita [aqui](https://releases.groupdocs.com/).