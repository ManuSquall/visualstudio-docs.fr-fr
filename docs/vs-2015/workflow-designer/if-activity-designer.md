---
title: Si le concepteur d’activités | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b35fe7f1b55dde25ec896f230f66cef00d24eed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659056"
---
# <a name="if-activity-designer"></a>Concepteur d'activités If
L'activité <xref:System.Activities.Statements.If> évalue une condition et exécute une activité en fonction des résultats de cette évaluation. Cette activité est très utile lors de l'utilisation d'un style de modélisation des procédures de la programmation. Une activité <xref:System.Activities.Statements.If> peut être imbriquée dans une activité <xref:System.Activities.Statements.Sequence> ou une activité <xref:System.Activities.Statements.Parallel>, par exemple. Si vous utilisez une activité <xref:System.Activities.Statements.Flowchart>, il est conseillé d'utiliser plutôt une activité <xref:System.Activities.Statements.FlowDecision>.

## <a name="if-properties-in-the-workflow-designer"></a>Propriétés d'If dans Workflow Designer
 Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.If> et décrit comment les utiliser dans le concepteur.

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|True|Condition qui détermine l'activité enfant à exécuter. Pour définir la <xref:System.Activities.Statements.If.Condition%2A>, tapez une expression de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] dans la zone **condition** du concepteur d’activités **If** ou dans la grille des propriétés.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Activité à exécuter si la <xref:System.Activities.Statements.If.Condition%2A> a la **valeur false**. Pour ajouter une activité qui est exécutée par l' <xref:System.Activities.Statements.If.Else%2A> branche, déplacez une activité de la boîte **à outils** vers la zone **else** sur le concepteur d’activités **If** avec le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.If.Then%2A>|False|Activité à exécuter si la <xref:System.Activities.Statements.If.Condition%2A> a la **valeur true**. Pour ajouter une activité qui est exécutée par l' <xref:System.Activities.Statements.If.Then%2A> branche, déplacez une activité de la boîte **à outils** vers la zone **Then** sur le concepteur d’activités **If** avec le texte d’indication « déposer l’activité ici ».|

## <a name="see-also"></a>Voir aussi
 [Workflow de contrôle](../workflow-designer/control-flow-activity-designers.md) [parallèle](../workflow-designer/parallel-activity-designer.md) de [séquence](../workflow-designer/sequence-activity-designer.md)