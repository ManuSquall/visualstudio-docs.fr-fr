---
title: "Erreur du compilateur CS0825 | Microsoft Docs"
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
  - "CS0825"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0825"
ms.assetid: 49393d23-ec5f-4b44-a3fd-7e0a95ac0edd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0825
Le mot clé contextuel 'var' ne peut apparaître que dans une déclaration de variable locale  
  
 Le typage implicite avec le mot clé `var` ne peut être appliqué qu’aux variables comprises dans la portée de la méthode locale.  
  
### Pour corriger cette erreur  
  
1.  Si la variable est comprise dans la portée de la classe, attribuez\-lui un type explicite.  Sinon, déplacez\-la à l’intérieur de la méthode dans laquelle elle sera utilisée.  
  
## Exemple  
 Le code suivant génère l’erreur CS0825, car `var` est utilisé sur un champ de classe :  
  
```  
// cs0825.cs class Test { private var myField; //CS0825 static int Main() { var a = 1; // var is OK here return -1; } }  
```  
  
## Voir aussi  
 [Variables locales implicitement typées](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)