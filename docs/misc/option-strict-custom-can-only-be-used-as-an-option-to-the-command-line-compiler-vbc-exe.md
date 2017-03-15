---
title: "Option Strict Custom ne peut &#234;tre utilis&#233; qu’en tant qu’option du compilateur de ligne de commande (vbc.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31141"
  - "bc31141"
helpviewer_keywords: 
  - "BC31141"
ms.assetid: c32ae8ff-aacc-40b4-960a-6f2d5d246671
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict Custom ne peut &#234;tre utilis&#233; qu’en tant qu’option du compilateur de ligne de commande (vbc.exe)
L’instruction `Option Strict` accepte uniquement `On` et `Off` en tant qu’arguments ; `Option Strict Custom` n’est pas autorisé.  
  
 Utilisez l’option du compilateur `/optionstrict:custom` pour signaler quand la syntaxe de langue stricte n’est pas respectée.  
  
 **ID d’erreur :** BC31141  
  
### Pour corriger cette erreur  
  
1.  Supprimez `Option Strict Custom` du code source.  
  
2.  Spécifiez l’option `/optionstrict:custom`. Pour plus d'informations, consultez [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
## Voir aussi  
 [Option \<keyword\> Statement](../Topic/Option%20%3Ckeyword%3E%20Statement.md)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)