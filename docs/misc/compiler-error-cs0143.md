---
title: "Erreur du compilateur CS0143 | Microsoft Docs"
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
  - "CS0143"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0143"
ms.assetid: dfe6f6ba-dec9-49bd-9d5b-3dc4743bd940
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0143
Aucun constructeur n’est défini pour le type 'classe'  
  
 Aucun constructeur approprié n’est disponible. C’est le cas des types valeur numériques intégrés, qui sont initialisés quand une valeur leur est assignée.  
  
 L’exemple suivant génère l’avertissement CS0143 :  
  
```  
// CS0143.cs class MyClass { static public void Main () { double d = new double(4.5);   // CS0143 // Try this line instead: // double d = 4.5; } }  
```