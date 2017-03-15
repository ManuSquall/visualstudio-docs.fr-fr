---
title: "&#201;chec de l’inf&#233;rence d’argument de type pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type1&gt;&#39; de &#39;&lt;signature_proc&#233;dure_g&#233;n&#233;rique&gt;&#39; | Microsoft Docs"
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
  - "vbc32116"
  - "bc32116"
helpviewer_keywords: 
  - "BC32116"
ms.assetid: 6bfb02ec-814a-4b1f-a585-6d902a861d00
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#201;chec de l’inf&#233;rence d’argument de type pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type1&gt;&#39; de &#39;&lt;signature_proc&#233;dure_g&#233;n&#233;rique&gt;&#39;
Échec de l’inférence d’argument de type pour le paramètre de type '\<nom\_paramètre\_type1\>' de '\<signature\_procédure\_générique\>'. L’argument de type inféré de l’argument passé au paramètre '\<nom\_paramètre1\>' est en conflit avec l’argument de type inféré de l’argument passé au paramètre '\<nom\_paramètre2\>'.  
  
 Une procédure générique est appelée sans argument de type et l’inférence de type tentée a généré un conflit de type de données parmi les paramètres de type.  
  
 Normalement, quand vous appelez une procédure générique, vous fournissez un argument de type pour chaque paramètre de type que la procédure générique définit. Si vous ne fournissez pas d’arguments de type, le compilateur tente de déduire les types à passer aux paramètres de type. Si le contexte de l’appel fournit des informations de type de données conflictuelles pour un paramètre de type, l’inférence de type échoue.  
  
 Le code suivant peut générer cette erreur.  
  
```  
Public Sub takeTwoValues(Of t)(ByVal x As t, ByVal y As t) End Sub Call takeTwoValues(4, 2.5)  
```  
  
 Étant donné que le premier argument indique au compilateur de déduire `Integer` pour le paramètre de type `t`, tandis que le deuxième argument provoque l’inférence de `Double` pour le même paramètre de type, il existe un conflit sur le type de données à passer à `t`.  
  
 **ID d’erreur :** BC32116  
  
### Pour corriger cette erreur  
  
-   Fournissez des arguments de type au type générique, afin que le compilateur n’ait pas à les déduire.  
  
    ```  
    Call takeTwoValues(Of Double)(4, 2.5)  
    ```  
  
     Notez que dans ce cas, quand les deux arguments normaux sont de différents types de données, le code appelant doit passer un argument de type qui peut prendre en charge ces deux types de données. Dans ce cas, `Integer` s’étend à `Double`.  
  
     ou  
  
-   Redéfinissez la procédure générique pour spécifier différents paramètres de type pour les paramètres normaux, afin qu’il n’existe aucun conflit d’inférence des types.  
  
    ```  
    Public Sub takeTwoValues(Of t1, t2)(ByVal x As t1, ByVal y As t2)  
    ```  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)