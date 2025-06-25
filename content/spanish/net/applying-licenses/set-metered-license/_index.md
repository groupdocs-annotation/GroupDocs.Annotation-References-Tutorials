---
"description": "Aprenda a configurar una licencia medida para GroupDocs.Annotation .NET para el uso de recursos y las capacidades de anotación de documentos en sus aplicaciones .NET."
"linktitle": "Establecer licencia medida"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Establecer licencia medida"
"url": "/es/net/applying-licenses/set-metered-license/"
"weight": 12
---

# Establecer licencia medida

## Introducción
GroupDocs.Annotation para .NET es una potente biblioteca que permite a los desarrolladores añadir funciones de anotación de documentos a sus aplicaciones .NET sin esfuerzo. Ya sea que esté creando un sistema de gestión documental, una plataforma de colaboración o cualquier aplicación que requiera revisión y marcado de documentos, GroupDocs.Annotation para .NET ofrece un conjunto completo de herramientas para agilizar el proceso.
En este tutorial, profundizaremos en el proceso de configuración de una licencia medida para GroupDocs.Annotation .NET. Una licencia medida le permite pagar solo por los recursos que consume, lo que la convierte en una solución rentable para proyectos de cualquier escala. Siguiendo los pasos que se describen a continuación, podrá integrar GroupDocs.Annotation sin problemas en su aplicación .NET, optimizando el uso de recursos y manteniendo el control presupuestario.
## Prerrequisitos
Antes de sumergirse en el tutorial, asegúrese de tener los siguientes requisitos previos:
1. Biblioteca GroupDocs.Annotation para .NET: Descargue la biblioteca desde [sitio web](https://releases.groupdocs.com/annotation/net/).
2. Acceso a la cuenta de GroupDocs: Necesitará una cuenta de GroupDocs para obtener las claves públicas y privadas necesarias para configurar la licencia medida. Si aún no tiene una cuenta, puede registrarse para obtener una prueba gratuita. [aquí](https://releases.groupdocs.com/).
3. Comprensión básica de C# y .NET Framework: la familiaridad con el lenguaje de programación C# y .NET Framework será beneficiosa para implementar los pasos descritos en este tutorial.

## Importar espacios de nombres
Para comenzar, asegúrese de importar los espacios de nombres necesarios a su proyecto de C#. Estos espacios de nombres son esenciales para interactuar con la funcionalidad de GroupDocs.Annotation.
```csharp
using System;
```
## Paso 1: Obtener claves públicas y privadas
Antes de configurar la licencia medida, debe obtener sus claves públicas y privadas desde el panel de su cuenta de GroupDocs.
1. Inicie sesión en su cuenta de GroupDocs.
2. Vaya a la sección de gestión de licencias.
3. Copie sus claves públicas y privadas proporcionadas por GroupDocs.
## Paso 2: Establecer una licencia medida
Una vez que haya obtenido sus claves públicas y privadas, puede configurar la licencia medida en su aplicación .NET.
```csharp
string publicKey = "*****"; // Reemplace ***** con su clave pública
string privateKey = "*****"; // Reemplace ***** con su clave privada
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Conclusión
En conclusión, configurar una licencia medida para GroupDocs.Annotation .NET es un proceso sencillo que garantiza un uso eficiente de los recursos y una buena relación calidad-precio para sus proyectos de anotación de documentos. Siguiendo los pasos de este tutorial, podrá integrar GroupDocs.Annotation sin problemas en su aplicación .NET y mejorar las funciones de colaboración y revisión de documentos.
## Preguntas frecuentes
### ¿Puedo utilizar GroupDocs.Annotation for .NET en proyectos comerciales?
Sí, GroupDocs.Annotation para .NET puede usarse en proyectos comerciales y no comerciales. Sin embargo, necesita adquirir una licencia adecuada según los requisitos de su proyecto.
### ¿Hay una versión de prueba disponible para GroupDocs.Annotation para .NET?
Sí, puede obtener una prueba gratuita de GroupDocs.Annotation para .NET visitando [este enlace](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte técnico para GroupDocs.Annotation para .NET?
Puede buscar soporte técnico visitando el foro de GroupDocs [aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Existen opciones de licencia temporal disponibles?
Sí, puede obtener una licencia temporal de GroupDocs para uso a corto plazo o con fines de evaluación. Visite [este enlace](https://purchase.groupdocs.com/temporary-license/) Para más información.
### ¿Puedo personalizar las funciones de anotación según los requisitos de mi proyecto?
Sí, GroupDocs.Annotation para .NET ofrece amplias opciones de personalización, lo que le permite adaptar las funciones de anotación para satisfacer las necesidades específicas de su proyecto.