---
title: Déboguer avec le débogueur Visual Studio C++ | Documents Microsoft
ms.custom: mvc
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: f591c4272dc50643dcb3c82f60d96fd218723405
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="debug-with-c-using-the-visual-studio-debugger"></a>Déboguer avec C++ à l’aide du débogueur Visual Studio

Le débogueur Visual Studio fournit de nombreuses fonctionnalités puissantes pour vous aider à déboguer vos applications. Cette rubrique vous offre un moyen rapide de vous familiariser avec quelques-unes des fonctionnalités de base.

## <a name="create-a-new-project"></a>Créer un nouveau projet 

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

2. Sous **Visual C++**, choisissez **Windows Desktop** puis, dans le volet central, choisissez **Application console Windows**.

    Si vous ne voyez pas le **Application Console Windows** modèle de projet, cliquez sur le **ouvrir Visual Studio Installer** lien dans le volet gauche de la **nouveau projet** boîte de dialogue. Visual Studio Installer est lancé. Choisissez le **bureau développement avec C++** charge de travail, puis choisissez **modifier**.

3. Tapez un nom tel que **MyDbgApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

4. Dans MyDbgApp.cpp, remplacez le code suivant

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

## <a name="set-a-breakpoint"></a>Définir un point d’arrêt

A *point d’arrêt* est un marqueur qui indique où Visual Studio interrompt votre en cours d’exécution de code afin de vous pouvez examiner les valeurs des variables ou le comportement de la mémoire, ou s’il faut ou non une branche de code la bonne exécution. Il s’agit de la fonctionnalité de base dans le débogage.

1. Pour définir le point d’arrêt, cliquez dans la marge à gauche de la `doWork` l’appel de fonction (ou sélectionnez la ligne de code, puis appuyez sur **F9**).

    ![Définir un point d’arrêt](../debugger/media/dbg-qs-set-breakpoint.png "définir un point d’arrêt")

2. Appuyez sur **F5** (ou choisissez **Déboguer > Démarrer le débogage**).

    ![Atteindre un point d’arrêt](../debugger/media/dbg-qs-hit-breakpoint.png "atteint un point d’arrêt")

    Les temps de pause débogueur où vous avez défini le point d’arrêt. L’instruction où l’exécution du débogueur et l’application est suspendue est indiquée par la flèche jaune. La ligne avec la `doWork` appel de fonction n’a pas encore exécutée.

    > [!TIP]
    > Si vous disposez d’un point d’arrêt dans une boucle ou une récurrence ou si vous avez plusieurs points d’arrêt que vous fréquemment parcourez, utilisez un [point d’arrêt conditionnel](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) pour vous assurer que votre code est interrompu uniquement lorsque certaines conditions sont remplies. Un point d’arrêt conditionnel fait gagner du temps et peut également rendre plus facile à déboguer les problèmes difficiles à reproduire.

    Lorsque vous tentez de déboguer les erreurs relatives à la mémoire d’en C++, vous pouvez également utiliser des points d’arrêt pour inspecter des valeurs d’adresse (recherchez NULL) et décomptes de références. 

## <a name="navigate-code"></a>Naviguer dans le code

Il existe plusieurs commandes pour instruire le débogueur pour continuer. Nous affichons une commande de navigation de code utiles est une nouveauté de Visual Studio 2017.

Pendant la suspension à un point d’arrêt, placez le curseur sur l’instruction `c1.push_back(20)` jusqu'à ce que le vert **exécuter cliquer sur** bouton ![exécuter. Cliquez ensuite sur](../debugger/media/dbg-tour-run-to-click.png "RunToClick") s’affiche, puis appuyez sur la **Exécuter cliquer sur** bouton.

![Cliquez sur exécuter](../debugger/media/dbg-qs-run-to-click.png "exécuter cliquer sur")

L’application poursuit son exécution, l’appel `doWork`et s’arrête à la ligne de code où vous avez cliqué sur le bouton.

Les commandes clavier courantes utilisées pour parcourir le code inclure **F10** et **F11**. Pour obtenir des instructions plus détaillées, consultez le [Guide du débutant](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspecter des variables dans un datatip

1. Dans la ligne actuelle de code (indiquée par le pointeur d’exécution jaune), pointez sur le `c1` objet avec la souris pour afficher un datatip.

    ![Afficher un datatip](../debugger/media/dbg-qs-data-tip.png "afficher un datatip")

    Le datatip vous indique la valeur actuelle de la `c1` variable et vous permet d’inspecter ses propriétés. Lors du débogage, si vous voyez une valeur que vous ne prévoyez pas, vous avez probablement un bogue dans les lignes précédentes ou d’appel de code. 

2. Développez le datatip pour examiner les valeurs de propriété actuelles de le `c1` objet.

3. Si vous souhaitez épingler un datatip afin que vous pouvez continuer à afficher la valeur de `c1` lors de l’exécution de code, cliquez sur l’icône d’épingle petit. (Vous pouvez déplacer le datatip épinglé à un emplacement pratique).

## <a name="edit-code-and-continue-debugging"></a>Modifier le code et continuer le débogage

Si vous identifiez une modification que vous souhaitez tester dans votre code au milieu d’une session de débogage, vous pouvez le faire, trop.

1. Cliquez sur la deuxième instance de `c2.front()` et modifiez `c2.front()` à `c2.back()`.

2. Appuyez sur **F10** (ou **Déboguer > pas à pas principal**) plusieurs fois pour faire avancer le débogueur et exécuter le code modifié.

    ![Modifier & Continuer](../debugger/media/dbg-qs-edit-and-continue.gif "Modifier & Continuer")

    **F10** avance la déclaration de débogueur une fois, mais les étapes sur les fonctions au lieu de pas à pas détaillé dans les (le code que vous passez toujours s’exécute).

Pour plus d’informations sur l’utilisation de modifier & Continuer et sur les limitations de fonctionnalités, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment démarrer le débogueur, parcourir le code et d’inspecter des variables. Vous souhaiterez plus haut niveau sur les fonctionnalités du débogueur, ainsi que des liens vers plus d’informations.

> [!div class="nextstepaction"]
> [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)
