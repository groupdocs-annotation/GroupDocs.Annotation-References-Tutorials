---
"description": "Aprenda a adicionar anotações de redação de texto a documentos PDF usando o GroupDocs.Annotation para .NET. Proteja informações confidenciais sem esforço."
"linktitle": "Adicionar anotação de redação de texto ao documento"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Adicionar anotação de redação de texto ao documento"
"url": "/pt/net/unlocking-annotation-power/add-text-redaction-annotation/"
type: docs
"weight": 23
---

# Adicionar anotação de redação de texto ao documento

## Introdução
Adicionar uma anotação de redação de texto a um documento pode ser uma etapa crucial para gerenciar informações confidenciais com segurança. O GroupDocs.Annotation para .NET oferece uma solução robusta para isso sem complicações. Neste tutorial, guiaremos você pelo processo de adicionar uma anotação de redação de texto ao seu documento, passo a passo.
## Pré-requisitos
Antes de começar, certifique-se de que você tenha os seguintes pré-requisitos:
1. GroupDocs.Annotation para .NET: Certifique-se de ter instalado a biblioteca GroupDocs.Annotation para .NET. Você pode baixá-la do site [site](https://releases.groupdocs.com/annotation/net/).
2. Ambiente de desenvolvimento: configure um ambiente de desenvolvimento com um IDE compatível com .NET, como o Visual Studio.

## Importando namespaces
Primeiro, vamos importar os namespaces necessários para o nosso projeto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Etapa 1: Definir o caminho de saída
Defina o caminho de saída onde deseja salvar o documento anotado. Certifique-se de que ele seja acessível e gravável.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: Inicializar o Annotator
Inicialize o anotador com o caminho do documento de entrada. Substituir `"input.pdf"` com o caminho para seu documento.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código de anotação irá aqui
}
```
## Etapa 3: Criar anotação de redação de texto
Criar um `TextRedactionAnnotation` objeto com as propriedades necessárias, como `PageNumber`, `FontColor`, e `Points`. Personalize a anotação conforme suas necessidades.
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
## Etapa 5: Verifique a saída
Por fim, confirme se o documento foi salvo com sucesso no caminho de saída especificado.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Neste tutorial, explicamos o processo de adição de uma anotação de redação de texto a um documento usando o GroupDocs.Annotation para .NET. Com essas etapas, agora você pode gerenciar informações confidenciais em seus documentos com segurança.
## Perguntas frequentes
### Posso personalizar a aparência da anotação de redação do texto?
Sim, você pode personalizar várias propriedades, como cor da fonte, cor de preenchimento e opacidade, para atender às suas necessidades.
### Existe uma versão de teste disponível antes da compra?
Sim, você pode acessar uma versão de teste gratuita no [site](https://releases.groupdocs.com/).
### Como posso obter suporte se tiver algum problema?
Você pode obter suporte no fórum da comunidade GroupDocs.Annotation [aqui](https://forum.groupdocs.com/c/annotation/10).
### Preciso de uma licença temporária para fins de testes?
Sim, você pode obter uma licença temporária na [página de compra](https://purchase.groupdocs.com/temporary-license/) para testes.
### Posso adicionar várias anotações a um único documento?
Com certeza, o GroupDocs.Annotation permite que você adicione vários tipos de anotações e múltiplas instâncias a um único documento.