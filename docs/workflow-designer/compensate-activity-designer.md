---
title: "Concepteur d&#39;activit&#233;s Compensate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Compensate.UI"
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Concepteur d&#39;activit&#233;s Compensate
Le concepteur d'activités **Compensate** permet de créer et configurer une activité <xref:System.Activities.Statements.Compensate>.  
  
## Activité Compensate  
 L'activité <xref:System.Activities.Statements.Compensate> appelle explicitement la propriété <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> pour une activité contenue dans un objet <xref:System.Activities.Statements.CompensableActivity>.Si l'activité <xref:System.Activities.Statements.Compensate> n'est pas utilisée dans la propriété <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> d'un objet <xref:System.Activities.Statements.CompensableActivity>, vous devez spécifier la propriété <xref:System.Activities.Statements.Compensate.Target%2A>.  
  
 L'objet <xref:System.Activities.Statements.CompensationToken> spécifié par la propriété <xref:System.Activities.Statements.Compensate.Target%2A> fournit un moyen de confirmer ou de compenser explicitement un objet <xref:System.Activities.Statements.CompensableActivity> une fois que le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> est terminé.  
  
### Utilisation du concepteur d'activités Compensate  
 Le concepteur d'activités **Compensate** se trouve dans la catégorie **Transaction** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **Compensate** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.Compensate> avec Compensate comme <xref:System.Activities.Activity.DisplayName%2A> par défaut.La valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **Compensate** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés de Compensate  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CancellationScope> et décrit comment elles sont utilisées dans le concepteur.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans la grille des propriétés ou dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], mais la propriété <xref:System.Activities.Statements.Compensate.Target%2A> doit être modifiée dans l'aire de conception.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.Compensate>.La valeur par défaut est Compensate.|  
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Spécifie l'objet <xref:System.Activities.InArgument%601> qui contient l'objet <xref:System.Activities.Statements.CompensationToken> pour cette activité <xref:System.Activities.Statements.Compensate>.|  
  
## Voir aussi  
 [Transaction](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate Activity Designer](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)