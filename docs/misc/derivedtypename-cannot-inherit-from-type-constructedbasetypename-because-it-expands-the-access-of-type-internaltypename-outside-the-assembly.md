---
title: "&#39;&lt;nom_type_d&#233;riv&#233;&gt;&#39; ne peut pas h&#233;riter de &lt;type&gt; &#39;&lt;nom_type_base_construit&gt;&#39;, car il &#233;tend l’acc&#232;s du type &#39;&lt;nom_type_interne&gt;&#39; en dehors de l’assembly | Microsoft Docs"
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
  - "BC30922"
  - "vbc30922"
helpviewer_keywords: 
  - "BC30922"
ms.assetid: 81909654-7e67-4b89-81a3-25ae57f678f7
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_type_d&#233;riv&#233;&gt;&#39; ne peut pas h&#233;riter de &lt;type&gt; &#39;&lt;nom_type_base_construit&gt;&#39;, car il &#233;tend l’acc&#232;s du type &#39;&lt;nom_type_interne&gt;&#39; en dehors de l’assembly
Une classe ou une interface dérivée tente d’étendre le niveau d’accès d’un type restreint en l’utilisant comme argument de type d’une classe de base ou d’une interface.  
  
 Le code suivant peut générer cette erreur.  
  
```  
Public Class baseClass(Of t)  
End Class  
Public Class derivedClass  
    Inherits baseClass(Of restrictedStructure)  
End Class  
Friend Structure restrictedStructure  
    Dim firstMember As Integer  
End Structure  
```  
  
 Le code situé en dehors de l’assembly n’est pas autorisé à accéder à `restrictedStructure`. Cependant, `derivedClass` est accessible à n’importe quel code qui peut le référencer.`derivedClass` ne peut donc pas hériter de `baseClass` s’il utilise `restrictedStructure` comme argument de type, car cela peut exposer `restrictedStructure` au code dans n’importe quel assembly.  
  
 **ID d’erreur :** BC30922  
  
### Pour corriger cette erreur  
  
-   Ajustez les niveaux d’accès des classes ou des interfaces pour que le type dérivé ne développe pas le niveau d’accès du type restreint.  
  
     ou  
  
-   Si vous ne pouvez pas ajuster les niveaux d’accès, n’utilisez pas le type restreint comme argument de type lors de la construction d’une classe de base ou d’une interface.  
  
## Voir aussi  
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)