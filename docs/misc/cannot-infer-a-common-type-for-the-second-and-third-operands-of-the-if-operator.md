---
title: "Impossible de d&#233;duire un type commun pour le second et le troisi&#232;me op&#233;randes de l’op&#233;rateur &#39;If&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33106"
  - "bc33106"
helpviewer_keywords: 
  - "BC33106"
ms.assetid: 793eed88-a9f9-43e3-b657-c16795ecbbcc
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire un type commun pour le second et le troisi&#232;me op&#233;randes de l’op&#233;rateur &#39;If&#39;
Impossible de déduire un type commun pour le second et le troisième opérandes de l’opérateur 'If'. L’un doit avoir une conversion étendue vers l’autre.  
  
 Lorsque l’opérateur `If` est appelé avec trois arguments, il doit y avoir une conversion étendue entre le deuxième et le troisième argument. Par exemple, comme il n’y aucune conversion étendue dans l’un ou l’autre sens entre `Integer` et `String`, le code suivant génère cette erreur.  
  
```vb#  
Dim divisor = 3  
' Not valid.  
' Console.WriteLine(If(divisor <> 0, number \ divisor, "Division by zero"))  
```  
  
 **ID d’erreur :** BC33106  
  
### Pour corriger cette erreur  
  
-   Fournissez une conversion explicite pour l’un des opérandes si cela est possible dans votre code.  
  
-   Utilisez une construction de condition différente, par exemple une instruction `If...Then...Else`.  
  
## Voir aussi  
 [If Operator](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)