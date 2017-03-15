---
title: "Concepteur d&#39;activit&#233;s If | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.If.UI"
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Concepteur d&#39;activit&#233;s If
L'activité <xref:System.Activities.Statements.If> évalue une condition et exécute une activité en fonction des résultats de cette évaluation.Cette activité est très utile lors de l'utilisation d'un style de modélisation des procédures de la programmation.Une activité <xref:System.Activities.Statements.If> peut être imbriquée dans une activité <xref:System.Activities.Statements.Sequence> ou une activité <xref:System.Activities.Statements.Parallel>, par exemple.Si vous utilisez une activité <xref:System.Activities.Statements.Flowchart>, il est conseillé d'utiliser plutôt une activité <xref:System.Activities.Statements.FlowDecision>.  
  
## Propriétés d'If dans Workflow Designer  
 Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.If> et décrit comment les utiliser dans le concepteur.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|Condition qui détermine l'activité enfant à exécuter.Pour définir la propriété <xref:System.Activities.Statements.If.Condition%2A>, tapez une expression [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] dans la zone **Condition** sur le concepteur d'activités **If** ou dans la grille des propriétés.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|Activité à exécuter si la propriété <xref:System.Activities.Statements.If.Condition%2A> a la valeur **false**.Pour ajouter une activité qui est exécutée par la branche <xref:System.Activities.Statements.If.Else%2A>, déplacez une activité de la **Boîte à outils** vers la zone **Else** sur le concepteur d'activités **If** avec le texte d'indication « Déposer l'activité ici ».|  
|<xref:System.Activities.Statements.If.Then%2A>|False|Activité à exécuter si la propriété <xref:System.Activities.Statements.If.Condition%2A> a la valeur **true**.Pour ajouter une activité qui est exécutée par la branche <xref:System.Activities.Statements.If.Then%2A>, déplacez une activité de la **Boîte à outils** vers la zone **Then** sur le concepteur d'activités **If** avec le texte d'indication « Déposer l'activité ici ».|  
  
## Voir aussi  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)