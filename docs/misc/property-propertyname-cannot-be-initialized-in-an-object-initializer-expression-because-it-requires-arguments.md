---
title: "La propri&#233;t&#233; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre initialis&#233;e dans une expression d’initialiseur d’objet, car elle requiert des arguments | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30992"
  - "vbc30992"
helpviewer_keywords: 
  - "BC30992"
ms.assetid: a4d050b2-7366-457a-a852-8eb490c97573
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propri&#233;t&#233; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre initialis&#233;e dans une expression d’initialiseur d’objet, car elle requiert des arguments
Les membres initialisés dans une liste d’initialiseurs d’objets doivent être des champs ou des propriétés, et les membres de propriété ne peuvent pas avoir de paramètres. Par exemple, les propriétés par défaut nécessitent des arguments. Elles ne peuvent donc pas être initialisées dans une liste d’initialiseurs d’objets. Pour plus d’informations, consultez [NOT IN BUILD : Propriétés par défaut](http://msdn.microsoft.com/fr-fr/a70f2a27-8176-4858-935e-f25afdd43ab5).  
  
 **ID d’erreur :** BC30992  
  
### Pour corriger cette erreur  
  
-   Supprimez de la liste d’initialisation toutes les propriétés qui possèdent des arguments.  
  
## Exemple  
 La classe suivante contient une propriété par défaut, `defaultProp`, qui nécessite un argument entier.  
  
```  
Public Class SomeStrings Private myStrings() As String Sub New(ByVal size As Integer) ReDim myStrings(size) End Sub Default Property defaultProp(ByVal index As Integer) As String Get Return myStrings(index) End Get Set(ByVal Value As String) myStrings(index) = Value End Set End Property End Class  
```  
  
 Étant donné que la propriété par défaut nécessite un argument, la déclaration suivante génère une erreur.  
  
```  
' Dim strs As New SomeStrings(2) With { .defaultProp = "One" }  
```  
  
## Voir aussi  
 [NOT IN BUILD : Propriétés par défaut](http://msdn.microsoft.com/fr-fr/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [NOT IN BUILD : Propriétés et procédures de propriété](http://msdn.microsoft.com/fr-fr/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)