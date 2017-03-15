---
title: "La propri&#233;t&#233; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre initialis&#233;e dans une expression d’initialiseur d’objet, car toutes les surcharges accessibles n&#233;cessitent des arguments | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30993"
  - "vbc30993"
helpviewer_keywords: 
  - "BC30993"
ms.assetid: d4476065-2ca2-4c9e-a571-c08917a6387f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propri&#233;t&#233; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre initialis&#233;e dans une expression d’initialiseur d’objet, car toutes les surcharges accessibles n&#233;cessitent des arguments
Les membres initialisés dans une liste d’initialiseurs d’objets doivent être des champs ou des propriétés. De plus, les propriétés dans une liste d’initialiseurs ne peuvent pas avoir de paramètres. La propriété à l’origine de cette erreur est surchargée, et chacune de ses versions requiert des arguments. Ainsi, la propriété ne peut pas être initialisée dans une liste d’initialiseurs d’objets.  
  
 **ID d’erreur :** BC30993  
  
### Pour corriger cette erreur  
  
-   Supprimez la propriété qui requiert des arguments de la liste d’initialiseurs.  
  
## Exemple  
 La classe suivante contient trois définitions de propriétés : une pour `TotalItems` et deux pour `Item`, qui est surchargée.  
  
```  
Class CollectionOfItems Property TotalItems() As Integer Get End Get Set(ByVal value As Integer) End Set End Property Property Item(ByVal Key As String) As Object Get End Get Set(ByVal value As Object) End Set End Property Property Item(ByVal Index As Integer) As Object Get End Get Set(ByVal value As Object) End Set End Property End Class  
```  
  
 La propriété `TotalItems` ne requiert aucun argument et peut être initialisée dans une liste d’initialiseurs d’objets, comme indiqué dans la déclaration suivante.  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 }  
```  
  
 La propriété `Item` est surchargée et chaque surcharge requiert un argument. Ainsi, `Item` ne peut pas apparaître dans une liste d’initialiseurs d’objets.  
  
```  
' The following declaration is not valid. ' Dim coinCollection As New CollectionOfItems With { .TotalItems = 0, _ '    .Item = aCoinObject }  
```  
  
 Pour éviter cette erreur, initialisez la propriété `Item` à l’extérieur de l’initialiseur d’objets.  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 } coinCollection.Item(1) = aCoinObject  
```  
  
## Voir aussi  
 [NOT IN BUILD : Propriétés et Procédures de propriétés](http://msdn.microsoft.com/fr-fr/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [How to: Call a Property Procedure](../Topic/How%20to:%20Call%20a%20Property%20Procedure%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Propriétés par défaut](http://msdn.microsoft.com/fr-fr/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)