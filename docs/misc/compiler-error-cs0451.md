---
title: "Erreur du compilateur CS0451 | Microsoft Docs"
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
  - "CS0451"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0451"
ms.assetid: e73544f8-856b-4a92-90e0-dd6cb9d688b1
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0451
La contrainte 'new\(\)' ne peut pas être utilisée avec la contrainte 'struct'  
  
 Au moment de spécifier des contraintes sur le type d’un générique, la contrainte `new()` ne peut être utilisée qu’avec des contraintes de type classe, des contraintes de type interface, des contraintes de type référence et des contraintes de paramètre de type, mais pas avec des contraintes de type valeur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0451.  
  
```  
// CS0451.cs using System; public class C4 { public void F4<T>() where T : struct, new() {}   // CS0451 } // OK public class C5 { public void F5<T>() where T : struct {} } public class C6 { public void F6<T>() where T : new() {} }  
  
```