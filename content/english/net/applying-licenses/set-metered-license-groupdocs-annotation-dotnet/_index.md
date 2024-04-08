---
title: Set Metered License - GroupDocs.Annotation .NET
linktitle: Set Metered License - GroupDocs.Annotation .NET
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 12
url: /net/applying-licenses/set-metered-license-groupdocs-annotation-dotnet/
---

## Complete Source Code
```csharp
using System;

namespace GroupDocs.Annotation.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to set Metered license.
    /// Learn more about Metered license at https://purchase.groupdocs.com/faqs/licensing/metered.
    /// </summary>
    class SetMeteredLicense
    {
        public static void Run()
        {
            string publicKey = "*****";
            string privateKey = "*****";
            Metered metered = new Metered();
            metered.SetMeteredKey(publicKey, privateKey);
            Console.WriteLine("License set successfully.");
        }
    }
}
```
