---
title: "Erreur du compilateur CS0738 | Microsoft Docs"
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
  - "CS0738"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0738"
ms.assetid: 01ce94ee-2435-4326-befc-2b020c441a4f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0738
type name' n’implémente pas le membre d’interface 'member name'. 'method name' ne peut pas implémenter 'interface member', car il n’a pas le type de retour 'type name' correspondant.  
  
 La valeur de retour d’une méthode d’implémentation dans une classe doit correspondre à la valeur de retour du membre d’interface qu’elle implémente.  
  
### Pour corriger cette erreur  
  
1.  Modifiez le type de retour de la méthode pour qu’il corresponde à celui du membre d’interface.  
  
## Exemple  
 Le code suivant génère CS0738, car la méthode de classe retourne `void` et le membre d’interface du même nom retourne `int` :  
  
```  
using System; interface ITest { int TestMethod(); } public class Test: ITest { public void TestMethod() { } // CS0738 // Try the following line instead. // public int TestMethod(); }  
```  
  
## Voir aussi  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)