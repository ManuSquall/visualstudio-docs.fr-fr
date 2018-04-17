---
title: Concepteur d’activités FinalState | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6360be9522fd8a3640780407cb5252da41515536
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="finalstate-activity-designer"></a>Concepteur d'activités FinalState
Le concepteur d'activités <xref:System.Activities.Core.Presentation.FinalState> permet de créer un <xref:System.Activities.Statements.State> qui arrête une instance de machine à états.

## <a name="using-the-finalstate-activity-designer"></a>Utilisation du concepteur d'activités FinalState
 Le **FinalState** concepteur est utilisé pour créer un <xref:System.Activities.Statements.State> qui est préconfiguré comme un état d’arrêt dans une machine à états. A <xref:System.Activities.Statements.State> qui est créé à l’aide de la <xref:System.Activities.Core.Presentation.FinalState> Concepteur d’activités a son <xref:System.Activities.Statements.State.IsFinal%2A> propriété **true**, n’a aucun <xref:System.Activities.Statements.State.Exit%2A> activité et aucune transition provenant de cette dernière. Pour utiliser le <xref:System.Activities.Core.Presentation.FinalState> Concepteur d’activités à ajouter un <xref:System.Activities.Statements.State> activité qui est préconfigurée comme un état d’arrêt dans une machine à états, faites glisser le **FinalState** Concepteur d’activités de la **Machine à états**section de la **boîte à outils** et déposez-le sur le Concepteur de workflow. Le concepteur d'activités <xref:System.Activities.Core.Presentation.FinalState> peut être déposé sur un <xref:System.Activities.Statements.StateMachine> et des transitions ajoutées ultérieurement ; ou une transition peut être créée lorsque le concepteur d'activités <xref:System.Activities.Core.Presentation.FinalState> est déposé. Pour plus d’informations sur la création de transitions, consultez [Transition](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité State dans le concepteur de workflow
 Le tableau suivant indique les propriétés qui peuvent être définies à l'aide du concepteur <xref:System.Activities.Core.Presentation.FinalState> et explique comment elles sont utilisées dans le concepteur. Certaines de ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiées dans l'aire de conception.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.State> dans l'en-tête. La valeur par défaut est **état**. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités. <xref:System.Activities.Statements.State.DisplayName%2A> est utilisé dans l'exploration à l'aide de la barre de navigation qui est affichée en haut du concepteur de workflow.<br /><br /> Bien que la propriété <xref:System.Activities.Statements.State.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Spécifie l'action qui se produit lorsque cet état subit une transition. Cette valeur peut être définie en faisant glisser une activité à partir de la **boîte à outils** et déposant sur la <xref:System.Activities.Statements.State.Entry%2A> section de l’état.|

## <a name="see-also"></a>Voir aussi

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [État](../workflow-designer/state-activity-designer.md)
- [transition](../workflow-designer/transition-activity-designer.md)