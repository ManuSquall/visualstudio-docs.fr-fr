---
title: "Concepteur d&#39;activit&#233;s TransactionScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TransactionScope.UI"
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Concepteur d&#39;activit&#233;s TransactionScope
Le concepteur d'activités **TransactionScope** permet de créer et configurer une activité <xref:System.Activities.Statements.TransactionScope>.  
  
## Activité TransactionScope  
 L'activité <xref:System.Activities.Statements.TransactionScope> exécute l'activité contenue dans une transaction unique.La transaction est validée lorsque l'activité <xref:System.Activities.Statements.TransactionScope.Body%2A> et tous les autres participants de la transaction sont terminés.  
  
### Utilisation du concepteur d'activités TransactionScope  
 Le concepteur d'activités **TransactionScope** se trouve dans la catégorie **Transaction** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **TransactionScope** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.TransactionScope> avec TransactionScope comme <xref:System.Activities.Activity.DisplayName%2A> par défaut.La valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **TransactionScope** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés TransactionScope  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.TransactionScope> et décrit comment elles sont utilisées dans le concepteur.Les propriétés <xref:System.Activities.Activity.DisplayName%2A> et <xref:System.Activities.Statements.TransactionScope.Body%2A> peuvent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].En revanche, les autres propriétés doivent être modifiées dans la grille des propriétés.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.TransactionScope>.La valeur par défaut est TransactionScope.Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Spécifie l'activité à exécuter dans une transaction unique.Pour ajouter l'activité <xref:System.Activities.Statements.TransactionScope.Body%2A>, déplacez une activité de la **Boîte à outils** vers la zone **Body** du concepteur d'activités **TransactionScope** avec le texte d'indication « Déposer l'activité ici ».|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Spécifie la valeur <xref:System.Transactions.IsolationLevel> de cet objet <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Spécifie l'intervalle de temps \(au format 00:00:00, qui correspond à heures:minutes:secondes\) dont dispose la transaction pour se terminer.La valeur par défaut est égale à 1 minute \(00:01:00\).|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A>|True|Spécifie la valeur qui indique si le flux de travail doit être abandonné en cas d'abandon de la transaction.|  
  
## Voir aussi  
 [Transaction](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)