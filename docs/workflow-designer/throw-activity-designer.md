---
title: "Concepteur d&#39;activit&#233;s Throw | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Throw.UI"
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Concepteur d&#39;activit&#233;s Throw
Le concepteur d'activités **Throw** permet de créer et configurer une activité <xref:System.Activities.Statements.Throw>.  
  
## Activité Throw  
 L'activité <xref:System.Activities.Statements.Throw> lève une exception.  
  
### Utilisation du concepteur d'activités Throw  
 Le concepteur d'activités **Throw** se trouve dans la catégorie **Gestion des erreurs** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **Throw** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.Throw> avec Throw comme **DisplayName** par défaut.La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **Throw** ou dans la zone **DisplayName** de la grille des propriétés.La propriété <xref:System.Activities.Statements.Throw.Exception%2A> doit être modifiée dans la grille des propriétés.  
  
### Propriétés de Throw  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Throw> et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.Throw>.La valeur par défaut est Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Exception à lever.Cette exception doit dériver de <xref:System.Exception>.Pour spécifier l'exception, tapez une expression Visual Basic dans la grille des propriétés.|  
  
## Voir aussi  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw Activity Designer](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)