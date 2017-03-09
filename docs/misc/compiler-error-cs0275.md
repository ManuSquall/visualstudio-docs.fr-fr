---
title: "Erreur du compilateur CS0275 | Microsoft Docs"
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
  - "CS0275"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0275"
ms.assetid: 4d59f11c-b0ea-4c91-b2cb-cbe3be9a9ba2
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0275
'accesseur' : les modificateurs d’accessibilité ne peuvent pas être utilisés sur des accesseurs dans une interface  
  
 Cette erreur se produit quand vous utilisez un modificateur d’accès sur l’un des accesseurs d’une propriété ou d’un indexeur dans une interface. Pour résoudre le problème, supprimez le modificateur d’accès.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0275 :  
  
```  
// CS0275.cs public interface MyInterface { int Property { get; internal set;   // CS0275 } }  
```