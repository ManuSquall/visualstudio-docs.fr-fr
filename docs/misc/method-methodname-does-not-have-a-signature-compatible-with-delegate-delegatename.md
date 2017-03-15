---
title: "La m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; n’a pas de signature compatible avec le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39; | Microsoft Docs"
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
  - "vbc31143"
  - "bc31143"
helpviewer_keywords: 
  - "BC31143"
ms.assetid: 88990637-7c92-467e-a3d3-db5498dc1dce
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; n’a pas de signature compatible avec le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39;
Cette erreur se produit quand une conversion nécessaire entre une méthode et un délégué n’est pas possible. La cause de l’erreur peut être la conversion entre des paramètres ou, lorsque la méthode et le délégué sont des fonctions, la conversion dans les valeurs de retour.  
  
 Le code suivant illustre des échecs de conversion. Le délégué est `FunDel`.  
  
```vb#  
Delegate Function FunDel(ByVal i As Integer, ByVal d As Double) As Integer  
```  
  
 Les fonctions suivantes diffèrent chacune de `FunDel` d’une manière qui provoque cette erreur.  
  
```vb#  
Function ExampleMethod1(ByVal m As Integer, ByVal aDate As Date) As Integer End Function Function ExampleMethod2(ByVal m As Integer, ByVal aDouble As Double) As Date End Function  
```  
  
 Chacune des instructions d’assignation suivantes provoque l’erreur.  
  
```vb#  
Sub Main() ' The second parameters of FunDel and ExampleMethod1, Double and Date, ' are not compatible. 'Dim d1 As FunDel = AddressOf ExampleMethod1 ' The return types of FunDel and ExampleMethod2, Integer and Date, ' are not compatible. 'Dim d2 As FunDel = AddressOf ExampleMethod2 End Sub  
```  
  
 **ID d’erreur :** BC31143  
  
### Pour corriger cette erreur  
  
-   Examinez les paramètres correspondants et les types de retour \(s’ils sont présents\) pour identifier la paire qui n’est pas compatible.  
  
## Voir aussi  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [NOT IN BUILD : Délégués et opérateur AddressOf](http://msdn.microsoft.com/fr-fr/7b2ed932-8598-4355-b2f7-5cedb23ee86f)