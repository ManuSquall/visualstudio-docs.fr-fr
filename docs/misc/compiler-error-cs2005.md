---
title: "Erreur du compilateur CS2005 | Microsoft Docs"
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
  - "CS2005"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2005"
ms.assetid: 03535d2a-ae30-4272-ab45-e277df5ee8e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS2005
Spécification de fichier manquante pour l’option 'option'  
  
 Une [option du compilateur](/dotnet/csharp/language-reference/compiler-options/index) n’a été spécifiée que partiellement.  
  
 Par exemple, lorsque vous utilisez [\/recurse](/dotnet/csharp/language-reference/compiler-options/recurse-compiler-option), vous devez spécifier le fichier à rechercher : **\/recurse:***nom\_fichier***.cs**.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS2005.  
  
```  
// CS2005.cs // compile with: /recurse: // CS2005 expected class x { public static void Main() {} }  
```