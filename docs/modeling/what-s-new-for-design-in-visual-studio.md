---
title: Nouveautés en matière de conception dans Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c25d89ae3ab3d25e415b4407a46fc903b1c05266
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="whats-new-for-design-in-visual-studio"></a>Nouveautés en matière de conception dans Visual Studio

## <a name="live-dependency-validation"></a>Validation de dépendance dynamique

Suppression de dépendances indésirables est une partie importante de la gestion de votre dette technique. Validation dynamique des dépendances est maintenant inclus, en fournissant des informations précises sur les problèmes et tirer pleinement des nouvelles fonctionnalités dans la liste d’erreurs et l’éditeur.

![Validation de dépendance dynamique en action](media/dep-validation-whatsnew-01.png)

L’expérience de création a changé pour effectuer la validation de dépendance plus visibles et plus accessibles, modification la terminologie à partir de « Diagramme de couche » à « Diagramme de dépendance ».

Le **Architecture** menu contient maintenant une commande permettant de créer directement un diagramme de dépendances :

![Élément de dépendance dynamique sur le menu de l’Architecture](media/dep-validation-whatsnew-02.png)

... et les noms des propriétés d’une couche dans un diagramme de dépendances et leurs descriptions, ont été modifiés pour les rendre plus explicites :

![Noms de propriété de dépendance dynamique mis à jour](media/dep-validation-whatsnew-03.png)

Vous voyez maintenant l’impact de vos modifications immédiatement dans les résultats de l’analyse du code en cours dans la solution chaque fois que vous enregistrez le diagramme. Vous n’êtes pas obligé d’attendre plus longtemps la fin de la commande « Dépendances de validation ».

Pour plus d’informations, consultez [ce billet de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Concepteurs UML ont été supprimées.

Les concepteurs UML ont été supprimées de cette version de Visual Studio Enterprise.

* Diagrammes UML sont maintenant présentés en tant que fichiers XML
* L’Explorateur de modèles UML n’existe plus
* Les références ne sont plus utilisés pour la validation de la dépendance de projet de modélisation
* Le nœud « Références de couche » dans l’Explorateur de solutions n’est plus affiché
* L’action de génération « Valider » sur un diagramme de dépendances (Layer) n’est plus utilisée, la tâche de génération a été supprimée.
* La structure de projet est conservée pour les allers-retours entre les versions
* Vous pouvez toujours ouvrir, créer, modifier et enregistrer un diagramme de dépendances (couche) au format XML
* Les éléments de travail TFS liés à un diagramme de dépendances (couche) ne sont pas accessibles sur l’aire de conception
* Liaison arrière à partir de DSL ou une couche est plus pris en charge
* Extensibilité UML dans le Kit de développement de modélisation n’est plus pris en charge.

Toutefois, la prise en charge pour visualiser l’architecture de code .NET et C++ est disponible via [cartes de code](map-dependencies-across-your-solutions.md)et les améliorations significatives apportées à la validation de dépendance décrites ci-dessus.

Si vous êtes un utilisateur significatives de concepteurs UML, vous pouvez continuer à utiliser Visual Studio 2015 ou une version antérieure alors que vous choisissez un autre outil à vos besoins UML.

Pour plus d’informations, consultez [ce billet de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-version-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Prise en charge de la version pour l’architecture et les outils de modélisation

Visual Studio 2015 est disponible dans plusieurs versions. Tous ces éléments prennent en charge l’architecture et les outils de modélisation. Le tableau ci-après décrit la disponibilité de chaque outil.

|**Fonctionnalité**|**Enterprise**|**Professionnel**|**Community**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Cartes de code**|Oui|Prend en charge la lecture de cartes de code, code de filtrage mappe uniquement, ajout de nouveaux nœuds génériques et la création d’un graphique orienté à partir d’une sélection.|-|-|
|**Diagrammes de dépendance**|Oui|Prend uniquement en charge la lecture des diagrammes de dépendance.|Prend uniquement en charge la lecture des diagrammes de dépendance.|-|
|**Graphiques orientés** (diagrammes DGML)|Oui|Oui|Oui|-|
|**Clone de code**|Oui|-|-|-|