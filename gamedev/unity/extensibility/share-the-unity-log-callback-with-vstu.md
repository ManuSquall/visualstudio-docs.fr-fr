---
title: Partager le rappel de journal Unity avec VSTU | Microsoft Docs
description: Partagez votre rappel de journal Unity avec celui qui est inscrit auprès de Outils Visual Studio pour Unity (VSTU) pour diffuser sa console vers Visual Studio.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a1f4e7be068a152fc76c95160bdc7930f61e1f74
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341662"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Partager le rappel de journal Unity avec VSTU
Visual Studio Tools pour Unity enregistre un rappel de journal avec Unity pour pouvoir diffuser sa console vers Visual Studio. Si vos scripts de l'éditeur enregistrent également un rappel de journal avec Unity, le rappel VSTU peut interférer avec votre rappel.  Pour éviter ce risque, utilisez l'événement `VisualStudioIntegration.LogCallback` pour coopérer avec VSTU.

## <a name="demonstrates"></a>Illustre le
 Comment partager le rappel de journal Unity créé par Visual Studio Tools pour Unity.

## <a name="example"></a>Exemple

```csharp
#if ENABLE_VSTU
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
#endif
```

## <a name="see-also"></a>Voir aussi
 [Exemple : génération de fichier projet](./customize-project-files-created-by-vstu.md)
