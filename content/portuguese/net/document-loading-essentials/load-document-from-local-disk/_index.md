---
"description": "Libere o poder da anotação em documentos com o GroupDocs.Annotation para .NET. Integre recursos de anotação aos seus aplicativos .NET com perfeição."
"linktitle": "Carregar documento do disco local"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Carregar documento do disco local"
"url": "/pt/net/document-loading-essentials/load-document-from-local-disk/"
type: docs
"weight": 13
---

# Carregar documento do disco local

## Introdução
Desbloquear o potencial da anotação em documentos nunca foi tão fácil com o GroupDocs.Annotation para .NET. Esta poderosa ferramenta permite que desenvolvedores integrem recursos robustos de anotação perfeitamente em seus aplicativos .NET. Neste guia completo, mostraremos passo a passo como utilizar o GroupDocs.Annotation para .NET para anotar documentos. Seja você um desenvolvedor experiente ou iniciante, este tutorial fornecerá o conhecimento necessário para aprimorar a colaboração em documentos e otimizar seu fluxo de trabalho.
## Pré-requisitos
Antes de começar a anotar documentos com o GroupDocs.Annotation for .NET, certifique-se de ter os seguintes pré-requisitos:
1. Conhecimento básico de C#: familiaridade com os fundamentos da linguagem de programação C# é essencial.
2. Instalação do GroupDocs.Annotation para .NET: Baixe e instale o GroupDocs.Annotation para .NET em [aqui](https://releases.groupdocs.com/annotation/net/).
3. Ambiente de desenvolvimento: configure um ambiente de desenvolvimento com o Visual Studio ou qualquer IDE compatível.

## Importar namespaces
Para começar a anotar documentos com o GroupDocs.Annotation for .NET, importe os namespaces necessários para o seu projeto:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Etapa 1: Carregar documento do disco local
Primeiro, você precisa carregar o documento do seu disco local. Use o seguinte trecho de código:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Etapa 2: Definir área de anotação
Em seguida, defina a área de anotação. Neste exemplo, criaremos uma AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Etapa 3: Salvar documento com anotações
Depois de anotar o documento, salve-o com as anotações:
```csharp
    annotator.Save(outputPath);
}
```
## Etapa 4: Exibir mensagem de sucesso
Por fim, exiba uma mensagem de sucesso com o caminho de saída:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Concluindo, o GroupDocs.Annotation para .NET oferece uma solução robusta para integrar recursos de anotação de documentos aos seus aplicativos .NET. Seguindo este guia passo a passo, você poderá anotar documentos sem esforço e aprimorar a colaboração em seus projetos.
## Perguntas frequentes
### Posso testar o GroupDocs.Annotation para .NET antes de comprar?
Sim, você pode baixar uma versão de teste gratuita em [aqui](https://releases.groupdocs.com/).
### Onde posso encontrar documentação do GroupDocs.Annotation para .NET?
Você pode acessar a documentação [aqui](https://tutorials.groupdocs.com/annotation/net/).
### Como posso obter uma licença temporária para o GroupDocs.Annotation para .NET?
Você pode obter uma licença temporária em [aqui](https://purchase.groupdocs.com/temporary-license/).
### Há suporte disponível para GroupDocs.Annotation para .NET?
Sim, você pode encontrar suporte no fórum do GroupDocs [aqui](https://forum.groupdocs.com/c/annotation/10).
### Onde posso comprar o GroupDocs.Annotation para .NET?
Você pode comprar o GroupDocs.Annotation para .NET [aqui](https://purchase.groupdocs.com/buy).