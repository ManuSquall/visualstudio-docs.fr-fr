---
title: "Erreur du compilateur CS0529 | Microsoft Docs"
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
  - "CS0529"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0529"
ms.assetid: 61de8086-f991-455c-b009-bb8cd05f34bd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0529
L’interface héritée 'interface1' provoque un cycle dans la hiérarchie des interfaces de 'interface2'  
  
 La liste d’héritage pour une [interface](/dotnet/csharp/language-reference/keywords/interface) comprend une référence directe ou indirecte à elle\-même. Une interface ne peut pas hériter d’elle\-même.  
  
 L’exemple suivant génère l’erreur CS0529 :  
  
```  
// CS0529.cs namespace x { public interface a { } public interface b : a, c { } public interface c : b   // CS0529, b inherits from c { } }  
```