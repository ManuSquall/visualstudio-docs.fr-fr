---
title: "Erreur du compilateur CS0546 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0546"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0546"
ms.assetid: d259c86f-ee29-4e2d-b381-6ba7252af87e
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0546
'accesseur' : substitution impossible, car 'propriété' n’a pas d’accesseur set substituable  
  
 La tentative de substitution de l’une des méthodes d’accesseur d’une propriété a échoué, car l’accesseur ne peut pas être substitué. Cette erreur peut se produire quand :  
  
-   la propriété de classe de base n’est pas déclarée comme [virtual](/dotnet/csharp/language-reference/keywords/virtual) ;  
  
-   la propriété de classe de base ne déclare pas l’accesseur [get](/dotnet/csharp/language-reference/keywords/get) ou [set](/dotnet/csharp/language-reference/keywords/set) que vous voulez remplacer.  
  
 Si vous ne voulez pas remplacer la propriété de classe de base, vous pouvez utiliser le mot clé [new](/dotnet/csharp/language-reference/keywords/new) avant la propriété dans une classe dérivée.  
  
 Pour plus d'informations, consultez [Utilisation de propriétés](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0546, car la classe de base ne déclare pas un accesseur set pour la propriété.  
  
```  
// CS0546.cs // compile with: /target:library public class a { public virtual int i { get { return 0; } } public virtual int i2 { get { return 0; } set {} } } public class b : a { public override int i { set {}   // CS0546 error no set } public override int i2 { set {}   // OK } }  
```  
  
## Voir aussi  
 [Propriétés](/dotnet/csharp/programming-guide/classes-and-structs/properties)