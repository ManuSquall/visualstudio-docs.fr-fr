---
title: "Les types Enum ne peuvent pas &#234;tre Nullable | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32129"
  - "bc32129"
helpviewer_keywords: 
  - "BC32129"
ms.assetid: 9e0fe5c9-72c7-4905-b177-d00cc3469ea9
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les types Enum ne peuvent pas &#234;tre Nullable
Le type sous\-jacent utilisé pour déclarer une énumération ne peut pas être Nullable. Par exemple, le code suivant génère cette erreur :  
  
```vb#  
'' Not valid. ' Enum exampleEnum As Integer? '     Member declarations. ' End Enum  
```  
  
 **ID d’erreur :** BC32129  
  
### Pour corriger cette erreur  
  
-   N’utilisez pas un type Nullable sous\-jacent dans une déclaration `Enum`.  
  
## Voir aussi  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Enum Statement](/dotnet/visual-basic/language-reference/statements/enum-statement)