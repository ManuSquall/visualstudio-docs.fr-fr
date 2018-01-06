---
title: "Procédure pas à pas : Débogage au moment du Design | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5869279a7bafb11368b7fb232e6ca68ca7d98478
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-at-design-time"></a>Procédure pas à pas : débogage au moment du design
Vous pouvez utiliser Visual Studio **exécution** fenêtre pour exécuter une fonction ou une sous-routine pendant que votre application n’est pas en cours d’exécution. Si la fonction ou la sous-routine contient un point d’arrêt, Visual Studio interrompt l’exécution au point approprié. Vous pouvez ensuite utiliser les fenêtres du débogueur pour examiner l’état de votre programme. Cette fonctionnalité est appelée débogage au moment du design.  
  
 La procédure suivante montre comment vous pouvez utiliser cette fonctionnalité.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Pour les points d’arrêt à partir de la fenêtre exécution  
  
1.  Collez le code suivant dans une application console Visual Basic :  
  
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
  
3.  Tapez la commande suivante dans le **exécution** fenêtre :`?MyFunction<enter>`  
  
4.  Vérifiez que le point d’arrêt a été atteint et que la pile des appels est exacte.  
  
5.  Sur le **déboguer** menu, cliquez sur **continuer**et vérifiez que vous êtes toujours en mode Création.  
  
6.  Tapez la commande suivante dans le **exécution** fenêtre :`?MyFunction<enter>`  
  
7.  Tapez la commande suivante dans le **exécution** fenêtre :`?MySub<enter>`  
  
8.  Vérifiez que vous atteignez le point d’arrêt et examinez la valeur de la variable statique `i` dans les **variables locales** fenêtre. Il doit avoir la valeur 3.  
  
9. Vérifiez que la pile des appels est exacte.  
  
10. Sur le **déboguer** menu, cliquez sur **continuer**et vérifiez que vous êtes toujours en mode Création.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)