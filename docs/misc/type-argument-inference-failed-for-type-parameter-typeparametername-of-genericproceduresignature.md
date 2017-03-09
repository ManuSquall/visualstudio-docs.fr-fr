---
title: "&#201;chec de l’inf&#233;rence d’argument de type pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; de &#39;&lt;signature_proc&#233;dure_g&#233;n&#233;rique&gt;&#39; | Microsoft Docs"
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
  - "vbc32051"
  - "bc32051"
helpviewer_keywords: 
  - "BC32051"
ms.assetid: a9c2a0ce-e225-4549-bfd8-d42df5d16bfd
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#201;chec de l’inf&#233;rence d’argument de type pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; de &#39;&lt;signature_proc&#233;dure_g&#233;n&#233;rique&gt;&#39;
Échec de l’inférence d’argument de type pour le paramètre de type '\<nom\_paramètre\_type\>' de '\<signature\_procédure\_générique\>'. L’argument de type n’a pas pu être déduit à partir de l’argument passé au paramètre '\<nom\_paramètre\>'.  
  
 Une procédure générique a été appelée sans que des arguments de type aient été fournis et le compilateur ne peut pas déduire le type à passer à l’un des paramètres.  
  
 Normalement, quand vous appelez une procédure générique, vous fournissez un argument de type pour chaque paramètre de type que la procédure générique définit. Si vous ne fournissez pas d’arguments de type, le compilateur tente de déduire les types à passer aux paramètres de type. Si le contexte de l’appel fournit des informations de type de données conflictuelles pour un paramètre de type, l’inférence de type échoue.  
  
 Le code suivant peut générer cette erreur.  
  
```  
Public Sub doSomething(Of t)(ByVal arg1 As t(), ByVal arg2 As t) End Sub Call doSomething(6, 42)  
```  
  
 Dans l’exemple précédent, le compilateur déduit le type `Integer` pour `t` en se basant sur la valeur 42 passée à `arg2`. Toutefois, cette inférence nécessite que `arg1` soit du type `Integer()`, autrement dit, un tableau `Integer`, mais la valeur 6 passée à `arg1` ne correspond pas à ce type.  
  
 **ID d’erreur :** BC32051  
  
### Pour corriger cette erreur  
  
-   Fournissez des arguments de type à la procédure générique afin que le compilateur n’ait pas besoin de les déduire.  
  
-   Fournissez des arguments normaux avec des types qui correspondent à ceux des arguments de type.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)