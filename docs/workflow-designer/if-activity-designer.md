---
title: Concepteur d’activités Concepteur de flux de travail-if
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 099be38c5585fe19c00b31c00ac3a7ddcd3d7fe2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76111446"
---
# <a name="if-activity-designer"></a>Concepteur d'activités If

L'activité <xref:System.Activities.Statements.If> évalue une condition et exécute une activité en fonction des résultats de cette évaluation. Cette activité est très utile lors de l'utilisation d'un style de modélisation des procédures de la programmation. Une activité <xref:System.Activities.Statements.If> peut être imbriquée dans une activité <xref:System.Activities.Statements.Sequence> ou une activité <xref:System.Activities.Statements.Parallel>, par exemple. Si vous utilisez une activité <xref:System.Activities.Statements.Flowchart>, il est conseillé d'utiliser plutôt une activité <xref:System.Activities.Statements.FlowDecision>.

## <a name="if-properties-in-the-workflow-designer"></a>Propriétés d'If dans Workflow Designer

Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.If> et décrit comment les utiliser dans le concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Vrai|Condition qui détermine l'activité enfant à exécuter. Pour définir le <xref:System.Activities.Statements.If.Condition%2A> , tapez une expression Visual Basic dans la zone **condition** sur le concepteur d’activités **If** ou dans la grille des propriétés.|
|<xref:System.Activities.Statements.If.Else%2A>|Faux|Activité à exécuter si a la <xref:System.Activities.Statements.If.Condition%2A> **valeur false**. Pour ajouter une activité qui est exécutée par la <xref:System.Activities.Statements.If.Else%2A> branche, déplacez une activité de la boîte **à outils** vers la zone **else** sur le concepteur d’activités **If** avec le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.If.Then%2A>|Faux|Activité à exécuter si la <xref:System.Activities.Statements.If.Condition%2A> propriété a la **valeur true**. Pour ajouter une activité qui est exécutée par la <xref:System.Activities.Statements.If.Then%2A> branche, déplacez une activité de la boîte **à outils** vers la zone **Then** sur le concepteur d’activités **If** avec le texte d’indication « déposer l’activité ici ».|

## <a name="see-also"></a>Voir aussi

- [Séquence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
