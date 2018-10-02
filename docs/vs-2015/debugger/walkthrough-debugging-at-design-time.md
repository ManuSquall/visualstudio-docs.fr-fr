---
title: 'Procédure pas à pas : Débogage au moment du Design | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd63fca37bbb55f99ecb99a18596c128451bd807
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504343"
---
# <a name="walkthrough-debugging-at-design-time"></a>Procédure pas à pas : débogage au moment du design
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [procédure pas à pas : débogage au moment du Design](https://docs.microsoft.com/visualstudio/debugger/walkthrough-debugging-at-design-time).  
  
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



