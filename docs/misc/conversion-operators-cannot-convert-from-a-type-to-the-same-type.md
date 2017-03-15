---
title: "Les op&#233;rateurs de conversion ne peuvent pas convertir d&#39;un type en un type identique | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33024"
  - "vbc33024"
helpviewer_keywords: 
  - "BC33024"
ms.assetid: 4b47bcb0-4f0c-4d1c-9274-cce5b8e2b370
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les op&#233;rateurs de conversion ne peuvent pas convertir d&#39;un type en un type identique
Un opérateur de conversion est déclaré avec le même type pour le paramètre et la valeur de retour.  
  
 Il n’est pas possible de convertir un type en lui\-même.  
  
 **ID d’erreur :** BC33024  
  
### Pour corriger cette erreur  
  
-   Modifiez le type du paramètre ou de la valeur de retour. L’un des deux doit être du type de la classe ou de la structure dans laquelle cet opérateur est défini. L’autre doit être d’un type différent.  
  
-   Si vous avez besoin de transformer le contenu du paramètre, utilisez une [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) pour définir une procédure `Function` au lieu d’un opérateur.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)