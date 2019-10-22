---
title: Choix d’un modèle de solution de langage spécifique à un domaine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6522e3a1ad10f221f0ed7fc1761559ee9bc3f9b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668352"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Choix d'un modèle de solution de langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour créer une solution de langage spécifique à un domaine, choisissez l’un des modèles de solution disponibles dans l’Assistant Concepteur Domain-Specific Language. En choisissant le modèle qui ressemble le plus à la langue que vous souhaitez créer, vous pouvez réduire les modifications que vous devez apporter à la solution de démarrage.

 Les modèles de solution suivants sont disponibles dans l’Assistant Concepteur Domain-Specific Language.

> [!NOTE]
> L’objectif des modèles est de fournir un DSL de départ. Les modèles nommés classes et diagrammes de composants ne sont pas des diagrammes UML complets. Si vous souhaitez créer un modèle UML, prenez en compte les outils de modélisation UML, qui fournissent un ensemble de diagrammes intégrés autour d’un modèle unique. Ils sont extensibles et peuvent être intégrés à votre solution DSL à l'aide de ModelBus. Pour plus d’informations, consultez [créer des modèles pour votre application](../modeling/create-models-for-your-app.md).

|Modèle|Fonctionnalités|Description|
|--------------|--------------|-----------------|
|Diagrammes de classes|-Formes de compartiments<br />-Héritage de classe<br />-Héritage de la relation<br />-Héritage de forme<br />-Propriétés de la relation|Utilisez ce modèle de solution si votre langage spécifique à un domaine comprend des entités et des relations qui ont des propriétés. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes de classes UML. Les entités principales sont des classes et des interfaces, ainsi que des relations d’association, de généralisation et d’implémentation. Une classe ou une interface apparaît sous la forme d’une zone qui contient une liste d’attributs.|
|Diagrammes de composants|-Ports|Utilisez ce modèle de solution si votre langage spécifique à un domaine comprend des composants, c’est-à-dire des parties d’un système logiciel. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes de composants UML. Les entités principales sont des composants et des ports, qui apparaissent sous forme de petites formes à l’extérieur des composants.|
|Diagrammes de déroulement des tâches|-Formes image et Geometry<br />*couloirs* de -   |Utilisez ce modèle de solution si votre langage spécifique à un domaine comprend des flux de travail, des États ou des séquences. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes d’activités UML. L’entité principale est une activité et la relation principale est une transition entre les activités. Le modèle comprend plusieurs autres éléments tels que l’état de démarrage, l’état final et une barre de synchronisation.|
|Langage minimal|-Une classe et une forme<br />-Une relation et un connecteur|Utilisez ce modèle de solution si votre langage spécifique à un domaine ne ressemble pas aux autres modèles. Ce modèle crée un langage spécifique à un domaine qui a deux classes et une relation, qui sont représentées dans la boîte **à outils** sous la forme d’une **zone** et d’une **ligne**. La classe et la relation ont chacune un exemple de propriété de chaîne.|
|Concepteur WinForm minimal|-Petit modèle.<br />-Un Windows Form qui affiche le modèle.|Utilisez ce modèle si vous souhaitez générer une application dans laquelle un DSL est lié à un Windows Form, plutôt qu’à un concepteur graphique.<br /><br /> Le formulaire qui agit en tant qu’interface utilisateur pour la langue se trouve dans le dossier Dsl\UI.<br /><br /> Vous devez générer le projet avant d’ouvrir le concepteur de formulaires.<br /><br /> Pour plus d’informations, consultez [création d’un langage spécifique à un domaine basé sur Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Concepteur WPF minimal|-Un petit modèle<br />-Interface utilisateur Windows Presentation Foundation qui affiche le modèle.|Utilisez ce modèle si vous souhaitez générer une application dans laquelle un DSL est lié à une interface utilisateur WPF, plutôt qu’un concepteur graphique.<br /><br /> Le concepteur de l’interface utilisateur se trouve dans le dossier Dsl\UI.<br /><br /> Vous devez générer le projet avant d’ouvrir le concepteur d’interface utilisateur.<br /><br /> Pour plus d’informations, consultez [création d’un langage spécifique à un domaine basé sur WPF](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Bibliothèque DSL|-Bibliothèque minimale|Utilisez ce modèle si vous souhaitez générer une définition DSL partielle qui peut être importée dans d’autres définitions DSL.|

## <a name="see-also"></a>Voir aussi
 [Vue d’ensemble des outils de langage spécifique à un domaine](../modeling/overview-of-domain-specific-language-tools.md)
