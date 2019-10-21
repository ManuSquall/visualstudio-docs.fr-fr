---
title: Concepteur d’activités Delay | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a47279bc68503ba645fea3ef23a04ce9d5ef4c41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656797"
---
# <a name="delay-activity-designer"></a>Concepteur d'activités Delay
Le concepteur d’activités **delay** est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.Delay>.

## <a name="the-delay-activity"></a>Activité Delay
 L'activité <xref:System.Activities.Statements.Delay> retarde l'exécution d'un workflow pour une durée spécifiée.

### <a name="using-the-delay-activity-designer"></a>Utilisation du concepteur d'activités Delay
 Le concepteur d’activités **delay** se trouve dans la catégorie **primitives** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans le menu **affichage** , ou encore en appuyant sur Ctrl + ALT + X.)

 Le concepteur d’activités **delay** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.Delay> avec Delay comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. La <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **delay** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-delay-properties"></a>Propriétés de Delay
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Delay> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Delay>. La valeur par défaut est Delay. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Durée pendant laquelle retarder le workflow. Cette propriété est définie dans la grille des propriétés. Tapez une valeur <xref:System.TimeSpan> littérale au format 00:00:00 ou une expression Visual Basic pour spécifier la durée.|

## <a name="see-also"></a>Voir aussi
 [Primitives](../workflow-designer/primitives-activity-designers.md) [assigner](../workflow-designer/assign-activity-designer.md) [activity designer](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)