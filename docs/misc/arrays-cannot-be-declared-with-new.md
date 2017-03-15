---
title: "Les tableaux ne peuvent pas &#234;tre d&#233;clar&#233;s avec &#39;New&#39; | Microsoft Docs"
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
  - "vbc30053"
  - "bc30053"
helpviewer_keywords: 
  - "BC30053"
ms.assetid: aa55f3b7-2045-497b-9543-5ec6e2b74fe2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les tableaux ne peuvent pas &#234;tre d&#233;clar&#233;s avec &#39;New&#39;
Le mot clé `New` peut figurer uniquement dans la partie initialisation d’une déclaration de tableau. Cela signifie que `New` doit être situé à droite du signe égal \(`=`\) pour lui permettre de créer un type de tableau à assigner à la variable tableau.  
  
 Le raccourci d’initialisation de classe n’est pas disponible pour les tableaux. Les deux lignes de code suivantes sont valides et équivalentes, car elles initialisent toutes les deux un objet de classe.  
  
```  
Dim formA as Form = New Form Dim formA as New Form  
```  
  
 Toutefois, l’initialisation de tableau ne peut pas utiliser le même raccourci comme initialisation de classe.  
  
 Notez que pour un tableau, la clause `New` doit contenir des parenthèses \(`()`\) et des accolades \(`{}`\). Les parenthèses indiquent que le nouveau type est un tableau, tandis que les accolades fournissent les valeurs d’initialisation. Le compilateur exige les accolades même si elles sont vides, c’est\-à\-dire, même si vous n’initialisez aucune valeur du tableau.  
  
 **ID d’erreur :** BC30053  
  
### Pour corriger cette erreur  
  
-   Remplacez une instruction telle que `Dim myDates() As New Date` par une instruction telle que `Dim myDates() As Date = New Date() {}`.  
  
## Voir aussi  
 [Tableaux](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)