---
title: "Erreur du compilateur CS0430 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0430"
ms.assetid: b63c4f9a-b1cd-41d2-a02e-2ed0f177450f
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0430
L’alias extern 'alias' n’a pas été spécifié dans une option \/reference  
  
 Cette erreur se produit quand l’alias extern est rencontré mais qu’Alias n’a pas été spécifié comme référence sur la ligne de commande. Pour résoudre l’erreur CS0430, compilez avec **\/reference**.  
  
## Exemple  
  
```  
// CS0430_a.cs // compile with: /target:library public class MyClass {}  
```  
  
## Exemple  
 La compilation avec **\/reference:MyType\=cs0430\_a.dll** pour faire référence à la DLL créée dans l’exemple précédent permet de résoudre cette erreur. L’exemple suivant génère l’erreur CS0430.  
  
```  
// CS0430_b.cs extern alias MyType;   // CS0430 public class Test { public static void Main() {} }  
  
```