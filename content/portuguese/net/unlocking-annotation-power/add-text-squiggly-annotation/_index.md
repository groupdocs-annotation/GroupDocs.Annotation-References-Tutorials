---
title: Adicionar anotação de texto ondulada ao documento
linktitle: Adicionar anotação de texto ondulada ao documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar facilmente anotações de texto onduladas a documentos usando Groupdocs.Annotation for .NET. Aprimore os processos de colaboração e revisão de documentos.
type: docs
weight: 25
url: /pt/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## Introdução

Groupdocs.Annotation for .NET é uma biblioteca versátil que permite aos desenvolvedores integrar recursos robustos de anotação em seus aplicativos .NET sem esforço. Esteja você trabalhando com PDFs, documentos do Word ou outros formatos de arquivo populares, Groupdocs.Annotation oferece uma solução perfeita para anotar e aprimorar a colaboração em documentos.

## Pré-requisitos

Antes de mergulhar no tutorial, certifique-se de ter os seguintes pré-requisitos em vigor:

## Importar namespaces

Certifique-se de importar os namespaces necessários para acessar as funcionalidades fornecidas pelo Groupdocs.Annotation for .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Agora que cobrimos os pré-requisitos, vamos dividir o processo de adição de anotações onduladas de texto em várias etapas.

## Etapa 1: definir o caminho de saída

Defina o caminho onde o documento anotado será salvo.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Etapa 2: inicializar o anotador

Inicialize o objeto Annotator fornecendo o caminho do documento de entrada.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código da anotação vai aqui
}
```

## Etapa 3: criar uma anotação ondulada

Crie um objeto SquigglyAnnotation e especifique suas propriedades.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

## Etapa 4: adicionar anotação

Adicione a anotação ondulada criada ao documento.

```csharp
annotator.Add(squiggly);
```

## Etapa 5: Salvar documento

Salve o documento anotado no caminho de saída especificado.

```csharp
annotator.Save(outputPath);
```

## Etapa 6: Exibir confirmação

Exibe uma mensagem confirmando o salvamento bem-sucedido do documento anotado.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão

Concluindo, Groupdocs.Annotation for .NET fornece aos desenvolvedores um conjunto robusto de ferramentas para integrar perfeitamente funcionalidades de anotação de documentos em seus aplicativos .NET. Seguindo este guia passo a passo, você pode adicionar facilmente anotações de texto onduladas aos seus documentos, aprimorando os processos de colaboração e revisão de documentos.

## Perguntas frequentes

### P: O Groupdocs.Annotation pode oferecer suporte a anotações em vários formatos de arquivo?

R: Sim, Groupdocs.Annotation suporta anotações em uma ampla variedade de formatos de arquivo, incluindo PDFs, documentos do Word, planilhas do Excel e muito mais.

### P: O Groupdocs.Annotation é compatível com aplicativos de desktop e web?

R: Absolutamente! Groupdocs.Annotation pode ser perfeitamente integrado em aplicativos de desktop e web, oferecendo flexibilidade e versatilidade.

### P: Há alguma opção de licenciamento disponível para Groupdocs.Annotation?

R: Sim, o Groupdocs.Annotation oferece opções de licenciamento flexíveis adaptadas às necessidades individuais ou empresariais, incluindo licenças temporárias para fins de avaliação.

### P: As anotações criadas usando Groupdocs.Annotation podem ser personalizadas?

R: Certamente! Groupdocs.Annotation oferece amplas opções de personalização para anotações, permitindo que os desenvolvedores adaptem as anotações aos seus requisitos específicos.

### P: O Groupdocs.Annotation oferece suporte e documentação para desenvolvedores?

R: De fato! Groupdocs.Annotation fornece documentação abrangente e fóruns de suporte dedicados para ajudar os desenvolvedores a utilizar seus recursos de maneira eficaz.