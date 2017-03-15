---
title: "Les m&#233;thodes d’extension doivent d&#233;clarer au moins un param&#232;tre | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36552"
  - "bc36552"
helpviewer_keywords: 
  - "BC36552"
ms.assetid: a8cc8cdd-cdb5-42ca-b5a1-c9a71abd46eb
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les m&#233;thodes d’extension doivent d&#233;clarer au moins un param&#232;tre
Les méthodes d’extension doivent déclarer au moins un paramètre. Le premier paramètre spécifie le type à étendre.  
  
 Une méthode d’extension sans paramètre n’est pas valide, car le premier paramètre spécifie le type de données que la méthode étend. Le premier paramètre est lié à l’instance du type de données qui appelle la méthode.  
  
 **ID d’erreur :** BC36552  
  
### Pour corriger cette erreur  
  
-   Ajoutez un paramètre qui soit du type étendu par votre méthode.  
  
## Exemple  
 Le premier paramètre de l’exemple suivant indique que la méthode `Print` étend le type de données `String`.  
  
```  
<Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 Quand la méthode d’extension est appelée de la façon suivante, le paramètre `str` de la méthode est lié à `greeting`, qui est l’instance de `String` qui appelle `Print`. Le compilateur utilise `greeting` comme argument de la méthode d’extension `Print`.  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Procedure Parameters and Arguments](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)   
 [Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/index)