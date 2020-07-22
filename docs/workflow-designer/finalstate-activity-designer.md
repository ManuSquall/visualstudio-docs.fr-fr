---
title: Concepteur d’activités Concepteur de flux de travail-FinalState
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23e8973de1deba610a90e21edb870000abbb03e3
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875590"
---
# <a name="finalstate-activity-designer"></a>Concepteur d'activités FinalState

Le concepteur d'activités <xref:System.Activities.Core.Presentation.FinalState> permet de créer un <xref:System.Activities.Statements.State> qui arrête une instance de machine à états.

## <a name="using-the-finalstate-activity-designer"></a>Utilisation du concepteur d'activités FinalState

**FinalState** Designer est utilisé pour créer un <xref:System.Activities.Statements.State> qui est préconfiguré comme un état d’arrêt dans une machine à États. Une <xref:System.Activities.Statements.State> propriété créée à l’aide du <xref:System.Activities.Core.Presentation.FinalState> Concepteur d’activités a sa <xref:System.Activities.Statements.State.IsFinal%2A> propriété définie sur **true**, elle n’a aucune <xref:System.Activities.Statements.State.Exit%2A> activité et aucune transition provenant de celle-ci. Pour utiliser le <xref:System.Activities.Core.Presentation.FinalState> Concepteur d’activités pour ajouter une <xref:System.Activities.Statements.State> activité qui est préconfigurée comme un état d’arrêt dans une machine à États, faites glisser le concepteur d’activités **FinalState** de la section **machine à États** de la **boîte à outils** et déposez-le sur le concepteur de Workflow. Le concepteur d’activités <xref:System.Activities.Core.Presentation.FinalState> peut être déposé sur un <xref:System.Activities.Statements.StateMachine> et des transitions ajoutées ultérieurement ; ou une transition peut être créée lorsque le concepteur d’activités <xref:System.Activities.Core.Presentation.FinalState> est déposé. Pour plus d’informations sur la création de transitions, consultez [transition](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité State dans le concepteur de workflow

Le tableau suivant indique les propriétés qui peuvent être définies à l'aide du concepteur <xref:System.Activities.Core.Presentation.FinalState> et explique comment elles sont utilisées dans le concepteur. Certaines de ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiées dans l'aire de conception.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.State> dans l'en-tête. La valeur par défaut est **State**. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités. <xref:System.Activities.Statements.State.DisplayName%2A> est utilisé dans l'exploration à l'aide de la barre de navigation qui est affichée en haut du concepteur de workflow.<br /><br /> Bien que la propriété <xref:System.Activities.Statements.State.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Spécifie l'action qui se produit lorsque cet état subit une transition. Cette valeur peut être définie en faisant glisser une activité de la **boîte à outils** et en la déposant sur la <xref:System.Activities.Statements.State.Entry%2A> section de l’État.|

## <a name="see-also"></a>Voir aussi

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)