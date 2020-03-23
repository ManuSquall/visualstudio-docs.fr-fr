---
title: Génération et nettoyage des projets et des solutions
description: Cet article décrit comment générer un projet dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128456"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Génération et nettoyage des projets et des solutions

Suivez les étapes de cet article pour apprendre à construire, reconstruire ou nettoyer tous ou quelques-uns des projets dans une solution.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, voir [Construire et nettoyer les projets et solutions dans Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Pour générer, régénérer ou nettoyer une solution entière

1. Sélectionnez le nœud Solution dans le **pad solution**:

    ![Sélection du nœud de solution](media/compiling-and-building-image1.png)

2. Sélectionnez le menu **Construire** dans la barre de menu et choisissez l’une des options suivantes :

    ![Sélection de l’élément de menu Générer tout](media/compiling-and-building-image2.png)

    * Choisissez **Build All** pour compiler les fichiers et les composants du projet qui ont changé depuis la version la plus récente.

    * Choisissez **Rebuild All** pour « nettoyer » la solution, puis créez tous les fichiers et composants du projet.

    * Choisissez **Clean All** pour supprimer tous les fichiers intermédiaires et de sortie. De nouvelles instances des fichiers intermédiaires et de sortie peuvent alors être générées avec uniquement les fichiers projet et les composant restants.

## <a name="to-build-or-rebuild-a-single-project"></a>Pour générer ou régénérer un projet unique

1. Sélectionnez le projet dans le **solution Pad**.

2. Sélectionnez le menu **Construire** dans la barre de menu.

3. Choisissez soit Build[ProjectName], Rebuild[ProjectName], soit Clean[ProjectName].

## <a name="to-stop-a-build"></a>Pour arrêter une génération

Pour arrêter une build, utilisez l’une des options suivantes :

* Appuyez sur le carré rouge dans la zone d’état:

    ![Cliquer sur le carré rouge pour arrêter la génération](media/compiling-and-building-image3.png)

* Utilisez l’élément **Stop** dans le menu **Build.**

* Appuyez sur **Cmd-Shift-Return**.

## <a name="see-also"></a>Voir aussi

- [Générer et nettoyer des projets et des solutions (Visual Studio sur Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)