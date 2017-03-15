---
title: "Erreur du compilateur CS1715 | Microsoft Docs"
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
  - "CS1715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1715"
ms.assetid: 740044d1-a61c-4156-bc6a-adf26c7499ec
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1715
'Type1': le type doit être 'Type2' pour correspondre au membre substitué 'nom\_membre'  
  
 Cette erreur est identique à [Erreur du compilateur CS0508](../misc/compiler-error-cs0508.md), sauf que CS0508 s’applique maintenant uniquement aux méthodes qui ont des types de retour, alors que l’erreur CS1715 s’applique aux propriétés et aux indexeurs qui ont uniquement des « types » plutôt que des « types de retour ».  
  
## Exemple  
 Le code suivant génère l’erreur CS1715.  
  
```  
// CS1715.cs abstract public class Base { abstract public int myProperty { get; set; } } public class Derived : Base { int myField; public override double myProperty  // CS1715 // try the following line instead // public override int myProperty { get { return myField; } set { myField;= value; } } public static void Main() { Derived d = new Derived(); d.myProperty = 5; } }  
```