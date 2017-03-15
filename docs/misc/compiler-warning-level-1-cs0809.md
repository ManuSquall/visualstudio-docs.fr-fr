---
title: "Avertissement du compilateur (niveau&#160;1) CS0809 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0809"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0809"
ms.assetid: 2c2f0248-ab3a-4cdc-a1b0-2f0e05eac4c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS0809
Le membre obsolète 'memberA' se substitue au membre non obsolète 'memberB'.  
  
 En règle générale, un membre qui est marqué comme obsolète ne doit pas se substituer à un membre qui n’est pas marqué comme obsolète. Cet avertissement est généré dans [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)], mais pas dans [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’attribut `Obsolete` du membre de substitution ou ajoutez\-le au membre de la classe de base.  
  
## Exemple  
  
```  
// CS0809.cs public class Base { public virtual void Test1() { } } public class C : Base { [System.Obsolete()] public override void Test1() // CS0809 { } }  
```