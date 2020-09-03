---
title: Concepteur d’activités Assign | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ebe465d5eeb12a956d285a8313b0acdbcfb8d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659188"
---
# <a name="assign-activity-designer"></a>Concepteur d'activités Assign
Le concepteur d’activités **Assign** est utilisé pour créer et configurer une <xref:System.Activities.Statements.Assign> activité.

## <a name="the-assign-activity"></a>Activité Assign
 L’activité <xref:System.Activities.Statements.Assign> affecte une valeur à une variable ou à un argument.

### <a name="using-the-assign-activity-designer"></a>Utilisation du concepteur d'activités Assign
 Le concepteur d’activités **Assign** se trouve dans la catégorie **primitives** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** (ou en sélectionnant **boîte à outils** dans le menu **affichage** , ou encore en appuyant sur CTRL + ALT + X).

 Le concepteur d’activités **Assign** peut être déplacé de la **boîte à outils** et déposé dans l' [!INCLUDE[wfd2](../includes/wfd2-md.md)] aire de conception, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . Cette opération crée une <xref:System.Activities.Statements.Assign> activité avec le **DisplayName** par défaut Assign. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **Assign** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-assign-properties"></a>Propriétés d'Assign
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Assign> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Assign>. La valeur par défaut est Assign. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|Variable ou argument auquel la propriété <xref:System.Activities.Statements.Assign.Value%2A> est affectée. Il doit s'agir d'un identificateur Visual Basic valide. Pour définir la propriété, tapez une expression Visual Basic dans la zone à dans le concepteur **d'** activités **Assign** ou dans la grille des propriétés.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valeur qui est affectée à la variable. Pour définir le <xref:System.Activities.Statements.Assign.Value%2A> , tapez une expression Visual Basic dans la zone **valeur** du concepteur d’activités **Assign** ou dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi
 [Retard](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) des [primitives](../workflow-designer/primitives-activity-designers.md) , [WriteLine WriteLine](../workflow-designer/writeline-activity-designer.md)