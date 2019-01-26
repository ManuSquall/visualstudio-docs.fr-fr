---
title: Choix d'un modèle de solution de langage spécifique à un domaine
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: ca1cb693977a5197bdf6adfe399ed269e0211a00
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55071070"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Choix d'un modèle de solution de langage spécifique à un domaine
Pour créer une solution de langage spécifique à un domaine, choisissez un des modèles de solution sont disponibles dans l’Assistant Concepteur de langage spécifique à un domaine. En choisissant le modèle qui ressemble le plus à la langue que vous souhaitez créer, vous pouvez limiter les modifications que vous avez à faire à la solution de départ.

 Les modèles de solution suivants sont disponibles dans l’Assistant Concepteur de langage spécifique à un domaine.

|Modèle|Fonctionnalités|Description|
|-|-|-|
|Diagrammes de classes|: Formes de compartiments<br />-L’héritage de classes<br />-L’héritage relation<br />-L’héritage forme<br />-Propriétés relation|Utilisez ce modèle de solution si votre langage spécifique à un domaine inclut les entités et les relations qui ont des propriétés. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes de classes UML. Les entités principales sont des classes et interfaces, ainsi que des relations d’association, généralisation et l’implémentation. Une classe ou interface apparaît comme une zone qui contient une liste d’attributs.|
|Diagrammes de composants|-Ports|Utilisez ce modèle de solution si votre langage spécifique à un domaine comporte des composants, autrement dit, les parties d’un système logiciel. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes de composants UML. Les entités principales sont des composants et les ports qui apparaissent sous forme de petites formes à l’extérieur des composants.|
|Diagrammes de flux de tâches|-Images et des formes géométriques<br />-   *Swimlanes*|Utilisez ce modèle de solution si votre langage spécifique à un domaine inclut des flux de travail, des États ou des séquences. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes d’activités UML. L’entité principale est une activité, et la relation principale est une transition entre les activités. Le modèle inclut plusieurs autres éléments tels que l’état de démarrage, état final et une barre de synchronisation.|
|Langage minimal|-Une classe et la forme<br />-Une relation et connecteur|Utilisez ce modèle de solution si votre langage spécifique à un domaine ne ressemble pas à d’autres modèles. Ce modèle crée un langage spécifique à un domaine qui a deux classes et une seule relation, qui sont représentés dans le **boîte à outils** comme **boîte** et **ligne**. La classe et la relation ont chacun un exemple de propriété de chaîne.|
|Concepteur WinForm minimal|-Un modèle petit.<br />-Un formulaire Windows qui affiche le modèle.|Utilisez ce modèle si vous souhaitez créer une application dans lequel une solution DSL est lié à un formulaire Windows, plutôt qu’un concepteur graphique.<br /><br /> Le formulaire qui sert d’interface utilisateur pour la langue est dans le dossier Dsl\UI.<br /><br /> Vous devez générer le projet avant d’ouvrir le Concepteur de formulaires.<br /><br /> Pour plus d’informations, consultez [création d’un langage spécifique à un domaine de Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Concepteur WPF minimal|-Un modèle petit<br />-Une interface utilisateur Windows Presentation Foundation qui affiche le modèle|Utilisez ce modèle si vous souhaitez créer une application dans lequel une solution DSL est lié à une interface utilisateur WPF, plutôt qu’un concepteur graphique.<br /><br /> Le Concepteur de l’interface utilisateur est dans le dossier Dsl\UI.<br /><br /> Vous devez générer le projet avant d’ouvrir le Concepteur d’interface utilisateur.<br /><br /> Pour plus d’informations, consultez [création d’un langage spécifique à un domaine de WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Bibliothèque DSL|-Une bibliothèque minimale|Utilisez ce modèle si vous souhaitez générer une définition DSL partielle qui peut être importée dans d’autres définitions DSL.|

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des outils de langage spécifique à un domaine](../modeling/overview-of-domain-specific-language-tools.md)
