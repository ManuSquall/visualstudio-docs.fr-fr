---
title: "Personnaliser les fichiers projet créés par VSTU | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: "2"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: d4447d0228cbf446d3376db96c5e23f795c9cf86
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="customize-project-files-created-by-vstu"></a>Personnaliser les fichiers projet créés par VSTU
Visual Studio Tools pour Unity fournit un rappel de type Unity pendant la génération du fichier projet. Inscrivez-vous avec l'événement `VisualStudioIntegration.ProjectFileGeneration` pour modifier le fichier projet chaque fois qu'il est régénéré.  
  
## <a name="demonstrates"></a>Démonstrations  
 Comment personnaliser les fichiers projet Visual Studio générés par Visual Studio Tools pour Unity.  
  
## <a name="example"></a>Exemple  
  
```csharp  
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
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple : rappel de journal](../cross-platform/share-the-unity-log-callback-with-vstu.md)