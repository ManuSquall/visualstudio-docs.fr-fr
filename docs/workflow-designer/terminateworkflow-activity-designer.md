---
title: "Concepteur d&#39;activit&#233;s TerminateWorkflow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TerminateWorkflow.UI"
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Concepteur d&#39;activit&#233;s TerminateWorkflow
Le concepteur d'activités **TerminateWorkflow** permet de créer et configurer une activité <xref:System.Activities.Statements.TerminateWorkflow>.  
  
## Activité TerminateWorkflow  
 L'activité <xref:System.Activities.Statements.TerminateWorkflow> termine l'exécution d'un workflow.  
  
### Utilisation du concepteur d'activités TerminateWorkflow  
 Le concepteur d'activités **TerminateWorkflow** se trouve dans la catégorie **Runtime** de la **Boîte à outils**, à laquelle il est possible d'accéder en cliquant sur l'onglet **Boîte à outils** \(ou en sélectionnant **Boîte à outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **TerminateWorkflow** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.TerminateWorkflow> avec TerminateWorkflow comme **DisplayName** par défaut.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **TerminateWorkflow** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés de TerminateWorkflow  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.TerminateWorkflow> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.TerminateWorkflow>.La valeur par défaut est TerminateWorkflow.Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Exception à lever lorsque le workflow est terminé.Définissez cette propriété dans la grille des propriétés.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Raison qui explique pourquoi le workflow a été terminé.Définissez cette propriété dans la grille des propriétés.|  
  
## Voir aussi  
 [Exécution](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)