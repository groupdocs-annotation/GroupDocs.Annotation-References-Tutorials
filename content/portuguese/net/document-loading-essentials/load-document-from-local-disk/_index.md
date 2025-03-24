---
title: Carregar documento do disco local
linktitle: Carregar documento do disco local
second_title: API GroupDocs.Annotation .NET
description: Desbloqueie o poder da anotação de documentos com GroupDocs.Annotation for .NET. Integre perfeitamente recursos de anotação em seus aplicativos .NET.
weight: 13
url: /pt/net/document-loading-essentials/load-document-from-local-disk/
---

# Carregar documento do disco local

## Introdução
Desbloquear o potencial da anotação de documentos nunca foi tão fácil com GroupDocs.Annotation for .NET. Essa ferramenta poderosa permite que os desenvolvedores integrem recursos robustos de anotação perfeitamente em seus aplicativos .NET. Neste guia abrangente, orientaremos você no processo de aproveitamento do GroupDocs.Annotation for .NET para anotar documentos passo a passo. Quer você seja um desenvolvedor experiente ou esteja apenas começando, este tutorial fornecerá o conhecimento necessário para aprimorar a colaboração em documentos e agilizar seu fluxo de trabalho.
## Pré-requisitos
Antes de mergulhar na anotação de documentos com GroupDocs.Annotation for .NET, certifique-se de ter os seguintes pré-requisitos:
1. Conhecimento básico de C#: A familiaridade com os fundamentos da linguagem de programação C# é essencial.
2. Instalação do GroupDocs.Annotation for .NET: Baixe e instale GroupDocs.Annotation for .NET em[aqui](https://releases.groupdocs.com/annotation/net/).
3. Ambiente de Desenvolvimento: Configure um ambiente de desenvolvimento com Visual Studio ou qualquer IDE compatível.

## Importar namespaces
Para começar a anotar documentos com GroupDocs.Annotation for .NET, importe os namespaces necessários para o seu projeto:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Etapa 1: carregar o documento do disco local
Primeiro, você precisa carregar o documento do seu disco local. Use o seguinte trecho de código:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Etapa 2: definir a área de anotação
A seguir, defina a área de anotação. Neste exemplo, criaremos uma AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Etapa 3: Salvar documento com anotações
Após anotar o documento, salve-o com as anotações:
```csharp
    annotator.Save(outputPath);
}
```
## Etapa 4: exibir mensagem de sucesso
Por fim, exiba uma mensagem de sucesso com o caminho de saída:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Concluindo, GroupDocs.Annotation for .NET fornece uma solução robusta para integração de recursos de anotação de documentos em seus aplicativos .NET. Seguindo este guia passo a passo, você pode anotar documentos sem esforço e aprimorar a colaboração em seus projetos.
## Perguntas frequentes
### Posso experimentar o GroupDocs.Annotation for .NET antes de comprar?
 Sim, você pode baixar uma avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Onde posso encontrar documentação para GroupDocs.Annotation for .NET?
 Você pode acessar a documentação[aqui](https://tutorials.groupdocs.com/annotation/net/).
### Como posso obter uma licença temporária do GroupDocs.Annotation for .NET?
 Você pode obter uma licença temporária em[aqui](https://purchase.groupdocs.com/temporary-license/).
### O suporte está disponível para GroupDocs.Annotation for .NET?
 Sim, você pode encontrar suporte no fórum GroupDocs[aqui](https://forum.groupdocs.com/c/annotation/10).
### Onde posso comprar GroupDocs.Annotation para .NET?
 Você pode comprar GroupDocs.Annotation para .NET[aqui](https://purchase.groupdocs.com/buy).