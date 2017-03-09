---
title: "Les d&#233;clarations de tableau ne peuvent pas sp&#233;cifier de limites inf&#233;rieures | Microsoft Docs"
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
  - "vbc30805"
  - "bc30805"
helpviewer_keywords: 
  - "BC30805"
ms.assetid: f2055387-f4dc-4366-89fb-d752929a0258
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les d&#233;clarations de tableau ne peuvent pas sp&#233;cifier de limites inf&#233;rieures
Les tableaux ont toujours une limite inférieure de zéro. Vous pouvez spécifier zéro comme limite inférieure pour rendre votre code plus lisible. Toutefois, vous ne pouvez pas spécifier d’autre valeur pour la limite inférieure.  
  
 **ID d’erreur :** BC30805  
  
### Pour corriger cette erreur  
  
-   Affectez aux tableaux une dimension égale au nombre total d’éléments de la dimension moins un. Par exemple, `Dim y(6)` a la même taille \(7 éléments\) que `Dim x(3 To 9)`. Vous pouvez également spécifier `Dim y(0 To 6)`.  
  
-   Utilisez des offsets pour simuler les limites inférieures différentes de zéro. L’exemple suivant simule un tableau dimensionné de 3 à 9.  
  
    ```  
    Const offset As Integer = 3 Dim arrayIndex As Integer ' arrayIndex can vary between 3 and 9. Dim y(0 To 6) ' The preceding statement allocates the same number of elements ' as Dim y(3 To 9). y(arrayIndex - offset) = value ' The preceding statement converts arrayIndex to the ' corresponding index of y.  
    ```  
  
## Voir aussi  
 [Tableaux](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [Array Dimensions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/array-dimensions)   
 [NOTINBUILD Procédure : spécification d’une limite inférieure de zéro sur un tableau](http://msdn.microsoft.com/fr-fr/20ffd49a-64f7-4634-8ed0-46ba1049d935)