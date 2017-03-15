---
title: "Concepteur d&#39;activit&#233;s While | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.While.UI"
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Concepteur d&#39;activit&#233;s While
L'activité <xref:System.Activities.Statements.While> exécute l'activité contenue dans sa propriété <xref:System.Activities.Statements.While.Body%2A> lorsque la propriété <xref:System.Activities.Statements.Condition%2A> spécifiée a la valeur **true**.L'activité contenue ne peut jamais s'exécuter.Si vous voulez que l'activité contenue soit exécutée au moins une fois, utilisez l'activité <xref:System.Activities.Statements.DoWhile> à la place.  
  
## Propriétés de While dans Workflow Designer  
 Le tableau suivant répertorie les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.While> et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.While> dans l'en\-tête.La valeur par défaut est While.La valeur peut être modifiée dans la fenêtre **Propriétés** ou directement dans l'en\-tête du concepteur d'activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.While.Body%2A>|False|Contient l'activité à exécuter pendant que la propriété <xref:System.Activities.Statements.Condition%2A> a la valeur **true**.|  
|<xref:System.Activities.Statements.Condition%2A>|True|Contient l'expression [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] évaluée pour déterminer si l'activité dans la propriété <xref:System.Activities.Statements.While.Body%2A> sera exécutée.|  
  
## Voir aussi  
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)