---
title: "Erreur du compilateur CS0734 | Microsoft Docs"
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
  - "CS0734"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0734"
ms.assetid: 9e1b0e49-bfc3-400c-9fd1-37e3c827e656
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0734
L’option \/moduleassemblyname ne peut être spécifiée que lors de la génération d’un type cible de 'module'  
  
 L’option de compilateur **\/moduleassemblyname** doit uniquement être utilisée lors de la création d’un fichier .netmodule. Pour plus d’informations, consultez [\/moduleassemblyname \(Specify Friend Assembly for Module\)](/dotnet/csharp/language-reference/compiler-options/moduleassemblyname-compiler-option).  
  
 Pour plus d’informations sur la création d’un fichier .netmodule, consultez [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0734 : Pour résoudre ce problème, ajoutez **\/target:module** à la compilation.  
  
```  
// CS0734.cs // compile with: /moduleassemblyname:A // CS0734 expected public class Test {}  
```