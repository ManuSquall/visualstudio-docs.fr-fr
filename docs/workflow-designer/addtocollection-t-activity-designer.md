---
title: "Concepteur d&#39;activit&#233;s AddToCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.AddToCollection`1.UI"
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Concepteur d&#39;activit&#233;s AddToCollection&lt;T&gt;
Le concepteur d'activités **AddToCollection\<T\>** permet de créer et configurer une activité <xref:System.Activities.Statements.AddToCollection%601>.  
  
## Activité AddToCollection\<T\>  
 L'activité <xref:System.Activities.Statements.AddToCollection%601> ajoute un élément à une collection.  
  
### Utilisation du concepteur d'activités AddToCollection\<T\>  
 Le concepteur d'activités **AddToCollection\<T\>** se trouve dans la catégorie **Collection** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **AddToCollection\<T\>** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.AddToCollection%601> avec AddToCollection\<Int32\> comme <xref:System.Activities.Activity.DisplayName%2A> par défaut.\(Par défaut, *TypeArgument* a la valeur**Int32**.Elle peut être modifiée dans la grille des propriétés.\) La valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **AddToCollection\<T\>** ou dans la zone **DisplayName** de la grille des propriétés.Les autres propriétés doivent être modifiées dans la grille des propriétés.  
  
### Propriétés d'AddToCollection\<T\>  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.AddToCollection%601> et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.AddToCollection%601>.La valeur par défaut est AddToCollection\<Int32\>.Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Élément à ajouter à Collection\<T\>.Cet élément est de type *T*, qui est de type *TypeArgument*.Pour spécifier l'élément, tapez une expression Visual Basic dans la grille des propriétés.|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Collection à laquelle l'élément doit être ajouté.Cette collection est de type **ICollection\<TypeArgument\>**.Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|  
|*TypeArgument*|True|Type T des éléments contenus dans la collection <xref:System.Collections.Generic.ICollection%601>.Par défaut, ce type *TypeArgument* a la valeur **Int32**.Pour modifier le type, modifiez la valeur de *TypeArgument* dans la zone de liste déroulante de la grille des propriétés.|  
  
## Voir aussi  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\> Activity Designer](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)