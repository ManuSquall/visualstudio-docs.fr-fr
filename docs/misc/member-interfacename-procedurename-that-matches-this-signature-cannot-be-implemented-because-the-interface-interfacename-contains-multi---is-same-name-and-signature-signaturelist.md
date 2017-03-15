---
title: "Le membre &#39;&lt;nom_interface&gt;.&lt;nom_proc&#233;dure&gt;&#39; qui correspond &#224; cette signature ne peut pas &#234;tre impl&#233;ment&#233;, car l’interface &#39;&lt;nom_interface&gt;&#39; contient plusieurs membres avec le m&#234;me nom et la m&#234;me signature&#160;: &lt;liste_signatures&gt; | Microsoft Docs"
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
  - "vbc30937"
  - "bc30937"
helpviewer_keywords: 
  - "BC30937"
ms.assetid: e917d85e-95e0-431a-9d09-39ce5d4fc894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre &#39;&lt;nom_interface&gt;.&lt;nom_proc&#233;dure&gt;&#39; qui correspond &#224; cette signature ne peut pas &#234;tre impl&#233;ment&#233;, car l’interface &#39;&lt;nom_interface&gt;&#39; contient plusieurs membres avec le m&#234;me nom et la m&#234;me signature&#160;: &lt;liste_signatures&gt;
Une procédure ou une propriété tente d’implémenter une procédure ou une propriété définie dans une interface implémentée, mais le compilateur détecte plusieurs versions de la procédure ou de la propriété d’interface avec le même nom et la même signature.  
  
 Cette erreur peut se produire avec les types génériques construits, comme l’illustrent les déclarations suivantes.  
  
```  
Public Interface baseInterface(Of t) Sub doSomething(ByVal inputValue As String) Sub doSomething(ByVal inputValue As t) End Class Public Class implementingClass Implements baseInterface(Of String) Sub doSomething(ByVal inputValue As String) _ Implements baseInterface(Of String).doSomething End Sub End Class  
```  
  
 Étant donné que `implementingClass` implémente `baseInterface` qui fournit `String` à son paramètre de type `t`, les deux versions de `doSomething` dans `baseInterface` ont des signatures identiques pour `implementingClass`. De ce fait, le compilateur ne peut pas déterminer quelle version implémenter.  
  
 **ID d’erreur :** BC30937  
  
### Pour corriger cette erreur  
  
-   Modifiez le ou les arguments de type que vous fournissez à la classe de base pour éviter la présence d’une ou plusieurs signatures de procédures ou propriétés membres identiques.  
  
     ou  
  
-   N’implémentez pas cette classe de base. Vous ne pouvez pas l’implémenter avec le jeu d’arguments de type que vous utilisez, car vous devez implémenter chacun de ses membres.  
  
## Voir aussi  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NOT IN BUILD : Implements, mot clé et instruction](http://msdn.microsoft.com/fr-fr/b96560f7-6413-480f-a1e2-f80253bab5be)