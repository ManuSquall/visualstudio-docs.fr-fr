---
title: "Erreur du compilateur CS0528 | Microsoft Docs"
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
  - "CS0528"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0528"
ms.assetid: 8f5dde55-7e4f-4ffa-be14-0e0f3a538118
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0528
'interface' est déjà énuméré dans la liste des interfaces  
  
 Une liste d’héritage d’interface comprend un doublon. Une [interface](/dotnet/csharp/language-reference/keywords/interface) ne peut être spécifiée qu’une seule fois dans la liste d’héritage.  
  
 L’exemple suivant génère l’erreur CS0528 :  
  
```  
// CS0528.cs namespace x { public interface a { } public class b : a, a   // CS0528 { public void Main() { } } }  
```