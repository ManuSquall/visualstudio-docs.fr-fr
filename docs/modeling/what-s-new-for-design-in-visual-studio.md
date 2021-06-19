---
title: Nouveautés en matière de conception dans Visual Studio 2017
description: Découvrez les nouvelles fonctionnalités de conception de code, telles que la validation de dépendances dynamiques, qui sont disponibles dans Visual Studio 2017.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: ed67836507d8328a4ba394986564820c6af7308f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388098"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Nouveautés en matière de conception dans Visual Studio 2017

## <a name="live-dependency-validation"></a>Validation de dépendances dynamiques

La suppression des dépendances indésirables est une partie importante de la gestion de votre dette technique. Visual Studio fournit une validation en temps réel des dépendances, notamment des informations précises sur les problèmes, tels que l’emplacement où ils se trouvent. La validation des dépendances dynamiques tire pleinement parti des nouvelles fonctionnalités de la Liste d’erreurs et de l’éditeur.

![Validation de dépendances dynamiques en action](media/dep-validation-whatsnew-01.png)

L’expérience de création a changé pour rendre la validation des dépendances plus détectable et plus accessible. La terminologie est passée de « diagramme de couche » à « diagramme de dépendance ».

Le menu **architecture** contient maintenant une commande permettant de créer directement un diagramme de dépendance :

![Élément de dépendance dynamique dans le menu architecture](media/dep-validation-whatsnew-02.png)

Les noms et les descriptions des propriétés de couche ont été modifiés pour les rendre plus explicites :

![Noms des propriétés mises à jour des dépendances dynamiques](media/dep-validation-whatsnew-03.png)

Vous voyez immédiatement l’impact de vos modifications dans les résultats de l’analyse du code actuel dans la solution chaque fois que vous enregistrez le diagramme. Vous n’avez pas besoin d’attendre la fin de la commande **valider les dépendances** .

Pour plus d’informations, consultez [ce billet de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Les concepteurs UML ont été supprimés

Les concepteurs UML ont été supprimés de Visual Studio.

* Les diagrammes UML sont maintenant présentés sous forme de fichiers XML
* L’Explorateur de modèles UML n’existe plus
* Les références de projet de modélisation ne sont plus utilisées pour la validation de dépendance
* Le nœud « Références de couche » dans Explorateur de solutions n’est plus affiché
* L’action de génération « valider » sur un diagramme de dépendance (couche) n’est plus utilisée-la tâche de génération a été supprimée
* La structure de projet est conservée pour l’aller-retour entre les versions
* Vous pouvez toujours ouvrir, créer, modifier et enregistrer un diagramme de dépendance (couche) au format XML
* Les éléments de travail TFS liés à un diagramme de dépendance (couche) ne sont pas accessibles sur l’aire de conception
* La liaison différée de vers DSL ou une couche n’est plus prise en charge
* L’extensibilité UML dans le kit de développement logiciel de modélisation n’est plus prise en charge

La prise en charge de la visualisation de l’architecture du code .NET et C++ est disponible via les [cartes de code](map-dependencies-across-your-solutions.md).

Si vous êtes un utilisateur significatif des concepteurs UML, vous pouvez continuer à utiliser Visual Studio 2015 ou des versions antérieures tout en décidant d’un autre outil pour vos besoins UML.

Pour plus d’informations, consultez [ce billet de blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Prise en charge d’édition pour les outils d’architecture et de modélisation

Visual Studio est disponible dans plusieurs éditions. Les outils d’architecture et de modélisation ne sont pas tous pris en charge. Le tableau ci-après décrit la disponibilité de chaque outil.

|**Fonctionnalité**|**Édition entreprise**|**Édition professionnel**|**Community Edition**|
|-|-|-|-|
|**Cartes de code**|Oui|Prend uniquement en charge la lecture de cartes de code, le filtrage de cartes de code, l’ajout de nouveaux nœuds génériques et la création d’un graphique orienté à partir d’une sélection.|-|
|**Diagrammes de dépendance**|Oui|Prend uniquement en charge la lecture des diagrammes de dépendance.|Prend uniquement en charge la lecture des diagrammes de dépendance.|
|**Graphiques orientés** (diagrammes dgml)|Oui|Oui|Oui|
|**Clone de code**|Oui|-|-|
