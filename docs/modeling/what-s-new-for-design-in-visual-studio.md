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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302951"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Nouveautés en matière de conception dans Visual Studio 2017

## <a name="live-dependency-validation"></a>Validation de dépendance en direct

La suppression des dépendances non désirées est une partie importante de la gestion de votre dette technique. Visual Studio fournit la validation en direct des dépendances, y compris des informations précises sur les questions, telles que l’endroit où ils sont situés. La validation de la dépendance en direct tire pleinement parti des nouvelles fonctionnalités de la liste d’erreurs et de l’éditeur.

![Validation de dépendance en direct en action](media/dep-validation-whatsnew-01.png)

L’expérience de rédaction a changé pour rendre la validation de la dépendance plus détectable et plus accessible. La terminologie est passée du « diagramme de couche » au « diagramme de dépendance ».

Le menu **Architecture** contient maintenant une commande pour créer directement un diagramme de dépendance :

![Article de dépendance en direct sur le menu Architecture](media/dep-validation-whatsnew-02.png)

Les noms et descriptions de propriété de couche ont été changés pour les rendre plus significatifs :

![Dépendance en direct mis à jour les noms de propriété](media/dep-validation-whatsnew-03.png)

Vous voyez immédiatement l’impact de vos modifications dans les résultats d’analyse du code actuel dans la solution chaque fois que vous enregistrez le diagramme. Vous n’avez pas à attendre l’achèvement de la commande **validate des dépendances.**

Pour plus d’informations, consultez [ce billet de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Les concepteurs d’UML ont été supprimés

Les concepteurs umL ont été retirés de Visual Studio.

* Les diagrammes UML sont maintenant présentés sous forme de fichiers XML
* L’UML Model Explorer n’existe plus
* Les références de projets de modélisation ne sont plus utilisées pour la validation de la dépendance
* Le nœud "Layer References" dans Solution Explorer n’est plus affiché
* L’action de construction "Validate" sur un diagramme de dépendance (couche) n’est plus utilisée - la tâche Build a été supprimée
* La structure du projet est maintenue pour l’aller-retour entre les versions
* Vous pouvez toujours ouvrir, créer, modifier et enregistrer un diagramme dépendance (couche) sous forme de XML
* Les éléments de travail TFS liés à un diagramme de dépendance (couche) ne sont pas accessibles sur la surface de conception
* Le retour de liaison vers DSL ou une couche n’est plus pris en charge
* L’extéabilité umL dans le SDK de modélisation n’est plus prise en charge

La prise en charge pour visualiser l’architecture du code .NET et C EST disponible sur [des cartes de code](map-dependencies-across-your-solutions.md).

Si vous êtes un utilisateur important des concepteurs UML, vous pouvez continuer à utiliser Visual Studio 2015 ou des versions antérieures pendant que vous décidez d’un outil alternatif pour vos besoins UML.

Pour plus d’informations, consultez [ce billet de blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Soutien en édition pour l’architecture et les outils de modélisation

Visual Studio est disponible en plusieurs éditions. Tous ne fournissent pas de soutien pour l’architecture et les outils de modélisation. Le tableau ci-après décrit la disponibilité de chaque outil.

|**Fonctionnalité**|**Édition Entreprise**|**Édition professionnelle**|**Édition communautaire**|
|-|-|-|-|
|**Cartes de code**|Oui|Prend uniquement en charge la lecture de cartes de code, le filtrage des cartes de code, l’ajout de nouveaux nœuds génériques et la création d’un nouveau graphique dirigé à partir d’une sélection.|-|
|**Diagrammes de dépendance**|Oui|Prend seulement en charge la lecture des diagrammes de dépendance.|Prend seulement en charge la lecture des diagrammes de dépendance.|
|**Graphiques dirigés** (diagrammes DGML)|Oui|Oui|Oui|
|**Clone de code**|Oui|-|-|
