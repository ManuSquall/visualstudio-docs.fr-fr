---
title: "Une expression constante est requise | Microsoft Docs"
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
  - "bc30059"
  - "vbc30059"
helpviewer_keywords: 
  - "BC30059"
ms.assetid: fdd5e7bb-6370-4a63-bbb6-23b15badb4c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une expression constante est requise
Une instruction `Const` n’initialise pas correctement une constante, ou une déclaration de tableau utilise une variable pour spécifier le nombre d’éléments.  
  
 **ID d’erreur :** BC30059  
  
### Pour corriger cette erreur  
  
1.  Si la déclaration est une instruction `Const`, vérifiez que la constante est initialisée avec un littéral, une constante précédemment déclarée, un membre d’énumération ou une combinaison de littéraux, de constantes, de membres d’énumération et d’opérateurs.  
  
2.  Si la déclaration spécifie un tableau, vérifiez qu’une variable est utilisée pour spécifier le nombre d’éléments. Dans ce cas, remplacez la variable par une expression constante.  
  
## Voir aussi  
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [NOTINBUILD Variable tableau](http://msdn.microsoft.com/fr-fr/c2da78bd-6928-46ba-805f-44f819dfaf93)