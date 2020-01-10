---
title: Nouveautés en matière de conception dans Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593497"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Nouveautés en matière de conception dans Visual Studio 2017

## <a name="live-dependency-validation"></a>Validation des dépendances en direct

Suppression des dépendances indésirables est une partie importante de la gestion de votre dette technique. Visual Studio fournit une validation en temps réel des dépendances, notamment des informations précises sur les problèmes, tels que l’emplacement où ils se trouvent. La validation des dépendances dynamiques tire pleinement parti des nouvelles fonctionnalités de la Liste d’erreurs et de l’éditeur.

![Validation des dépendances en direct en action](media/dep-validation-whatsnew-01.png)

L’expérience de création a changé pour rendre la validation des dépendances plus détectable et plus accessible. La terminologie est passée de « diagramme de couche » à « diagramme de dépendance ».

Le **Architecture** menu contient maintenant une commande pour créer directement un diagramme de dépendances :

![Élément de direct des dépendances dans le menu de l’Architecture](media/dep-validation-whatsnew-02.png)

Les noms et les descriptions des propriétés de couche ont été modifiés pour les rendre plus explicites :

![Noms de propriété de dépendance Live mis à jour](media/dep-validation-whatsnew-03.png)

Vous voyez immédiatement l’impact de vos modifications dans les résultats de l’analyse du code actuel dans la solution chaque fois que vous enregistrez le diagramme. Vous n’avez pas besoin d’attendre la fin de la commande **valider les dépendances** .

Pour plus d’informations, consultez [ce billet de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Des concepteurs UML ont été supprimés.

Les concepteurs UML ont été supprimés de Visual Studio.

* Diagrammes UML sont maintenant présentés en tant que fichiers XML
* L’Explorateur de modèles UML n’existe plus
* Références ne sont plus utilisés pour la validation de dépendance de projet de modélisation
* Le nœud « Références de couche » dans l’Explorateur de solutions n’est plus affiché
* L’action de génération « Valider » sur un diagramme de dépendances (couche) n’est plus utilisée : la tâche de génération a été supprimée.
* La structure de projet est conservée pour les allers-retours entre les versions
* Vous pouvez toujours ouvrir, créer, modifier et enregistrer un diagramme de dépendances (couche) au format XML
* Les éléments de travail TFS liés à un diagramme de dépendances (couche) ne sont pas accessibles sur l’aire de conception
* Liaison différé à partir de DSL ou d’une couche est n’est plus pris en charge
* Extensibilité UML dans le SDK de modélisation n’est plus pris en charge.

La prise en charge de la visualisation de l' C++ architecture de .net et du code est disponible via les [cartes de code](map-dependencies-across-your-solutions.md).

Si vous êtes un utilisateur important des concepteurs UML, vous pouvez continuer à utiliser Visual Studio 2015 ou une version antérieure alors que vous choisissez un autre outil pour vos besoins UML.

Pour plus d’informations, consultez [ce billet de blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Prise en charge de l’édition pour l’architecture et les outils de modélisation

Visual Studio est disponible dans plusieurs éditions. N’est pas en charge l’architecture et les outils de modélisation. Le tableau ci-après décrit la disponibilité de chaque outil.

|**Fonctionnalité**|**Édition entreprise**|**Édition professionnelle**|**Édition Community**|
|-|-|-|-|
|**Cartes de code**|Oui|Prend en charge la lecture de cartes de code, code de filtrage mappe uniquement, ajout de nouveaux nœuds génériques et la création d’un graphique orienté à partir d’une sélection.|-|
|**Diagrammes de dépendance**|Oui|Seulement prend en charge la lecture des diagrammes de dépendance.|Seulement prend en charge la lecture des diagrammes de dépendance.|
|**Graphiques orientés** (diagrammes DGML)|Oui|Oui|Oui|
|**Clone de code**|Oui|-|-|
