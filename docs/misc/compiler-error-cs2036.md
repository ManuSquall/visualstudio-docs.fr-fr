---
title: "Erreur du compilateur CS2036 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2036"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2036"
ms.assetid: 44b73be4-b792-4735-bdbd-bd757ab22683
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS2036
L’option \/pdb exige que l’option \/debug soit également utilisée.  
  
 Les fichiers de base de données de programme sont générés uniquement pour les versions debug. L’option **\/pdb** n’a donc aucun sens dans une version commerciale.  
  
### Pour corriger cette erreur  
  
-   Ajoutez l’option du compilateur **\/debug**.  
  
-   Supprimez l’option du compilateur **\/pdb**.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS2036 lorsqu’il est compilé avec l’option **\/pdb** mais sans l’option \/debug :  
  
```  
// cs2036.cs // Compile with: /pdb // CS2036 class Test { public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [\/pdb \(Specify Debug Symbol File\)](/dotnet/csharp/language-reference/compiler-options/pdb-compiler-option)   
 [\/debug \(Emit Debugging Information\)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)