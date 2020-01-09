---
title: Concepteur de flux de travail-concepteur d’activités parallèles
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f07dd02f682cd5c61d4d17099c1aeb76bb39bf8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593159"
---
# <a name="parallel-activity-designer"></a>Concepteur d'activités Parallel

L'activité <xref:System.Activities.Statements.Parallel> exécute simultanément une collection d'activités enfants.

## <a name="the-parallel-activity"></a>Activité parallèle

L'activité <xref:System.Activities.Statements.Parallel> stocke ses activités enfants dans une collection <xref:System.Activities.Statements.Parallel.Branches%2A>. Utilisez l'activité <xref:System.Activities.Statements.Parallel> au lieu de l'activité <xref:System.Activities.Statements.Sequence> si quelques-unes des activités enfants peuvent devenir inactives.

L’activité <xref:System.Activities.Statements.Parallel> a une propriété <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> qui contient une expression d’Visual Basic spécifiée par l’utilisateur. L’activité <xref:System.Activities.Statements.Parallel> évalue cette propriété après l’exécution de chaque branche. Si elle prend la **valeur true**, l’activité de <xref:System.Activities.Statements.Parallel> se termine sans exécuter les autres branches. Si la <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> n’a pas la **valeur true**, l’activité de <xref:System.Activities.Statements.Parallel> se termine lorsque toutes ses activités enfants sont terminées.

### <a name="using-the-parallel-activity-designer"></a>Utilisation du concepteur d'activités Parallel

Accédez au concepteur d’activités **Parallel** dans la catégorie **Flow Control** de la **boîte à outils**.

Le concepteur d’activités **Parallel** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les concepteurs d’activités sont généralement placés, par exemple dans un concepteur d’activités **Sequence** . Après l’avoir supprimée dans le Concepteur de flux de travail, elle crée une activité <xref:System.Activities.Statements.Parallel> qui, par défaut, contient un <xref:System.Activities.Activity.DisplayName%2A> de **Parallel**

Pour ajouter une activité à la collection <xref:System.Activities.Statements.Parallel.Branches%2A> de l’activité parallèle, faites glisser un autre concepteur d’activités de la **boîte à outils** et déposez-le sur le triangle à l’intérieur du concepteur d’activités **Parallel** . Les triangles encadrent les activités contenues dans les branches. Il est possible d'ajouter des activités supplémentaires en répétant cette procédure. Les activités peuvent être réorganisées en les faisant glisser et en les supprimant dans le concepteur d’activités **Parallel** .

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité Parallel dans le concepteur de workflow

Le tableau suivant répertorie les propriétés des activités parallèles et décrit comment elles sont utilisées dans le concepteur.

|Nom de propriété|Obligatoire|Contrôle|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom d'affichage convivial du concepteur d'activités dans l'en-tête. La valeur par défaut est **Parallel**. La valeur peut éventuellement être modifiée dans la grille des **Propriétés** ou directement dans l’en-tête du concepteur d’activités.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contient la collection des activités enfants à exécuter.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Évaluée une fois qu'une branche est terminée. Si elle prend la **valeur true**, les branches planifiées en attente sont annulées. Si cette propriété n’est pas définie ou a la valeur **false**, l’activité se termine lorsque toutes ses activités enfants sont terminées. La valeur par défaut est **null**.|

## <a name="see-also"></a>Voir aussi

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
