---
title: "&#39;New&#39; ne peut pas &#234;tre utilis&#233; pour un param&#232;tre de type qui n’a pas de contrainte &#39;New&#39; | Microsoft Docs"
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
  - "bc32046"
  - "vbc32046"
helpviewer_keywords: 
  - "BC32046"
ms.assetid: 7ec6b52d-6fd5-47a0-b4a2-163bfd3dae35
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; ne peut pas &#234;tre utilis&#233; pour un param&#232;tre de type qui n’a pas de contrainte &#39;New&#39;
Une instruction de déclaration utilise une clause [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator) qui spécifie un paramètre de type comme le type à créer, et le paramètre de type est déclaré sans contrainte `New`.  
  
 Une *contrainte* appliquée à un paramètre de type impose des exigences à tous les arguments de type passés à ce paramètre de type quand le type générique est créé. La contrainte `New` spécifie que l’argument de type doit exposer un constructeur sans paramètre accessible par le code de création. C’est ce qui permet à une clause `New` d’une instruction de déclaration de créer une instance de ce type.  
  
 **ID d’erreur :** BC32046  
  
### Pour corriger cette erreur  
  
-   Si vous pouvez exiger que l’argument de type expose un constructeur sans paramètre accessible, ajoutez la contrainte `New` à la déclaration du paramètre de type.  
  
-   Si vous ne voulez pas que l’argument de type expose un constructeur sans paramètre accessible, supprimez la clause `New` de l’instruction de déclaration. Vous ne pouvez pas garantir que tous les arguments de type passés à ce paramètre de type permettront de créer une instance.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)