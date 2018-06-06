---
title: Débogage ASP.NET
description: Débogage ASP.NET à l’aide du débogueur Visual Studio
ms.custom: mvc
ms.date: 03/16/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: b3cfe8d0af7bebac5bce48e82b4237de071a41d8
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2018
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>Démarrage rapide : Débogage ASP.NET avec le débogueur Visual Studio

Le débogueur Visual Studio fournit de nombreuses fonctionnalités puissantes pour vous aider à déboguer vos applications. Cette rubrique vous offre un moyen rapide de vous familiariser avec quelques-unes des fonctionnalités de base.

## <a name="create-a-new-project"></a>Créer un nouveau projet 

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

1. Sous **Visual C#**, choisissez **Web**, puis, dans le volet central, choisissez **Application ASP.NET Core Web**.

1. Tapez un nom tel que **MyDbgApp** et cliquez sur **OK**.

1. Dans la boîte de dialogue qui s’affiche, choisissez **Application Web** dans le volet central, puis cliquez sur **OK**.

     Si vous ne voyez pas le **Application Web** modèle de projet, cliquez sur le **ouvrir Visual Studio Installer** lien dans le volet gauche de la **nouveau projet** boîte de dialogue. Visual Studio Installer est lancé. Choisissez le **ASP.NET** et **.NET Core** charge de travail, puis choisissez **modifier**.

    ![Choisissez une application Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio crée le projet.

1. Dans l’Explorateur de solutions, ouvrez About.cshtml.cs (sous Pages/About.cshtml) et remplacez le code suivant

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    par le code suivant :

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Définir un point d’arrêt

A *point d’arrêt* est un marqueur qui indique où Visual Studio interrompt votre en cours d’exécution de code afin de vous pouvez examiner les valeurs des variables ou le comportement de la mémoire, ou s’il faut ou non une branche de code la bonne exécution. Il s’agit de la fonctionnalité de base dans le débogage.

1. Pour définir le point d’arrêt, cliquez dans la marge à gauche de la `doWork` (fonction) (ou sélectionnez la ligne de code, puis appuyez sur **F9**).

    ![Définir un point d’arrêt](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Le point d’arrêt est défini à gauche de l’accolade ouvrante (`{`).

1. Appuyez sur **F5** (ou choisissez **Déboguer > Démarrer le débogage**).

1. Lors du chargement de la page web, cliquez sur le **sur** lien en haut de la page web.

    Les temps de pause débogueur où vous avez défini le point d’arrêt. L’instruction où l’exécution du débogueur et l’application est suspendue est indiquée par la flèche jaune. La ligne de l’accolade ouvrante (`{`) après le `doWork` déclaration de fonction n’a pas encore exécutée.

    ![Atteindre un point d’arrêt](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Si vous disposez d’un point d’arrêt dans une boucle ou une récurrence ou si vous avez plusieurs points d’arrêt que vous fréquemment parcourez, utilisez un [point d’arrêt conditionnel](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) pour vous assurer que votre code est interrompu uniquement lorsque certaines conditions sont remplies. Cela fait gagner du temps et peut également rendre plus facile à déboguer les problèmes difficiles à reproduire.

## <a name="navigate-code"></a>Naviguer dans le code

Il existe plusieurs commandes pour instruire le débogueur pour continuer. Nous affichons une commande de navigation de code utiles est une nouveauté de Visual Studio 2017.

Pendant la suspension à un point d’arrêt, placez le curseur sur l’instruction `return c2` jusqu'à ce que le vert **exécuter cliquer sur** bouton ![exécuter. Cliquez ensuite sur](../debugger/media/dbg-tour-run-to-click.png) s’affiche, puis appuyez sur la **exécuter cliquer sur** bouton.

![Exécution de cliquer sur](../debugger/media/dbg-qs-run-to-click-aspnet.png)

L’application continue l’exécution et s’arrête à la ligne de code où vous avez cliqué sur le bouton.

Les commandes clavier courantes utilisées pour parcourir le code inclure **F10** et **F11**. Pour obtenir des instructions plus détaillées, consultez le [Guide du débutant](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspecter des variables dans un datatip

1. Dans la ligne actuelle de code (indiquée par le pointeur d’exécution jaune), pointez sur le `c2` objet avec la souris pour afficher un datatip.

    ![Afficher un datatip](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Le datatip vous indique la valeur actuelle de la `c2` variable et vous permet d’inspecter ses propriétés. Lors du débogage, si vous voyez une valeur que vous ne prévoyez pas, vous avez probablement un bogue dans les lignes précédentes ou d’appel de code. 

2. Développez le datatip pour examiner les valeurs de propriété actuelles de le `c2` objet.

3. Si vous souhaitez épingler un datatip afin que vous pouvez continuer à afficher la valeur de `c2` lors de l’exécution de code, cliquez sur l’icône d’épingle petit. (Vous pouvez déplacer le datatip épinglé à un emplacement pratique).

## <a name="edit-code-and-continue-debugging"></a>Modifier le code et continuer le débogage

Si vous identifiez une modification que vous souhaitez tester dans votre code au milieu d’une session de débogage, vous pouvez le faire, trop.

1. Dans le `OnGet` (méthode), cliquez sur la deuxième instance de `result.First.Value` et modifiez `result.First.Value` à `result.Last.Value`.

1. Appuyez sur **F10** (ou **Déboguer > pas à pas principal**) plusieurs fois pour faire avancer le débogueur et exécuter le code modifié.

    ![Modifier & Continuer](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Modifier & Continuer")

    **F10** avance la déclaration de débogueur une fois, mais les étapes sur les fonctions au lieu de pas à pas détaillé dans les (le code que vous passez toujours s’exécute).

Pour plus d’informations sur l’utilisation de modifier & Continuer et sur les limitations de fonctionnalités, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment démarrer le débogueur, parcourir le code et d’inspecter des variables. Vous souhaiterez plus haut niveau sur les fonctionnalités du débogueur, ainsi que des liens vers plus d’informations.

> [!div class="nextstepaction"]
> [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)
