---
title: "Erreur du compilateur CS2024 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2024"
ms.assetid: 65cf7419-a5a6-4128-88af-176dc8dba14f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS2024
Numéro d’alignement de section de fichier non valide '\#'  
  
 Une valeur non valide a été passée à l’option de compilateur [\/filealign](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).  
  
 L’exemple suivant génère l’erreur CS2024 :  
  
```  
// CS2024.cs // compile with: /filealign:ex // CS2024 expected class MyClass { public static void Main() { } }  
```