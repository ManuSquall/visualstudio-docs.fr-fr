---
title: "L’op&#233;rande &#39;Throw&#39; doit d&#233;river de &#39;System.Exception&#39; | Microsoft Docs"
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
  - "vbc30665"
  - "bc30665"
helpviewer_keywords: 
  - "BC30665"
ms.assetid: 7c228087-39ea-4b30-a410-6ba711e67e5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rande &#39;Throw&#39; doit d&#233;river de &#39;System.Exception&#39;
L’argument fourni à `Throw` doit être une instance de `System.Exception` ou une instance d’une classe dérivée de `System.Exception`.  
  
 **ID d’erreur :** BC30665  
  
### Pour corriger cette erreur  
  
-   Utilisez un argument dérivé de `System.Exception`, comme dans l’exemple suivant.  
  
    ```  
    Throw New System.Exception("This is an error.")  
    ```  
  
## Voir aussi  
 [Throw Statement](/dotnet/visual-basic/language-reference/statements/throw-statement)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Classe d’exception en Visual Basic](http://msdn.microsoft.com/fr-fr/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Gestion des exceptions et des erreurs en Visual Basic](http://msdn.microsoft.com/fr-fr/3e351e73-cf23-40ab-8b60-05794160529e)