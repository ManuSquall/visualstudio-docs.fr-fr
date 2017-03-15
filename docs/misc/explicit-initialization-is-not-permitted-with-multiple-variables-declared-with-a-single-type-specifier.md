---
title: "Une initialisation explicite n’est pas autoris&#233;e avec plusieurs variables d&#233;clar&#233;es avec un sp&#233;cificateur de type unique | Microsoft Docs"
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
  - "bc30671"
  - "vbc30671"
helpviewer_keywords: 
  - "BC30671"
ms.assetid: 57bbdd58-b58d-4144-8fa6-366a7167df27
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une initialisation explicite n’est pas autoris&#233;e avec plusieurs variables d&#233;clar&#233;es avec un sp&#233;cificateur de type unique
L’initialisation n’est pas autorisée quand plusieurs variables sont déclarées sur la même ligne.  
  
 **ID d’erreur :** BC30671  
  
### Pour corriger cette erreur  
  
1.  Déclarez et initialisez chaque élément séparément.  
  
2.  Déclarez plusieurs éléments ensemble, puis initialisez chacun d’eux, par exemple :  
  
    ```  
    Dim x, b, i As Integer x = 9 : b = 9 : i = 9 ' ":" is the same as a new line.  
    ```  
  
## Voir aussi  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Déclaration de variable](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)