---
title: "Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; pour &#39;&lt;nom_proc&#233;dure_g&#233;n&#233;rique&gt;&#39; ne peut pas &#234;tre d&#233;duit | Microsoft Docs"
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
  - "vbc32050"
  - "bc32050"
helpviewer_keywords: 
  - "BC32050"
ms.assetid: e4a69ffb-0764-4e5a-8de1-40f881a3f4fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; pour &#39;&lt;nom_proc&#233;dure_g&#233;n&#233;rique&gt;&#39; ne peut pas &#234;tre d&#233;duit
Une procédure générique est appelée sans fournir de liste d’arguments de type, et l’inférence du type échoue pour l’un des arguments de type.  
  
 Quand vous appelez une procédure générique, vous fournissez normalement un argument de type pour chaque paramètre de type défini par la procédure. Cependant, vous pouvez omettre totalement la liste d’arguments de type. Dans ce cas, le compilateur essaie de déduire le type de chaque argument de type à partir du contexte de votre appel. Pour plus d’informations, consultez « Inférence de type » dans [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 Une des causes possibles de l’échec de l’inférence de type est une incompatibilité de rang entre un paramètre de type et le type appelant. Le code suivant illustre ce comportement :  
  
```  
Public Sub displayLargest(Of t As IComparable)(ByVal arg() As t) ' Insert code to find and display the largest element of arg(). End Sub Public Sub callGenericSub() Dim testValue As Integer findLargest(testValue) Dim testMatrix(,) As Integer findLargest(testMatrix) End Sub  
```  
  
 Dans le code précédent, les deux appels à `findLargest` génèrent cette erreur, car le paramètre de type `t` appelle un tableau unidimensionnel, alors que les arguments de type déduits à partir des appels par le compilateur sont une valeur scalaire \(`testValue`\) et un tableau à deux dimensions \(`testMatrix`\).  
  
 **ID d’erreur :** BC32050  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les types des arguments normaux sont tels que l’inférence du type est cohérente par rapport aux paramètres de type déclarés pour la procédure générique.  
  
     ou  
  
-   Appelez la procédure générique avec une liste d’arguments de type complète pour que l’inférence du type ne soit pas nécessaire.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)