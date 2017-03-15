---
title: "&#39;ParamArray&#39; ne peut pas &#234;tre appliqu&#233; au premier param&#232;tre d’une m&#233;thode d’extension | Microsoft Docs"
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
  - "vbc36554"
  - "bc36554"
helpviewer_keywords: 
  - "BC36554"
ms.assetid: 0778a854-246f-4c2b-943d-ea8883b3aa6f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ParamArray&#39; ne peut pas &#234;tre appliqu&#233; au premier param&#232;tre d’une m&#233;thode d’extension
'ParamArray' ne peut pas être appliqué au premier paramètre d’une méthode d’extension. Le premier paramètre spécifie le type à étendre.  
  
 Le premier paramètre d’une méthode d’extension spécifie le type de données que la méthode étend. Ainsi, le premier paramètre est obligatoire et ne peut pas être facultatif. Puisqu’un tableau de paramètres est automatiquement facultatif, il n’est pas valide en tant que premier argument de la méthode d’extension.  
  
> [!NOTE]
>  Quand la méthode est exécutée, l’instance du type de données étendu qui appelle la méthode devient l’argument du premier paramètre de la méthode. Par exemple, l’instance `greeting` dans `greeting.Print()` est l’argument du premier paramètre, `str`, dans la méthode d’extension `Public Sub Print (ByVal str As String)`.  
  
 **ID d’erreur :** BC36554  
  
### Pour corriger cette erreur  
  
-   Si le tableau de paramètres ne spécifie pas le type de données à étendre, ajoutez un nouveau premier paramètre qui spécifie ce type.  
  
    ```  
    <Extension()> Public Sub AddTo(ByRef str As String, ByVal ParamArray addOns() As String) ' Concatenate the strings in addOns to str. End Sub  
    ```  
  
-   Si le tableau de paramètres ne spécifie pas le type de données à étendre, envisagez de le modifier en tableau standard, ce qui exige un argument, au lieu d’un tableau de paramètres. Les tableaux standard peuvent être étendus.  
  
    ```  
    <Extension()> Public Function Sum(ByVal ints() As Integer) As Integer Dim total As Integer = 0 For Each i As Integer In ints total = total + i Next i Return total End Function  
    ```  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)   
 [Optional Parameters](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)