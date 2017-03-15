---
title: "Le nom du param&#232;tre de type &#39;&lt;nom_param&#232;tre_type1&gt;&#39; ne correspond pas &#224; &#39;&lt;nom_param&#232;tre_type2&gt;&#39;, le param&#232;tre de type correspondant d&#233;fini dans la d&#233;claration de m&#233;thode partielle &#39;&lt;nom_m&#233;thode&gt;&#39; | Microsoft Docs"
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
  - "vbc31443"
  - "bc31443"
helpviewer_keywords: 
  - "BC31443"
ms.assetid: 27c81cc1-325e-4e86-9d00-34f81e928076
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le nom du param&#232;tre de type &#39;&lt;nom_param&#232;tre_type1&gt;&#39; ne correspond pas &#224; &#39;&lt;nom_param&#232;tre_type2&gt;&#39;, le param&#232;tre de type correspondant d&#233;fini dans la d&#233;claration de m&#233;thode partielle &#39;&lt;nom_m&#233;thode&gt;&#39;
Dans une méthode partielle qui inclut un ou plusieurs paramètres de type, les noms des paramètres de type doivent être identiques dans la déclaration et dans l’implémentation de la méthode.  
  
 Par exemple, la déclaration et l’implémentation suivantes provoquent cette erreur.  
  
```vb#  
' Definition of the partial method signature with type parameter T. Partial Private Sub OnNameChanged(Of T)() End Sub  
```  
  
```vb#  
'' Implementation of the partial method with type parameter N. 'Private Sub OnNameChanged(Of N)() '    Console.WriteLine("Name was changed to " & Me.Name) 'End Sub  
```  
  
 **ID d’erreur :** BC31443  
  
### Pour corriger cette erreur  
  
-   Examinez les paramètres de type pour déterminer à quel endroit ils ne correspondent pas. Au besoin, modifiez les noms pour qu’ils soient identiques.  
  
## Voir aussi  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)