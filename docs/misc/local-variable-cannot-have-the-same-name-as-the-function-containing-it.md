---
title: "Une variable locale ne peut pas porter le m&#234;me nom que la fonction qui la contient | Microsoft Docs"
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
  - "vbc30290"
  - "bc30290"
helpviewer_keywords: 
  - "BC30290"
ms.assetid: 34c38cff-fb9c-406d-82e8-ca251ee77104
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une variable locale ne peut pas porter le m&#234;me nom que la fonction qui la contient
Une instruction `Dim` spécifie une variable avec le même nom que la procédure `Function` qui la contient.  
  
 **ID d’erreur :** BC30290  
  
### Pour corriger cette erreur  
  
-   Supprimez la déclaration de la variable ou modifiez le nom de la variable.  
  
## Voir aussi  
 [NOTINBUILD : Résolution d’une référence quand plusieurs variables portent le même nom](http://msdn.microsoft.com/fr-fr/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [Function, procédures](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)