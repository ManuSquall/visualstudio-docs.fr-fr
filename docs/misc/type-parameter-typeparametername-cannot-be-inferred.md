---
title: "Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; ne peut pas &#234;tre d&#233;duit | Microsoft Docs"
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
  - "bc36572"
  - "vbc36572"
helpviewer_keywords: 
  - "BC36572"
ms.assetid: 02264070-b055-4ab0-8d2a-eac4d90d9fdf
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; ne peut pas &#234;tre d&#233;duit
Une procédure générique est appelée sans fournir une liste d’arguments de type, et l’inférence du type échoue pour l’un des arguments de type.  
  
 Lorsque vous appelez une procédure générique, vous fournissez normalement un argument de type pour chaque paramètre de type défini par la procédure. Toutefois, vous avez la possibilité d’omettre totalement la liste d’arguments de type. Dans ce cas, le compilateur essaie de déduire le type de chaque argument de type à partir du contexte de votre appel. Pour plus d’informations, consultez « Inférence de type » dans [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **ID d’erreur :** BC36572  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les types des arguments normaux se présentent de telle sorte que l’inférence du type soit cohérente par rapport aux paramètres de type déclarés pour la procédure générique.  
  
     ou  
  
-   Appelez la procédure générique avec une liste d’arguments de type complète pour que l’inférence du type ne soit pas nécessaire.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)