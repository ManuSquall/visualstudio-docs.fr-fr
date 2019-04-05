---
title: 'Procédure pas à pas : Débogage au moment du Design | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 392e50b9494d2de17f2d1ac2b0f3c23f1e872fa6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952990"
---
# <a name="walkthrough-debugging-at-design-time"></a>Procédure pas à pas : Débogage au moment du Design
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser Visual Studio **immédiat** fenêtre pour exécuter une fonction ou une sous-routine pendant que votre application n’est pas en cours d’exécution. Si la fonction ou une sous-routine contient un point d’arrêt, Visual Studio s’arrête l’exécution au point approprié. Vous pouvez ensuite utiliser les fenêtres du débogueur pour examiner l’état de votre programme. Cette fonctionnalité est appelée débogage au moment du design.  
  
 La procédure suivante montre comment vous pouvez utiliser cette fonctionnalité.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Atteindre des points d’arrêt à partir de la fenêtre exécution  
  
1.  Collez le code suivant dans une application de console Visual Basic :  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Définissez un point d’arrêt sur la ligne qui lit, `s="Add BreakPoint Here"`.  
  
3.  Tapez la commande suivante dans le **immédiat** fenêtre : `?MyFunction<enter>`  
  
4.  Vérifiez que le point d’arrêt a été atteint et que la pile des appels est exacte.  
  
5.  Sur le **déboguer** menu, cliquez sur **continuer**et vérifiez que vous êtes toujours en mode de conception.  
  
6.  Tapez la commande suivante dans le **immédiat** fenêtre : `?MyFunction<enter>`  
  
7.  Tapez la commande suivante dans le **immédiat** fenêtre : `?MySub<enter>`  
  
8.  Vérifiez que vous atteignez le point d’arrêt et examinez la valeur de la variable statique `i` dans le **variables locales** fenêtre. Il doit avoir la valeur de 3.  
  
9. Vérifiez que la pile des appels est exacte.  
  
10. Sur le **déboguer** menu, cliquez sur **continuer**et vérifiez que vous êtes toujours en mode de conception.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)
