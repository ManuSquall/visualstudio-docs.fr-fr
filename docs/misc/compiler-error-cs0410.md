---
title: "Erreur du compilateur CS0410 | Microsoft Docs"
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
  - "CS0410"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0410"
ms.assetid: a8b11042-9119-465e-abf6-235cbc7b8db5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0410
Aucune surcharge pour 'méthode' ne possède les types de paramètres et de retour corrects  
  
 Cette erreur se produit si vous essayez d’instancier un délégué avec une fonction qui ne possède pas les bons types de paramètres. Les types de paramètre du délégué doivent correspondre à la fonction que vous assignez au délégué.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0410 :  
  
```  
// CS0410.cs // compile with: /langversion:ISO-1 class Test { delegate void D(double d ); static void F(int i) { } static void Main() { D d = new D(F);  // CS0410 } }  
```