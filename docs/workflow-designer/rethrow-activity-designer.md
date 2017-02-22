---
title: "Concepteur d&#39;activit&#233;s Rethrow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Rethrow.UI"
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Concepteur d&#39;activit&#233;s Rethrow
Le concepteur d'activités **Rethrow** permet de créer et configurer une activité <xref:System.Activities.Statements.Rethrow>.  
  
## Activité Rethrow  
 L'activité <xref:System.Activities.Statements.Rethrow> lève une exception précédemment levée.Cette activité ne peut être utilisée que dans un gestionnaire <xref:System.Activities.Statements.Catch> dans l'activité <xref:System.Activities.Statements.TryCatch>.  
  
### Utilisation du concepteur d'activités Rethrow  
 Le concepteur d'activités **Rethrow** se trouve dans la catégorie **Gestion des erreurs** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **Rethrow** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.Rethrow> avec Throw comme **DisplayName** par défaut.La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **Rethrow** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés de Rethrow  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Rethrow> et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.ReThrow>.La valeur par défaut est Rethrow.|  
  
## Voir aussi  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)