---
title: "Erreur du compilateur&#160;CS1917 | Microsoft Docs"
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
  - "CS1917"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1917"
ms.assetid: 05688706-e4b4-4273-9244-48cce1f7f9b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1917
Les membres d’un champ en lecture seule 'name' de type 'struct name' ne peuvent pas être assignés à l’aide d’un initialiseur d’objet, car il s’agit d’un type valeur.  
  
 Les champs en lecture seule qui sont des types valeur peuvent uniquement être assignés dans un constructeur.  
  
### Pour corriger cette erreur  
  
-   Remplacez le struct par un type de classe.  
  
-   Initialisez le struct avec un constructeur.  
  
## Exemple  
 Le code suivant génère l’erreur CS1917 :  
  
```  
// cs1917.cs class CS1917 { public struct TestStruct { public int i; } public class C { public readonly TestStruct str = new TestStruct(); public static int Main() { C c = new C { str = { i = 1 } }; // CS1917 return 0; } } }  
```