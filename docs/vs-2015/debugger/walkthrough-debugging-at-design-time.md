---
title: 'Procédure pas à pas : débogage au moment du design | Microsoft Docs'
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
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149426"
---
# <a name="walkthrough-debugging-at-design-time"></a>Procédure pas à pas : débogage au moment du design
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser la fenêtre **exécution** Visual Studio pour exécuter une fonction ou une sous-routine pendant que votre application n’est pas en cours d’exécution. Si la fonction ou la sous-routine contient un point d’arrêt, Visual Studio interrompt l’exécution au point approprié. Vous pouvez ensuite utiliser les fenêtres du débogueur pour examiner l’état de votre programme. Cette fonctionnalité est appelée débogage au moment de la conception.  
  
 La procédure suivante montre comment vous pouvez utiliser cette fonctionnalité.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Pour atteindre des points d’arrêt à partir de la fenêtre exécution  
  
1. Collez le code suivant dans une application console Visual Basic :  
  
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
  
2. Définissez un point d’arrêt sur la ligne qui lit, `s="Add BreakPoint Here"` .  
  
3. Tapez la commande suivante dans la fenêtre **exécution** : `?MyFunction<enter>`  
  
4. Vérifiez que le point d’arrêt a été atteint et que la pile des appels est exacte.  
  
5. Dans le menu **Déboguer** , cliquez sur **Continuer**et vérifiez que vous êtes toujours en mode création.  
  
6. Tapez la commande suivante dans la fenêtre **exécution** : `?MyFunction<enter>`  
  
7. Tapez la commande suivante dans la fenêtre **exécution** : `?MySub<enter>`  
  
8. Vérifiez que vous avez atteint le point d’arrêt, puis examinez la valeur de la variable statique `i` dans la fenêtre **variables locales** . Elle doit avoir la valeur 3.  
  
9. Vérifiez que la pile des appels est précise.  
  
10. Dans le menu **Déboguer** , cliquez sur **Continuer**et vérifiez que vous êtes toujours en mode création.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)
