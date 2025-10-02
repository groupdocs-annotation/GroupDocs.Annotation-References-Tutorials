---
"description": "Aprenda a adicionar Anotações de Ponto a PDFs usando o GroupDocs.Annotation para .NET. Guia passo a passo para uma integração perfeita."
"linktitle": "Adicionar anotação de ponto ao documento"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Adicionar anotação de ponto ao documento"
"url": "/pt/net/unlocking-annotation-power/add-point-annotation/"
type: docs
"weight": 17
---

# Adicionar anotação de ponto ao documento

## Introdução
O GroupDocs.Annotation para .NET é uma ferramenta poderosa que permite aos desenvolvedores adicionar vários tipos de anotações a documentos programaticamente. Neste tutorial, vamos nos concentrar em adicionar uma Anotação de Ponto a um documento usando C#.
## Pré-requisitos
Antes de começar, certifique-se de ter o seguinte:
1. Noções básicas de linguagem de programação C#.
2. Visual Studio instalado no seu sistema.
3. Biblioteca GroupDocs.Annotation para .NET instalada. Você pode baixá-la em [aqui](https://releases.groupdocs.com/annotation/net/).

## Importando namespaces necessários
Para começar, você precisa importar os namespaces necessários para o seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Etapa 1: Definir o caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Nesta etapa, definimos o caminho de saída onde o documento anotado será salvo.
## Etapa 2: Inicializar o Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Aqui, inicializamos o `Annotator` objeto com o documento de entrada ("input.pdf").
## Etapa 3: Criar anotação de ponto
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
Nesta etapa, criamos uma `PointAnnotation` objeto e especifique suas propriedades, como posição, mensagem, número de página e respostas.
## Etapa 4: Adicionar anotação
```csharp
annotator.Add(point);
```
Aqui, adicionamos a anotação de ponto criada ao documento.
## Etapa 5: Salvar documento
```csharp
annotator.Save(outputPath);
```
Por fim, salvamos o documento anotado no caminho de saída especificado.

## Conclusão
Neste tutorial, aprendemos como adicionar uma Anotação de Ponto a um documento usando o GroupDocs.Annotation para .NET. Com esta poderosa biblioteca, você pode aprimorar seus aplicativos de gerenciamento de documentos incorporando funcionalidades de anotação.
## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documento?
Sim, o GroupDocs.Annotation para .NET suporta uma ampla variedade de formatos de documentos, incluindo PDF, Microsoft Word, Excel, PowerPoint e muito mais.
### Posso personalizar a aparência das anotações?
Com certeza! O GroupDocs.Annotation para .NET oferece diversas opções para personalizar a aparência das anotações de acordo com as necessidades do seu aplicativo.
### Existe uma avaliação gratuita disponível para o GroupDocs.Annotation para .NET?
Sim, você pode aproveitar um teste gratuito em [aqui](https://releases.groupdocs.com/).
### Como posso obter suporte para quaisquer problemas ou dúvidas relacionadas ao GroupDocs.Annotation para .NET?
Você pode obter suporte no fórum GroupDocs.Annotation [aqui](https://forum.groupdocs.com/c/annotation/10).
### Posso obter uma licença temporária para fins de testes?
Sim, você pode obter uma licença temporária em [aqui](https://purchase.groupdocs.com/temporary-license/).