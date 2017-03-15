---
title: "Erreur du compilateur CS1675 | Microsoft Docs"
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
  - "CS1675"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1675"
ms.assetid: add10021-f751-45c7-addc-0f73fa4a267c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1675
Les enums ne peuvent pas avoir de paramètres de type  
  
 Pour résoudre cette erreur, supprimez le paramètre de type de la déclaration `enum`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1675 :  
  
```  
// CS1675.cs enum E<T>  // CS1675 { } class CMain { public static void Main() { } }  
```