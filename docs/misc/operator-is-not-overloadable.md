---
title: "L’op&#233;rateur n’est pas surchargeable | Microsoft Docs"
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
  - "vbc33002"
  - "bc33002"
helpviewer_keywords: 
  - "BC33002"
ms.assetid: 8628ea42-57d8-41ca-8bdc-5e4c27be543e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rateur n’est pas surchargeable
Seuls certains opérateurs prennent en charge la surcharge. Le tableau suivant présente les opérateurs que vous pouvez définir.  
  
|Type|Opérateurs|  
|----------|----------------|  
|Unaire|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binaire|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversion \(unaire\)|`CType`|  
  
 Notez que l’opérateur `=` dans la liste binaire est l’opérateur de comparaison, et non l’opérateur d’assignation.  
  
 **ID d’erreur :** BC33002  
  
### Pour corriger cette erreur  
  
1.  Sélectionnez un opérateur dans le jeu d’opérateurs surchargeables.  
  
2.  Si vous avez besoin des fonctionnalités de surcharge d’un opérateur que vous ne pouvez pas surcharger directement, créez une procédure `Function` qui accepte les paramètres appropriés et retourne la valeur adéquate.  
  
## Voir aussi  
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)