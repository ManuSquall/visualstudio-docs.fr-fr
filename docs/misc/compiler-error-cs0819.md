---
title: "Erreur du compilateur CS0819 | Microsoft Docs"
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
  - "CS0819"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0819"
ms.assetid: a5369e03-eb7d-4c88-b390-51304bd8d1ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0819
Les variables locales implicitement typées ne peuvent pas avoir plusieurs déclarateurs  
  
 L’utilisation de plusieurs déclarateurs est autorisée dans les déclarations de type explicite, mais pas dans les variables implicitement typées.  
  
### Pour corriger cette erreur  
  
1.  Déclarez, puis affectez une valeur à chaque variable locale implicitement typée sur une ligne distincte.  
  
## Exemple  
 Le code suivant génère l’erreur CS0819 :  
  
```  
// cs0819.cs class A { public static int Main() { var a = 3, b = 2; // CS0819 return -1; } }  
```  
  
## Voir aussi  
 [Variables locales implicitement typées](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)