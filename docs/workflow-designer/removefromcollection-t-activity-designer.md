---
title: "Concepteur d&#39;activit&#233;s RemoveFromCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.RemoveFromCollection`1.UI"
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Concepteur d&#39;activit&#233;s RemoveFromCollection&lt;T&gt;
Le concepteur d'activités **RemoveFromCollection\<T\>** permet de créer et configurer une activité <xref:System.Activities.Statements.RemoveFromCollection%601>.  
  
## Activité RemoveFromCollection\<T\>  
 L'activité <xref:System.Activities.Statements.RemoveFromCollection%601> supprime un élément spécifié d'une collection particulière.  
  
### Utilisation du concepteur d'activités RemoveFromCollection\<T\>  
 Le concepteur d'activités **RemoveFromCollection\<T\>** se trouve dans la catégorie **Collection** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **RemoveFromCollection\<T\>** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.RemoveFromCollection%601> avec RemoveFromCollection\<Int32\> comme propriété <xref:System.Activities.Activity.DisplayName%2A> par défaut.La valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **RemoveFromCollection\<T\>** ou dans la zone **DisplayName** de la grille des propriétés.Les autres propriétés doivent être modifiées dans la grille des propriétés.  
  
### Propriétés de RemoveFromCollection\<T\>  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.RemoveFromCollection%601> et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.RemoveFromCollection%601>.La valeur par défaut est RemoveFromCollection\<Int32\>.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Élément à ajouter à **Collection\<T\>**.Cet élément est de type *T*, qui est de type *TypeArgument*.Pour spécifier l'élément, tapez une expression Visual Basic dans la grille des propriétés.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Collection à laquelle l'élément doit être ajouté.Cette collection est de type **ICollection\<TypeArgument\>.** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|  
|*TypeArgument*|True|Type T des éléments contenus dans la collection <xref:System.Collections.Generic.ICollection%601>.Par défaut, ce type *TypeArgument* a la valeur **Int32**.Pour modifier le type, modifiez la valeur de *TypeArgument* dans la zone de liste déroulante de la grille des propriétés.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Valeur qui indique si l'élément spécifié a été supprimé de la collection.Pour spécifier une variable à lier au résultat, entrez une variable dans la grille des propriétés|  
  
## Voir aussi  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)