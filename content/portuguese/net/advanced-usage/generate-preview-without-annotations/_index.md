---
title: Gerar visualização sem anotações
linktitle: Gerar visualização sem anotações
second_title: API GroupDocs.Annotation .NET
description: Aprimore a colaboração e anotação de documentos em aplicativos .NET usando GroupDocs.Annotation for .NET. Anote, marque e revise documentos facilmente com esta poderosa biblioteca.
weight: 13
url: /pt/net/advanced-usage/generate-preview-without-annotations/
---
## Introdução
Na era digital de hoje, a colaboração eficiente em documentos é fundamental para a produtividade e o sucesso. Esteja você trabalhando em um projeto com membros da equipe espalhados por todo o mundo ou colaborando com clientes em contratos importantes, a capacidade de anotar e revisar documentos perfeitamente é crucial. Com GroupDocs.Annotation for .NET, você pode levar a colaboração de documentos para o próximo nível, permitindo fácil anotação, marcação e revisão diretamente em seus aplicativos .NET.
## Pré-requisitos
Antes de mergulhar no mundo da anotação de documentos com GroupDocs.Annotation for .NET, existem alguns pré-requisitos que você precisa ter em vigor:
### 1. Instale GroupDocs.Annotation para .NET
 Em primeiro lugar, você precisará baixar e instalar GroupDocs.Annotation for .NET. Você pode encontrar o link para download[aqui](https://releases.groupdocs.com/annotation/net/). Siga as instruções de instalação fornecidas para configurar a biblioteca em seu ambiente .NET.
### 2. Obtenha uma licença (opcional)
Embora GroupDocs.Annotation for .NET ofereça uma avaliação gratuita, você pode considerar a obtenção de uma licença para acesso total aos seus recursos. Você pode comprar uma licença[aqui](https://purchase.groupdocs.com/buy) ou solicite uma licença temporária[aqui](https://purchase.groupdocs.com/temporary-license/) para fins de teste.
### 3. Familiaridade com desenvolvimento em C# e .NET
Para aproveitar ao máximo o GroupDocs.Annotation for .NET, é útil ter uma compreensão básica do desenvolvimento em C# e .NET. Isso permitirá que você integre perfeitamente a biblioteca aos seus aplicativos e fluxos de trabalho existentes.
### 4. Instale um visualizador de PDF
Como o GroupDocs.Annotation for .NET funciona com documentos PDF, você precisará de um visualizador de PDF instalado em seu sistema para visualizar documentos anotados. Adobe Acrobat Reader ou qualquer outro visualizador de PDF será suficiente.

## Importar namespaces
Antes de começar a anotar documentos, você precisará importar os namespaces necessários para o seu projeto .NET. Isso permite acessar as classes e métodos fornecidos por GroupDocs.Annotation for .NET.

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

Agora que você configurou tudo, vamos gerar uma visualização de um documento sem nenhuma anotação. Siga estas etapas para fazer isso:
## Etapa 1: inicializar o anotador
 Primeiro, crie uma instância do`Annotator` class, passando o caminho para o documento que deseja anotar.
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```
## Etapa 2: configurar opções de visualização
A seguir, configure as opções de visualização de acordo com suas necessidades. Você pode especificar os números de página que deseja incluir na visualização, o formato de visualização (por exemplo, PNG) e se deseja renderizar anotações.
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```
## Etapa 3: gerar visualização
 Por fim, gere a visualização usando o`GeneratePreview` método do`Document` class, passando as opções de visualização configuradas.
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Seguindo estas etapas simples, você pode gerar uma visualização de um documento sem anotações usando GroupDocs.Annotation for .NET.

## Conclusão
Concluindo, GroupDocs.Annotation for .NET fornece uma solução poderosa para colaboração e anotação de documentos em aplicativos .NET. Seguindo as etapas descritas neste tutorial, você pode integrar perfeitamente recursos de anotação de documentos em seus projetos, melhorando a colaboração e a produtividade.
## Perguntas frequentes
### P: Posso usar GroupDocs.Annotation for .NET com outros formatos de documento além de PDF?
Sim, GroupDocs.Annotation for .NET oferece suporte a uma variedade de formatos de documentos, incluindo DOCX, XLSX, PPTX e muito mais.
### P: O GroupDocs.Annotation for .NET é compatível com o .NET Core?
Sim, GroupDocs.Annotation for .NET é compatível com ambientes .NET Framework e .NET Core.
### P: O GroupDocs.Annotation for .NET oferece ferramentas de anotação personalizáveis?
Sim, o GroupDocs.Annotation for .NET fornece uma variedade de ferramentas de anotação que podem ser personalizadas para atender às suas necessidades específicas.
### P: Posso integrar o GroupDocs.Annotation for .NET em meus aplicativos da web?
Sim, o GroupDocs.Annotation for .NET pode ser integrado a aplicativos desktop e web, fornecendo recursos contínuos de colaboração de documentos.
### P: Existe um fórum da comunidade onde posso obter suporte e assistência com GroupDocs.Annotation for .NET?
 Sim, você pode encontrar suporte e assistência no fórum GroupDocs.Annotation[aqui](https://forum.groupdocs.com/c/annotation/10).