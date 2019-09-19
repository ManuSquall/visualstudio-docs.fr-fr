---
title: Génération et nettoyage des projets et des solutions
description: Cet article décrit comment générer un projet dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128456"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Génération et nettoyage des projets et des solutions

Suivez les étapes décrites dans cet article pour savoir comment générer, régénérer ou nettoyer votre ensemble ou certains des projets d’une solution.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, consultez [générer et nettoyer des projets et des solutions dans Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Pour générer, régénérer ou nettoyer une solution entière

1. Sélectionnez le nœud de la solution dans la **panneau solutions**:

    ![Sélection du nœud de solution](media/compiling-and-building-image1.png)

2. Sélectionnez le menu **générer** dans la barre de menus et choisissez l’une des options suivantes :

    ![Sélection de l’élément de menu Générer tout](media/compiling-and-building-image2.png)

    * Choisissez **générer tout** pour compiler les fichiers et les composants dans le projet qui ont été modifiés depuis la dernière génération.

    * Choisissez **régénérer tout** pour « nettoyer » la solution, puis générez tous les fichiers et composants du projet.

    * Choisissez **nettoyer tout** pour supprimer tous les fichiers intermédiaires et de sortie. De nouvelles instances des fichiers intermédiaires et de sortie peuvent alors être générées avec uniquement les fichiers projet et les composant restants.

## <a name="to-build-or-rebuild-a-single-project"></a>Pour générer ou régénérer un projet unique

1. Sélectionnez le projet dans la **panneau solutions**.

2. Dans la barre de menus, sélectionnez le menu **générer** .

3. Choisissez Build [ProjectName], Rebuild [ProjectName] ou Clean [ProjectName].

## <a name="to-stop-a-build"></a>Pour arrêter une génération

Pour arrêter une build, utilisez l’une des options suivantes :

* Appuyez sur le carré rouge dans la zone d’État :

    ![Cliquer sur le carré rouge pour arrêter la génération](media/compiling-and-building-image3.png)

* Utilisez l’élément **arrêter** dans le menu **générer** .

* Appuyez sur **cmd + Maj + Retour**.

## <a name="see-also"></a>Voir aussi

- [Générer et nettoyer des projets et des solutions (Visual Studio sur Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)