---
title: Choix d'un modèle de solution de langage spécifique à un domaine
description: Découvrez comment créer une solution de langage spécifique à un domaine en choisissant l’un des modèles de solution disponibles dans l’Assistant Domain-Specific Language designer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1c638c5a45427fd474f085ff58c9d38682ee054
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385433"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Choix d'un modèle de solution de langage spécifique à un domaine
Pour créer une solution de langage spécifique à un domaine, choisissez l’un des modèles de solution disponibles dans l’Assistant Domain-Specific Language designer. En choisissant le modèle qui ressemble le plus à la langue que vous souhaitez créer, vous pouvez réduire les modifications que vous devez apporter à la solution de démarrage.

 Les modèles de solution suivants sont disponibles dans l’Assistant Domain-Specific Language designer.

|Modèle|Fonctionnalités|Description|
|-|-|-|
|Diagrammes de classes|-Formes de compartiments<br />-Héritage de classe<br />-Héritage de la relation<br />-Héritage de forme<br />-Propriétés de la relation|Utilisez ce modèle de solution si votre langage spécifique à un domaine comprend des entités et des relations qui ont des propriétés. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes de classes UML. Les entités principales sont des classes et des interfaces, ainsi que des relations d’association, de généralisation et d’implémentation. Une classe ou une interface apparaît sous la forme d’une zone qui contient une liste d’attributs.|
|Diagrammes de composants|-Ports|Utilisez ce modèle de solution si votre langage spécifique à un domaine comprend des composants, c’est-à-dire des parties d’un système logiciel. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes de composants UML. Les entités principales sont des composants et des ports, qui apparaissent sous forme de petites formes à l’extérieur des composants.|
|Diagrammes de déroulement des tâches|-Formes image et Geometry<br />-   *Couloir*|Utilisez ce modèle de solution si votre langage spécifique à un domaine comprend des flux de travail, des États ou des séquences. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes d’activités UML. L’entité principale est une activité et la relation principale est une transition entre les activités. Le modèle comprend plusieurs autres éléments tels que l’état de démarrage, l’état final et une barre de synchronisation.|
|Langage minimal|-Une classe et une forme<br />-Une relation et un connecteur|Utilisez ce modèle de solution si votre langage spécifique à un domaine ne ressemble pas aux autres modèles. Ce modèle crée un langage spécifique à un domaine qui a deux classes et une relation, qui sont représentées dans la boîte **à outils** sous la forme d’une **zone** et d’une **ligne**. La classe et la relation ont chacune un exemple de propriété de chaîne.|
|Concepteur WinForm minimal|-Petit modèle.<br />-Un Windows Form qui affiche le modèle.|Utilisez ce modèle si vous souhaitez générer une application dans laquelle un DSL est lié à un Windows Form, plutôt qu’à un concepteur graphique.<br /><br /> Le formulaire qui agit en tant qu’interface utilisateur pour la langue se trouve dans le dossier Dsl\UI.<br /><br /> Vous devez générer le projet avant d’ouvrir le concepteur de formulaires.<br /><br /> Pour plus d’informations, voir [Creating a Windows Forms-Based Domain-Specific Language](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Concepteur WPF minimal|-Un petit modèle<br />-Interface utilisateur Windows Presentation Foundation qui affiche le modèle.|Utilisez ce modèle si vous souhaitez générer une application dans laquelle un DSL est lié à une interface utilisateur WPF, plutôt qu’un concepteur graphique.<br /><br /> Le concepteur de l’interface utilisateur se trouve dans le dossier Dsl\UI.<br /><br /> Vous devez générer le projet avant d’ouvrir le concepteur d’interface utilisateur.<br /><br /> Pour plus d’informations, consultez [création d’un WPF-Based Domain-Specific langage](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Bibliothèque DSL|-Bibliothèque minimale|Utilisez ce modèle si vous souhaitez générer une définition DSL partielle qui peut être importée dans d’autres définitions DSL.|

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des outils de langage spécifique à un domaine](../modeling/overview-of-domain-specific-language-tools.md)
