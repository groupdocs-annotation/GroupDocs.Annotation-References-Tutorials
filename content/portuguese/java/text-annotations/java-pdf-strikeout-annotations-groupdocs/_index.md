---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Aprenda como adicionar anotações de tachado a PDFs em Java usando o GroupDocs.
  Este tutorial passo a passo cobre configuração, código, solução de problemas e dicas
  de desempenho.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Guia de tachado de texto em PDF Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Como adicionar anotações de tachado a PDFs em Java – Guia completo do GroupDocs
type: docs
url: /pt/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Como Adicionar Anotações de Tachado a PDFs em Java

Já precisou riscar texto em um PDF programaticamente? Seja construindo um sistema de revisão de documentos, criando um fluxo de edição ou apenas precisando marcar texto para exclusão, **how to add strikeout** annotations in Java é uma habilidade prática que economiza tempo e reduz o esforço manual. Neste guia abrangente você descobrirá tudo o que precisa saber para implementar anotações de tachado com GroupDocs.Annotation para Java, desde a configuração do projeto até a otimização de desempenho.

## Respostas Rápidas
- **Qual é o primeiro passo?** Adicione a dependência Maven do GroupDocs.Annotation ao seu `pom.xml`.  
- **Como criar um tachado?** Instancie `Annotator`, defina `StrikeoutAnnotation` com pontos, configure cor/opacidade e, em seguida, chame `addAnnotation`.  
- **Posso adicionar comentários?** Sim, anexe um objeto `Comment` à anotação para colaboração.  
- **E se a anotação estiver fora do lugar?** Ajuste os pontos de coordenadas; o PDF usa um sistema de origem no canto inferior esquerdo.  
- **Existe um limite de tamanho de documento?** O GroupDocs processa PDFs com centenas de páginas sem carregar o arquivo inteiro na memória.

## O que é “how to add strikeout” em anotação de PDF?
A frase “how to add strikeout” refere‑se ao processo de desenhar programaticamente uma linha através do texto selecionado dentro de um documento PDF usando uma API de anotação. Em Java, o GroupDocs.Annotation fornece a classe dedicada `StrikeoutAnnotation` que lida com renderização, estilo e persistência das marcas de tachado.

## Por que usar GroupDocs para tachado de PDF em Java?
O GroupDocs.Annotation suporta **mais de 50 formatos de entrada e saída** — incluindo PDF, DOCX, XLSX, PPTX, HTML e tipos comuns de imagem — então você não fica preso a um único tipo de arquivo. Ele fornece uma API de alto nível que abstrai a estrutura de PDF de baixo nível, lidando automaticamente com incorporação de fontes, renderização de páginas e persistência de anotações, permitindo que os desenvolvedores se concentrem na lógica de negócios em vez dos detalhes internos do PDF.

## Pré-requisitos e Requisitos de Configuração

### Requisitos Essenciais
- **Java Development Kit (JDK):** Versão 8 ou superior (JDK 11+ recomendado para coleta de lixo otimizada).  
- **GroupDocs.Annotation for Java:** Integrado via Maven (veja o trecho Maven abaixo).  
- **IDE:** IntelliJ IDEA, Eclipse ou qualquer editor compatível com Java.

### Configuração de Dependências Maven
Adicione o seguinte bloco de dependência ao seu `pom.xml`:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/annotation/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>25.2</version>
    </dependency>
</dependencies>
```

**Pro Tip:** Sempre verifique a versão mais recente na página de releases do GroupDocs; versões mais novas adicionam recursos e corrigem bugs que podem afetar a renderização das anotações.

### Obtendo sua Licença
O GroupDocs.Annotation requer uma licença válida para uso em produção. Você tem três opções:

- **Teste Gratuito:** Baixe em [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)
- **Licença Temporária:** Solicite uma chave de desenvolvimento em [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Licença Completa:** Compre para produção em [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

O teste adiciona uma marca d'água sutil, então planeje seus testes adequadamente.

## Guia de Implementação Passo a Passo

### Entendendo os Componentes Principais
As definições a seguir fornecem um modelo mental rápido:

- **Annotator:** O objeto API principal que carrega um PDF e expõe métodos de anotação.  
- **StrikeoutAnnotation:** Representa a linha visual de tachado e suas opções de estilo.  
- **Point:** Um par de coordenadas (X, Y) que indica à biblioteca onde a linha começa e termina.  
- **Comment:** Texto opcional anexado a uma anotação para colaboração.

### Etapa 1: Configurando os Caminhos de Arquivo
Defina os locais do seu PDF de origem e do arquivo de destino. Caminhos incorretos são uma fonte comum de erros “File Not Found”.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** Certifique‑se de que o diretório de saída exista e seja gravável; o GroupDocs não criará pastas ausentes automaticamente.

### Etapa 2: Inicializar o Annotator
Crie uma instância `Annotator` que carrega o PDF na memória.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** A biblioteca analisa a estrutura do PDF, constrói uma representação interna e prepara uma tela de anotação por página. Para arquivos com centenas de páginas, esta etapa pode levar alguns segundos.

### Etapa 3: Adicionando Comentários (Opcional, mas Recomendado)
`Comment` é uma classe que representa uma nota textual anexada a uma anotação, permitindo que colaboradores expliquem o motivo do tachado.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** Use comentários para explicar por que o texto está sendo removido — isso é especialmente útil em fluxos de revisão jurídica ou editorial.

### Etapa 4: Definindo Coordenadas da Anotação
Objetos `Point` armazenam pares de coordenadas X‑Y que definem a localização exata de uma anotação em uma página PDF.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** As coordenadas PDF começam no canto inferior esquerdo (0,0). O exemplo cria uma linha horizontal de (80,730) a (240,730) na página alvo.

**Finding the Right Coordinates:** Muitos desenvolvedores criam um helper que converte percentuais da largura/altura da página em pontos absolutos, tornando o código resiliente a diferentes tamanhos de página.

### Etapa 5: Criando a Anotação de Tachado
`StrikeoutAnnotation` encapsula a linha visual, suas propriedades de estilo como cor e opacidade, e quaisquer metadados associados a uma marca de tachado.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Color Values:** O `fontColor` usa valores RGB decimais (por exemplo, 65535 para amarelo brilhante). Use um conversor online se precisar de tons específicos da marca.

**Opacity Recommendation:** Uma opacidade de `0.7` (70 %) oferece um indicativo visual claro enquanto mantém o texto subjacente legível.

### Etapa 6: Aplicar a Anotação
`addAnnotation` é um método do `Annotator` que registra a anotação preparada no documento para que seja renderizada e salva.

```java
annotator.add(strikeout);
```

### Etapa 7: Salvar e Limpar
`dispose()` libera recursos nativos mantidos pela instância `Annotator`, evitando vazamentos de memória após a conclusão do processamento.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** Chamar `dispose()` libera recursos nativos e previne vazamentos de memória ao processar lotes de PDFs.

## Problemas Comuns e Como Corrigi‑los

### Problema 1: Erros “File Not Found”
**Sintomas:** Exceção lançada durante a construção do `Annotator`.  
**Solução:** Verifique os caminhos de entrada e saída e confirme que a aplicação tem permissões de leitura/escrita.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Problema 2: O Tachado Aparece no Local Errado
**Sintomas:** A linha não se alinha ao texto desejado.  
**Solução:** Lembre‑se de que as coordenadas Y do PDF aumentam para cima. Use uma ferramenta de depuração visual ou imprima as dimensões da página para ajustar finamente os pontos.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Problema 3: Anotação Não Visível
**Sintomas:** Nenhum tachado aparece após salvar.  
**Possíveis Causas e Correções:**
- **Opacidade muito baixa:** Defina temporariamente a opacidade para `1.0` para verificar a visibilidade.  
- **Mistura de cores:** Use uma cor de alto contraste como vermelho (`255`).  
- **Índice de página incorreto:** Os números de página começam em zero; certifique‑se de direcionar a página correta.

### Problema 4: Problemas de Memória com Arquivos Grandes
**Sintomas:** `OutOfMemoryError` ou desempenho lento.  
**Soluções:**  
- Processar documentos em lotes menores.  
- Usar a API de streaming, se disponível.  
- Sempre invocar `dispose()` após cada documento.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Aplicações e Casos de Uso no Mundo Real

### Revisão de Documentos Legais
Escritórios de advocacia anotam contratos com tachados para indicar cláusulas excluídas enquanto preservam um registro de auditoria.

### Edição de Artigos Acadêmicos
Professores usam tachados para sugerir remoções durante a revisão por pares, mantendo o texto original visível para contexto.

### Sistemas de Gerenciamento de Conteúdo
Plataformas de publicação sinalizam automaticamente seções que violam políticas com tachados antes da moderação manual.

### Controle de Versão para Documentos
Empresas tratam anotações de tachado como “marcadores de exclusão” em um fluxo de controle de versão centrado em documentos, semelhante a diffs de código.

## Dicas de Otimização de Performance

### Estratégia de Processamento em Lote
Ao lidar com muitos PDFs, reutilize uma única instância `Annotator` sempre que possível e processe arquivos em threads paralelas.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Melhores Práticas de Gerenciamento de Memória
- Chamar `dispose()` em cada `Annotator`.  
- Limitar carregamentos simultâneos de documentos para evitar pressão na heap.  
- Monitorar o uso de memória da JVM com ferramentas como VisualVM.

### Cache de Coordenadas
Se você aplicar o mesmo layout de anotação em vários arquivos, faça cache dos objetos `Point` para evitar recomputação.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Opções Avançadas de Customização

### Seleção Dinâmica de Cor
Escolha cores em tempo de execução com base em regras de negócio (por exemplo, vermelho para exclusões críticas, amarelo para as tentativas).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### Tachados de Múltiplas Linhas
Crie uma série de pares `Point` para desenhar uma linha em zigue‑zague que cruza várias linhas de texto.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Lista de Verificação de Solução de Problemas
1. **Permissões de Arquivo:** Verifique o acesso de leitura/escrita.  
2. **Versão da Biblioteca:** Certifique‑se de que está usando uma versão suportada do GroupDocs.Annotation.  
3. **Status da Licença:** Confirme que o arquivo de licença está referenciado corretamente.  
4. **Compatibilidade do PDF:** Verifique se o PDF não está corrompido e está dentro dos limites de tamanho suportados.  
5. **Validação de Coordenadas:** Certifique‑se de que todos os pontos estejam dentro dos limites da página.  
6. **Espaço de Heap:** Aumente o `-Xmx` da JVM se estiver processando arquivos muito grandes.

## Perguntas Frequentes

**Q: Posso tachar texto em várias linhas?**  
A: Sim. Crie vários objetos `Point` que traçam o caminho desejado; a anotação seguirá a polilinha fornecida.

**Q: O que acontece se eu especificar coordenadas fora dos limites da página?**  
A: A anotação será recortada e pode ficar invisível. Sempre valide as coordenadas contra a largura e altura da página.

**Q: Posso remover anotações de tachado após adicioná‑las?**  
A: Absolutamente. Use o método `removeAnnotation` com o ID da anotação ou filtre por tipo para excluí‑las programaticamente.

**Q: Existe um limite de quantas anotações posso adicionar a um único PDF?**  
A: O GroupDocs não impõe um limite rígido, mas o desempenho pode degradar após milhares de anotações. Considere paginação ou resumir anotações para conjuntos muito grandes.

**Q: Como trabalhar com PDFs protegidos por senha?**  
A: Passe a senha ao construtor `Annotator`. A biblioteca descriptografará o documento na memória antes de aplicar quaisquer anotações.

**Q: Como lidar com PDFs com diferentes tamanhos e orientações de página?**  
A: Recupere as dimensões de cada página via `annotator.getPageInfo(pageNumber)` e calcule coordenadas relativas a essas dimensões para garantir posicionamento consistente.

## Conclusão
Você agora tem uma solução completa e pronta para produção de **how to add strikeout** annotations to PDFs in Java usando o GroupDocs.Annotation. Ao dominar o manuseio de caminhos de arquivos, cálculo de coordenadas e gerenciamento de recursos, você pode incorporar essa capacidade em ferramentas de revisão de documentos, pipelines de conteúdo ou qualquer aplicação baseada em Java que precise de feedback visual preciso.

**Próximos Passos**
1. Clone o projeto de exemplo e execute‑o contra um PDF de amostra.  
2. Experimente diferentes cores, opacidades e textos de comentário.  
3. Integre o fluxo de trabalho de anotação ao seu serviço de processamento de documentos existente.  
4. Explore tipos de anotação relacionados — realces, notas adesivas e anotações de forma — para ampliar seu conjunto de ferramentas de manipulação de PDF.

Pronto para mais? Mergulhe na documentação oficial para obter insights mais profundos da API.

## Recursos Adicionais

- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Documentação geral das bibliotecas GroupDocs
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Referência completa da API  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Detalhes método a método  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Mantenha sua biblioteca atualizada  
- [Purchase License](https://purchase.groupdocs.com/buy) - Licenciamento pronto para produção  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Avalie antes de comprar  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Teste de desenvolvimento  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Ajuda da comunidade e suporte oficial  

---

**Última Atualização:** 2026-05-21  
**Testado com:** GroupDocs.Annotation 23.12 for Java  
**Autor:** GroupDocs

## Tutoriais Relacionados

- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)