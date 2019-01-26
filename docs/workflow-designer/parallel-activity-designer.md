---
title: Concepteur de flux de travail - Concepteur d’activités Parallel
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: adc84c10f703488357adcee7739c46183f8c2e85
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925793"
---
# <a name="parallel-activity-designer"></a>Concepteur d'activités Parallel

L’activité <xref:System.Activities.Statements.Parallel> exécute simultanément une collection d’activités enfants.

## <a name="the-parallel-activity"></a>Activité parallèle

L'activité <xref:System.Activities.Statements.Parallel> stocke ses activités enfants dans une collection <xref:System.Activities.Statements.Parallel.Branches%2A>. Utilisez l'activité <xref:System.Activities.Statements.Parallel> au lieu de l'activité <xref:System.Activities.Statements.Sequence> si quelques-unes des activités enfants peuvent devenir inactives.

Le <xref:System.Activities.Statements.Parallel> activité possède un <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> propriété qui contient un utilisateur spécifié expression Visual Basic. L’activité <xref:System.Activities.Statements.Parallel> évalue cette propriété après l’exécution de chaque branche. Si elle a la valeur **True**, puis le <xref:System.Activities.Statements.Parallel> activité se termine sans exécuter les autres branches. Si le <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> ne correspond pas à **True**, puis le <xref:System.Activities.Statements.Parallel> activité se termine lorsque toutes ses activités enfants sont terminées.

### <a name="using-the-parallel-activity-designer"></a>Utilisation du concepteur d'activités Parallel

Accès le **parallèles** Concepteur d’activités dans le **flux de contrôle** catégorie de la **boîte à outils**.

Le **parallèles** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les concepteurs d’activités sont généralement placés, par exemple, à l’intérieur d’un **Séquence** Concepteur d’activités. Une fois déposé dans le Concepteur de flux de travail, il crée un <xref:System.Activities.Statements.Parallel> activité, laquelle contient par défaut un <xref:System.Activities.Activity.DisplayName%2A> de **parallèles**

Pour ajouter une activité à la <xref:System.Activities.Statements.Parallel.Branches%2A> collection de l’activité parallèle, faites glisser un autre Concepteur d’activité de la **boîte à outils** et déposez-le sur le triangle à l’intérieur de la **parallèles** Concepteur d’activités. Les triangles encadrent les activités contenues dans les branches. Il est possible d'ajouter des activités supplémentaires en répétant cette procédure. Les activités peuvent être réorganisées par glisser- déposer dans le **parallèles** Concepteur d’activités.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité Parallel dans le concepteur de workflow

Le tableau suivant répertorie les propriétés des activités parallèles et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom d'affichage convivial du concepteur d'activités dans l'en-tête. La valeur par défaut est **parallèles**. La valeur peut être modifiée si vous le souhaitez dans le **propriétés** grille ou directement sur l’en-tête du Concepteur d’activité.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contient la collection des activités enfants à exécuter.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Évaluée une fois qu’une branche est terminée. Si elle a la valeur **True**, puis planifiées branches en attente sont annulées. Si cette propriété n’est pas définie ou a la valeur **False**, l’activité se termine lorsque toutes ses activités enfants sont terminées. La valeur par défaut est **null**.|

## <a name="see-also"></a>Voir aussi

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)