---
title: "Erreur du compilateur CS1508 | Microsoft Docs"
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
  - "CS1508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1508"
ms.assetid: 979bc615-58ce-49f8-ba73-e6cf57c56418
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1508
L’identificateur de ressource 'identifier' a déjà été utilisé dans cet assembly  
  
 Dans une compilation, le même identificateur \(***identifier***\) a été passé à deux options de compilateur [\/resource](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option) ou [\/linkresource](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option), ou plus.  
  
 Par exemple, les options suivantes génèrent l’erreur CS1508 :  
  
```  
/resource:anyfile.bmp,DuplicatIdent /linkresource:a.bmp,DuplicatIdent  
```