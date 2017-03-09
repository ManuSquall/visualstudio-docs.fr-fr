---
title: "Chaque param&#232;tre d’expression lambda de Option Strict On doit &#234;tre d&#233;clar&#233; avec une clause &#39;As&#39; si son type ne peut pas &#234;tre d&#233;duit | Microsoft Docs"
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
  - "bc36642"
  - "vbc36642"
helpviewer_keywords: 
  - "BC36642"
ms.assetid: 2aaa62b8-49c9-4ae8-b0f5-08e3f0b5ad10
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Chaque param&#232;tre d’expression lambda de Option Strict On doit &#234;tre d&#233;clar&#233; avec une clause &#39;As&#39; si son type ne peut pas &#234;tre d&#233;duit
Vous avez déclaré un paramètre dans une expression lambda sans utiliser de clause `As`, avec `Option Strict` activé.  
  
```  
' Not valid when Option Strict is on. ' Dim increment1 = Function (n) n + 1  
```  
  
 La déclaration précédente est valide si le type de `n` peut être déduit. Par exemple, si vous assignez l’expression lambda précédente à un délégué de fonction, `Del` :  
  
```  
Delegate Function Del(ByVal p As Integer) As Integer  
```  
  
 Le type de `n` peut désormais être déduit du paramètre `p` :  
  
```  
Dim increment2 as Del = Function(n) n + 1  
```  
  
 **ID d’erreur :** BC36642  
  
### Pour corriger cette erreur  
  
-   Ajoutez une clause `As` à la déclaration du paramètre :  
  
    ```  
    Dim increment3 = Function (n As Integer) n + 1  
    ```  
  
## Voir aussi  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)