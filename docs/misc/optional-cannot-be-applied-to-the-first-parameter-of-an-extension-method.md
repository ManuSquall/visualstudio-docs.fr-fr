---
title: "&#39;Optional&#39; ne peut pas &#234;tre appliqu&#233; au premier param&#232;tre d’une m&#233;thode d’extension | Microsoft Docs"
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
  - "bc36553"
  - "vbc36553"
helpviewer_keywords: 
  - "BC36553"
ms.assetid: 8ea0b90c-f155-47a9-988b-5b8009b510af
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Optional&#39; ne peut pas &#234;tre appliqu&#233; au premier param&#232;tre d’une m&#233;thode d’extension
'Optional' ne peut pas être appliqué au premier paramètre d’une méthode d’extension. Le premier paramètre spécifie le type à étendre.  
  
 Le premier paramètre d’une méthode d’extension spécifie le type de données étendu par la méthode. Quand la méthode est exécutée, le premier paramètre est lié à l’instance du type de données qui appelle la méthode. Ainsi, le premier paramètre est obligatoire et ne peut pas être facultatif.  
  
 La restriction s’applique uniquement au premier paramètre. Les autres paramètres peuvent être facultatifs et respectent les mêmes règles que dans toute autre méthode. Pour plus d'informations, consultez [Parameter List](/dotnet/visual-basic/language-reference/statements/parameter-list).  
  
 **ID d’erreur :** BC36553  
  
### Pour corriger cette erreur  
  
-   Si vous souhaitez que le premier paramètre actuel spécifie le type de données étendu, supprimez le mot clé `Optional`.  
  
-   Si le premier paramètre actuel est un paramètre standard de la méthode et que vous ne souhaitez pas qu’il représente le type de données étendu, ajoutez un nouveau premier paramètre.  
  
## Exemple  
 Dans l’exemple suivant, le premier paramètre est la seule indication que la méthode `Print` étend le type de données `String`. Ainsi, il ne peut pas être facultatif.  
  
```  
<Extension()> Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 Quand la méthode d’extension est appelée de la façon suivante, le paramètre `str` de la méthode est lié à `greeting`, qui est l’instance de `String` qui appelle `Print`. Le compilateur utilise `greeting` comme argument de la méthode d’extension `Print`.  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Procédure : définition des paramètres facultatifs pour une procédure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/0b32b312-0da0-489b-96ad-7dcb1f1f8f88)   
 [Optional Parameters](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)