---
title: "Impossible de d&#233;duire un type commun pour le premier et le second op&#233;randes de l’op&#233;rateur &#39;If&#39; binaire | Microsoft Docs"
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
  - "vbc33110"
  - "bc33110"
helpviewer_keywords: 
  - "BC33110"
ms.assetid: f46873aa-f6cd-4cc9-9e8e-e668bddf0980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire un type commun pour le premier et le second op&#233;randes de l’op&#233;rateur &#39;If&#39; binaire
Impossible de déduire un type commun pour le premier et le second opérandes de l’opérateur 'If' binaire. L’un doit avoir une conversion étendue vers l’autre.  
  
 L’opérateur `If` binaire exige une conversion étendue entre l’un des arguments et l’autre argument. Par exemple, comme il n’y aucune conversion étendue dans l’un ou l’autre sens entre `Integer` et `String`, le code suivant génère cette erreur.  
  
```vb#  
Dim first? As Integer  
Dim second As String = "First is Nothing"  
'' Not valid.  
' Console.WriteLine(If(first, second))  
```  
  
 **ID d’erreur :** BC33110  
  
### Pour corriger cette erreur  
  
-   Fournissez une conversion explicite pour l’un des opérandes si cela est possible dans votre code :  
  
    ```  
    Console.WriteLine(If(first, CInt(second)))   
    ```  
  
-   Réécrivez le code à l’aide d’une construction conditionnelle différente.  
  
    ```  
    If first IsNot Nothing Then  
        Console.WriteLine(first)  
    Else  
        Console.WriteLine(second)  
    End If  
    ```  
  
## Voir aussi  
 [If Operator](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)