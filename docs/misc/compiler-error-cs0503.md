---
title: "Erreur du compilateur CS0503 | Microsoft Docs"
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
  - "CS0503"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0503"
ms.assetid: 12a337c9-8c5d-473d-8ce6-057b2c7e7935
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0503
La méthode 'méthode' de type abstract ne peut pas être marquée virtual  
  
 Il est superflu de marquer une méthode membre à la fois comme [abstract](/dotnet/csharp/language-reference/keywords/abstract) et [virtual](/dotnet/csharp/language-reference/keywords/virtual), car **abstract** implique **virtual**.  
  
 L’exemple suivant génère l’erreur CS0503 :  
  
```  
// CS0503.cs namespace x { abstract public class clx { abstract virtual public void f();   // CS0503 } }  
```