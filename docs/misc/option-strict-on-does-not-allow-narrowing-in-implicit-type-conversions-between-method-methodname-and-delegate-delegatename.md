---
title: "Option Strict On n’autorise pas les conversions restrictives lors des conversions de types implicites entre la m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; et le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39; | Microsoft Docs"
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
  - "bc36663"
  - "vbc36663"
helpviewer_keywords: 
  - "BC36663"
ms.assetid: fefc7ab5-b587-4ff9-a6bc-4c4e5d4b6b29
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On n’autorise pas les conversions restrictives lors des conversions de types implicites entre la m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; et le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39;
Quand `Option Strict` est On, vous ne pouvez pas avoir une conversion restrictive entre le type de données d’un paramètre dans un délégué et le paramètre correspondant d’une fonction ou d’un `Sub` assigné à une variable de ce type de délégué. Par exemple, le délégué de fonction `Del` a un paramètre de type `Integer`, et les fonctions `Conversion1`, `Conversion2` et `Conversion3` ont un paramètre de types numériques différents.  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String Function Conversion1(ByVal n As Integer) As String Return "Valid" End Function Function Conversion2(ByVal n As Long) As String Return "Valid" End Function Function Conversion3(ByVal n As Short) As String Return "Not valid" End Function  
```  
  
 En raison de l’existence d’une conversion étendue de `Integer` à `Integer` et à `Long`, les assignations suivantes sont valides.  
  
```vb#  
' Valid. Dim funDel1 As Del = AddressOf Conversion1 Dim funDel2 As Del = AddressOf Conversion2  
```  
  
 La conversion de `Integer` à `Short` est une conversion restrictive. L’assignation suivante n’est donc pas valide.  
  
```vb#  
' Not valid. Dim funDel3 As Del = AddressOf Conversion3  
```  
  
 ID d’erreur : BC36663  
  
### Pour corriger cette erreur  
  
-   Modifiez le type de données du paramètre dans le délégué ou la méthode pour que la relation d’étendue nécessaire existe.  
  
## Voir aussi  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Delegates](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [NOT IN BUILD : Délégués et opérateur AddressOf](http://msdn.microsoft.com/fr-fr/7b2ed932-8598-4355-b2f7-5cedb23ee86f)