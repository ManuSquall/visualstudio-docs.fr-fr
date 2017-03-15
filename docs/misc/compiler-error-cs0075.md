---
title: "Erreur du compilateur CS0075 | Microsoft Docs"
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
  - "CS0075"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0075"
ms.assetid: 5084d260-705e-4ff5-8f7a-7f74052fcbbb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0075
Pour effectuer un cast d'une valeur négative, vous devez la mettre entre parenthèses  
  
 Si vous effectuez une conversion de type \(transtypage\) à partir d’un mot clé qui identifie un type prédéfini, vous n’avez pas besoin de parenthèses. Dans le cas contraire, vous devez utiliser des parenthèses, car \(x\) –y ne seront pas considérés comme une expression cast. D’après la spécification C\#, section 7.6.6 :  
  
 *La règle de suppression de l’ambiguïté permet de déduire que si x et y sont des identificateurs, \(x\)y, \(x\)\(y\) et \(x\)\(\-y\) sont des expressions cast, mais \(x\)\-y ne l’est pas, même si x identifie un type. Cependant, si x est un mot clé qui identifie un type prédéfini \(tel que int\), les quatre formes sont alors des expressions cast \(car un tel mot clé ne peut pas être une expression en lui\-même\).*  
  
 Le code suivant génère l’erreur CS0075 :  
  
```  
// CS0075 namespace MyNamespace { enum MyEnum { } public class MyClass { public static void Main() { // To fix the error, place the negative // values below in parentheses int i = (System.Int32) - 4; //CS0075 MyEnum e = (MyEnum) - 1;    //CS0075 System.Console.WriteLine(i); //to avoid warning System.Console.WriteLine(e); //to avoid warning } } }  
```  
  
## Voir aussi  
 [Cast et conversions de types](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)