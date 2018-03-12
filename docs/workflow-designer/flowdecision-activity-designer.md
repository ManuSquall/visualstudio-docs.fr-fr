---
title: "Concepteur d’activités FlowDecision | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 3e3fd48f33e5499f7a67aed02c7b732ebe6b3b7b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="flowdecision-activity-designer"></a>Concepteur d'activités FlowDecision
Le nœud <xref:System.Activities.Statements.FlowDecision> est un nœud conditionnel qui fournit une branche pour le flux de contrôle dans l'une des deux alternatives suivant qu'une condition spécifiée est satisfaite. Si le flux requiert plusieurs branches, utilisez <xref:System.Activities.Statements.FlowSwitch%601> à la place.  
  
## <a name="the-flowdecision-node"></a>Nœud FlowDecision  
 Utilisez <xref:System.Activities.Statements.FlowDecision> lorsque le flux peut faire l'objet d'une création de branche dans deux chemins d'accès. Un nœud <xref:System.Activities.Statements.FlowDecision> a un <xref:System.Activities.Statements.FlowDecision.Condition%2A> et un <xref:System.Activities.Statements.FlowNode> associés avec chacun des deux résultats possibles : <xref:System.Activities.Statements.FlowDecision.True%2A> ou <xref:System.Activities.Statements.FlowDecision.False%2A>. La propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> est évaluée et la valeur de cette évaluation détermine le <xref:System.Activities.Statements.FlowNode> suivant à traiter dans le <xref:System.Activities.Statements.Flowchart>.  
  
### <a name="using-the-flowdecision-designer"></a>Utilisation du concepteur FlowDecision  
 Le **FlowDecision** concepteur n’est trouvé dans le **organigramme** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils** onglet sur le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **FlowDecision** concepteur peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface au sein d’un **organigramme** Concepteur d’activités. Cette opération crée un <xref:System.Activities.Statements.FlowDecision> intitulé **décision** dans le <xref:System.Activities.Statements.Flowchart> activité. Pointez la souris sur le concepteur et le **True** et **False** apparaître les poignées carrées pour les deux branches.  
  
 Après avoir fait glisser le **FlowDecision** concepteur et autres concepteurs sur le **organigramme**, les nœuds peuvent être liés ensemble pour spécifier l’ordre d’exécution. Pour créer un lien entre un nœud source (y compris le **True** et **False** branches de la **FlowDecision**) et un nœud de destination, la souris au-dessus du concepteur du nœud source et apparaître les poignées carrées de chaque côté de celui-ci. Cliquez sur l'une des poignées carrées et faites-la glisser en maintenant le bouton de la souris enfoncé jusqu'à l'une des poignées qui s'affiche de la même façon autour du nœud de destination lorsque vous déplacez la souris dessus. Relâchez le bouton de la souris. Un lien est créé entre ces deux nœuds, représenté par une flèche allant du concepteur source au concepteur de destination.  
  
 L’expression qui déclare le <xref:System.Activities.Statements.FlowDecision.Condition%2A> peuvent être tapés dans le **Condition** zone de la **propriétés** fenêtre en cliquant sur « Entrer une expression VB » où le texte d’information indique que.  
  
### <a name="the-flowdecision-properties"></a>Propriétés de FlowDecision  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.FlowDecision> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|Condition qui détermine le chemin d'accès emprunté par le contrôle de flux.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Chemin d'accès emprunté par le contrôle de flux si la propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> est satisfaite.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Chemin d'accès emprunté par le contrôle de flux si la propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> n'est pas satisfaite.|  
  
## <a name="see-also"></a>Voir aussi  
 [Diagramme de flux](../workflow-designer/flowchart-activity-designers.md)   
 [Diagramme de flux](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)