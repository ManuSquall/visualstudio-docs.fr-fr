---
title: "Concepteur d’activités FinalState | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: "5"
ms.author: sdanie
manager: erikre
ms.openlocfilehash: 4bc8e8c9278561cbeee06828e8d828e4072296b8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
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
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [État](../workflow-designer/state-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)