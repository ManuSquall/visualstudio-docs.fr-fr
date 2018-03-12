---
title: "Vérifiez que votre application avec débogage d’historique | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 315a5c06a1ecda7976f17e20a299daed5dad65bd
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Vérifiez que votre application avec débogage dans Visual Studio historique d’IntelliTrace
Vous pouvez utiliser [le débogage d’historique](../debugger/historical-debugging.md) à déplacer vers le haut et vers l’avant dans l’exécution de votre application et inspecter son état.  
  
Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise edition, mais pas les éditions Professional ou Community.  
  
## <a name="navigate-your-code-with-historical-debugging"></a>Parcourir votre code avec le débogage d’historique  
 Commençons par un programme simple qui comporte un bogue. Dans une application de console C#, ajoutez le code suivant :  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Nous supposons que la valeur attendue de `resultInt` après avoir appelé `AddAll()` est 20 (le résultat de l’incrémentation `testInt` 20 fois). (Nous supposons également que vous ne voyez pas le bogue dans `AddInt()`). Mais le résultat est bien 44. Comment trouver le bogue sans parcourir 10 fois `AddAll()` ? Nous pouvons utiliser le débogage d’historique pour rechercher le bogue plus rapidement et facilement. Voici comment :  
  
1.  Dans **Outils > Options > IntelliTrace > Général**, vérifiez qu’IntelliTrace est activé, puis sélectionnez **événements IntelliTrace et informations d’appels**. Si vous ne sélectionnez pas cette option, vous ne verrez pas la marge de navigation (comme expliqué ci-dessous).  
  
2.  Définissez un point d'arrêt sur la ligne `Console.WriteLine(resultInt);`.  
  
3.  Démarrez le débogage. Le code s'exécute jusqu'au point d'arrêt. Dans le **variables locales** fenêtre, vous pouvez voir que la valeur de `resultInt` est 44.  
  
4.  Ouvrez le **outils de Diagnostic** fenêtre (**Déboguer > Afficher les outils de Diagnostic**). La fenêtre de code doit ressembler à ce qui suit :  
  
     ![Fenêtre de code sur le point d’arrêt](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Vous devez voir une double flèche en regard de la marge de gauche, juste au-dessus du point d'arrêt. Cette zone est appelée la marge de navigation et est utilisée pour le débogage d’historique. Cliquez sur la flèche.  
  
     Dans la fenêtre de code, vous devez voir que la ligne de code précédente (`int resultInt = AddIterative(testInt);`) est de couleur rose. Au-dessus de la fenêtre, vous devez voir un message que vous êtes maintenant dans le débogage d’historique.  
  
     La fenêtre de code doit maintenant ressembler à ceci :  
  
     ![fenêtre de code en mode débogage historique](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Maintenant que vous pouvez exécuter dans le `AddAll()` (méthode) (**F11**, ou **pas à pas détaillé** bouton dans la marge de navigation. Avancez (**F10**, ou **aller à l’appel suivant** dans la marge de navigation. Le trait rose est désormais sur la ligne `j = AddInt(j);`. **F10** dans ce cas ne permet pas d’accéder à la ligne suivante de code. En fait, vous accédez à l'appel de fonction suivant. Le débogage d'historique permet de naviguer d'un appel à l'autre. Il ignore les lignes de code qui n'incluent pas d'appel de fonction.  
  
7.  Maintenant, effectuez un pas à pas détaillé de la méthode `AddInt()`. Vous devez voir immédiatement le bogue dans ce code.  

## <a name="next-steps"></a>Étapes suivantes

Cette procédure ne présente que succinctement ce que vous pouvez faire avec le débogage d’historique.

- Pour afficher des instantanés pendant le débogage, consultez [afficher des instantanés à l’aide d’IntelliTrace étape différée](../debugger/how-to-use-intellitrace-step-back.md).
- Pour plus d’informations sur les différents paramètres et les effets des différents boutons de la marge de navigation, consultez [des fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).