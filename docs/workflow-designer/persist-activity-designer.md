---
title: "Concepteur d&#39;activit&#233;s Persist | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Persist.UI"
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Concepteur d&#39;activit&#233;s Persist
Le concepteur d'activités **Persist** permet de créer et configurer une activité <xref:System.Activities.Statements.Persist>.  
  
## Activité Persist  
 L'activité <xref:System.Activities.Statements.Persist> enregistre un workflow sur le disque, si possible.L'activité <xref:System.Activities.Statements.Persist> ne peut pas être exécutée dans une zone sans persistance comme, par exemple, dans une activité <xref:System.Activities.Statements.TransactionScope>.Si vous utilisez une activité <xref:System.Activities.Statements.Persist> dans une étendue sans persistance, une exception est levée au moment de l'exécution.  
  
### Utilisation du concepteur d'activités Persist  
 Le concepteur d'activités **Persist** se trouve dans la catégorie **Runtime** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **Persist** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.Persist> avec Persist comme **DisplayName** par défaut.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **Persist** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés de Persist  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Persist> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Persist>.La valeur par défaut est Persist.Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|  
  
## Voir aussi  
 [Exécution](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)