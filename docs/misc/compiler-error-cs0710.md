---
title: "Erreur du compilateur CS0710 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0710"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0710"
ms.assetid: 753a1a87-f5e5-4758-a960-515069a6c7b0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0710
Les classes static ne peuvent pas avoir de constructeurs d'instance  
  
 Une classe static ne pouvant pas être instanciée, elle n’a pas besoin de constructeur. Pour éviter cette erreur, supprimez tous les constructeurs des classes static ou, si vous souhaitez vraiment construire des instances, faites en sorte que la classe ne soit pas static.  
  
 L’exemple suivant génère l’erreur CS0710 :  
  
```  
// CS0710.cs public static class C { public C()  // CS0710 { } public static void Main() { } }  
```