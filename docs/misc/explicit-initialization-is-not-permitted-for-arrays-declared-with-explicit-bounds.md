---
title: "Une initialisation explicite n’est pas autoris&#233;e pour les tableaux d&#233;clar&#233;s avec des limites explicites | Microsoft Docs"
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
  - "bc30672"
  - "vbc30672"
helpviewer_keywords: 
  - "BC30672"
ms.assetid: 4b525e8d-bde5-4408-8c10-7605ca039f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une initialisation explicite n’est pas autoris&#233;e pour les tableaux d&#233;clar&#233;s avec des limites explicites
Les tableaux ne peuvent pas être initialisés si leur taille est déclarée.  
  
 **ID d’erreur :** BC30672  
  
### Pour corriger cette erreur  
  
-   Déclarez le tableau, puis initialisez\-le séparément.  
  
-   Déclarez, puis initialisez le tableau sous forme de tableau dynamique, et utilisez `ReDim` si nécessaire. Par exemple :  
  
    ```  
    Dim A() As Integer = {0, 1, 2, 3} ReDim Preserve A(3)  
    ```  
  
## Voir aussi  
 [Tableaux](/dotnet/visual-basic/programming-guide/language-features/arrays/index)