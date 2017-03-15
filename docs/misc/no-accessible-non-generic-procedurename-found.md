---
title: "Aucun &#39;&lt;nom_proc&#233;dure&gt;&#39; accessible non g&#233;n&#233;rique trouv&#233;. | Microsoft Docs"
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
  - "vbc32117"
  - "bc32117"
helpviewer_keywords: 
  - "BC32117"
ms.assetid: a7bf8b67-8a0a-499e-9992-dc00e09b7ff4
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Aucun &#39;&lt;nom_proc&#233;dure&gt;&#39; accessible non g&#233;n&#233;rique trouv&#233;.
Une instruction appelle une procédure qui possède plusieurs versions surchargées, mais toutes les versions surchargées sont génériques et l’appel ne fournit pas d’arguments de type.  
  
 S’il n’existe qu’une seule version générique et si vous l’appelez sans argument de type, le compilateur peut tenter une *inférence de type*. Pour plus d’informations, consultez « Inférence de type » dans [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures). Toutefois, s’il existe plusieurs versions génériques, le compilateur n’est pas en mesure de choisir entre eux, sauf si vous fournissez des arguments de type. Si vous fournissez un argument de type, vous devrez le faire pour chaque paramètre de type défini par l’une des versions surchargées.  
  
 **ID d’erreur :** BC32117  
  
### Pour corriger cette erreur  
  
-   Appelez la procédure avec une liste d’arguments de type.  
  
## Voir aussi  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)