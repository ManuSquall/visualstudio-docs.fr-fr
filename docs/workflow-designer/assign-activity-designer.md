---
title: "Concepteur d&#39;activit&#233;s Assign | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Assign.UI"
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Concepteur d&#39;activit&#233;s Assign
Le concepteur d'activités **Assign** permet de créer et configurer une activité <xref:System.Activities.Statements.Assign>.  
  
## Activité Assign  
 L'activité <xref:System.Activities.Statements.Assign> affecte une valeur à une variable ou à un argument.  
  
### Utilisation du concepteur d'activités Assign  
 Le concepteur d'activités **Assign** se trouve dans la catégorie **Primitives** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **Assign** peut être déplacé de la **boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.Assign> avec Assign comme **DisplayName** par défaut.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **Assign** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés d'Assign  
 Le tableau suivant présente les propriétés d'<xref:System.Activities.Statements.Assign> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Assign>.La valeur par défaut est Assign.Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|Variable ou argument auquel la propriété <xref:System.Activities.Statements.Assign.Value%2A> est affectée.Il doit s'agir d'un identificateur Visual Basic valide.Pour définir la propriété, tapez une expression Visual Basic dans la zone **À** sur le concepteur d'activités **Assign** ou dans la grille des propriétés.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valeur qui est affectée à la variable.Pour définir la propriété <xref:System.Activities.Statements.Assign.Value%2A>, tapez une expression Visual Basic dans la zone **Valeur** sur le concepteur d'activités **Assign** ou dans la grille des propriétés.|  
  
## Voir aussi  
 [Primitives](../workflow-designer/primitives-activity-designers.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)