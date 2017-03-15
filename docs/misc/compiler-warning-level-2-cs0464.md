---
title: "Avertissement du compilateur (niveau&#160;2) CS0464 | Microsoft Docs"
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
  - "CS0464"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0464"
ms.assetid: 3dff97d4-e1f6-4a71-91e2-68cffc38d49a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0464
La comparaison avec null de type 'type' produit toujours 'false'  
  
 Cet avertissement est généré quand vous effectuez une comparaison entre une variable Nullable et une valeur Null, et que la comparaison n’est pas `==` ni `!=`. Pour résoudre cette erreur, assurez\-vous de bien vouloir vérifier une valeur pour `null`. Une comparaison comme `i == null` peut être true ou false. Une comparaison comme `i > null` est toujours false.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0464 :  
  
```  
// CS0464.cs class MyClass { public static void Main() { int? i = 0; if (i < null) ;   // CS0464 i++; } }  
```