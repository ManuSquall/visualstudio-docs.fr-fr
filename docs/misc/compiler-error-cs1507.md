---
title: "Erreur du compilateur CS1507 | Microsoft Docs"
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
  - "CS1507"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1507"
ms.assetid: e1be3aba-81dc-4f65-87a4-d3f90b82dc7d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1507
Impossible de lier le fichier de ressources 'fichier' lors de la génération d’un module  
  
 [\/linkresource](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option) a été utilisé dans la même compilation que [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md), ce qui n’est pas autorisé. Par exemple, les options suivantes génèrent l’erreur CS1507 :  
  
```  
csc /linkresource:rf.resource /target:module in.cs  
```  
  
 Cependant, l’incorporation de ressources \([\/resource](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option)\) est autorisée.