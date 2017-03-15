---
title: "Erreur du compilateur CS2016 | Microsoft Docs"
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
  - "CS2016"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2016"
ms.assetid: 69f77502-f726-4856-ac87-e556eeb67349
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS2016
La page de code 'codepage' n’est pas valide ou n’est pas installée  
  
 Une valeur non valide a été passée à l’option de compilateur [\/codepage](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).  
  
 L’exemple suivant génère l’erreur CS2016 :  
  
```  
// CS2016.cs // compile with: /codepage:x // CS2016 expected class MyClass { public static void Main() { } }  
```