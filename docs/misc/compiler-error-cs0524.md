---
title: "Erreur du compilateur CS0524 | Microsoft Docs"
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
  - "CS0524"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0524"
ms.assetid: a5cd8fb0-f5df-4580-9116-a6be4dffd1cb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0524
'type' : les interfaces ne peuvent pas déclarer de types  
  
 Une [interface](/dotnet/csharp/language-reference/keywords/interface) ne peut pas contenir un type défini par l’utilisateur. Elle doit contenir uniquement des méthodes et des propriétés.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0524 :  
  
```  
// CS0524.cs public interface Clx { public class Cly   // CS0524, delete user-defined type { } }  
  
```