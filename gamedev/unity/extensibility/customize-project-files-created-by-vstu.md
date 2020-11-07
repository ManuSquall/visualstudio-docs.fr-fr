---
title: Personnaliser les fichiers projet créés par VSTU | Microsoft Docs
description: Découvrez comment personnaliser les fichiers projet créés par Outils Visual Studio pour Unity (VSTU). Passez en revue un exemple de code C#.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 071dc7a9f12dcfeb5fff9e59bbbf34dc64f61cf5
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341689"
---
# <a name="customize-project-files-created-by-vstu"></a>Personnaliser les fichiers projet créés par VSTU
Visual Studio Tools pour Unity fournit un rappel de type Unity pendant la génération du fichier projet. Inscrivez-vous avec l'événement `VisualStudioIntegration.ProjectFileGeneration` pour modifier le fichier projet chaque fois qu'il est régénéré.

## <a name="demonstrates"></a>Illustre le
 Comment personnaliser les fichiers projet Visual Studio générés par Visual Studio Tools pour Unity.

## <a name="example"></a>Exemple

```csharp
#if ENABLE_VSTU
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
#endif
```

## <a name="see-also"></a>Voir aussi
 [Exemple : rappel de journal](/cross-platform/share-the-unity-log-callback-with-vstu.md)
