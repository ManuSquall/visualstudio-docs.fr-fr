---
title: Déboguer du code C++
description: Déboguer du code natif avec le débogueur Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b619b2b6c93da8be399b2fc35d81ffe226f408ad
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679415"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Démarrage rapide : Déboguer du code C++ avec le débogueur Visual Studio

Le débogueur Visual Studio fournit de nombreuses fonctionnalités puissantes pour vous aider à déboguer vos applications. Cette rubrique vous offre un moyen rapide de vous familiariser avec quelques-unes des fonctionnalités de base.

## <a name="create-a-new-project"></a>Créer un projet

1. Ouvrez Visual Studio et créez un projet.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **Ctrl+Q** pour ouvrir la zone de recherche, tapez **c++**, choisissez **Modèles**, puis choisissez **Créer un projet d’application console**. Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, sous **Visual C++**, choisissez **Windows Desktop** puis, dans le volet central, choisissez **Application console Windows**. Tapez ensuite un nom tel que **MyDbgApp** et cliquez sur **OK**.
    ::: moniker-end

    Si vous ne voyez pas le modèle de projet **Application console Windows**, accédez à **Outils** > **Obtenir les outils et fonctionnalités...**, qui ouvre Visual Studio Installer. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement Desktop en C++**, puis choisissez **Modifier**.

    Visual Studio crée le projet.

1. Dans MyDbgApp.cpp, remplacez le code suivant

    ```c++
    int main()
    {
        return 0;
    }
    ```

    par ce code (ne supprimez pas `#include "stdafx.h"`) :

    ```c++
    #include <list>
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt

Un *point d’arrêt* est un marqueur qui indique où Visual Studio doit interrompre l’exécution du code pour vous permettre d’examiner les valeurs des variables, le comportement de la mémoire, ou l’exécution ou non d’une branche de code. C’est la fonctionnalité la plus élémentaire du débogage.

1. Pour définir le point d’arrêt, cliquez dans la marge à gauche de l’appel de la fonction `doWork` (ou sélectionnez la ligne de code et appuyez sur **F9**).

    ![Définir un point d’arrêt](../debugger/media/dbg-qs-set-breakpoint.png "Définir un point d’arrêt")

2. Appuyez maintenant sur **F5** (ou choisissez **Déboguer > Démarrer le débogage**).

    ![Atteindre un point d’arrêt](../debugger/media/dbg-qs-hit-breakpoint.png "Atteindre un point d’arrêt")

    Le débogueur se met en pause là où vous avez défini le point d’arrêt. L’instruction où l’exécution du débogueur et de l’application est en pause est indiquée par la flèche jaune. La ligne avec l’appel de la fonction `doWork` n’a pas encore été exécutée.

    > [!TIP]
    > Si vous avez défini un point d’arrêt dans une boucle ou une récurrence, ou si vous effectuez fréquemment un pas à pas dans du code contenant un grand nombre de points d’arrêt, utilisez un [point d’arrêt conditionnel](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) pour mettre en pause votre code SEULEMENT quand certaines conditions sont remplies. Un point d’arrêt conditionnel fait gagner du temps et peut également faciliter le débogage de problèmes qui sont difficiles à reproduire.

    Quand vous essayez de déboguer des échecs liés à la mémoire en C++, vous pouvez également utiliser des points d’arrêt pour inspecter des valeurs d’adresses (recherchez NULL) et des nombres de références.

## <a name="navigate-code"></a>Naviguer dans le code

Il existe différentes commandes pour indiquer au débogueur de continuer. Nous montrons une commande de navigation pratique dans le code qui est disponible à compter de Visual Studio 2017.

Avec l’exécution en pause au point d’arrêt, placez le curseur sur l’instruction `c1.push_back(20)` jusqu’à ce que le bouton vert **Exécuter jusqu’au clic** ![Exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick") apparaisse, puis appuyez sur le bouton **Exécuter jusqu’au clic**.

![Exécuter jusqu’au clic](../debugger/media/dbg-qs-run-to-click.png "Exécuter jusqu’au clic")

L’application poursuit son exécution en appelant `doWork`, puis s’arrête à la ligne de code où vous avez cliqué sur le bouton.

**F10** et **F11** sont des commandes clavier fréquemment utilisées pour avancer pas à pas dans le code. Pour des instructions plus détaillées, voir [Présentation du débogueur](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspecter des variables dans une bulle d’informations (datatip)

1. Dans la ligne de code active (indiquée par le pointeur d’exécution jaune), placez le curseur de la souris sur l’objet `c1` pour afficher un datatip.

    ![Afficher un datatip](../debugger/media/dbg-qs-data-tip.png "Afficher un datatip")

    Le datatip vous montre la valeur actuelle de la variable `c1` et vous permet d’inspecter ses propriétés. Lors du débogage, si vous remarquez une valeur que vous n’attendiez pas, vous avez probablement un bogue dans les lignes de code précédentes ou d’appel.

2. Développez le datatip pour examiner les valeurs des propriétés actuelles de l’objet `c1`.

3. Si vous voulez épingler le datatip pour continuer à voir la valeur de `c1` pendant que vous exécutez du code, cliquez sur la petite icône d’épingle. (Vous pouvez déplacer le datatip épinglé vers un emplacement approprié.)

## <a name="edit-code-and-continue-debugging"></a>Modifier le code et continuer le débogage

Si vous identifiez une modification que vous voulez tester dans votre code pendant votre session de débogage, vous pouvez également le faire.

1. Cliquez sur la deuxième instance de `c2.front()` et remplacez `c2.front()` par `c2.back()`.

2. Appuyez plusieurs fois sur **F10** (ou **Déboguer > Pas à pas principal**) pour faire avancer le débogueur et pour exécuter le code modifié.

    ![Modifier & Continuer](../debugger/media/dbg-qs-edit-and-continue.gif "Modifier & Continuer")

    **F10** fait avancer le débogueur d’une instruction à la fois, mais il effectue un pas à pas principal sur les fonctions au lieu d’un pas à pas détaillé (le code que vous ignorez s’exécute tout de même).

Pour plus d’informations sur l’utilisation de Modifier & Continuer et sur les limitations de cette fonctionnalité, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez découvert comment démarrer le débogueur, parcourir le code pas à pas et inspecter des variables. Vous pouvez obtenir une présentation générale des fonctionnalités du débogueur et suivre des liens qui donnent accès à plus d’informations.

> [!div class="nextstepaction"]
> [Présentation du débogueur](../debugger/debugger-feature-tour.md)
