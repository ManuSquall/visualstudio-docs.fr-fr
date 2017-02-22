---
title: "Concepteur d&#39;activit&#233;s ClearCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ClearCollection`1.UI"
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Concepteur d&#39;activit&#233;s ClearCollection&lt;T&gt;
Le concepteur d'activités **ClearCollection\<T\>** permet de créer et configurer une activité <xref:System.Activities.Statements.ClearCollection%601>.  
  
## Activité ClearCollection\<T\>  
 L'activité <xref:System.Activities.Statements.ClearCollection%601> efface tous les éléments d'une collection spécifiée.  
  
### Utilisation du concepteur d'activités ClearCollection\<T\>  
 Le concepteur d'activités **ClearCollection\<T\>** se trouve dans la catégorie **Collection** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **ClearCollection\<T\>** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.ClearCollection%601> avec ClearCollection\<Int32\> comme <xref:System.Activities.Activity.DisplayName%2A> par défaut.\(Par défaut, *TypeArgument* a la valeur**Int32**.Elle peut être modifiée dans la grille des propriétés.\) La valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **ClearCollection\<T\>** ou dans la zone **DisplayName** de la grille des propriétés.Les autres propriétés doivent être modifiées dans la grille des propriétés.  
  
### Propriétés de ClearCollection\<T\>  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.ClearCollection%601> et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.ClearCollection%601>.La valeur par défaut est ClearCollection\<Int32\>.Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Spécifie la collection dont les éléments doivent être effacés.Cette collection est de type **ICollection\<TypeArgument\>.** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|  
|*TypeArgument*|True|Spécifie le type T des éléments contenus dans l'objet <xref:System.Collections.Generic.ICollection%601>.Par défaut, ce type *TypeArgument* a la valeur **Int32**.Pour modifier le type, modifiez la valeur de *TypeArgument* dans la zone de liste déroulante de la grille des propriétés.|  
  
## Voir aussi  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)