---
title: "Concepteur d&#39;activit&#233;s Parallel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Parallel.UI"
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Concepteur d&#39;activit&#233;s Parallel
L'activité <xref:System.Activities.Statements.Parallel> exécute simultanément une collection d'activités enfants.  
  
## Activité parallèle  
 L'activité <xref:System.Activities.Statements.Parallel> stocke ses activités enfants dans une collection <xref:System.Activities.Statements.Parallel.Branches%2A>.Utilisez l'activité <xref:System.Activities.Statements.Parallel> au lieu de l'activité <xref:System.Activities.Statements.Sequence> si quelques\-unes des activités enfants peuvent devenir inactives.  
  
 L'activité <xref:System.Activities.Statements.Parallel> comporte une propriété <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> qui contient une expression [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] spécifiée par l'utilisateur.L'activité <xref:System.Activities.Statements.Parallel> évalue cette propriété après l'exécution de chaque branche.Si la propriété prend la valeur **True**, l'activité <xref:System.Activities.Statements.Parallel> se termine sans exécuter les autres branches.Si la propriété <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> ne prend pas la valeur **True**, l'activité <xref:System.Activities.Statements.Parallel> se termine lorsque toutes ses activités enfants sont achevées.  
  
### Utilisation du concepteur d'activités Parallel  
 Le concepteur d'activités **Parallel** se trouve dans la catégorie **Flux de contrôle** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** situé sur le côté gauche du [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **Parallel** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les concepteurs d'activités sont généralement placés, par exemple dans un concepteur d'activités **Sequence**.Une fois déposé dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], il crée une activité <xref:System.Activities.Statements.Parallel>, qui, par défaut, contient une propriété <xref:System.Activities.Activity.DisplayName%2A> ayant la valeur **Parallel**  
  
 Pour ajouter une activité à la collection <xref:System.Activities.Statements.Parallel.Branches%2A> de l'activité parallèle, faites glisser un autre concepteur d'activités de la  **Boîte à outils** et déposez\-le sur le triangle à l'intérieur du concepteur d'activités **Parallel**.Les triangles encadrent les activités contenues dans les branches.Il est possible d'ajouter des activités supplémentaires en répétant cette procédure.Les activités peuvent être réorganisées par glisser\-déplacer dans le concepteur d'activités **Parallel**.  
  
### Propriétés de l'activité Parallel dans le concepteur de workflow  
 Le tableau suivant répertorie les propriétés des activités parallèles et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------------|-----------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom d'affichage convivial du concepteur d'activités dans l'en\-tête.La valeur par défaut est **Parallel**.La valeur peut être éventuellement modifiée dans la grille **Propriétés** ou directement dans l'en\-tête du concepteur d'activités.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contient la collection des activités enfants à exécuter.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Évaluée une fois qu'une branche est terminée.Si sa valeur est **True**, les branches en attente planifiées sont annulées.Si cette propriété n'est pas définie ou prend la valeur **False**, l'activité se termine lorsque toutes ses activités enfants sont achevées.La valeur par défaut est **null**.|  
  
## Voir aussi  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)