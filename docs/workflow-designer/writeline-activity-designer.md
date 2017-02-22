---
title: "Concepteur d&#39;activit&#233;s WriteLine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.WriteLine.UI"
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Concepteur d&#39;activit&#233;s WriteLine
Le concepteur d'activités **WriteLine** permet de créer et configurer une activité <xref:System.Activities.Statements.WriteLine>.  
  
## Activité WriteLine  
 L'activité <xref:System.Activities.Statements.Writeline> écrit du texte dans un objet <xref:System.IO.TextWriter> spécifié.Si aucun objet <xref:System.IO.TextWriter> n'est spécifié, <xref:System.Activities.Statements.Writeline> écrit le texte dans la console.  
  
### Utilisation du concepteur d'activités WriteLine  
 Le concepteur d'activités **WriteLine** se trouve dans la catégorie **Primitives** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **WriteLine** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.WriteLine> avec WriteLine comme <xref:System.Activities.Activity.DisplayName%2A> par défaut.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **WriteLine** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés de WriteLine  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.WriteLine> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.WriteLine>.La valeur par défaut est WriteLine.Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Texte à écrire.Pour définir la propriété, tapez une expression Visual Basic dans la zone **Texte** sur le concepteur d'activités **WriteLine** ou dans la grille des propriétés.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> dans lequel <xref:System.Activities.Statements.WriteLine> écrit <xref:System.Activities.Statements.WriteLine.Text%2A>.La valeur par défaut est la console.|  
  
## Voir aussi  
 [Primitives](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)