---
title: Partager le rappel de journal Unity avec VSTU | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 9e309f7d7340eb73de587c7a5f569377354dbab9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186860"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Partager le rappel de journal Unity avec VSTU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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

