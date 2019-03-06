---
title: Concepteur de flux de travail - Concepteur d’activités Assign
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4179c23cefbf995242288c1e778f9e0413bfe28e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913965"
---
# <a name="assign-activity-designer"></a>Concepteur d'activités Assign

Le **affecter** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Assign> activité.

## <a name="the-assign-activity"></a>Activité Assign

L'activité <xref:System.Activities.Statements.Assign> affecte une valeur à une variable ou à un argument.

### <a name="using-the-assign-activity-designer"></a>Utilisation du concepteur d'activités Assign

Le **affecter** Concepteur d’activités peut être trouvé dans le **Primitives** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils**onglet (ou bien, sélectionnez **boîte à outils** à partir de la **vue** menu ou CTRL + ALT + X.)

Le **affecter** Concepteur d’activités peut être déplacé de la **boîte à outils** et supprimé une session sur l’aire du Concepteur de flux de travail, quel que soit les activités sont placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Suppression de la **affecter** Concepteur d’activités crée un <xref:System.Activities.Statements.Assign> activité avec une valeur par défaut **DisplayName** Assign. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **affecter** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.

### <a name="the-assign-properties"></a>Propriétés d'Assign

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Assign> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Assign>. La valeur par défaut est Assign. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|Variable ou argument auquel la propriété <xref:System.Activities.Statements.Assign.Value%2A> est affectée. La valeur doit être un identificateur Visual Basic valide. Pour définir la propriété, tapez une expression Visual Basic dans le **à** zone sur le **affecter** activité concepteur ou dans la grille des propriétés.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valeur qui est affectée à la variable. Pour définir le <xref:System.Activities.Statements.Assign.Value%2A>, tapez une expression Visual Basic dans le **valeur** zone sur le **affecter** activité concepteur ou dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)