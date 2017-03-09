---
title: "Erreur du compilateur CS0822 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0822"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0822"
ms.assetid: 519091be-2332-4df4-acd9-e3b633966b3d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0822
Les variables locales implicitement typées ne peuvent pas être const  
  
 Les variables locales implicitement typées ne sont nécessaires que pour stocker des types anonymes. Dans tous les autres cas, leur intérêt réside seulement dans leur aspect pratique. Si la valeur de la variable ne change jamais, attribuez\-lui simplement un type explicite. L’utilisation du modificateur `readonly` avec une variable locale implicitement typée aura pour effet de générer l’erreur CS0106.  
  
### Pour corriger cette erreur  
  
1.  Si vous avez besoin que la variable soit de type constant ou `readonly`, attribuez\-lui un type explicite.  
  
## Exemple  
 Le code suivant génère l’erreur CS0822 :  
  
```  
// cs0822.cs class A { public static int Main() { const var x = 0; // CS0822.cs return -1; } }  
```  
  
## Voir aussi  
 [Variables locales implicitement typées](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)