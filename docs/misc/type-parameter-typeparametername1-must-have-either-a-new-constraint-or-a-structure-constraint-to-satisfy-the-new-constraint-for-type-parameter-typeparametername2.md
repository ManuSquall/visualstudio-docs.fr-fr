---
title: "Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type1&gt;&#39; doit avoir une contrainte &#39;New&#39; ou une contrainte &#39;Structure&#39; pour satisfaire la contrainte &#39;New&#39; pour le param&#232;tre de type &#39;nom_param&#232;tre_type2&#39;. | Microsoft Docs"
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
  - "vbc32084"
  - "BC32084"
helpviewer_keywords: 
  - "BC32084"
ms.assetid: a7ff58d3-8c67-40e4-9fd8-92cc00524c22
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type1&gt;&#39; doit avoir une contrainte &#39;New&#39; ou une contrainte &#39;Structure&#39; pour satisfaire la contrainte &#39;New&#39; pour le param&#232;tre de type &#39;nom_param&#232;tre_type2&#39;.
Une instruction construit un type générique en passant un paramètre de type qui n’est pas contraint pour satisfaire une contrainte `New`.  
  
 La contrainte `New` signifie que l’argument de type fourni à ce paramètre de type doit exposer un constructeur sans paramètre accessible au code qui crée des objets à partir de celui\-ci. Tous les types valeur ont des constructeurs sans paramètre, mais ce n’est pas le cas de tous les types référence. La contrainte `Structure` satisfait donc la contrainte `New`, mais la contrainte `Class`, ou un nom de classe ou d’interface, ne la satisfont pas.  
  
 Les instructions suivantes peuvent générer cette erreur.  
  
```  
Public Class c1(Of t As New) End Class Public Class c2(Of u) Public testObject As New c1(Of u) End Class  
```  
  
 Quand la classe `c2` crée un objet à partir de `c1`, le paramètre de type `u` ne satisfait pas la contrainte `New` appliquée au paramètre de type `t`.  
  
 **ID d’erreur :** BC32084  
  
### Pour corriger cette erreur  
  
-   Si le paramètre de type à passer au type générique peut satisfaire la contrainte `Structure` ou `New`, ajoutez la contrainte appropriée à sa définition.  
  
    ```  
    Public Class c2(Of u As Structure)  
    ```  
  
-   Si le paramètre de type ne peut pas satisfaire la contrainte `Structure` ou `New`, ne le passez pas au type générique. Vous devez passer un autre élément comme argument de type.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Classe \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)