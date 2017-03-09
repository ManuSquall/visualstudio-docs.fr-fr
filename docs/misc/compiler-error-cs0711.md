---
title: "Erreur du compilateur CS0711 | Microsoft Docs"
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
  - "CS0711"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0711"
ms.assetid: 3a5a6d90-e15d-4808-a7a6-c85fd011a0d0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0711
Les classes static ne peuvent pas contenir de destructeurs  
  
 Une classe static ne pouvant pas être instanciée, elle n’a pas besoin de constructeur ni de destructeur. Pour éviter cette erreur, supprimez tous les destructeurs des classes static ou, si vous voulez vraiment construire et détruire des instances, faites en sorte que la classe ne soit pas static.  
  
 L’exemple suivant génère l’erreur CS0711 :  
  
```  
// CS0711.cs public static class C { ~C()  // CS0711 { } public static void Main() { } }  
```