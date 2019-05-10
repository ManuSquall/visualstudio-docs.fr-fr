---
title: Nouveautés en matière de conception dans Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: dc75c7414e0fff18f76d14f8f9a4e0779a9e7a2b
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476533"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Nouveautés en matière de conception dans Visual Studio 2017

## <a name="live-dependency-validation"></a>Validation des dépendances en direct

Suppression des dépendances indésirables est une partie importante de la gestion de votre dette technique. Visual Studio fournit une validation en direct des dépendances, notamment des informations précises sur les problèmes, tels qu’où ils se trouvent. Direct des dépendances validation prend tous les avantages de nouvelles fonctionnalités dans la liste d’erreurs et de l’éditeur.

![Validation des dépendances en direct en action](media/dep-validation-whatsnew-01.png)

L’expérience de création a changé pour que la validation des dépendances plus détectable et plus accessible. La terminologie a changé depuis « Diagramme de couche » à « Diagramme de dépendance ».

Le **Architecture** menu contient maintenant une commande pour créer directement un diagramme de dépendances :

![Élément de direct des dépendances dans le menu de l’Architecture](media/dep-validation-whatsnew-02.png)

Les noms de propriétés de couche et descriptions ont été modifiées pour les rendre plus explicites :

![Noms de propriété de dépendance Live mis à jour](media/dep-validation-whatsnew-03.png)

Vous voyez immédiatement l’impact de vos modifications dans les résultats d’analyse du code en cours dans la solution chaque fois que vous enregistrez le diagramme. Vous n’êtes pas obligé d’attendre la fin de la **valider les dépendances** commande.

Pour plus d’informations, consultez [ce billet de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Des concepteurs UML ont été supprimés.

Les concepteurs UML ont été supprimés à partir de Visual Studio.

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

Prise en charge permettant de visualiser l’architecture de .NET et C++ code est disponible via [cartes de code](map-dependencies-across-your-solutions.md).

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