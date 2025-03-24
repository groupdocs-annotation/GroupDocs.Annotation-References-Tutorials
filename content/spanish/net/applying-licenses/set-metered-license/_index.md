---
title: Establecer licencia medida
linktitle: Establecer licencia medida
second_title: API GroupDocs.Annotation .NET
description: Aprenda a configurar una licencia medida para GroupDocs.Annotation .NET para el uso de recursos y capacidades de anotación de documentos en sus aplicaciones .NET.
weight: 12
url: /es/net/applying-licenses/set-metered-license/
---

# Establecer licencia medida

## Introducción
GroupDocs.Annotation para .NET es una poderosa biblioteca que permite a los desarrolladores agregar capacidades de anotación de documentos a sus aplicaciones .NET sin esfuerzo. Ya sea que esté creando un sistema de gestión de documentos, una plataforma de colaboración o cualquier aplicación que implique revisión y marcado de documentos, GroupDocs.Annotation para .NET proporciona un conjunto completo de herramientas para agilizar el proceso.
En este tutorial, profundizaremos en el proceso de configuración de una licencia medida para GroupDocs.Annotation .NET. Una licencia medida le permite pagar sólo por los recursos que consume, lo que la convierte en una solución rentable para proyectos de cualquier escala. Si sigue los pasos que se describen a continuación, podrá integrar sin problemas GroupDocs.Annotation en su aplicación .NET mientras optimiza el uso de recursos y mantiene el control presupuestario.
## Requisitos previos
Antes de sumergirse en el tutorial, asegúrese de tener los siguientes requisitos previos:
1.  GroupDocs.Annotation para la biblioteca .NET: descargue la biblioteca desde[sitio web](https://releases.groupdocs.com/annotation/net/).
2. Acceso a la cuenta de GroupDocs: necesitará una cuenta de GroupDocs para obtener las claves públicas y privadas necesarias para configurar la licencia medida. Si aún no tienes una cuenta, puedes registrarte para una prueba gratuita[aquí](https://releases.groupdocs.com/).
3. Comprensión básica de C# y .NET Framework: la familiaridad con el lenguaje de programación C# y .NET Framework será beneficiosa para implementar los pasos descritos en este tutorial.

## Importar espacios de nombres
Para comenzar, asegúrese de importar los espacios de nombres necesarios a su proyecto C#. Estos espacios de nombres son esenciales para interactuar con la funcionalidad GroupDocs.Annotation.
```csharp
using System;
```
## Paso 1: obtener claves públicas y privadas
Antes de configurar la licencia medida, debe obtener sus claves públicas y privadas desde el panel de su cuenta de GroupDocs.
1. Inicie sesión en su cuenta de GroupDocs.
2. Navegue a la sección de administración de licencias.
3. Copie sus claves públicas y privadas proporcionadas por GroupDocs.
## Paso 2: configurar la licencia medida
Una vez que haya obtenido sus claves públicas y privadas, puede configurar la licencia medida en su aplicación .NET.
```csharp
string publicKey = "*****"; // Reemplace ***** con su clave pública
string privateKey = "*****"; // Reemplace ***** con su clave privada
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Conclusión
En conclusión, configurar una licencia medida para GroupDocs.Annotation .NET es un proceso sencillo que garantiza una utilización eficiente de los recursos y rentabilidad para sus proyectos de anotación de documentos. Si sigue los pasos descritos en este tutorial, puede integrar fácilmente GroupDocs.Annotation en su aplicación .NET y mejorar las capacidades de revisión y colaboración de documentos.
## Preguntas frecuentes
### ¿Puedo utilizar GroupDocs.Annotation para .NET en proyectos comerciales?
Sí, GroupDocs.Annotation para .NET se puede utilizar tanto en proyectos comerciales como no comerciales. Sin embargo, debe adquirir una licencia adecuada según los requisitos de su proyecto.
### ¿Existe una versión de prueba disponible para GroupDocs.Annotation para .NET?
 Sí, puede aprovechar una prueba gratuita de GroupDocs.Annotation para .NET visitando[este enlace](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte técnico para GroupDocs.Annotation para .NET?
 Puede buscar soporte técnico visitando el foro de GroupDocs[aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Hay opciones de licencia temporal disponibles?
 Sí, puede obtener una licencia temporal de GroupDocs para uso a corto plazo o con fines de evaluación. Visita[este enlace](https://purchase.groupdocs.com/temporary-license/) para más información.
### ¿Puedo personalizar las funciones de anotación según los requisitos de mi proyecto?
Sí, GroupDocs.Annotation para .NET ofrece amplias opciones de personalización, lo que le permite adaptar las funciones de anotación para satisfacer las necesidades específicas de su proyecto.