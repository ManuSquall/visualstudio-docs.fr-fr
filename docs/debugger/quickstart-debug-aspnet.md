---
title: ASP.NET Core de débogage
description: ASP.NET Core de débogage à l’aide du débogueur Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 882a192a96764356e90d78498ef5ed5ccd29ce25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908340"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Démarrage rapide : déboguer ASP.NET Core avec le débogueur Visual Studio

Le débogueur Visual Studio fournit de nombreuses fonctionnalités puissantes pour vous aider à déboguer vos applications. Cette rubrique vous offre un moyen rapide de vous familiariser avec quelques-unes des fonctionnalités de base.

## <a name="create-a-new-project"></a>Création d'un projet

1. Ouvrez Visual Studio.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **Ctrl+Q** pour ouvrir la zone de recherche, tapez **asp.net**, choisissez **Modèles**, puis choisissez **Créer une application web ASP.NET Core**. Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, sous **Visual C#**, choisissez **Web** puis, dans le volet central, choisissez **Application web ASP.NET Core**. Tapez un nom comme **MyDbgApp**, puis cliquez sur **OK**.

    Dans la boîte de dialogue qui s’affiche, choisissez **Application web** dans le volet central, puis cliquez sur **OK**.

    ![Choisir une application web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    Si vous ne voyez pas le modèle de projet **Application web ASP.NET Core**, accédez à **Outils** > **Obtenir les outils et fonctionnalités...**, qui ouvre Visual Studio Installer. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

    Visual Studio crée le projet.

1. Dans l’Explorateur de solutions, ouvrez About.cshtml.cs (sous pages/About.cshtml) et remplacez le code suivant

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    par ce code :

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

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt

Un *point d’arrêt* est un marqueur qui indique où Visual Studio doit interrompre l’exécution du code pour vous permettre d’examiner les valeurs des variables, le comportement de la mémoire, ou l’exécution ou non d’une branche de code. C’est la fonctionnalité la plus élémentaire du débogage.

1. Pour définir le point d’arrêt, cliquez dans la marge à gauche de la fonction `doWork` (ou sélectionnez la ligne de code et appuyez sur **F9**).

    ![Définir un point d'arrêt](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Le point d’arrêt est défini à gauche de l’accolade ouvrante (`{`).

1. Appuyez maintenant sur **F5** (ou choisissez **Déboguer > Démarrer le débogage**).

1. Une fois la page web chargée, cliquez sur le lien **À propos de** en haut de la page web.

    Le débogueur se met en pause là où vous avez défini le point d’arrêt. L’instruction où l’exécution du débogueur et de l’application est en pause est indiquée par la flèche jaune. La ligne avec l’accolade ouvrante (`{`) après la déclaration de la fonction `doWork` n’a pas encore été exécutée.

    ![Atteindre un point d’arrêt](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Si vous avez défini un point d’arrêt dans une boucle ou une récurrence, ou si vous effectuez fréquemment un pas à pas dans du code contenant un grand nombre de points d’arrêt, utilisez un [point d’arrêt conditionnel](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) pour mettre en pause votre code SEULEMENT quand certaines conditions sont remplies. Ceci fait gagner du temps et peut également faciliter le débogage de problèmes qui sont difficiles à reproduire.

## <a name="navigate-code"></a>Naviguer dans le code

Il existe différentes commandes pour indiquer au débogueur de continuer. Nous montrons une commande de navigation pratique dans le code qui est disponible à compter de Visual Studio 2017.

Avec l’exécution en pause au point d’arrêt, placez le curseur sur l’instruction `return c2` jusqu’à ce que le bouton vert **Exécuter jusqu’au clic**![Exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png) apparaisse, puis appuyez sur le bouton **Exécuter jusqu’au clic**.

![Exécuter jusqu’au clic](../debugger/media/dbg-qs-run-to-click-aspnet.png)

L’application poursuit son exécution, puis se met en pause sur la ligne de code où vous avez cliqué sur le bouton.

**F10** et **F11** sont des commandes clavier fréquemment utilisées pour avancer pas à pas dans le code. Pour des instructions plus détaillées, voir [Présentation du débogueur](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspecter des variables dans une bulle d’informations (datatip)

1. Dans la ligne de code active (indiquée par le pointeur d’exécution jaune), placez le curseur de la souris sur l’objet `c2` pour afficher un datatip.

    ![Afficher un datatip](../debugger/media/dbg-qs-data-tip-aspnet.png)

    La bulle d’informations (datatip) vous montre la valeur actuelle de la variable `c2` et vous permet d’inspecter ses propriétés. Lors du débogage, si vous remarquez une valeur que vous n’attendiez pas, vous avez probablement un bogue dans les lignes de code précédentes ou d’appel.

2. Développez le datatip pour examiner les valeurs des propriétés actuelles de l’objet `c2`.

3. Si vous voulez épingler le datatip pour continuer à voir la valeur de `c2` pendant que vous exécutez du code, cliquez sur la petite icône d’épingle. (Vous pouvez déplacer le datatip épinglé vers un emplacement approprié.)

## <a name="edit-code-and-continue-debugging"></a>Modifier le code et continuer le débogage

Si vous identifiez une modification que vous voulez tester dans votre code pendant votre session de débogage, vous pouvez également le faire.

1. Dans la méthode `OnGet`, cliquez sur la deuxième instance de `result.First.Value` et remplacez `result.First.Value` par `result.Last.Value`.

1. Appuyez plusieurs fois sur **F10** (ou **Déboguer > Pas à pas principal**) pour faire avancer le débogueur et pour exécuter le code modifié.

    ![Modifier & continuer](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Modifier & Continuer")

    **F10** fait avancer le débogueur d’une instruction à la fois, mais il effectue un pas à pas principal sur les fonctions au lieu d’un pas à pas détaillé (le code que vous ignorez s’exécute tout de même).

Pour plus d’informations sur l’utilisation de Modifier & Continuer et sur les limitations de cette fonctionnalité, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez découvert comment démarrer le débogueur, parcourir le code pas à pas et inspecter des variables. Vous pouvez obtenir une présentation générale des fonctionnalités du débogueur et suivre des liens qui donnent accès à plus d’informations.

> [!div class="nextstepaction"]
> [Présentation du débogueur](../debugger/debugger-feature-tour.md)
