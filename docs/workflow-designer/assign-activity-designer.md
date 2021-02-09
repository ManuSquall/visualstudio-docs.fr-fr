---
title: Concepteur d’activités Concepteur de flux de travail-Assign
description: Découvrez comment vous pouvez utiliser le concepteur d’activités Assign pour créer et configurer une activité Assign et comment l’activité Assign assigne une valeur à une variable ou à un argument.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe6f649543cee66a1050e5724a9317b7b8806534
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888639"
---
# <a name="assign-activity-designer"></a>Concepteur d'activités Assign

Le concepteur d’activités **Assign** est utilisé pour créer et configurer une <xref:System.Activities.Statements.Assign> activité.

## <a name="the-assign-activity"></a>Activité Assign

L’activité <xref:System.Activities.Statements.Assign> affecte une valeur à une variable ou à un argument.

### <a name="using-the-assign-activity-designer"></a>Utilisation du concepteur d'activités Assign

Le concepteur d’activités **Assign** se trouve dans la catégorie **primitives** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** (ou en sélectionnant **boîte à outils** dans le menu **affichage** , ou encore en appuyant sur CTRL + ALT + X).

Le concepteur d’activités **Assign** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail où les activités sont placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . La suppression du concepteur d’activités **Assign** crée une <xref:System.Activities.Statements.Assign> activité avec le **DisplayName** par défaut Assign. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **Assign** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-assign-properties"></a>Propriétés d'Assign

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Assign> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d’entre elles peuvent être modifiées sur Concepteur de flux de travail surface.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Assign>. La valeur par défaut est Assign. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|Variable ou argument auquel la propriété <xref:System.Activities.Statements.Assign.Value%2A> est affectée. La valeur doit être un identificateur de Visual Basic valide. Pour définir la propriété, tapez une expression Visual Basic dans la zone à dans le concepteur **d'** activités **Assign** ou dans la grille des propriétés.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valeur qui est affectée à la variable. Pour définir le <xref:System.Activities.Statements.Assign.Value%2A> , tapez une expression Visual Basic dans la zone **valeur** du concepteur d’activités **Assign** ou dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Retard](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)