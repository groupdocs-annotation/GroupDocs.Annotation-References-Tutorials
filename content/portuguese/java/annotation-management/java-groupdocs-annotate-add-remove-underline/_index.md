---
categories:
- Java Development
date: '2025-12-21'
description: Aprenda como criar arquivos PDF limpos em Java e anotar PDFs em Java
  usando o GroupDocs.Annotation, com exemplos de código completos e dicas de solução
  de problemas.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Criar PDF Limpo em Java: Anotações de Sublinhado com GroupDocs'
type: docs
url: /pt/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Criar PDF Limpo em Java: Anotações de Sublinhado com GroupDocs

## Introdução

Lutando com gerenciamento e colaboração de documentos em suas aplicações Java? Você não está sozinho. Muitos desenvolvedores enfrentam o desafio de implementar recursos robustos de anotação de documentos que funcionem de forma confiável em diferentes formatos de arquivo.

Neste guia, você **criará PDFs limpos em Java** e aprenderá como **anotar PDF em Java** usando GroupDocs.Annotation. Ao final deste tutorial, você saberá exatamente como adicionar anotações de sublinhado com comentários, remover anotações existentes e integrar esses recursos perfeitamente em seus projetos.

**O que você dominará neste guia:**
- Configurar o GroupDocs.Annotation em seu projeto Java (da maneira correta)  
- Adicionar anotações de sublinhado com comentários personalizados e estilo  
- Remover todas as anotações para criar versões limpas do documento  
- Solucionar problemas comuns que os desenvolvedores encontram  
- Otimizar o desempenho para aplicações em produção  

Seja você quem está construindo um sistema de revisão de documentos, uma plataforma educacional ou uma ferramenta de edição colaborativa, este tutorial cobre tudo com exemplos de código práticos e testados.

## Respostas Rápidas
- **Como adiciono uma anotação de sublinhado?** Use `UnderlineAnnotation` e `annotator.add()` e depois salve o documento.  
- **Como criar um PDF limpo em Java?** Carregue o arquivo anotado, defina `AnnotationType.NONE` em `SaveOptions` e salve uma nova cópia.  
- **Quais bibliotecas são necessárias?** GroupDocs.Annotation v25.2 (ou mais recente) e seu repositório Maven.  
- **Preciso de licença para produção?** Sim—aplique uma licença válida do GroupDocs para evitar marcas d'água.  
- **Posso processar vários documentos de forma eficiente?** Envolva cada `Annotator` em um bloco try‑with‑resources e descarte-o após cada arquivo.

## Como criar PDFs limpos em Java
Criar um PDF limpo em Java significa gerar uma versão do documento **sem nenhuma anotação**, preservando o conteúdo original. Isso é útil para distribuição final, arquivamento ou quando você precisa compartilhar uma cópia “limpa” após um ciclo de revisão.

O GroupDocs.Annotation torna isso simples: carregue o arquivo anotado, configure `SaveOptions` para excluir todos os tipos de anotação e salve o resultado. As etapas são ilustradas mais adiante na seção **Remoção de Anotações**.

## Como anotar PDF em Java usando GroupDocs
O GroupDocs.Annotation fornece uma API rica para **anotar PDF em Java**. Ele suporta uma ampla variedade de tipos de anotação, incluindo realces, carimbos e sublinhados. Neste tutorial, focamos nas anotações de sublinhado porque elas são comumente usadas para enfatizar texto enquanto permitem comentários em cadeia.

## Pré‑requisitos e Configuração do Ambiente

### O que você precisará antes de começar

**Requisitos do Ambiente de Desenvolvimento:**
- Java Development Kit (JDK) 8 ou superior (JDK 11+ recomendado)  
- Maven 3.6+ ou Gradle 6.0+ para gerenciamento de dependências  
- IDE como IntelliJ IDEA, Eclipse ou VS Code com extensões Java  
- Pelo menos 2 GB de RAM disponível (processamento de documentos pode ser intensivo em memória)

**Pré‑requisitos de Conhecimento:**
Você deve estar confortável com conceitos básicos de Java—inicialização de objetos, chamadas de método e dependências Maven. Experiência prévia com bibliotecas de terceiros acelerará a adoção.

**Documentos de Teste:**
Tenha alguns PDFs de exemplo prontos. PDFs baseados em texto funcionam melhor; imagens escaneadas podem exigir OCR antes da anotação.

### Configuração Maven: Obtendo o GroupDocs no seu Projeto

Veja como configurar corretamente seu projeto Maven (isso costuma confundir muitos desenvolvedores na primeira tentativa):

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

**Importante:** A versão 25.2 é a última release estável no momento da escrita. Verifique o repositório GroupDocs regularmente para versões mais recentes que incluam correções de bugs e melhorias de desempenho.

### Configuração de Licença (Não pule esta etapa)

**Para Desenvolvimento/Testes:**  
Baixe a avaliação gratuita no site do GroupDocs. A avaliação inclui todos os recursos, mas adiciona marca d'água aos documentos processados.

**Para Produção:**  
Adquira uma licença e aplique-a durante a inicialização da aplicação. Sem uma licença válida, builds de produção terão limitações.

## Guia de Implementação: Adicionando Anotações de Sublinhado

### Entendendo o Fluxo de Trabalho da Anotação

Antes de mergulharmos no código, vamos percorrer o fluxo de quatro etapas que ocorre quando você **anota PDF em Java**:

1. **Carregamento do Documento** – `Annotator` lê o arquivo para a memória.  
2. **Criação da Anotação** – Defina propriedades como posição, estilo e comentários.  
3. **Aplicação da Anotação** – A biblioteca injeta a anotação na estrutura do PDF.  
4. **Salvamento do Documento** – Persista o arquivo modificado, opcionalmente preservando o original.

O processo é não destrutivo; o arquivo fonte permanece intacto a menos que você o sobrescreva.

### Etapa 1: Inicializar o Annotator e Carregar seu Documento

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Dica Profissional:** Use caminhos absolutos durante o desenvolvimento para evitar erros “arquivo não encontrado”. Em produção, considere carregar recursos do classpath ou de um bucket de armazenamento em nuvem.

### Etapa 2: Criando Comentários e Respostas (A Parte Colaborativa)

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

**Uso no Mundo Real:** Revisores podem discutir uma cláusula específica adicionando respostas em cadeia, mantendo a conversa vinculada à anotação exata.

### Etapa 3: Definindo as Coordenadas da Anotação (Ajustando a Posição)

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

**Sistema de Coordenadas:**  
- Pontos 1 e 2 definem a borda superior do sublinhado.  
- Pontos 3 e 4 definem a borda inferior.  
- A diferença em Y (730 vs 650) controla a espessura.

### Etapa 4: Criando e Configurando a Anotação de Sublinhado

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

**Dicas de Cor e Opacidade:**  
- `FontColor` usa ARGB; `65535` (0x00FFFF) gera amarelo brilhante.  
- Para vermelho, use `16711680` (0xFF0000); para azul, `255` (0x0000FF).  
- Valores de opacidade entre 0.5 e 0.8 proporcionam boa legibilidade sem ocultar o texto.

### Etapa 5: Salvando seu Documento Anotado

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Gerenciamento de Memória:** A chamada `dispose()` libera recursos nativos e evita vazamentos de memória—crítico ao processar muitos arquivos em lote.

## Remoção de Anotações: Criando Versões Limpas do Documento

Às vezes você precisa de uma versão do PDF **sem nenhuma anotação**—por exemplo, ao entregar o contrato final aprovado. O GroupDocs facilita isso.

### Entendendo as Opções de Remoção de Anotações

Você pode:
- Remover **todas** as anotações (opção mais comum)  
- Remover tipos específicos (ex.: apenas realces)  
- Remover anotações por autor ou página  

### Remoção de Anotações Passo a Passo

**Etapa 1: Carregar o Documento Anotado Anteriormente**

```java
Annotator annotator = new Annotator(outputPath);
```

**Etapa 2: Configurar Opções de Salvamento para Saída Limpa**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Etapa 3: Salvar a Versão Limpa**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Isso produz um **PDF limpo em Java** que não contém objetos de anotação, perfeito para distribuição final.

## Problemas Comuns e Soluções

### Problema 1: Erro “Documento não encontrado”

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

### Problema 2: Anotações Aparecendo em Locais Errados

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problema 3: Problemas de Memória com Documentos Grandes

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Problema 4: Problemas de Licença em Produção

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

## Melhores Práticas de Desempenho para Aplicações em Produção

### Estratégias de Gerenciamento de Memória

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

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

### Considerações de Threading

O GroupDocs.Annotation **não é thread‑safe** por padrão. Se sua aplicação processa documentos simultaneamente:

- **Nunca compartilhe** uma instância de `Annotator` entre threads.  
- **Sincronize** o acesso a arquivos ou use um mecanismo de bloqueio.  
- Considere um **pool** de objetos `Annotator` se precisar de alta taxa de transferência.

### Estratégias de Cache

- Cacheie modelos de anotação usados com frequência.  
- Reutilize coleções `Point` para conjuntos de coordenadas comuns.  
- Mantenha um **PDF modelo** em memória se você anotar repetidamente o mesmo documento base.

## Aplicações Reais e Casos de Uso

### Sistemas de Revisão de Documentos

- **Revisão Jurídica:** Sublinhado de cláusulas contratuais e comentários sobre riscos.  
- **Auditorias de Conformidade:** Realce de seções problemáticas em demonstrações financeiras.  
- **Revisão Acadêmica por Pares:** Professores sublinham trechos que precisam de esclarecimento.

### Plataformas Educacionais

- **Ferramentas de Anotação para Estudantes:** Permita que aprendizes sublinhem conceitos-chave em e‑books.  
- **Feedback de Professores:** Comentários inline diretamente nas tarefas entregues.

### Fluxos de Trabalho de Garantia de Qualidade

- **Revisão de Documentação Técnica:** Engenheiros sublinham seções que precisam de atualização.  
- **Procedimentos Operacionais Padrão:** Oficiais de segurança destacam etapas críticas.

### Sistemas de Gerenciamento de Conteúdo

- **Fluxo Editorial:** Editores sublinham texto que requer verificação de fatos.  
- **Controle de Versão:** Rastreie o histórico de anotações ao longo das revisões de documentos.

## Dicas Avançadas para Implementação Profissional

### Estilos Personalizados de Anotação

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Metadados de Anotação para Rastreamento

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integração com Sistemas de Gerenciamento de Usuários

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

## Solucionando Problemas em Produção

### Monitoramento de Desempenho

Observe estas métricas em produção:
- **Uso de heap** – garanta que `dispose()` seja chamado.  
- **Tempo de processamento por documento** – registre timestamps antes/depois de `annotator.save()`.  
- **Taxa de erro** – capture exceções e categorize-as.

### Armadilhas Comuns em Produção

- **Bloqueio de arquivos** – assegure que arquivos enviados estejam fechados antes da anotação.  
- **Edições concorrentes** – implemente bloqueio otimista ou verificações de versão.  
- **Arquivos grandes (> 50 MB)** – aumente o timeout da JVM e considere APIs de streaming.

### Melhores Práticas de Tratamento de Erros

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

## Conclusão

Agora você tem tudo que precisa para **criar PDFs limpos em Java** e **anotar PDF em Java** com anotações de sublinhado usando GroupDocs.Annotation. Lembre‑se de:

- Gerenciar recursos com try‑with‑resources ou `dispose()` explícito.  
- Validar coordenadas antecipadamente para evitar sublinhados fora de lugar.  
- Implementar tratamento de erros robusto para estabilidade em produção.  
- Aproveitar estilos baseados em papéis e metadados para adequar ao seu fluxo de trabalho.

Próximos passos? Experimente adicionar outros tipos de anotação—realces, carimbos ou substituições de texto—para construir uma solução completa de revisão de documentos.

## Perguntas Frequentes

**P: Como anoto várias áreas de texto em uma única operação?**  
R: Crie vários objetos `UnderlineAnnotation` com coordenadas diferentes e adicione‑os sequencialmente usando `annotator.add()`.

**P: Posso anotar imagens dentro de documentos PDF?**  
R: Sim. Use o mesmo sistema de coordenadas, garantindo que os pontos estejam dentro dos limites da imagem.

**P: Quais formatos de arquivo, além de PDF, o GroupDocs.Annotation suporta?**  
R: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) e formatos de imagem como JPEG, PNG, TIFF.

**P: Como lidar com documentos muito grandes sem esgotar a memória?**  
R: Processe os documentos um de cada vez, aumente o heap da JVM (`-Xmx`) e sempre descarte as instâncias de `Annotator` prontamente.

**P: É possível extrair anotações existentes de um documento?**  
R: Sim. Use `annotator.get()` para recuperar todas as anotações e, em seguida, filtre por tipo, autor ou página conforme necessário.

---

**Última atualização:** 2025-12-21  
**Testado com:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

---