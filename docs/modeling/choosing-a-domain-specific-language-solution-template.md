---
title: "Choix d’un modèle de Solution de langage spécifique à un domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 2a1ad374c709b9575ff8e3d46bb3d2178a1c3f95
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Choix d'un modèle de solution de langage spécifique à un domaine
Pour créer une solution de langage spécifique à un domaine, choisissez un des modèles de solution qui sont disponibles dans l’Assistant Générateur de langage spécifique à un domaine. En choisissant le modèle qui ressemble le plus à la langue que vous souhaitez créer, vous pouvez limiter les modifications que vous avez à faire à la solution de départ.  
  
 Les modèles de solution suivants sont disponibles dans l’Assistant Générateur de langage spécifique à un domaine.  
  
|Modèle|Fonctionnalités|Description|  
|--------------|--------------|-----------------|  
|Diagrammes de classes|-Formes de compartiment<br />-L’héritage de classes<br />: Héritage de relations<br />-Forme héritage<br />: Propriétés de relation|Utilisez ce modèle de solution si votre langage spécifique à un domaine inclut les entités et les relations qui ont des propriétés. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes de classes UML. Les entités principales sont des classes et interfaces, ainsi que les relations de généralisation, association et d’implémentation. Une classe ou interface apparaît comme une zone qui contient une liste d’attributs.|  
|Diagrammes de composants|-Ports|Utilisez ce modèle de solution si votre langage spécifique à un domaine inclut des composants, autrement dit, les parties d’un système logiciel. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes de composants UML. Les entités principales sont les ports qui apparaissent sous forme de petites formes à l’extérieur de composants et les composants.|  
|Diagrammes de flux de tâches|-L’image et des formes de géométrie<br />-   *Couloirs*|Utilisez ce modèle de solution si votre langage spécifique à un domaine inclut des flux de travail, des États ou des séquences. Ce modèle crée un langage spécifique à un domaine qui ressemble à des diagrammes d’activités UML. L’entité principale est une activité, et la relation principale est une transition entre les activités. Le modèle inclut plusieurs autres éléments tels que l’état de démarrage, état final et une barre de synchronisation.|  
|Langage minimale|-Une classe et la forme<br />-Une relation et connecteur|Utilisez ce modèle de solution si votre langage spécifique à un domaine ne ressemble pas à d’autres modèles. Ce modèle crée un langage spécifique à un domaine qui a deux classes et une relation, qui sont représentés dans le **boîte à outils** en tant que **zone** et **ligne**. La classe et la relation ont une propriété de chaîne d’exemple.|  
|Concepteur Windows Form minimale|: Un modèle petit.<br />-Un Windows Form qui affiche le modèle.|Utilisez ce modèle si vous souhaitez créer une application dans laquelle une DSL est liée à un Windows Form, plutôt qu’un concepteur graphique.<br /><br /> Le formulaire qui agit en tant que l’interface utilisateur pour la langue se trouve dans le dossier Dsl\UI.<br /><br /> Vous devez générer le projet avant d’ouvrir le Concepteur de formulaires.<br /><br /> Pour plus d’informations, consultez [création d’un langage spécifique à un domaine de Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|Concepteur WPF minimale|: Un modèle petit<br />-Une interface utilisateur Windows Presentation Foundation qui affiche le modèle|Utilisez ce modèle si vous souhaitez créer une application dans laquelle une DSL est liée à une interface utilisateur WPF, plutôt qu’un concepteur graphique.<br /><br /> Le Concepteur de l’interface utilisateur est dans le dossier Dsl\UI.<br /><br /> Vous devez générer le projet avant d’ouvrir le Concepteur de l’interface utilisateur.<br /><br /> Pour plus d’informations, consultez [création d’un langage spécifique à un domaine de WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|Bibliothèque DSL|-Une bibliothèque minimale|Utilisez ce modèle si vous souhaitez générer une définition partielle DSL qui peut être importée dans d’autres définitions DSL.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des outils de langage spécifique à un domaine](../modeling/overview-of-domain-specific-language-tools.md)
