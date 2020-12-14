---
title: Inspecter votre application avec le débogage d’historique | Microsoft Docs
description: Suivez une investigation qui utilise le débogage d’historique IntelliTrace pour détecter un bogue dans une application console C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d51327f67429071d08f6dfd02c0ec0a1fc55822f
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398699"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio-c-visual-basic-c"></a>Inspecter votre application avec le débogage d’historique IntelliTrace dans Visual Studio (C#, Visual Basic, C++)

Vous pouvez utiliser le [débogage d’historique](../debugger/historical-debugging.md) pour vous déplacer vers l’avant et l’arrière dans l’exécution de votre application et inspecter son état.

Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise Edition, mais pas dans les éditions Professional ou Community.

## <a name="navigate-your-code-with-historical-debugging"></a>Naviguer dans votre code avec le débogage d’historique

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

Nous partons du principe que la valeur attendue de `resultInt` après l’appel de `AddAll()` est 20 (le résultat de 20 incrémentations de `testInt`). (Nous partons également du principe que vous ne pouvez pas voir le bogue dans `AddInt()` ). Mais le résultat est en fait 44. Comment trouver le bogue sans parcourir 10 fois `AddAll()` ? Nous pouvons utiliser le débogage d’historique pour simplifier et accélérer l’identification du bogue. Voici comment faire :

1. Dans **outils > Options > intellitrace > général**, assurez-vous qu’IntelliTrace est activé, puis sélectionnez **événements IntelliTrace et informations sur les appels**. Si vous ne sélectionnez pas cette option, vous ne verrez pas la marge de navigation (comme expliqué ci-dessous).

2. Définissez un point d’arrêt sur la ligne `Console.WriteLine(resultInt);` .

3. Démarrez le débogage. Le code s'exécute jusqu'au point d'arrêt. Dans la fenêtre **Variables locales**, vous pouvez constater que la valeur de `resultInt` est 44.

4. Ouvrez la fenêtre **Outils de diagnostic** (**Déboguer > Afficher les outils de diagnostic**). La fenêtre de code doit ressembler à ce qui suit :

    ![Fenêtre de code au point d'arrêt](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")

5. Vous devez voir une double flèche en regard de la marge de gauche, juste au-dessus du point d'arrêt. Cette zone est appelée « marge de navigation » et est utilisée pour le débogage d’historique. Cliquez sur la flèche.

    Dans la fenêtre de code, vous devez voir que la ligne de code précédente (`int resultInt = AddIterative(testInt);`) est de couleur rose. Au-dessus de la fenêtre, vous devez voir un message indiquant que vous êtes en mode de débogage d’historique.

    La fenêtre de code doit maintenant ressembler à ceci :

    ![fenêtre de code en mode débogage d’historique](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")

6. À présent, vous pouvez effectuer un pas à pas détaillé dans la méthode `AddAll()` (appuyez sur la touche **F11** ou sur le bouton **Pas à pas détaillé** dans la marge de navigation). Avancez (touche **F10** ou bouton **Aller à l’appel suivant** dans la marge de navigation). Le trait rose est désormais sur la ligne `j = AddInt(j);`. Appuyer sur la touche **F10** dans ce cas ne permet pas d’accéder à la ligne de code suivante. En fait, vous accédez à l'appel de fonction suivant. Le débogage d'historique permet de naviguer d'un appel à l'autre. Il ignore les lignes de code qui n'incluent pas d'appel de fonction.

7. Maintenant, effectuez un pas à pas détaillé de la méthode `AddInt()`. Vous devez voir immédiatement le bogue dans ce code.

## <a name="next-steps"></a>Étapes suivantes

Cette procédure ne présente que succinctement ce que vous pouvez faire avec le débogage d’historique.

- Pour afficher les instantanés pendant le débogage, consultez [inspecter les États d’application précédents à l’aide d’IntelliTrace](../debugger/view-historical-application-state.md).
- Pour en savoir plus sur les différents paramètres et les effets des différents boutons de la marge de navigation, consultez [Fonctionnalités d’IntelliTrace](../debugger/intellitrace-features.md).
