---
title: Concepteur d’activités Concepteur de flux de travail-Delay
description: Découvrez les activités de délai et comment vous pouvez utiliser le concepteur d’activités Delay pour créer et configurer une activité Delay.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e6bbadcbabbe1dbd274c48f2325217c17d3933d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438085"
---
# <a name="delay-activity-designer"></a>Concepteur d'activités Delay

Le concepteur d’activités **delay** est utilisé pour créer et configurer une <xref:System.Activities.Statements.Delay> activité.

## <a name="the-delay-activity"></a>Activité Delay

L'activité <xref:System.Activities.Statements.Delay> retarde l'exécution d'un workflow pour une durée spécifiée.

### <a name="use-the-delay-activity-designer"></a>Utiliser le concepteur d’activités Delay

Le concepteur d’activités **delay** se trouve dans la catégorie **primitives** de la **boîte à outils** , accessible en cliquant sur l’onglet **boîte à outils** de la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** + **ALT** + **X**.

Le concepteur d’activités **delay** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . La suppression du concepteur d’activités crée une <xref:System.Activities.Statements.Delay> activité avec un <xref:System.Activities.Activity.DisplayName%2A> délai par défaut. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **delay** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-delay-properties"></a>Propriétés Delay

Le tableau suivant présente les <xref:System.Activities.Statements.Delay> Propriétés et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d’entre elles peuvent être modifiées sur l’aire de Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Nom convivial de l'activité <xref:System.Activities.Statements.Delay>. La valeur par défaut est Delay. Bien que la <xref:System.Activities.Activity.DisplayName%2A> valeur ne soit pas strictement obligatoire, il est recommandé d’en utiliser une.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Vrai|Durée pendant laquelle retarder le workflow. Cette propriété est définie dans la grille des propriétés. Tapez une valeur <xref:System.TimeSpan> littérale au format 00:00:00 ou une expression Visual Basic pour spécifier la durée.|

## <a name="see-also"></a>Voir aussi

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Concepteur d'activités Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)