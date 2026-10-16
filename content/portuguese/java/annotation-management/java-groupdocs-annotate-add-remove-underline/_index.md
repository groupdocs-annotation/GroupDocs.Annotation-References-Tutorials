---
date: '2026-10-16'
description: Aprenda como salvar PDF sem anotações em Java, domine java pdf memory
  management, e adicione underline annotations com o GroupDocs.Annotation. Guia passo
  a passo.
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: Anotação de Documentos Java com GroupDocs
og_description: Aprenda como salvar PDF sem anotações em Java, domine java pdf memory
  management, e adicione underline annotations com o GroupDocs.Annotation. Guia passo
  a passo.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: Como salvar PDF sem anotações em Java usando o GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  headline: How to save PDF without annotations in Java using GroupDocs
  type: TechArticle
- description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  name: How to save PDF without annotations in Java using GroupDocs
  steps:
  - name: initialize the annotator and load your document
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and modifying PDF documents. It abstracts file‑system handling, stream management,
      and native resource allocation. **Pro tip:** Use absolute paths while developing
      to avoid “file not found” errors. In production, consider loadin'
  - name: creating comments and replies (the collaborative part)
    text: '`Comment` objects represent threaded discussion attached to an annotation.
      Each comment can have an author, a timestamp, and optional replies, enabling
      a full conversation around a specific markup. **Real‑world use:** Reviewers
      can discuss a specific clause by adding threaded replies, keeping the co'
  - name: defining annotation coordinates (getting the position right)
    text: '`Point` defines a single coordinate in PDF space (measured in points, where
      72 points = 1 inch). Four points are required for an underline: two for the
      start line and two for the end line. **Coordinate system:** - Points 1 & 2 define
      the top edge of the underline. - Points 3 & 4 define the bottom ed'
  - name: creating and configuring the underline annotation
    text: '`UnderlineAnnotation` is the concrete class that represents an underline
      markup. It inherits from the base `Annotation` class and adds properties specific
      to underlines, such as line thickness and style. **Color & opacity tips:** -
      `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow. - Fo'
  - name: saving your annotated document
    text: '`SaveOptions` lets you control the output format, whether to embed annotations,
      and how to handle metadata. Setting `AnnotationType.NONE` instructs the library
      to strip all annotation objects, which is the key to **save PDF without annotations**.
      **Memory management:** The `dispose()` call releases '
  type: HowTo
- questions:
  - answer: Create several `UnderlineAnnotation` objects with different coordinates
      and add them sequentially using `annotator.add()`.
    question: How do I annotate multiple areas of text in a single operation?
  - answer: Yes. Use the same coordinate system, ensuring the points lie inside the
      image bounds.
    question: Can I annotate images within PDF documents?
  - answer: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats
      such as JPEG, PNG, TIFF.
    question: What file formats besides PDF does GroupDocs.Annotation support?
  - answer: Process documents one at a time, increase the JVM heap (`-Xmx`), and always
      dispose of `Annotator` instances promptly.
    question: How do I handle very large documents without running out of memory?
  - answer: Yes. Use `annotator.get()` to retrieve all annotations, then filter by
      type, author, or page as needed.
    question: Is it possible to extract existing annotations from a document?
  type: FAQPage
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
- java pdf memory management
title: Como salvar PDF sem anotações em Java usando o GroupDocs
type: docs
url: /pt/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Como salvar PDF sem anotações em Java usando GroupDocs

Se você precisa **salvar PDF sem anotações** enquanto ainda pode adicionar notas sublinhadas colaborativas, está no lugar certo. Muitos desenvolvedores Java têm dificuldade em manter uma versão limpa de um documento para distribuição final, especialmente quando o mesmo arquivo é usado para revisões iterativas. Neste tutorial você aprenderá como gerar um PDF limpo, gerenciar a memória de forma eficiente e aplicar anotações de sublinhado com comentários usando GroupDocs.Annotation. Ao final, você entenderá todo o fluxo de trabalho — desde o carregamento de um PDF até a produção de uma cópia final sem marca d'água — além de dicas de boas práticas para construir um **sistema de revisão de documentos java** robusto.

## Respostas rápidas
- **Como adiciono uma anotação de sublinhado?** Use `UnderlineAnnotation` com `annotator.add()` e depois salve o documento.  
- **Como posso salvar PDF sem anotações?** Carregue o arquivo anotado, defina `AnnotationType.NONE` em `SaveOptions` e salve uma nova cópia.  
- **Quais bibliotecas são necessárias?** GroupDocs.Annotation v25.2 (ou mais recente) e seu repositório Maven.  
- **Preciso de licença para produção?** Sim — aplique uma licença válida do GroupDocs para evitar marcas d'água.  
- **Posso processar vários documentos de forma eficiente?** Envolva cada `Annotator` em um bloco try‑with‑resources e descarte após cada arquivo.

## Como salvar PDF sem anotações em Java?

Carregue o PDF de origem com um `Annotator`, configure `SaveOptions` para excluir todos os tipos de anotação e chame `save()` para gravar uma cópia limpa. Esta operação não modifica o arquivo original, de modo que você mantém tanto a versão anotada para revisores quanto a versão impecável para distribuição. O processo usa streaming internamente, o que significa que o documento inteiro nunca reside completamente na memória — crucial para PDFs grandes.

## O que é salvar PDF sem anotações?

`save pdf without annotations` refere‑se à exportação de um documento PDF removendo todos os objetos de anotação (realces, comentários, carimbos, sublinhados, etc.). O arquivo resultante contém apenas o conteúdo e o layout originais, tornando‑o adequado para arquivamento legal, divulgação pública ou armazenamento de longo prazo.

## Por que criar arquivos PDF limpos em um sistema de revisão de documentos java?

Uma versão limpa elimina marcas de revisores, comentários e realces, proporcionando um documento polido pronto para clientes, reguladores ou divulgação pública. Também reduz o tamanho do arquivo em até 30 % em média e impede a divulgação acidental de notas internas — crítico para fluxos de trabalho legais e de conformidade. O GroupDocs.Annotation pode remover todos os objetos de anotação em uma única passagem, suportando PDFs de até 500 MB sem carregar o arquivo inteiro na memória.

## Pré‑requisitos e configuração do ambiente

### Requisitos antes de começar

**Requisitos do ambiente de desenvolvimento**  
- Java Development Kit (JDK) 8 ou superior (JDK 11+ recomendado)  
- Maven 3.6+ ou Gradle 6.0+ para gerenciamento de dependências  
- IDE como IntelliJ IDEA, Eclipse ou VS Code com extensões Java  
- Pelo menos 2 GB de RAM disponível (o processamento de documentos pode ser intensivo em memória)

**Pré‑requisitos de conhecimento**  
Você deve estar confortável com conceitos básicos de Java — inicialização de objetos, chamadas de método e dependências Maven. Experiência prévia com bibliotecas de terceiros acelerará a adoção.

**Documentos de teste**  
Tenha alguns PDFs de exemplo prontos. PDFs baseados em texto funcionam melhor; imagens escaneadas podem exigir OCR antes da anotação.

### Configuração Maven: adicionando GroupDocs ao seu projeto

Adicione a dependência a seguir ao seu `pom.xml`. Esta etapa costuma surpreender muitos desenvolvedores na primeira tentativa porque o group ID e o artifact ID devem coincidir exatamente.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Importante:** A versão 25.2 é a última release estável no momento da escrita. Verifique o repositório GroupDocs regularmente para versões mais recentes que incluam correções de bugs e melhorias de desempenho.

### Configuração de licença (não pule esta etapa)

**Para desenvolvimento/testes** – Baixe a avaliação gratuita no site do GroupDocs. A avaliação inclui todos os recursos, mas adiciona uma marca d'água aos documentos processados.

**Para produção** – Adquira uma licença e aplique‑a durante a inicialização da aplicação. Sem uma licença válida, builds de produção serão limitados e terão marca d'água.

## Guia de implementação: adicionando anotações de sublinhado

### Entendendo o fluxo de trabalho de anotação

Antes de mergulharmos no código, vamos percorrer o fluxo de quatro etapas que ocorre quando você **anota PDF em Java**:

1. **Carregamento do documento** – `Annotator` lê o arquivo para a memória.  
2. **Criação da anotação** – Defina propriedades como posição, estilo e comentários.  
3. **Aplicação da anotação** – A biblioteca injeta a anotação na estrutura do PDF.  
4. **Salvamento do documento** – Persista o arquivo modificado, opcionalmente preservando o original.

O processo é não destrutivo; o arquivo fonte permanece intacto a menos que você o sobrescreva.

### Etapa 1: inicializar o annotator e carregar seu documento

`Annotator` é o ponto de entrada principal no GroupDocs.Annotation para carregar e modificar documentos PDF. Ele abstrai o manuseio do sistema de arquivos, gerenciamento de streams e alocação de recursos nativos.

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

**Dica profissional:** Use caminhos absolutos durante o desenvolvimento para evitar erros “arquivo não encontrado”. Em produção, considere carregar recursos do classpath ou de um bucket de armazenamento em nuvem.

### Etapa 2: criando comentários e respostas (a parte colaborativa)

Objetos `Comment` representam discussões em thread anexadas a uma anotação. Cada comentário pode ter autor, timestamp e respostas opcionais, permitindo uma conversa completa ao redor de uma marcação específica.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Uso no mundo real:** Revisores podem discutir uma cláusula específica adicionando respostas em thread, mantendo a conversa vinculada à anotação exata.

### Etapa 3: definindo coordenadas da anotação (posicionamento correto)

`Point` define uma única coordenada no espaço PDF (medida em pontos, onde 72 pontos = 1 polegada). Quatro pontos são necessários para um sublinhado: dois para a linha inicial e dois para a linha final.

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**Sistema de coordenadas:**  
- Pontos 1 & 2 definem a borda superior do sublinhado.  
- Pontos 3 & 4 definem a borda inferior.  
- A diferença em Y (730 vs 650) controla a espessura.

### Etapa 4: criando e configurando a anotação de sublinhado

`UnderlineAnnotation` é a classe concreta que representa a marcação de sublinhado. Ela herda da classe base `Annotation` e adiciona propriedades específicas para sublinhados, como espessura da linha e estilo.

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**Dicas de cor e opacidade:**  
- `FontColor` usa ARGB; `65535` (0x00FFFF) produz amarelo brilhante.  
- Para vermelho, use `16711680` (0xFF0000); para azul, `255` (0x0000FF).  
- Valores de opacidade entre 0.5 e 0.8 oferecem boa legibilidade sem obscurecer o texto.

### Etapa 5: salvando seu documento anotado

`SaveOptions` permite controlar o formato de saída, se as anotações devem ser incorporadas e como lidar com metadados. Definir `AnnotationType.NONE` instrui a biblioteca a remover todos os objetos de anotação, que é a chave para **salvar PDF sem anotações**.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**Gerenciamento de memória:** A chamada `dispose()` libera recursos nativos e previne vazamentos de memória — crítico ao processar muitos arquivos em lote.

## Removendo anotações: criando versões limpas do documento

Às vezes você precisa de uma versão do PDF **sem nenhuma anotação** — por exemplo, ao entregar o contrato final aprovado. O GroupDocs facilita isso.

### Entendendo as opções de remoção de anotação

Você pode:  
- Remover **todas** as anotações (opção mais comum)  
- Remover tipos específicos (ex.: apenas realces)  
- Remover anotações por autor ou página  

### Remoção de anotação passo a passo

**Etapa 1: carregar o documento previamente anotado**

`Annotator` novamente atua como carregador; ele lerá o arquivo que ainda contém objetos de anotação.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Etapa 2: configurar opções de salvamento para saída limpa**

`SaveOptions` fornece uma API fluente para especificar que nenhum tipo de anotação deve ser escrito no arquivo de saída.

```java
Annotator annotator = new Annotator(outputPath);
```

**Etapa 3: salvar a versão limpa**

Chamar `save()` com as opções configuradas grava um PDF que contém apenas o conteúdo original.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

Isso produz um arquivo **PDF limpo** que não contém objetos de anotação, perfeito para distribuição final.

## Problemas comuns e soluções

### Problema 1: erro “Document not found”

Certifique‑se de que o caminho do arquivo está correto e que a aplicação tem permissão de leitura. Usar `Path.of()` com caminhos absolutos elimina a maioria das ambiguidades.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### Problema 2: anotações aparecendo em locais errados

A origem das coordenadas do PDF está no canto inferior‑esquerdo. Verifique se seus valores de Y aumentam para cima e se você considera a rotação da página.

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### Problema 3: problemas de memória com documentos grandes

GroupDocs.Annotation faz streaming do conteúdo e nunca carrega o arquivo inteiro na memória heap. Contudo, ainda é necessário chamar `dispose()` e considerar aumentar o heap da JVM (`-Xmx`) para arquivos maiores que 200 MB.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problema 4: questões de licença em produção

Se o arquivo de licença estiver ausente ou o caminho incorreto, a biblioteca reverte ao modo de avaliação, adicionando marca d'água a cada página. Coloque o arquivo de licença em um local que esteja no classpath e carregue‑o cedo no ciclo de vida da aplicação.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## Melhores práticas de desempenho para aplicações de produção

### Estratégias de gerenciamento de memória

GroupDocs.Annotation processa PDFs de forma streaming, permitindo lidar com arquivos de até 500 MB sem carregar todo o documento na memória. Ainda assim, siga estas diretrizes:

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

### Considerações sobre threading

GroupDocs.Annotation **não é thread‑safe** por padrão. Se sua aplicação processa documentos simultaneamente:

- **Nunca compartilhe** uma instância de `Annotator` entre threads.  
- **Sincronize** o acesso a arquivos ou use um mecanismo de bloqueio.  
- Considere um **pool** de objetos `Annotator` se precisar de alta taxa de transferência.

### Estratégias de cache

- Cacheie modelos de anotação usados com frequência.  
- Reutilize coleções de `Point` para conjuntos de coordenadas comuns.  
- Mantenha um **PDF modelo** em memória se você anotar repetidamente o mesmo documento base.

## Melhores práticas de gerenciamento de memória Java PDF

O uso eficiente de memória é essencial ao lidar com PDFs grandes ou processar muitos arquivos em lote. Aqui estão algumas recomendações práticas:

- **Use try‑with‑resources** para cada `Annotator` a fim de garantir a liberação.  
- **Aumente o heap da JVM** (`-Xmx`) somente quando necessário; monitore o uso com ferramentas de profiling.  
- **Processar documentos sequencialmente** quando possível, liberando memória após cada arquivo.  
- **Evite carregar o mesmo PDF várias vezes**; reutilize o mesmo stream se precisar lê‑lo repetidamente.

Aplicar essas práticas ajuda a manter sua aplicação responsiva e previne falhas por falta de memória durante cargas intensas de anotação.

## Aplicações reais e casos de uso

### Sistemas de revisão de documentos

- **Revisão jurídica:** Sublinha cláusulas contratuais e adiciona comentários sobre riscos.  
- **Auditorias de conformidade:** Realça seções problemáticas em demonstrações financeiras.  
- **Revisão acadêmica por pares:** Professores sublinham trechos que precisam de esclarecimento.

### Plataformas educacionais

- **Ferramentas de anotação para estudantes:** Permitem que aprendizes sublinhem conceitos-chave em e‑books.  
- **Feedback de professores:** Fornecem comentários inline diretamente em trabalhos entregues.

### Fluxos de trabalho de garantia de qualidade

- **Revisão de documentação técnica:** Engenheiros sublinham seções que precisam de atualização.  
- **Procedimentos operacionais padrão:** Oficiais de segurança destacam etapas críticas.

### Sistemas de gerenciamento de conteúdo

- **Fluxo editorial:** Editores sublinham texto que requer verificação de fatos.  
- **Controle de versão:** Rastreia histórico de anotações ao longo de revisões de documentos.

## Dicas avançadas para implementação profissional

### Estilos de anotação personalizados

Você pode estender a aparência visual de um sublinhado definindo padrões de traço personalizados, extremidades de linha e níveis de opacidade. Isso é útil quando é necessário diferenciar papéis de revisores (ex.: jurídico vs. engenharia).

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### Metadados de anotação para rastreamento

Cada anotação pode carregar um dicionário de metadados definido pelo usuário. Armazene IDs, timestamps ou estado do fluxo de trabalho para integrar com sistemas externos de rastreamento.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Integração com sistemas de gerenciamento de usuários

Mapeie a propriedade `author` de um `Comment` para os IDs de usuário da sua aplicação. Isso permite estilização baseada em papéis e geração de trilhas de auditoria.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## Solucionando problemas em produção

### Monitoramento de desempenho

Observe estas métricas em produção:  
- **Uso de heap** – assegure que `dispose()` seja chamado.  
- **Tempo de processamento por documento** – registre timestamps antes/depois de `annotator.save()`.  
- **Taxa de erro** – capture exceções e categorize‑as.

### Armadilhas comuns em produção

- **Bloqueio de arquivos** – garanta que arquivos enviados estejam fechados antes da anotação.  
- **Edições concorrentes** – implemente bloqueio otimista ou verificações de versão.  
- **Arquivos grandes (> 50 MB)** – aumente o timeout da JVM e considere APIs de streaming.

### Melhores práticas de tratamento de erros

Envolva todas as chamadas de anotação em blocos try‑catch, registre o stack trace completo e relance uma `AnnotationException` personalizada com uma mensagem amigável ao usuário. Esse padrão simplifica a depuração e fornece feedback claro aos consumidores da API.

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## Perguntas frequentes

**P: Como anoto várias áreas de texto em uma única operação?**  
R: Crie vários objetos `UnderlineAnnotation` com coordenadas diferentes e adicione‑os sequencialmente usando `annotator.add()`.

**P: Posso anotar imagens dentro de documentos PDF?**  
R: Sim. Use o mesmo sistema de coordenadas, garantindo que os pontos estejam dentro dos limites da imagem.

**P: Quais formatos de arquivo além de PDF o GroupDocs.Annotation suporta?**  
R: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) e formatos de imagem como JPEG, PNG, TIFF.

**P: Como lidar com documentos muito grandes sem esgotar a memória?**  
R: Processar documentos um de cada vez, aumentar o heap da JVM (`-Xmx`) e sempre descartar instâncias de `Annotator` prontamente.

**P: É possível extrair anotações existentes de um documento?**  
R: Sim. Use `annotator.get()` para recuperar todas as anotações e, em seguida, filtre por tipo, autor ou página conforme necessário.

---

**Última atualização:** 2026-10-16  
**Testado com:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

---

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## Tutoriais relacionados

- [Create Clean PDF Java: Underline Annotations with GroupDocs](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Annotate Pdfs Groupdocs Annotation Java](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)