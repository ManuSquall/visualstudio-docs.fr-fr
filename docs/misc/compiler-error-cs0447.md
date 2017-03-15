---
title: "Erreur du compilateur CS0447 | Microsoft Docs"
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
  - "CS0447"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0447"
ms.assetid: a25486c5-e9bf-4528-8533-c1aaab22ace0
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0447
Les attributs ne peuvent pas être utilisés sur des arguments de type, uniquement sur des paramètres de type  
  
 Cette erreur se produit quand vous appliquez un attribut à un argument de type qui se trouve dans une instruction d’appel. Vous pouvez appliquer un attribut à un paramètre de type dans une instruction de déclaration de classe ou de méthode, telle que la suivante :  
  
```  
class C<[some attribute] T> {…}  
```  
  
 La ligne de code suivante génère cette erreur. Il est supposé que la classe `C`, qui est définie dans la ligne de code précédente, possède une méthode statique nommée `MyStaticMethod`.  
  
```  
C<[some attribute] T>.MyStaticMethod();  
```  
  
## Exemple  
 Le code suivant génère l’erreur CS0447.  
  
```  
// CS0447.cs using System; namespace Test41 { public interface I<A> { void Meth<B>(); } public class B : I<int> { void I<[Test] int>.Meth<X>() { }  // CS0447 } }  
```