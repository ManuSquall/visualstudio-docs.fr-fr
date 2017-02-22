---
title: "Concepteur d&#39;activit&#233;s FlowDecision | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.FlowDecision.UI"
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Concepteur d&#39;activit&#233;s FlowDecision
Le nœud <xref:System.Activities.Statements.FlowDecision> est un nœud conditionnel qui fournit une branche pour le flux de contrôle dans l'une des deux alternatives suivant qu'une condition spécifiée est satisfaite.Si le flux requiert plusieurs branches, utilisez <xref:System.Activities.Statements.FlowSwitch%601> à la place.  
  
## Nœud FlowDecision  
 Utilisez <xref:System.Activities.Statements.FlowDecision> lorsque le flux peut faire l'objet d'une création de branche dans deux chemins d'accès.Un nœud <xref:System.Activities.Statements.FlowDecision> a un <xref:System.Activities.Statements.FlowDecision.Condition%2A> et un <xref:System.Activities.Statements.FlowNode> associés avec chacun des deux résultats possibles : <xref:System.Activities.Statements.FlowDecision.True%2A> ou <xref:System.Activities.Statements.FlowDecision.False%2A>.La propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> est évaluée et la valeur de cette évaluation détermine le <xref:System.Activities.Statements.FlowNode> suivant à traiter dans le <xref:System.Activities.Statements.Flowchart>.  
  
### Utilisation du concepteur FlowDecision  
 Le concepteur d'activités **FlowDecision** se trouve dans la catégorie **Flowchart** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur **FlowDecision** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] dans un concepteur d'activités **Flowchart**.Cette action crée un <xref:System.Activities.Statements.FlowDecision> libellé **Décision** dans l'activité <xref:System.Activities.Statements.Flowchart>.Déplacez la souris au\-dessus du concepteur pour faire apparaître les poignées carrées **True** et **False** pour les deux branches.  
  
 Après avoir fait glisser le concepteur **FlowDecision** et d'autres concepteurs sur **Flowchart**, les nœuds peuvent être liés ensemble pour spécifier l'ordre d'exécution.Pour créer un lien entre un nœud source \(notamment les branches **True** et **False** de **FlowDecision**\) et un nœud de destination, déplacez la souris au\-dessus du concepteur du nœud source, afin de faire apparaître des poignées carrées de chaque côté.Cliquez sur l'une des poignées carrées et faites\-la glisser en maintenant le bouton de la souris enfoncé jusqu'à l'une des poignées qui s'affiche de la même façon autour du nœud de destination lorsque vous déplacez la souris dessus.Relâchez le bouton de la souris. Un lien est créé entre ces deux nœuds, représenté par une flèche allant du concepteur source au concepteur de destination.  
  
 L'expression qui déclare la propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> peut être tapée dans la zone **Condition** de la fenêtre **Propriétés** en cliquant à l'endroit où le texte d'indication est « Entrer une expression VB ».  
  
### Propriétés de FlowDecision  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.FlowDecision> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|Condition qui détermine le chemin d'accès emprunté par le contrôle de flux.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Chemin d'accès emprunté par le contrôle de flux si la propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> est satisfaite.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Chemin d'accès emprunté par le contrôle de flux si la propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> n'est pas satisfaite.|  
  
## Voir aussi  
 [Organigramme](../workflow-designer/flowchart-activity-designers.md)   
 [Organigramme](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)