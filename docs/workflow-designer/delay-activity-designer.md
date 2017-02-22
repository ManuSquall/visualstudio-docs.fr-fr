---
title: "Concepteur d&#39;activit&#233;s Delay | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Delay.UI"
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Concepteur d&#39;activit&#233;s Delay
Le concepteur d'activités **Delay** permet de créer et configurer une activité <xref:System.Activities.Statements.Delay>.  
  
## Activité Delay  
 L'activité <xref:System.Activities.Statements.Delay> retarde l'exécution d'un workflow pour une durée spécifiée.  
  
### Utilisation du concepteur d'activités Delay  
 Le concepteur d'activités **Delay** se trouve dans la catégorie **Primitives** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **Delay** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.Delay> avec Delay comme <xref:System.Activities.Activity.DisplayName%2A> par défaut.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **Delay** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés de Delay  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Delay> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------------|-----------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Delay>.La valeur par défaut est Delay.Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Durée pendant laquelle retarder le workflow.Cette propriété est définie dans la grille des propriétés.Tapez une valeur <xref:System.TimeSpan> littérale au format 00:00:00 ou une expression Visual Basic pour spécifier la durée.|  
  
## Voir aussi  
 [Primitives](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay Activity Designer](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)