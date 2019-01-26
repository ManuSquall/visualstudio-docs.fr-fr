---
title: Concepteur de flux de travail - Concepteur d’activités Delay
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c26bcbe535d45e81cb37138d26192271437b9fb6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981569"
---
# <a name="delay-activity-designer"></a>Concepteur d'activités Delay

Le **délai** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Delay> activité.

## <a name="the-delay-activity"></a>L’activité de délai

L'activité <xref:System.Activities.Statements.Delay> retarde l'exécution d'un workflow pour une durée spécifiée.

### <a name="use-the-delay-activity-designer"></a>Utiliser le Concepteur d’activités Delay

Le **délai** Concepteur d’activités peut être trouvé dans le **Primitives** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils**onglet du Concepteur de Workflow. Vous pouvez également sélectionner **boîte à outils** à partir de la **vue** menu, ou appuyez sur **Ctrl**+**Alt** + **X**.

Le **délai** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Suppression du Concepteur d’activités crée un <xref:System.Activities.Statements.Delay> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de retard. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **délai** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.

### <a name="the-delay-properties"></a>Propriétés de Delay

Le tableau suivant présente le <xref:System.Activities.Statements.Delay> propriétés et décrit leur utilisation dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Delay>. La valeur par défaut est Delay. Bien que le <xref:System.Activities.Activity.DisplayName%2A> valeur n’est pas strictement obligatoire, il est recommandé d’utiliser un.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Durée pendant laquelle retarder le workflow. Cette propriété est définie dans la grille des propriétés. Tapez une valeur <xref:System.TimeSpan> littérale au format 00:00:00 ou une expression Visual Basic pour spécifier la durée.|

## <a name="see-also"></a>Voir aussi

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Concepteur d’activités Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)