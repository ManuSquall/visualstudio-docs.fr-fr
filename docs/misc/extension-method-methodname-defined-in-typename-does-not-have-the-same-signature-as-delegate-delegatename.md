---
title: "La m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_type&gt;&#39; n’a pas la m&#234;me signature que le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39; | Microsoft Docs"
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
  - "bc36580"
  - "vbc36580"
helpviewer_keywords: 
  - "BC36580"
ms.assetid: dc6b6a63-02b0-43d8-b6a7-c1cd397c6ee3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_type&gt;&#39; n’a pas la m&#234;me signature que le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39;
Il y a une incompatibilité entre les signatures de la méthode d’extension et le délégué que vous essayez d’utiliser. L’instruction `Delegate` définit les types de paramètre et les types de retour d’une classe déléguée. Toute procédure ayant des paramètres, des types et un type de retour correspondants peut être utilisée pour créer une instance de ce type de délégué. Cette erreur est signalée dans l’exemple suivant, car la signature d’extension de la méthode `Example` n’est pas compatible avec la signature du délégué `Del`.  
  
```vb#  
' Definition of the delegate, with two parameters. Delegate Sub Del(ByVal m As Integer, ByVal s As String)  
```  
  
```vb#  
' Definition of the extension method, with one parameter. <Extension()> _ Sub Example(ByVal s As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
'' This assignment causes the error. ' Dim exampleDel As Del = AddressOf Example  
```  
  
 **ID d’erreur :** BC36580  
  
### Pour corriger cette erreur  
  
-   Vérifiez que le délégué et la méthode d’extension possèdent le même nombre de paramètres.  
  
-   Vérifiez que l’ordre des paramètres est le même dans le délégué et la méthode d’extension.  
  
-   Comparez le type de données de chaque paramètre de délégué avec le type de données du paramètre de méthode d’extension correspondant pour vous assurer qu’ils sont compatibles.  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)