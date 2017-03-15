---
title: "&#39;&lt;nom_&#233;l&#233;ment&gt;&#39; ne peut pas &#234;tre d&#233;clar&#233; &#39;Partial&#39;, car les m&#233;thodes partielles doivent &#234;tre des Subs | Microsoft Docs"
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
  - "vbc31437"
  - "bc31437"
helpviewer_keywords: 
  - "BC31437"
ms.assetid: 31ca12ab-2c26-4907-a253-e7c57bb4f34b
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_&#233;l&#233;ment&gt;&#39; ne peut pas &#234;tre d&#233;clar&#233; &#39;Partial&#39;, car les m&#233;thodes partielles doivent &#234;tre des Subs
Seules les procédures `Sub` peuvent être déclarées comme étant des méthodes partielles. Par exemple, le code suivant génère cette erreur, car `partialMethod` est une fonction.  
  
```  
' Partial Private Function partialMethod(ByVal n As Integer) As Integer ' End Function  
```  
  
 **ID d’erreur :** BC31437  
  
### Pour corriger cette erreur  
  
-   Convertissez ce que vous déclarez comme méthode partielle en `Sub`.  
  
-   N’utilisez pas de méthode partielle dans ce cas.  
  
## Voir aussi  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)