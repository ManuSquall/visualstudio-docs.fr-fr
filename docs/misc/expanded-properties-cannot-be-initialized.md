---
title: "Les propri&#233;t&#233;s d&#233;velopp&#233;es ne peuvent pas &#234;tre initialis&#233;es | Microsoft Docs"
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
  - "vbc36714"
  - "bc36714"
helpviewer_keywords: 
  - "BC36714"
ms.assetid: ba9408f3-e606-4749-8372-987999f405f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les propri&#233;t&#233;s d&#233;velopp&#233;es ne peuvent pas &#234;tre initialis&#233;es
Contrairement à une propriété implémentée automatiquement, une propriété développée ne peut pas être initialisée dans le cadre de sa déclaration.  
  
 **ID d’erreur :** BC36714  
  
### Pour corriger cette erreur  
  
-   Utilisez une propriété implémentée automatiquement ou supprimez l’initialisation de la déclaration de la propriété.  
  
## Exemple  
 Les exemples suivants montrent des propriétés implémentées automatiquement et des propriétés développées. Contrairement aux propriétés implémentées automatiquement, les propriétés développées ne peuvent pas être initialisées par assignation ou à l’aide d’une clause `New`.  
  
```vb#  
Class AutoImplementedExample ' An auto-implemented property can be assigned an initial value. Property IDNum As Integer = 33542 ' An auto-implemented property can be initialized with New. Property Name As New String("Don Hall") End Class Class ExpandedExample ' Attempting to expand an initialized auto-implemented property ' causes this error. 'Property IDNum As Integer = 33542 '    Get '    End Get '    Set(ByVal value As Integer) '    End Set 'End Property ' Instead, you can assign the initial value to the backing field. Private _IDNum As Integer = 33542 Property IDNum As Integer Get End Get Set(ByVal value As Integer) End Set End Property End Class  
```  
  
## Voir aussi  
 [Auto\-Implemented Properties](/dotnet/visual-basic/programming-guide/language-features/procedures/auto-implemented-properties)   
 [How to: Create a Property](../Topic/How%20to:%20Create%20a%20Property%20\(Visual%20Basic\).md)   
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)