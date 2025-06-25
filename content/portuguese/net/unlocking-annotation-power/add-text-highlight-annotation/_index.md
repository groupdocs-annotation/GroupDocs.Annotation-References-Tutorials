---
"description": "Aprenda a adicionar anotações de destaque de texto a documentos usando o GroupDocs.Annotation para .NET. Aprimore a colaboração e a produtividade com este guia abrangente."
"linktitle": "Adicionar anotação de destaque de texto ao documento"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Adicionar anotação de destaque de texto ao documento"
"url": "/pt/net/unlocking-annotation-power/add-text-highlight-annotation/"
"weight": 22
---

# Adicionar anotação de destaque de texto ao documento

## Introdução
No âmbito da gestão e colaboração de documentos, o GroupDocs.Annotation para .NET surge como uma solução robusta, capacitando desenvolvedores a integrar perfeitamente anotações de destaque de texto em seus aplicativos. Este tutorial serve como um guia completo para adicionar anotações de destaque de texto a documentos usando o GroupDocs.Annotation para .NET. Por meio de instruções passo a passo e explicações detalhadas, você adquirirá proficiência no aproveitamento dos recursos desta poderosa biblioteca.
## Pré-requisitos
Antes de se aprofundar na implementação de anotações de destaque de texto, certifique-se de ter os seguintes pré-requisitos em vigor:
1. Configuração do ambiente: tenha um ambiente de desenvolvimento adequado configurado para desenvolvimento .NET.
2. Instalação do GroupDocs.Annotation para .NET: Baixe e instale o GroupDocs.Annotation para .NET do fornecido [link para download](https://releases.groupdocs.com/annotation/net/).
3. Familiaridade com C#: Noções básicas de linguagem de programação C#.
4. Documento a ser anotado: prepare um documento (por exemplo, PDF) que você pretende anotar.

## Importar namespaces
Para começar, importe os namespaces necessários no seu código C# para utilizar as funcionalidades do GroupDocs.Annotation para .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Agora, vamos dividir o processo de adição de anotações de destaque de texto em várias etapas:
## Etapa 1: Definir o caminho de saída
Especifique o caminho de saída onde o documento anotado será salvo:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: Inicializar o Annotator
Crie uma instância do `Annotator` classe, passando o nome do arquivo do documento como parâmetro:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Etapa 3: Criar anotação de destaque
Instanciar um `HighlightAnnotation` objeto e configurar suas propriedades:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
## Etapa 4: Adicionar anotação
Adicione a anotação de destaque criada ao documento:
```csharp
annotator.Add(highlight);
```
## Etapa 5: Salvar documento anotado
Salve o documento anotado no caminho de saída especificado:
```csharp
annotator.Save(outputPath);
```

## Conclusão
Concluindo, o GroupDocs.Annotation para .NET oferece uma abordagem simplificada para incorporar anotações de destaque de texto em documentos. Seguindo os passos descritos neste tutorial, os desenvolvedores podem aprimorar perfeitamente a colaboração e a produtividade em seus aplicativos.
## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documento?
O GroupDocs.Annotation para .NET oferece suporte a vários formatos de documento, incluindo PDF, Word, Excel e outros. Consulte a documentação para obter a lista completa.
### As anotações podem ser personalizadas de acordo com requisitos específicos?
Sim, os desenvolvedores têm controle total sobre as propriedades e a aparência das anotações, permitindo a personalização para atender a diversas necessidades.
### Existe uma avaliação gratuita disponível para o GroupDocs.Annotation para .NET?
Sim, você pode explorar os recursos do GroupDocs.Annotation para .NET acessando o teste gratuito fornecido [link](https://releases.groupdocs.com/).
### Como posso obter suporte para quaisquer problemas ou dúvidas relacionadas ao GroupDocs.Annotation para .NET?
Para obter suporte e assistência, você pode visitar o fórum GroupDocs.Annotation [aqui](https://forum.groupdocs.com/c/annotation/10).
### Quais opções de licenciamento estão disponíveis para o GroupDocs.Annotation para .NET?
O GroupDocs.Annotation para .NET oferece diversas opções de licenciamento, incluindo licenças temporárias para fins de teste e licenças comerciais para ambientes de produção. Visite a página de compra. [aqui](https://purchase.groupdocs.com/buy) para mais detalhes.