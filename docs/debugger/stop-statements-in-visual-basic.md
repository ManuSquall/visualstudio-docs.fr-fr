---
title: Instructions Stop en Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74be447f523713cdef9ee5c52876ee0acf4c25b2
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056141"
---
# <a name="stop-statements-in-visual-basic"></a>Instructions Stop en Visual Basic
L'instruction Stop de Visual Basic fournit une alternative de programmation à la définition d'un point d'arrêt. Lorsque le débogueur rencontre une instruction Stop, il interrompt l'exécution du programme (passe en mode arrêt). Les programmeurs C# peuvent parvenir au même résultat à l'aide d'un appel à System.Diagnostics.Debugger.Break.  
  
 Vous définissez ou supprimez une instruction Stop en modifiant votre code source. Vous ne pouvez pas définir ou supprimer des instructions Stop en utilisant des commandes du débogueur, comme pour un point d'arrêt.  
  
 À la différence d'une instruction End, l'instruction Stop ne réinitialise pas les variables ou ne retourne pas en mode design. Vous pouvez choisir Continuer dans le menu Déboguer pour poursuivre l'exécution de l'application.  
  
 Lorsque vous exécutez une application Visual Basic en dehors du débogueur, une instruction Stop lance le débogueur si le débogage juste-à-temps est activé. Si le débogage juste-à-temps n'est pas activé, l'instruction Stop se comporte comme si une instruction End était présente, et l'exécution prend fin. Si aucun événement QueryUnload ou Unload ne se produit, vous devez supprimer toutes les instructions Stop de la version Release de votre application Visual Basic. Pour plus d’informations, consultez [débogage juste à temps](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Pour éviter de supprimer les instructions Stop, vous pouvez utiliser la compilation conditionnelle :  
  
```cpp
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Vous pouvez également utiliser une instruction Assert à la place de l'instruction Stop. Une instruction Debug.Assert interrompt l’exécution uniquement lorsqu’une condition spécifique n’est pas vérifiée et est automatiquement supprimée lorsque vous compilez une version Release. Pour plus d’informations, consultez [Assertions dans du Code managé](../debugger/assertions-in-managed-code.md). Si vous souhaitez utiliser une instruction Assert qui interrompt toujours l'exécution en version Debug, procédez comme suit :  
  
```csharp
Debug.Assert(false)  
```  
  
 Vous pouvez également utiliser la méthode Debug.Fail :  
  
```csharp
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)
