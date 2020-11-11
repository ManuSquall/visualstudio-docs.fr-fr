---
title: Création de projets et de solutions
description: Cet article décrit comment créer des projets et des solutions dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2020
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 7ee9b23f9ede12a353f6c6fdc0f578d7f78a772c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493292"
---
# <a name="create-a-new-project"></a>Création d'un projet

## <a name="opening-the-project-creation-dialog"></a>Ouverture de la boîte de dialogue de création de projet

Il existe diverses façons de créer un projet dans Visual Studio pour Mac. La première fois que vous ouvrez Visual Studio pour Mac, la fenêtre démarrer s’affiche. À partir de là, vous pouvez choisir **nouveau** pour accéder à l’écran de création du projet.

> [!TIP]
> En outre, à partir de la fenêtre Démarrer, vous pouvez également ouvrir et Rechercher des projets et solutions récents. Vous pouvez également ouvrir des projets récents en accédant à la barre de menus et en choisissant **File > Recent Solutions** (Fichier > Solutions récentes).

![Démarrer la fenêtre avec créer un projet](media/first-run-project.png)

Si Visual Studio pour Mac est déjà ouvert avec une solution chargée, vous pouvez créer une solution en accédant à la barre de menus et en choisissant **File > New Solution** (Fichier > Nouvelle solution). La création d’une solution de cette façon ferme la solution déjà chargée.

## <a name="creating-a-new-project"></a>Création d'un projet

La boîte de dialogue **New Project** (Nouveau projet) affiche par défaut les modèles récemment utilisés, en commençant par ceux les *plus récemment utilisés*.

Si vous ne souhaitez pas utiliser un modèle récent, vous pouvez effectuer votre choix parmi les catégories proposées à gauche de la boîte de dialogue. Chaque catégorie met à votre disposition plusieurs modèles de projet. Quand vous cliquez sur un type de projet, une description apparaît sur le côté droit de l’écran.

![Écran Nouveau projet](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Configuration de votre nouveau projet

Une fois que vous avez choisi un modèle de projet, les écrans suivants vous guident tout au long des étapes de configuration nécessaires pour configurer le projet ; la procédure peut varier d’un type de projet à l’autre.

Tous les projets nécessitent un nouveau projet ainsi qu’un emplacement pour le stockage des fichiers. Si le projet fait partie d’une nouvelle solution, au lieu d’être ajouté à une solution existante, un nom de solution est également requis.

Si vous le souhaitez, à ce stade, vous pouvez également configurer les options de contrôle de code source Git. L’image suivante illustre la dernière étape de configuration d’un projet .NET Core :

![Configuration d’un nouveau projet](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Ajout de projets à une solution

Vous pouvez ajouter des projets supplémentaires à une solution en cliquant avec le bouton droit sur la solution dans la **fenêtre de solution** et en choisissant **Ajouter > ajouter un nouveau projet** ou **Ajouter > ajouter un projet existant**.

Si vous ajoutez un nouveau projet, vous entamez la procédure de création de projet, comme indiqué dans [Configuration de votre nouveau projet](#configuring-your-new-project).

Si vous choisissez d’ajouter un projet existant, vous pouvez le rechercher sur votre machine et l’ajouter à la solution.

## <a name="see-also"></a>Voir aussi

- [Créer des solutions et des projets (Visual Studio sur Windows)](/visualstudio/ide/creating-solutions-and-projects)
