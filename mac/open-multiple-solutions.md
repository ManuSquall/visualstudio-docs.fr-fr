---
title: Guide pratique pour ouvrir plusieurs solutions
description: Découvrez comment ouvrir plusieurs solutions dans Visual Studio pour Mac, et comment ouvrir plusieurs instances de l’application.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: e54f002141379d93a40df69ea070d5a64eba2f7d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493437"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Ouvrir plusieurs solutions ou instances de Visual Studio pour Mac

Par défaut, toutes les applications d’un Mac, y compris Visual Studio pour Mac, sont des applications _à instance unique_. Cela signifie que si l’application que vous souhaitez utiliser est déjà ouverte (ce qui se voit par le point sous l’icône dans le panneau d’ancrage), le fait de sélectionner de nouveau l’icône ouvre l’instance en cours d’exécution, au lieu d’une nouvelle instance. Si vous avez besoin d’instances supplémentaires de l’application, vous pouvez demander au système de les ouvrir pour vous, comme décrit dans la [section suivante](#open-a-second-instance-of-visual-studio-for-mac).

En outre, lorsque vous ouvrez une solution, le comportement par défaut est d’ouvrir la solution dans un nouvel espace de travail et de fermer l’espace de travail actuel (si nécessaire). Vous pouvez remplacer ce comportement par défaut de manière à garder l’actuel espace de travail ouvert, comme décrit dans la section [Ouvrir une deuxième solution](#open-a-second-solution-inside-a-single-instance).

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Ouvrir une deuxième instance de Visual Studio pour Mac

Pour ouvrir une deuxième instance de l’environnement de développement intégré (IDE), cliquez avec le bouton droit sur l’icône Visual Studio dans votre station d’accueil ou sur le dossier **Applications** , puis sélectionnez **Nouvelle instance**.

![Capture d’écran de l’option de menu Nouvelle instance sur l’icône Visual Studio sur laquelle l’utilisateur a cliqué avec le bouton droit](media/open-new-instance.png)

## <a name="open-a-second-solution-inside-a-single-instance"></a>Ouvrir une deuxième solution dans une même instance

Pour ouvrir une autre solution à côté de votre première solution, effectuez les étapes suivantes :

1. Une fois que votre première solution est déjà ouverte, sélectionnez **fichier**  >  **ouvrir**.
2. Parcourez le système de fichiers pour trouver la solution existante.
3. Sélectionnez le fichier **.sln** et **Options** :

    ![Capture d’écran de Visual Studio pour Mac, avec le fichier .sln et Options en surbrillance](media/open-multiple-solutions-image3.png)

4. Décochez la case **Fermer l’espace de travail actif** :

    ![Capture d’écran de la boîte de dialogue Options, avec la case Fermer l’espace de travail actif décochée](media/open-multiple-solutions-image1.png)

5. Sélectionnez **ouvrir** pour ouvrir la deuxième solution dans la fenêtre de la solution.

Autre possibilité, si vous avez récemment ouvert la solution, vous pouvez suivre les étapes ci-dessous :

1. Accédez à **fichier**  >  **solutions récentes**.

    ![Capture d’écran du menu Solutions récentes](media/open-multiple-solutions-image2.png)

1. Maintenez la touche **Ctrl** appuyée, puis sélectionnez la solution. Cette combinaison ouvre la deuxième solution dans la fenêtre de la solution.

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
