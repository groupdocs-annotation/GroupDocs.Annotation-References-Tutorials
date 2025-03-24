---
title: Adicionar anotação de redação de texto ao documento
linktitle: Adicionar anotação de redação de texto ao documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotações de redação de texto a documentos PDF usando GroupDocs.Annotation for .NET. Proteja informações confidenciais sem esforço.
weight: 23
url: /pt/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Introdução
Adicionar uma anotação de redação de texto a um documento pode ser uma etapa crucial no gerenciamento seguro de informações confidenciais. GroupDocs.Annotation for .NET fornece uma solução robusta para conseguir isso perfeitamente. Neste tutorial, orientaremos você passo a passo no processo de adição de uma anotação de redação de texto ao seu documento.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos em vigor:
1.  GroupDocs.Annotation for .NET: certifique-se de ter instalado a biblioteca GroupDocs.Annotation for .NET. Você pode baixá-lo no[local na rede Internet](https://releases.groupdocs.com/annotation/net/).
2. Ambiente de desenvolvimento: configure um ambiente de desenvolvimento com um IDE compatível com .NET, como o Visual Studio.

## Importando Namespaces
Primeiramente, vamos importar os namespaces necessários para o nosso projeto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Etapa 1: definir o caminho de saída
Defina o caminho de saída onde deseja salvar o documento anotado. Certifique-se de que esteja acessível e gravável.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: inicializar o anotador
 Inicialize o anotador com o caminho do documento de entrada. Substituir`"input.pdf"` com o caminho para o seu documento.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código da anotação irá aqui
}
```
## Etapa 3: criar anotação de redação de texto
 Criar uma`TextRedactionAnnotation`objeto com as propriedades necessárias, como`PageNumber`, `FontColor` , e`Points`. Personalize a anotação de acordo com suas necessidades.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Etapa 4: adicionar anotação e salvar
Adicione a anotação criada ao documento usando o anotador e salve o documento anotado no caminho de saída especificado.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Etapa 5: verificar o resultado
Finalmente, confirme se o documento foi salvo com sucesso no caminho de saída especificado.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Neste tutorial, percorremos o processo de adição de uma anotação de redação de texto a um documento usando GroupDocs.Annotation for .NET. Com essas etapas, agora você pode gerenciar com segurança informações confidenciais em seus documentos.
## Perguntas frequentes
### Posso personalizar a aparência da anotação de redação de texto?
Sim, você pode personalizar várias propriedades, como cor da fonte, cor de preenchimento e opacidade, para atender às suas necessidades.
### Existe uma versão de teste disponível antes de comprar?
 Sim, você pode acessar uma versão de avaliação gratuita no[local na rede Internet](https://releases.groupdocs.com/).
### Como posso obter suporte se encontrar algum problema?
 Você pode obter suporte no fórum da comunidade GroupDocs.Annotation[aqui](https://forum.groupdocs.com/c/annotation/10).
### Preciso de uma licença temporária para fins de teste?
 Sim, você pode obter uma licença temporária do[página de compra](https://purchase.groupdocs.com/temporary-license/)para teste.
### Posso adicionar várias anotações a um único documento?
Com certeza, GroupDocs.Annotation permite adicionar vários tipos de anotações e múltiplas instâncias a um único documento.