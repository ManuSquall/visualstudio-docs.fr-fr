---
title: Débogage d’historique | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d43e48b67cdbfabcb38703469f8570f78336dcab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794593"
---
# <a name="historical-debugging"></a>Débogage d'historique
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogage d'historique est un mode de débogage qui repose sur les informations recueillies par IntelliTrace. Il vous permet de parcourir l'exécution de votre application et d'inspecter son état.  
  
 Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise Edition (mais pas dans les éditions Professional ou Community).  
  
## <a name="why-use-historical-debugging"></a>Pourquoi utiliser le débogage d'historique ?  
 La définition de points d'arrêt pour rechercher des bogues peut être assez aléatoire. Vous définissez un point d'arrêt proche de l'endroit dans votre code où vous pensez que se trouve le bogue, puis vous exécutez l'application dans le débogueur en espérant que votre point d'arrêt soit atteint et que l'endroit où l'exécution s'arrête puisse révéler la source du bogue. Si ce n'est pas le cas, vous devez essayer de définir un point d'arrêt autre part dans le code puis réexécuter le débogueur, en réexécutant vos étapes de façon répétée jusqu'à ce que vous puissiez identifier le problème.  
  
 ![définir un point d’arrêt](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Vous pouvez utiliser IntelliTrace et le débogage d'historique pour parcourir votre application et inspecter son état (pile des appels et variables locales) sans avoir à définir des points d'arrêt, à redémarrer le débogage et à répéter les étapes de test. Vous pouvez gagner beaucoup de temps, en particulier quand le bogue se trouve loin dans un scénario de test dont l'exécution est  très longue.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Comment utiliser le débogage d'historique ?  
 IntelliTrace est activé par défaut. Tout ce que vous avez à faire, c'est identifier les événements et les appels de fonction qui vous intéressent. Pour plus d’informations sur la définition de ce que vous voulez rechercher, consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md). Pour un compte de pas à pas de débogage avec IntelliTrace, consultez [procédure pas à pas : utilisation d’IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
## <a name="navigating-your-code-with-historical-debugging"></a>Navigation dans votre code avec le débogage d'historique  
 Commençons par un programme simple qui contient un bogue. Dans une application de console C#, ajoutez le code suivant :  
  
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
  
 Nous partons du principe que la valeur attendue de `resultInt` après avoir appelé `AddAll()` est 20 (le résultat de 20 incrémentations de `testInt`). (Nous partons également du principe que vous ne voyez pas le bogue dans `AddInt()`). Mais le résultat est bien 44. Comment trouver le bogue sans parcourir 10 fois `AddAll()` ? Nous pouvons utiliser le débogage d'historique pour simplifier et accélérer l'identification du bogue. Voici comment :  
  
1. Dans Outils / Options / IntelliTrace / Général, assurez-vous qu'IntelliTrace est activé et sélectionnez l'option Événements IntelliTrace et informations d'appel. Si vous ne sélectionnez pas cette option, vous ne verrez pas la marge de navigation (comme expliqué ci-dessous).  
  
2. Définissez un point d'arrêt sur la ligne `Console.WriteLine(resultInt);`.  
  
3. Démarrez le débogage. Le code s'exécute jusqu'au point d'arrêt. Dans le **variables locales** fenêtre, vous pouvez voir que la valeur de `resultInt` est 44.  
  
4. Ouvrez le **outils de Diagnostic** fenêtre (**déboguer / afficher les outils de Diagnostic**). La fenêtre de code doit ressembler à ce qui suit :  
  
    ![Fenêtre de code sur le point d’arrêt](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. Vous devez voir une double flèche en regard de la marge de gauche, juste au-dessus du point d'arrêt. Cette zone est appelée « marge de navigation » et est utilisée pour le débogage d'historique. Cliquez sur la flèche.  
  
    Dans la fenêtre de code, vous devez voir que la ligne de code précédente (`int resultInt = AddIterative(testInt);`) est de couleur rose. Au-dessus de la fenêtre, vous devez voir un message indiquant que vous êtes en mode de débogage d'historique.  
  
    La fenêtre de code doit maintenant ressembler à ceci :  
  
    ![fenêtre de code en mode débogage d’historique](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. Maintenant que vous pouvez entrer dans le `AddAll()` (méthode) (**F11**, ou le **pas à pas détaillé** bouton dans la marge de navigation. Avancez (**F10**, ou **accédez à l’appel suivant** dans la marge de navigation. Le trait rose est désormais sur la ligne `j = AddInt(j);`. **F10** dans ce cas ne pas d’accéder à la ligne de code suivante. En fait, vous accédez à l'appel de fonction suivant. Le débogage d'historique permet de naviguer d'un appel à l'autre. Il ignore les lignes de code qui n'incluent pas d'appel de fonction.  
  
7. Maintenant, effectuez un pas à pas détaillé de la méthode `AddInt()`. Vous devez voir immédiatement le bogue dans ce code.  
  
   Cette procédure ne présente que succinctement ce que vous pouvez faire avec le débogage d'historique. Pour en savoir plus sur les différents paramètres et les effets des différents boutons dans la marge de navigation, consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).





