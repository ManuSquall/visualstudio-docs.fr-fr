---
title: "Concepteur d&#39;activit&#233;s ParallelForEach&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ParallelForEach`1.UI"
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Concepteur d&#39;activit&#233;s ParallelForEach&lt;T&gt;
L'activité <xref:System.Activities.Statements.ParallelForEach%601> énumère les éléments d'une collection et, pour chacun d'eux, exécute en parallèle une instruction incorporée, qui se trouve de façon asynchrone sur le même thread.Utilisez cette activité de contrôle de flux au lieu de l'activité <xref:System.Activities.Statements.Sequence> si ses activités enfants sont censées devenir inactives.  
  
 L'activité <xref:System.Activities.Statements.ParallelForEach%601> a une propriété <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> qui contient une expression [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] spécifiée par l'utilisateur.L'activité <xref:System.Activities.Statements.ParallelForEach%601> évalue cette propriété après l'exécution de chaque branche.Si la propriété prend la valeur **true**, l'activité <xref:System.Activities.Statements.ParallelForEach%601> se termine sans exécuter les autres branches.Si la propriété <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> ne prend pas la valeur **true**, l'activité <xref:System.Activities.Statements.ParallelForEach%601> se termine lorsque toutes ses activités enfants sont terminées.  
  
## Activité ParallelForEach\<T\>  
 L'activité <xref:System.Activities.Statements.ParallelForEach%601> énumère ses valeurs et planifie la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> pour chaque valeur énumérée.Elle planifie seulement la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>.La manière dont le corps s'exécute dépend de l'inactivation de la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>.  
  
 Si la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> ne devient pas inactive, son exécution s'effectue dans l'ordre inverse, car les activités planifiées sont gérées comme une pile, la dernière activité planifiée s'exécutant en premier.Par exemple, si vous avez une collection {1,2,3,4} dans <xref:System.Activities.Statements.ParallelForEach%601> et que vous utilisez **WriteLine** comme corps pour écrire la valeur.L'impression suit l'ordre 4, 3, 2, 1 dans la console.Cela est dû au fait que **WriteLine** ne devient pas inactif ; par conséquent, une fois planifiées, les 4 activités **WriteLine** se sont exécutées en adoptant le comportement d'une pile, « premier entré\-dernier sorti ».  
  
 Par contre, si des activités dans la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> peuvent devenir inactives, par exemple une activité <xref:System.ServiceModel.Activities.Receive> ou <xref:System.Activities.Statements.Delay>,Il n'est pas nécessaire d'attendre qu'elles soient terminées.<xref:System.Activities.Statements.ParallelForEach%601> accède à l'activité de corps planifiée suivante et l'exécute.Si cette activité devient inactive à son tour, <xref:System.Activities.Statements.ParallelForEach%601> passe de nouveau à l'activité de corps suivante.  
  
### Utilisation du concepteur d'activités ParallelForEach\<T\>  
 Le concepteur d'activités **ParallelForEach\<T\>** se trouve dans la catégorie **Flux de contrôle** de la **boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** à gauche de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **ParallelForEach\<T\>** peut être déplacé de la **boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les concepteurs d'activités sont généralement placés, par exemple, dans un concepteur d'activités **Sequence**.Une fois déposé dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], il crée une activité <xref:System.Activities.Statements.ParallelForEach%601>, qui, par défaut, contient une propriété <xref:System.Activities.Activity.DisplayName%2A> ayant la valeur **ParallelForEach\<Int32\>.**  
  
### Propriétés de l'activité ParallelForEach\<T\> dans Workflow Designer  
 Le tableau suivant répertorie les propriétés de l'activité <xref:System.Activities.Statements.ParallelForEach%601> qui sont les plus utiles et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------------|-----------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom d'affichage convivial du concepteur d'activités dans l'en\-tête.La valeur par défaut est **ParallelForEach\<Int32\>**.La valeur peut être éventuellement modifiée dans la grille **Propriétés** ou directement dans l'en\-tête du concepteur d'activités.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Activité à exécuter pour chaque élément dans la collection.Pour ajouter l'activité <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, déplacez une activité de la boîte à outils à la zone **Body** dans le concepteur d'activités **ParallelForEach\<T\>** avec le texte d'indication « Déposer l'activité ici ».|  
|**TypeArgument**|True|Type des éléments de la collection <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> spécifiée par le paramètre générique *T*.Par défaut, **TypeArgument** a la valeur **Int32**.Pour modifier le type T dans le concepteur d'activités **ParallelForEach\<T\>**, changez la valeur de la zone de liste déroulante **TypeArgument** dans la grille des propriétés.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Collection d'éléments à itérer.Pour définir la propriété <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, tapez une expression [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] dans la zone **Valeurs** du concepteur d'activités **ForEach\<T\>**, dans la zone avec le texte d'indication « Entrer une expression VB » ou dans la zone **Valeurs** de la fenêtre **Propriétés**.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Propriété évaluée à l'issue de chaque itération.Si sa valeur est True, les itérations en attente planifiées sont annulées.Si cette propriété n'est pas définie, toutes les instructions planifiées s'exécutent jusqu'à ce qu'elles soient terminées.|  
  
 Par défaut, l'itérateur de boucle est nommé « item ».Vous pouvez modifier le nom de la variable d'itérateur dans la zone **ForEach** du concepteur d'activités **ParallelForEach\<T\>**.L'itérateur de boucle peut être utilisé dans des expressions dans les enfants de l'activité <xref:System.Activities.Statements.ParallelForEach%601>.  
  
## Voir aussi  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)