---
title: Concepteur d’activités Concepteur de flux de travail-Delay
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5190807bba08f05e176acc15ac8daf42ac028c50
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650548"
---
# <a name="delay-activity-designer"></a>Concepteur d'activités Delay

Le concepteur d’activités **delay** est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.Delay>.

## <a name="the-delay-activity"></a>Activité Delay

L'activité <xref:System.Activities.Statements.Delay> retarde l'exécution d'un workflow pour une durée spécifiée.

### <a name="use-the-delay-activity-designer"></a>Utiliser le concepteur d’activités Delay

Le concepteur d’activités **delay** se trouve dans la catégorie **primitives** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** de la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** +**ALT** +**X**.

Le concepteur d’activités **delay** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. La suppression du concepteur d’activités crée une activité <xref:System.Activities.Statements.Delay> avec un <xref:System.Activities.Activity.DisplayName%2A> par défaut Delay. La <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **delay** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-delay-properties"></a>Propriétés Delay

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Delay> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d’entre elles peuvent être modifiées sur l’aire de Concepteur de flux de travail.

|Nom de propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Delay>. La valeur par défaut est Delay. Bien que la valeur de <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d’en utiliser une.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Durée pendant laquelle retarder le workflow. Cette propriété est définie dans la grille des propriétés. Tapez une valeur <xref:System.TimeSpan> littérale au format 00:00:00 ou une expression Visual Basic pour spécifier la durée.|

## <a name="see-also"></a>Voir aussi

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Concepteur d’activités Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)