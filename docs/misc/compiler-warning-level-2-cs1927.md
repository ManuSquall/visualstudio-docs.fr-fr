---
title: "Avertissement du compilateur (niveau&#160;2) CS1927 | Microsoft Docs"
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
  - "CS1927"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1927"
ms.assetid: 32b4e58f-668c-4596-9529-7f3a293ff4ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS1927
L’option \/win32manifest est ignorée pour le module car elle s’applique uniquement aux assemblys.  
  
 Un manifeste win32 s’applique uniquement au niveau de l’assembly. Votre module va se compiler, mais il n’aura pas de manifeste.  
  
### Pour corriger cette erreur  
  
1.  Supprimez **\/win32manifest option**.  
  
2.  Compilez le code en tant qu’assembly.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS1927 quand il est compilé avec les options du compilateur **\/target:module** et **\/win32manifest**.  
  
```  
// cs1927.cs // Compile with: /target:module /win32manifest using System; class ManifestWithModule { static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [\/win32manifest \(Import a Custom Win32 Manifest File\)](/dotnet/csharp/language-reference/compiler-options/win32manifest-compiler-option)   
 [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)