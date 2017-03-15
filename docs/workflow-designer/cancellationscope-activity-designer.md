---
title: "Concepteur d&#39;activit&#233;s CancellationScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CancellationScope.UI"
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Concepteur d&#39;activit&#233;s CancellationScope
Le concepteur d'activités **CancellationScope** permet de créer et configurer une activité <xref:System.Activities.Statements.CancellationScope>.  
  
## Activité CancellationScope  
 L'activité <xref:System.Activities.Statements.CancellationScope> vous permet de spécifier une activité pour la logique d'exécution et d'annulation de cette activité.  
  
### Utilisation du concepteur d'activités CancellationScope  
 Le concepteur d'activités **CancellationScope** se trouve dans la catégorie **Transaction** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **CancellationScope** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.CancellationScope> avec CancellationScope comme <xref:System.Activities.Activity.DisplayName%2A> par défaut.La valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **CancellationScope** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés de CancellationScope  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CancellationScope> et décrit comment elles sont utilisées dans le concepteur.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans la grille des propriétés, mais les autres propriétés doivent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.CancellationScope>.La valeur par défaut est CancellationScope.Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Spécifie l'activité pour laquelle la logique d'annulation est fournie.Pour ajouter l'activité <xref:System.Activities.Statements.CancellationScope.Body%2A>, déplacez une activité de la **Boîte à outils** vers la zone **Body** du concepteur d'activités **CancellationScope** avec le texte d'indication « Déposer l'activité ici ».|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Spécifie l'activité qui est exécutée dans l'événement d'annulation.Pour ajouter l'activité <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, déplacez une activité de la **Boîte à outils** vers la zone **CancellationHandler** du concepteur d'activités **CancellationScope** avec le texte d'indication « Déposer l'activité ici ».|  
  
## Voir aussi  
 [Transaction](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)