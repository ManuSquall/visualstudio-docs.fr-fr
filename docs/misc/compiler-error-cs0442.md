---
title: "Erreur du compilateur CS0442 | Microsoft Docs"
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
  - "CS0442"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0442"
ms.assetid: a411660d-0db6-4b63-b19e-f4538fc201e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0442
'Propriété' : les propriétés abstraites ne peuvent pas avoir d’accesseurs private  
  
 Cette erreur se produit quand vous utilisez le modificateur d’accès « private » pour modifier un accesseur abstrait. Pour résoudre ce problème, utilisez un autre modificateur d’accès ou rendez la propriété non abstraite.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0442 :  
  
```  
// CS0442.cs public abstract class MyClass { public abstract int AbstractProperty { get; private set;   // CS0442 // Try this instead: // set; } }  
```