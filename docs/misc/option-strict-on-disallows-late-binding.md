---
title: "Option Strict On rejette toute liaison tardive | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30574"
  - "vbc30574"
helpviewer_keywords: 
  - "BC30574"
ms.assetid: 9da4b826-2e12-4a5d-9e17-762b0b68fc9b
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On rejette toute liaison tardive
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] permet les conversions implicites de tout type de données vers tous les types de données. Toutefois, une perte de données peut se produire si la valeur d’un type de données est convertie en un type de données ayant une précision moindre ou une capacité réduite.`Option Strict On` garantit la notification au moment de la compilation de ces types de conversions pour qu’elles puissent être évitées. Vous ne pouvez pas utiliser `Option Strict On` avec une liaison tardive.  
  
 L’exemple de code suivant utilise la liaison tardive et génère cette erreur quand `Option Strict` a la valeur `On`.  
  
 [!CODE [VbVbalrOptionStrictError#1](VbVbalrOptionStrictError#1)]  
  
 **ID d’erreur :** BC30574  
  
### Pour corriger cette erreur  
  
-   Modifiez la déclaration de l’objet pour qu’elle utilise un type explicite, comme illustré dans l’exemple suivant :  
  
     [!CODE [VbVbalrOptionStrictError#2](VbVbalrOptionStrictError#2)]  
  
 ou  
  
-   Modifiez l’expression de liaison tardive pour qu’elle spécifie un type explicite, comme illustré dans l’exemple suivant :  
  
     [!CODE [VbVbalrOptionStrictError#3](VbVbalrOptionStrictError#3)]  
  
 ou  
  
-   Laissez le compilateur déduire un type spécifique, comme illustré dans l’exemple suivant :  
  
     [!CODE [VbVbalrOptionStrictError#4](VbVbalrOptionStrictError#4)]  
  
 ou  
  
-   Désactivez `Option Strict` en supprimant le mot clé `On` qui le suit ou en spécifiant explicitement `Off`.  
  
## Voir aussi  
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)