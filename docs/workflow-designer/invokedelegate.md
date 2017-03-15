---
title: "InvokeDelegate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InvokeDelegate Designer"
  - "System.Activities.Statements.InvokeDelegate.UI"
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# InvokeDelegate
Le concepteur d'activités **InvokeDelegate** permet de créer et configurer une activité <xref:System.Activities.Statements.InvokeDelegate>.  
  
## Activité InvokeDelegate  
 <xref:System.Activities.Statements.InvokeDelegate> appelle un délégué public.  
  
### Utilisation du concepteur d'activités InvokeDelegate  
 Le concepteur d'activités **InvokeDelegate** se trouve dans la catégorie **Primitives** de la **boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur Ctrl\+Alt\+X\).  
  
 Le concepteur d'activités **InvokeDelegate** peut être déplacé de la **boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette opération crée une activité <xref:System.Activities.Statements.InvokeDelegate> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut InvokeDelegate.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **InvokeDelegate** ou dans la zone **DisplayName** de la grille des propriétés.  
  
### Propriétés InvokeDelegate  
 Le tableau suivant présente les propriétés <xref:System.Activities.Statements.InvokeDelegate> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------------|-----------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.InvokeDelegate>.InvokeDelegate est la valeur par défaut.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nom du <xref:System.Activities.Statements.ActivityDelegate> à appeler lorsque l'activité s'exécute.Cette propriété peut être modifiée dans l'aire du concepteur.Il s'agit d'une propriété obligatoire.|  
|<xref:System.Activities.Statements.InvokeMethod.DelegateArguments%2A>|False|Collection d'argument du délégué appelé.Les clés sont les noms des objets <xref:System.Activities.Statements.ActivityDelegateParameter> de l'<xref:System.Activities.Statements.ActivityDelegate>, tandis que les valeurs sont les arguments dont les expressions sont évaluées et affectées aux objets <xref:System.Activities.Statements.ActivityDelegateParameter> correspondants.Dans la grille des propriétés, cliquez sur le bouton de sélection dans le champ **DelegateArguments**, la boîte de dialogue **DelegateArguments** s'affiche pour vous permettre de définir cette propriété.Cliquez sur le champ **Créer un argument** pour ajouter les arguments.|  
  
## Voir aussi  
 [Procédure : définir et utiliser des délégués d'activité dans le Concepteur de flux de travail](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)