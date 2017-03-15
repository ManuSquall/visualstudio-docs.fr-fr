---
title: "Erreur du compilateur CS0057 | Microsoft Docs"
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
  - "CS0057"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0057"
ms.assetid: 0bdd628f-7a1f-4209-bb28-c4a66eb3bf1d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0057
Accessibilité incohérente : le type de paramètre 'type' est moins accessible que l’opérateur 'operator'  
  
 Une construction publique doit retourner un objet accessible publiquement. Pour plus d'informations, consultez [Modificateurs d'accès](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 L’exemple suivant génère l’erreur CS0057 :  
  
```  
// CS0057.cs class MyClass //defaults to private accessibility // try the following line instead // public class MyClass { } public class MyClass2 { public static implicit operator MyClass2(MyClass iii)   // CS0057 { return new MyClass2(); } public static void Main() { } }  
```