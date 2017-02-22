---
title: "Concepteur d&#39;activit&#233;s d&#39;&#233;tat | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.State.UI"
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 5
---
# Concepteur d&#39;activit&#233;s d&#39;&#233;tat
Un <xref:System.Activities.Statements.State> représente un état dans lequel une machine à états peut être.  
  
## Utilisation du concepteur d'activités State  
 Pour ajouter un état <xref:System.Activities.Statements.State> à un workflow, faites glisser le concepteur d'activités **State** de la section **Machine à états** de la **Boîte à outils** et déposez\-le sur une activité <xref:System.Activities.Statements.StateMachine> sur l'aire [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Une activité <xref:System.Activities.Statements.State> peut être déposée sur un <xref:System.Activities.Statements.StateMachine> et des transitions ajoutées ultérieurement ; ou une transition peut être créée lorsque l'activité <xref:System.Activities.Statements.State> est déposée.Pour ajouter une activité <xref:System.Activities.Statements.State> et créer une transition en une seule étape, faites glisser une activité **State** de la section **Machine à états** de la **Boîte à outils** et placez\-la sur un autre état dans le concepteur de workflow.Lorsque le <xref:System.Activities.Statements.State> est déplacé vers un autre <xref:System.Activities.Statements.State>, quatre triangles apparaissent autour de l'autre <xref:System.Activities.Statements.State>.Si <xref:System.Activities.Statements.State> est déposé sur un des quatre triangles, il est ajouté à la machine à états et une transition est créée à partir du <xref:System.Activities.Statements.State> source vers le <xref:System.Activities.Statements.State> de destination de dépôt.Pour plus d'informations, consultez [Transition](../workflow-designer/transition-activity-designer.md).  
  
### Propriétés de l'activité State dans le concepteur de workflow  
 Le tableau suivant indique les propriétés <xref:System.Activities.Statements.State> qui peuvent être définies à l'aide du concepteur et explique comment elles sont utilisées dans le concepteur.Certaines de ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiées dans l'aire de conception.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------------|-----------------|-----------------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.State> dans l'en\-tête.La valeur par défaut est **State**.La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en\-tête du concepteur d'activités.<xref:System.Activities.Statements.State.DisplayName%2A> est utilisé dans l'exploration à l'aide de la barre de navigation qui est affichée en haut du concepteur de workflow.<br /><br /> Bien que la propriété <xref:System.Activities.Statements.State.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Spécifie l'action qui se produit lorsque cet état subit une transition.Lorsque l'activité <xref:System.Activities.Statements.State> est développée, cette valeur peut être définie en faisant glisser une activité **Toolbox** et en la déposant sur la section **Entry** de l'état.|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|Spécifie l'action qui se produit lorsque cet état subit une transition.Lorsque l'activité <xref:System.Activities.Statements.State> est développée, cette valeur peut être définie en faisant glisser une activité **Toolbox** et en la déposant sur la section **Exit** de l'état.|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Répertorie les transitions possibles qui proviennent de <xref:System.Activities.Statements.State>.Chaque élément de la liste inclut un lien vers le <xref:System.Activities.Statements.Transition> associé et <xref:System.Activities.Statements.State> de destination.Cliquez sur le lien pour faire basculer le concepteur dans un affichage développé de <xref:System.Activities.Statements.Transition> ou <xref:System.Activities.Statements.State>.|  
  
## Voir aussi  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)