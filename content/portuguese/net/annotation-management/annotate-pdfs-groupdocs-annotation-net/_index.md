---
categories:
- PDF Processing
date: '2026-05-26'
description: Aprenda como criar um sistema de revisão de documentos usando o GroupDocs
  Annotation para .NET. Tutorial passo a passo cobre configuração, tipos de anotação,
  otimização de desempenho e solução de problemas para desenvolvedores C#.
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: Guia de Anotação PDF .NET
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: 'Criar Sistema de Revisão de Documentos: Guia de Anotação PDF .NET'
type: docs
url: /pt/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# Criar Sistema de Revisão de Documentos: Guia de Anotação PDF .NET

Se você precisa **criar um sistema de revisão de documentos** que permite aos usuários adicionar comentários, realces e formas a PDFs diretamente de uma aplicação .NET, você está no lugar certo. GroupDocs.Annotation para .NET elimina a dor de cabeça do manuseio de PDF em baixo nível enquanto oferece controle granular sobre cada tipo de anotação. Neste guia você verá como configurar a biblioteca, adicionar anotações de área, elipse e texto, filtrar o que é salvo e manter o desempenho ágil mesmo com arquivos de várias centenas de páginas.

## Respostas Rápidas
- **Qual biblioteca lida com anotação de PDF em .NET?** GroupDocs.Annotation for .NET.
- **Posso adicionar realces, círculos e comentários programaticamente?** Sim – use os objetos AreaAnnotation, EllipseAnnotation e TextAnnotation.
- **É necessária uma licença para produção?** Uma licença válida do GroupDocs é obrigatória para qualquer implantação em produção.
- **Qual o tamanho máximo de PDF que pode ser processado?** Até 500 MB podem ser manipulados sem carregar o arquivo inteiro na memória.
- **Isso me ajudará a criar um sistema de revisão de documentos?** Absolutamente – você pode salvar em lote, filtrar e versionar anotações para revisores.

## O que é um sistema de revisão de documentos?

Um **sistema de revisão de documentos** é uma solução de software que permite que múltiplas partes interessadas anotem, comentem e aprovem arquivos PDF em um fluxo de trabalho coordenado. Ele centraliza o feedback, rastreia alterações e frequentemente exporta uma versão limpa para aprovação final.

## Por que usar GroupDocs Annotation para .NET para criar um sistema de revisão de documentos?

GroupDocs Annotation suporta **mais de 30 tipos de anotação**, processa PDFs de até **500 MB** de tamanho e funciona em **.NET Framework 4.6.1+**, **.NET Core 2.0+** e **.NET 6+**. Sua API permite adicionar, remover e filtrar anotações sem jamais tocar na estrutura interna do PDF, o que acelera o desenvolvimento e reduz bugs.

## Pré-requisitos e Configuração do Ambiente

Antes de escrever qualquer código, certifique‑se de que seu ambiente de desenvolvimento atenda aos seguintes critérios:

- **IDE:** Visual Studio 2019 ou mais recente, ou VS Code com a extensão C#.
- **Framework de Destino:** .NET Framework 4.6.1 + ou .NET Core 2.0 + (nós recomendamos .NET 6 para novos projetos).
- **Acesso ao NuGet:** Capacidade de instalar pacotes a partir do nuget.org.
- **PDFs de Exemplo:** Pelo menos um PDF multipágina para testar a colocação de anotações.
- **Memória e Disco:** Mínimo de 4 GB de RAM e espaço livre suficiente em disco para arquivos temporários (o processamento de anotações pode gerar streams temporários).

### Práticas de Desenvolvimento Recomendadas
- Mantenha sua solução sob controle de versão (Git) para que você possa reverter alterações relacionadas a anotações.
- Use uma pasta dedicada **Annotations** em seu projeto para armazenar arquivos de configuração e chaves de licença.
- Habilite **nullable reference types** (`<Nullable>enable</Nullable>`) para capturar potenciais bugs de referência nula cedo.

## Começando: Instalação do GroupDocs.Annotation

### Métodos de Instalação

**Opção 1: Console do Gerenciador de Pacotes NuGet**  
Execute o seguinte comando no Console do Gerenciador de Pacotes:  

`Install-Package GroupDocs.Annotation`

**Opção 2: .NET CLI (recomendado para desenvolvimento multiplataforma)**  
Execute em um terminal:  

`dotnet add package GroupDocs.Annotation`

**Opção 3: Interface do Gerenciador de Pacotes do Visual Studio**  
- Clique com o botão direito no projeto → **Gerenciar Pacotes NuGet**  
- Pesquise por **GroupDocs.Annotation**  
- Clique em **Instalar** na versão estável mais recente  

Todos os três métodos instalam o mesmo binário; escolha o que corresponde ao seu fluxo de trabalho.

### Configuração de Licença

GroupDocs requer uma licença válida para qualquer uso em produção. Você tem três opções:

- **Teste Gratuito:** avaliação de 30 dias com conjunto completo de recursos.  
- **Licença Temporária:** avaliação estendida para desenvolvimento e testes.  
- **Licença Comercial:** uso ilimitado em ambientes de produção.  

A classe `License` carrega e aplica um arquivo de licença GroupDocs para habilitar a funcionalidade completa. Você pode obter uma licença na [página de compra do GroupDocs](https://purchase.groupdocs.com/buy). Após receber o arquivo `.lic`, coloque-o em uma pasta que sua aplicação possa ler e aponte a classe `License` para ele na inicialização.

### Verificação da Configuração Inicial

Crie um pequeno programa de console que carregue um PDF e escreva o número de páginas no console. Se o programa executar sem lançar exceção, a biblioteca está corretamente instalada e licenciada.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **Nota:** O código acima é apenas para ilustração; você **não** precisa adicionar um bloco de código delimitado no artigo final, mas o snippet inline mostra o uso exato da API.

Se você vir a contagem de páginas impressa, está pronto para começar a adicionar anotações reais.

## Implementação Central: Adicionando Anotações a PDFs

### Definição Âncora – Annotator

A classe `Annotator` é o ponto de entrada para todas as operações de anotação de PDF no GroupDocs.Annotation para .NET. Ela carrega um PDF na memória, expõe métodos para adicionar, editar e recuperar anotações, e gerencia a gravação do documento modificado.

### Como adicionar anotações de área e elipse?

Carregue o PDF com `new Annotator(...)`, crie objetos `AreaAnnotation` e `EllipseAnnotation`, defina suas coordenadas e adicione-os à coleção do annotator. Finalmente, chame `Save` para persistir as alterações. Esse fluxo de trabalho permite que você destaque seções (área) ou circule gráficos importantes de forma programática em uma única operação atômica.

#### Etapa 1: Inicializar o Annotator
```csharp
var annotator = new Annotator("input.pdf");
```

#### Etapa 2: Criar um AreaAnnotation
`AreaAnnotation` representa uma área de destaque retangular em uma página PDF.  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### Etapa 3: Criar um EllipseAnnotation
`EllipseAnnotation` representa uma anotação de forma elíptica em uma página PDF.  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### Etapa 4: Adicionar Anotações em Lote
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**Dica Pro:** Adicionar anotações em uma lista e chamar `Add` uma única vez reduz a sobrecarga de I/O, especialmente quando você precisa inserir dezenas de marcas em muitas páginas.

### Como salvar anotações seletivas?

`SaveOptions` configura como o PDF anotado é salvo, incluindo quais tipos de anotação incluir. GroupDocs.Annotation permite filtrar quais tipos de anotação são gravados no arquivo de saída. Crie uma instância `SaveOptions`, defina a coleção `AnnotationTypes` para os tipos que deseja manter e passe as opções para `Save`. Isso é perfeito para gerar PDFs apenas para revisores ou remover notas temporárias antes de arquivar.

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## Cenários de Implementação no Mundo Real

### Cenário 1: Fluxo de Trabalho de Revisão de Documentos

Vários revisores adicionam anotações **Area**, **Ellipse** e **Text**. Após a rodada de revisão, você gera três PDFs:
1. Versão completa com todos os comentários.  
2. Versão apenas para revisores (filtra notas internas).  
3. Versão limpa para aprovação final (mantém apenas realces).

### Cenário 2: Geração Automatizada de Relatórios

Seu backend processa relatórios de vendas diários, destacando automaticamente métricas chave com anotações de área e circulando gráficos fora do padrão com anotações de elipse. Os PDFs gerados são então enviados por e‑mail aos interessados sem qualquer intervenção manual.

### Cenário 3: Documentos Legais Colaborativos

Escritórios de advocacia frequentemente precisam separar comentários de sócios das notas de associados juniores. Ao marcar anotações com metadados personalizados e usar salvamento seletivo, você pode produzir um PDF de revisão para sócios que oculta observações juniores, simplificando o controle de versões.

## Otimização de Desempenho para Uso em Produção

### Como gerenciar memória ao anotar PDFs grandes?

`LoadOptions` permite especificar como um PDF é carregado, como intervalos de páginas ou senhas. Quando um PDF excede 100 MB, evite carregar o arquivo inteiro usando o construtor `LoadOptions` que aceita um intervalo de páginas. Processar páginas em lotes, descartar cada instância `Annotator` com um bloco `using` e limpar arquivos temporários após cada lote. Essa abordagem mantém o uso máximo de memória abaixo de 200 MB mesmo para documentos de 500 páginas.

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### Melhores Práticas de Gerenciamento de Memória
- **Sempre envolva `Annotator` em uma instrução `using`** para garantir a liberação de recursos não gerenciados.  
- **Processar anotações em lote**: colecione todas as anotações de um documento e então chame `Add` uma única vez.  
- **Evite carregar PDFs completos** quando você só precisa modificar um subconjunto de páginas; use `LoadOptions.PageNumbers`.

### Estratégias para Manipulação de Arquivos Grandes
1. **Processamento página a página** – Carregue, anote e salve uma página de cada vez.  
2. **Saída em streaming** – Direcione o método `Save` para um `MemoryStream` para evitar gravações intermediárias em disco.  
3. **Limpeza de arquivos temporários** – Exclua quaisquer arquivos temporários criados pelo annotator após cada operação.

### Considerações para Processamento Concorrente
- **Segurança de thread:** Instâncias de `Annotator` não são thread‑safe. Crie uma instância separada por thread.  
- **Limitação de recursos:** Limite trabalhos concorrentes ao número de núcleos de CPU para evitar saturação da CPU.  
- **API assíncrona:** `SaveAsync` salva o documento anotado de forma assíncrona, retornando um Task, o que é útil em ambientes ASP.NET Core.

## Solução de Problemas Comuns

### Problema 1: Erros “File Not Found”

**Resposta direta:** Verifique se o caminho do arquivo passado para `new Annotator(...)` é absoluto ou relativo corretamente à assembly em execução, e assegure que o processo da aplicação tenha permissões de leitura para esse local. Se o arquivo estiver em um compartilhamento de rede, mapeie o compartilhamento ou use caminhos UNC.

**Correções típicas:**  
- Use `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")`.  
- Conceda à identidade do pool de aplicativos IIS permissões de leitura/gravação na pasta.

### Problema 2: Anotações aparecem em locais incorretos

**Resposta direta:** Certifique‑se de que está usando o mesmo sistema de coordenadas (origem superior‑esquerda) e que o DPI da página corresponde aos valores fornecidos. Recupere o tamanho da página via `annotator.GetPageInfo(pageNumber)` e calcule as coordenadas relativas a esse tamanho.

**Correções típicas:**  
- Multiplique as coordenadas pelo fator de escala da página se o PDF foi criado com DPI não padrão.  
- Verifique novamente se não está misturando pontos (1/72 polegada) com pixels.

### Problema 3: Problemas de desempenho com arquivos grandes

**Resposta direta:** Troque para carregamento por intervalo de páginas, processe anotações em lotes e descarte cada instância `Annotator` prontamente. Também habilite a opção `MemoryCache` em `LoadOptions` para reutilizar buffers entre operações.

**Correções típicas:**  
- Defina `LoadOptions.UseMemoryCache = true`.  
- Processar arquivos de forma assíncrona com `await annotator.SaveAsync(...)`.

### Problema 4: Erros relacionados à licença

**Resposta direta:** Coloque o arquivo `.lic` em uma pasta que a aplicação possa ler e chame `License license = new License(); license.SetLicense("path/to/license.lic");` antes de qualquer outra chamada ao GroupDocs. Verifique se a versão da licença corresponde à versão da biblioteca que você está usando.

**Correções típicas:**  
- Verifique se o arquivo de licença não está corrompido (compare o tamanho do arquivo).  
- Certifique‑se de que não está misturando uma licença de avaliação com uma comercial no mesmo ambiente.

## Dicas Avançadas e Melhores Práticas

### Gerenciamento de Cores

Cores consistentes melhoram a legibilidade para os revisores. Defina uma paleta (por exemplo, Amarelo para realces, Vermelho para questões críticas) e armazene-a em uma classe auxiliar estática. Lembre‑se de usar cores de alto contraste para acessibilidade e de adicionar uma página de legenda no PDF como referência.

### Padrões de Tratamento de Erros

Envolva todas as chamadas de anotação em blocos try‑catch que capturem especificamente `GroupDocs.Annotation.Exceptions.AnnotationException`. Registre a mensagem da exceção, o stack trace e o nome do PDF para auxiliar na depuração.

### Estratégias de Teste

- **Testes Unitários:** Use um PDF pequeno com dimensões conhecidas, adicione uma anotação e verifique que `GetAnnotations()` retorna as coordenadas esperadas.  
- **Testes de Integração:** Execute o fluxo completo em PDFs de 1 página a 200 páginas e verifique que o tempo de processamento permanece abaixo de 5 segundos para arquivos menores que 50 MB.  
- **Testes de Carga:** Simule 50 solicitações de anotação simultâneas usando uma ferramenta como k6 ou Apache JMeter e monitore CPU/memória.

## Perguntas Frequentes

**Q: Como lidar com PDFs com tamanhos de página diferentes?**  
A: O GroupDocs lê automaticamente as dimensões de cada página. Ao posicionar anotações, sempre consulte `annotator.GetPageInfo(pageNumber)` e calcule as coordenadas com base na largura e altura daquela página.

**Q: Posso anotar PDFs protegidos por senha?**  
A: Sim. Use o construtor `LoadOptions` que aceita uma string de senha, por exemplo, `new LoadOptions { Password = "secret" }`, e passe-o ao construtor `Annotator`.

**Q: Qual é o número máximo de anotações que posso adicionar a um único PDF?**  
A: Não há um limite rígido, mas o desempenho degrada após algumas milhares de anotações. Para conjuntos de anotações muito grandes, agrupe-as em seções lógicas e processe cada seção separadamente.

**Q: Como remover anotações específicas programaticamente?**  
A: Recupere o `Id` da anotação via `GetAnnotations()`, então chame `Delete(id)` ou crie uma instância `SaveOptions` que exclua o `AnnotationType` indesejado.

**Q: Posso personalizar a aparência da anotação além das cores?**  
A: Absolutamente. Você pode definir opacidade, espessura da borda, estilo de traço e até incorporar ícones SVG personalizados para anotações de selo.

**Q: O que acontece se eu tentar anotar um PDF escaneado (baseado em imagem)?**  
A: As anotações serão renderizadas como objetos sobrepostos sobre a imagem da página. Elas não modificam os dados raster subjacentes, portanto o PDF permanece pesquisável se houver camadas OCR.

**Q: Como lidar com PDFs muito grandes sem ficar sem memória?**  
A: Processe o documento página por página usando `LoadOptions.PageNumbers`, descarte cada instância `Annotator` imediatamente após o uso e habilite salvamentos em streaming para um `MemoryStream` para evitar picos de disco.

## Integração com Aplicações ASP.NET

Ao expor a funcionalidade de anotação através de uma API web, siga o padrão a seguir:

1. **O controlador recebe o stream do PDF** do cliente.  
2. **Valide o tamanho do arquivo** (rejeite > 200 MB a menos que tenha tratamento especial).  
3. **Instancie `Annotator` dentro de um bloco `using`** para garantir a liberação.  
4. **Aplique anotações** com base na carga JSON que descreve o tipo de anotação, coordenadas e texto.  
5. **Salve em um local temporário**, então faça o streaming do resultado de volta ao cliente com o cabeçalho `Content‑Disposition` apropriado.

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## Recursos Adicionais
- [Página de compra do GroupDocs](https://purchase.groupdocs.com/buy)  
- [Comprar GroupDocs](https://purchase.groupdocs.com/buy)  
- [Documentação do GroupDocs Annotation](https://docs.groupdocs.com/annotation/net/)  
- [Referência da API do GroupDocs](https://reference.groupdocs.com/annotation/net/)  
- [Últimas versões](https://releases.groupdocs.com/annotation/net/)  
- [Experimente o GroupDocs gratuitamente](https://releases.groupdocs.com/annotation/net/)  
- [Solicitar uma Licença Temporária](https://purchase.groupdocs.com/temporary-license/)  
- [Fórum do GroupDocs](https://forum.groupdocs.com/c/annotation/)

## Conclusão e Próximos Passos

Agora você tem um **roteiro completo e pronto para produção** para construir um **sistema de revisão de documentos** alimentado pelo GroupDocs.Annotation para .NET. Você aprendeu como configurar a biblioteca, adicionar anotações de área, elipse e texto, filtrar salvamentos e manter o uso de memória baixo mesmo com PDFs massivos.

**Próximas ações que você pode realizar hoje:**  

1. **Experimentar** com tipos adicionais de anotação como `ArrowAnnotation` e `StampAnnotation`.  
2. **Integrar** o fluxo de trabalho em sua API ASP.NET Core existente ou aplicação desktop WPF.  
3. **Explorar** a referência completa da API para descobrir recursos avançados como versionamento de anotações e metadados personalizados.  
4. **Participar** dos fóruns da comunidade GroupDocs para suporte entre pares e ficar atualizado sobre novas versões.

---

**Última atualização:** 2026-05-26  
**Testado com:** GroupDocs.Annotation 23.11 para .NET  
**Autor:** GroupDocs  

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```

```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```

```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```

```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```

```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```

```csharp
annotator.Save(outputPath, saveOptions);
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```

```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```

```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```

```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```

```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```

```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```

```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## Tutoriais Relacionados

- [Tutorial de GroupDocs Annotation .NET - Guia Completo para Gerenciamento de Documentos](/annotation/net/annotation-management/)
- [Tutoriais de Visualização de Documentos .NET - Guia Completo do GroupDocs.Annotation](/annotation/net/document-preview/)
- [Tutorial de Licença Metered do GroupDocs Annotation - Guia Completo de Configuração .NET](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)