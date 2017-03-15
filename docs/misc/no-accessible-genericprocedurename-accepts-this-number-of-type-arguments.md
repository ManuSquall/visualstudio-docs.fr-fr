---
title: "Aucun &#39;&lt;nom_proc&#233;dure_g&#233;n&#233;rique&#39; accessible n’accepte ce nombre d’arguments de type | Microsoft Docs"
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
  - "bc32118"
  - "vbc32118"
helpviewer_keywords: 
  - "BC32118"
ms.assetid: 4ee942ba-0fa1-4ec1-9c2c-a0c0dc3f1b17
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Aucun &#39;&lt;nom_proc&#233;dure_g&#233;n&#233;rique&#39; accessible n’accepte ce nombre d’arguments de type
Une instruction appelle une procédure générique qui contient plusieurs versions surchargées, mais aucune des versions surchargées ne définit le même nombre pour les paramètres de type et les arguments de type fournis dans l’appel.  
  
 S’il n’existe qu’une seule version générique et si vous l’appelez sans argument de type, le compilateur peut tenter une *inférence de type*. Pour plus d’informations, consultez « Inférence de type » dans [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures). Toutefois, s’il existe plusieurs versions génériques, le compilateur n’est pas en mesure de choisir entre eux, sauf si vous fournissez des arguments de type. Si vous fournissez un argument de type, vous devrez le faire pour chaque paramètre de type défini par l’une des versions surchargées.  
  
 **ID d’erreur :** BC32118  
  
### Pour corriger cette erreur  
  
-   Choisissez la version surchargée que vous voulez appeler, puis fournissez le nombre d’arguments de type approprié.  
  
## Voir aussi  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)