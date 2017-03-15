---
title: "Erreur de syntaxe dans l’op&#233;rateur de cast&#160;; deux arguments s&#233;par&#233;s par une virgule sont requis | Microsoft Docs"
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
  - "vbc30944"
  - "bc30944"
helpviewer_keywords: 
  - "BC30944"
ms.assetid: 1f7ed4a1-6ff5-4836-8424-21618c68ff45
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Erreur de syntaxe dans l’op&#233;rateur de cast&#160;; deux arguments s&#233;par&#233;s par une virgule sont requis
Une expression utilise la fonction de conversion `CType` ou le mot clé de conversion `DirectCast` ou `TryCast`, mais ne fournit qu’un seul argument.  
  
 `CType`, `DirectCast` et `TryCast` nécessitent tous deux arguments. Le premier argument est une expression à convertir et le second argument est le type de données ou de classe de conversion.  
  
 **ID d’erreur :** BC30944  
  
### Pour corriger cette erreur  
  
-   Fournissez les deux arguments selon les besoins de conversion.  
  
-   Si vous comptez utiliser l’une des [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions) spécifiques, par exemple `CString`, vous devez utiliser ce nom de fonction au lieu de `CType`. Un seul argument est requis.  
  
## Voir aussi  
 [CType, fonction](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)