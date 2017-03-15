---
title: "Option Strict On n’autorise pas les conversions restrictives lors des conversions de types implicites entre l’expression lambda et le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39; | Microsoft Docs"
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
  - "bc36662"
  - "vbc36662"
helpviewer_keywords: 
  - "BC36662"
ms.assetid: 4504497b-56ba-4631-ad7b-59975f7fee04
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On n’autorise pas les conversions restrictives lors des conversions de types implicites entre l’expression lambda et le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39;
Quand `Option Strict` est On, vous ne pouvez pas avoir une conversion restrictive entre le type de données d’un paramètre dans un délégué et le paramètre correspondant d’une expression lambda assignée à une variable de ce type de délégué. Par exemple, dans le code suivant, le délégué `Del` a un paramètre de type `Integer`.  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String  
```  
  
 Ainsi, le paramètre correspondant d’une expression lambda assignée à une variable de type `Del` peut être un `Integer` ou n’importe quel type de données pour lequel il existe une conversion étendue à partir de `Integer`.  
  
```vb#  
' Valid. Dim example1 As Del = Function(n As Integer) "Valid" Dim example2 As Del = Function(n As Long) "Valid" ' Not valid. Dim example3 As Del = Function(n As Short) "Not Valid"  
```  
  
 **ID d’erreur :** BC36662  
  
### Pour corriger cette erreur  
  
-   Modifiez le type de données du paramètre dans le délégué ou l’expression lambda pour que la relation d’étendue nécessaire existe.  
  
-   Ne spécifiez pas de types de données de paramètres dans l’expression lambda. Les types seront déduits des paramètres correspondants dans le délégué.  
  
    ```vb#  
    Dim example4 As Del = Function(n) "Valid"  
    ```  
  
## Voir aussi  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Delegates](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)