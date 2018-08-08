---
title: Guide pratique pour ouvrir plusieurs solutions
description: Découvrez comment ouvrir plusieurs solutions dans Visual Studio pour Mac, et comment ouvrir plusieurs instances de cette application.
author: asb3993
ms.author: amburns
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.openlocfilehash: 85d300c5131dad2d6f4480fceb4770e2e8a126a5
ms.sourcegitcommit: b544e2157ac20866baf158eef9cfed3e3f1d68b9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39388491"
---
# <a name="opening-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Ouverture de plusieurs solutions ou instances de Visual Studio pour Mac

Par défaut, toutes les applications d’un Mac, y compris Visual Studio pour Mac, sont des applications _à instance unique_. Cela signifie que si l’application que vous souhaitez utiliser est déjà ouverte (ce qui se voit par le « point » qui s’affiche sous l’icône de l’application, dans le panneau d’ancrage), le fait de cliquer de nouveau sur l’icône ouvrira l’instance en cours d’exécution, plutôt qu’une nouvelle application.  Si vous avez besoin d’instances supplémentaires de l’application, vous pouvez demander au système de les ouvrir pour vous, comme décrit dans la [section suivante](#open-a-second-instance-of-visual-studio-for-mac).

En outre, lorsque vous ouvrez une solution, le comportement par défaut est d’ouvrir la solution dans un nouvel espace de travail et de fermer l’espace de travail actuel (si nécessaire). Vous pouvez remplacer ce comportement par défaut de manière à garder l’actuel espace de travail ouvert, comme décrit dans la section [Ouvrir une deuxième solution](#open-a-second-solution-inside-a-single-instance).

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Ouvrir une deuxième instance de Visual Studio pour Mac

Pour ouvrir une deuxième instance de l’IDE, ouvrez l’application **Terminal**, puis entrez la ligne suivante :

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Ouvrir une deuxième solution dans une même instance

Pour ouvrir une autre solution à côté de votre première solution, effectuez les étapes suivantes :

1. Avec votre première solution déjà ouverte, sélectionnez **Fichier > Ouvrir**.
2. Parcourez le système de fichiers pour trouver la solution existante.
3. Sélectionnez le fichier **.sln**, puis appuyez sur le bouton **Options** :
    
    ![Emplacement du bouton Options](media/open-multiple-solutions-image3.png)
4. Décochez la case **Fermer l’espace de travail en cours** :

    ![Capture d’écran de l’espace de travail en cours](media/open-multiple-solutions-image1.png)

1. Appuyez sur le bouton Ouvrir pour ouvrir la deuxième solution dans le panneau Solutions.

**Autre possibilité :** si vous avez ouvert la solution récemment, vous pouvez effectuer les étapes suivantes :

1. Accédez à Fichier > élément de menu Solutions récentes :

    ![Capture d’écran de l’élément de menu Solutions récentes](media/open-multiple-solutions-image2.png)

1. Maintenez la touche **Ctrl**appuyée, puis sélectionnez la solution. Cette combinaison permet d’ouvrir la solution dans le panneau Solutions.
