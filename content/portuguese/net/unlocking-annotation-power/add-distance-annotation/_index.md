---
"description": "Aprenda a adicionar anotações de distância a documentos usando o GroupDocs.Annotation para .NET. Aprimore a colaboração e a comunicação sem esforço."
"linktitle": "Adicionar anotação de distância ao documento"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Adicionar anotação de distância ao documento"
"url": "/pt/net/unlocking-annotation-power/add-distance-annotation/"
"weight": 12
---

# Adicionar anotação de distância ao documento

## Introdução
Neste tutorial, você aprenderá a adicionar uma anotação de distância a um documento usando o GroupDocs.Annotation para .NET. Siga estes passos para concluir a tarefa:
## Pré-requisitos

Certifique-se de ter os seguintes pré-requisitos antes de prosseguir:

- Biblioteca GroupDocs.Annotation para .NET: Baixe e instale a biblioteca GroupDocs.Annotation para .NET em [este link](https://releases.groupdocs.com/annotation/net/).
- Documento a ser anotado: prepare o documento (por exemplo, PDF) ao qual você deseja adicionar a anotação de distância.
- Ambiente de desenvolvimento: configure seu ambiente de desenvolvimento com o Visual Studio ou qualquer outro IDE de sua escolha.

## Importar namespaces

Antes de começar, certifique-se de incluir os namespaces necessários no seu código. Esses namespaces são essenciais para acessar as classes e métodos necessários.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Etapa 1: Inicializar o Annotator

Comece inicializando o `Annotator` objeto com o caminho para o documento que você deseja anotar.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código de anotação irá aqui
}
```

## Etapa 2: Criar anotação de distância

Agora, crie um `DistanceAnnotation` objeto e configurar suas propriedades, como dimensões da caixa, mensagem, opacidade, cor da caneta, etc.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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

## Etapa 3: Adicionar anotação

Adicione a anotação de distância criada ao documento usando o `Add` método do objeto anotador.

```csharp
annotator.Add(distance);
```

## Etapa 4: Salvar documento

Salve o documento anotado no local desejado no seu sistema.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Etapa 5: Confirmação de exibição

Por fim, exiba uma mensagem confirmando o salvamento bem-sucedido do documento anotado.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão

Adicionar anotações de distância a documentos usando o GroupDocs.Annotation para .NET é um processo simples. Seguindo os passos descritos neste tutorial, você pode aprimorar seus documentos com anotações valiosas, facilitando a colaboração e a comunicação.

## Perguntas frequentes

### P: Posso personalizar a aparência da anotação de distância?

R: Sim, você pode personalizar várias propriedades, como cor, opacidade, estilo de linha, etc., para atender às suas necessidades.

### P: O GroupDocs.Annotation suporta anotações em diferentes tipos de documentos?

R: Sim, o GroupDocs.Annotation suporta anotações em uma ampla variedade de formatos de documentos, incluindo PDF, Word, Excel, PowerPoint e muito mais.

### P: Existe um teste gratuito disponível para o GroupDocs.Annotation?

R: Sim, você pode acessar uma avaliação gratuita do GroupDocs.Annotation em [este link](https://releases.groupdocs.com/).

### P: Onde posso encontrar a documentação do GroupDocs.Annotation para .NET?

R: Você pode consultar a documentação detalhada disponível [aqui](https://tutorials.groupdocs.com/annotation/net/).

### P: Como posso obter suporte ou assistência com o GroupDocs.Annotation?

R: Você pode buscar suporte e assistência no fórum da comunidade GroupDocs.Annotation [aqui](https://forum.groupdocs.com/c/annotation/10).