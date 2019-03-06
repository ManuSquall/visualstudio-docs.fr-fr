---
title: 'Procédure : Ouvrir plusieurs solutions dans Visual Studio pour Mac'
description: Découvrez comment ouvrir plusieurs solutions dans Visual Studio pour Mac, et comment ouvrir plusieurs instances de l’application.
author: conceptdev
ms.author: crdun
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.openlocfilehash: cdbe02cf3d60b460252f09764521afd240551115
ms.sourcegitcommit: 5dc74b4fdff1357df43a19f6e8a51d7bf706abd6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55768225"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Ouvrir plusieurs solutions ou instances de Visual Studio pour Mac

Par défaut, toutes les applications d’un Mac, y compris Visual Studio pour Mac, sont des applications _à instance unique_. Cela signifie que si l’application que vous souhaitez utiliser est déjà ouverte (ce qui se voit par le point sous l’icône dans le panneau d’ancrage), le fait de sélectionner de nouveau l’icône ouvre l’instance en cours d’exécution, au lieu d’une nouvelle instance. Si vous avez besoin d’instances supplémentaires de l’application, vous pouvez demander au système de les ouvrir pour vous, comme décrit dans la [section suivante](#open-a-second-instance-of-visual-studio-for-mac).

En outre, lorsque vous ouvrez une solution, le comportement par défaut est d’ouvrir la solution dans un nouvel espace de travail et de fermer l’espace de travail actuel (si nécessaire). Vous pouvez remplacer ce comportement par défaut de manière à garder l’actuel espace de travail ouvert, comme décrit dans la section [Ouvrir une deuxième solution](#open-a-second-solution-inside-a-single-instance).

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Ouvrir une deuxième instance de Visual Studio pour Mac

Pour ouvrir une deuxième instance de l’environnement de développement intégré (IDE), ouvrez l’application **Terminal** et entrez la ligne suivante :

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Ouvrir une deuxième solution dans une même instance

Pour ouvrir une autre solution à côté de votre première solution, effectuez les étapes suivantes :

1. Dans la première solution déjà ouverte, sélectionnez **Fichier** > **Ouvrir**.
2. Parcourez le système de fichiers pour trouver la solution existante.
3. Sélectionnez le fichier **.sln** et **Options** :

    ![Capture d’écran de Visual Studio pour Mac, avec le fichier .sln et Options en surbrillance](media/open-multiple-solutions-image3.png)

4. Décochez la case **Fermer l’espace de travail actif** :

    ![Capture d’écran de la boîte de dialogue Options, avec la case Fermer l’espace de travail actif décochée](media/open-multiple-solutions-image1.png)

5. Sélectionnez **Ouvrir** pour ouvrir la deuxième solution dans le Panneau Solutions.

Autre possibilité, si vous avez récemment ouvert la solution, vous pouvez suivre les étapes ci-dessous :

1. Accédez à **Fichier** > **Solutions récentes**.

    ![Capture d’écran du menu Solutions récentes](media/open-multiple-solutions-image2.png)

1. Maintenez la touche **Ctrl**appuyée, puis sélectionnez la solution. Cette combinaison permet d’ouvrir la deuxième solution dans le Panneau Solutions.

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
