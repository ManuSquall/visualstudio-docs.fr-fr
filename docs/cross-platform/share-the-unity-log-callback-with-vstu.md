---
title: Partager le rappel de journal Unity avec VSTU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: "2"
author: conceptdev
ms.author: crdun
manager: crdun
ms.openlocfilehash: 7aae3c7bc11cdde209ef4d663793f25fa1e9e67e
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2017
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Partager le rappel de journal Unity avec VSTU
Visual Studio Tools pour Unity enregistre un rappel de journal avec Unity pour pouvoir diffuser sa console vers Visual Studio. Si vos scripts de l'éditeur enregistrent également un rappel de journal avec Unity, le rappel VSTU peut interférer avec votre rappel.  Pour éviter ce risque, utilisez l'événement `VisualStudioIntegration.LogCallback` pour coopérer avec VSTU.  

## <a name="demonstrates"></a>Démonstrations  
 Comment partager le rappel de journal Unity créé par Visual Studio Tools pour Unity.  

## <a name="example"></a>Exemple  

```csharp  
using System;  

using UnityEngine;  
using UnityEditor;  

using SyntaxTree.VisualStudio.Unity.Bridge;  

[InitializeOnLoad]  
public class LogCallbackHook  
{  
    static LogCallbackHook()  
    {  
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>  
        {  
            // place code that implements your log callback here  
        };  
    }  
}  
```  

## <a name="see-also"></a>Voir aussi  
 [Exemple : génération de fichier projet](../cross-platform/customize-project-files-created-by-vstu.md)
