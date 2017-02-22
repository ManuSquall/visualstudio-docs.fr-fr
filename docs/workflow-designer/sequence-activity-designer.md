---
title: "Concepteur d&#39;activit&#233;s Sequence | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Sequence.UI"
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Concepteur d&#39;activit&#233;s Sequence
L'activité <xref:System.Activities.Statements.Sequence> contient une collection ordonnée d'activités enfants qu'elle exécute dans l'ordre.  
  
 Une autre façon d'exécuter un ensemble d'activités dans l'ordre consiste à utiliser une activité <xref:System.Activities.Statements.Flowchart>.Utilisez le [Organigramme](../workflow-designer/flowchart-activity-designer.md) lorsque vous avez un programme de branchement ou en boucle que vous voulez modéliser par le biais d'un diagramme.  
  
## Utilisation du concepteur d'activités Sequence  
 Pour ajouter une activité <xref:System.Activities.Statements.Sequence>, faites glisser le concepteur d'activités **Sequence** de la **Boîte à outils** et déposez\-le dans l'aire de conception [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Pour ajouter une activité enfant à cette activité <xref:System.Activities.Statements.Sequence>, faites glisser une autre activité de la **Boîte à outils** et déposez\-la sur le triangle dans la zone avec le texte d'indication « Déposer l'activité ici ».  
  
### Propriétés de l'activité Sequence dans le concepteur de workflow  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Sequence> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire de conception.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Sequence> dans l'en\-tête.La valeur par défaut est Sequence.La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en\-tête du concepteur d'activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
  
## Voir aussi  
 [Organigramme](../workflow-designer/flowchart-activity-designer.md)   
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)