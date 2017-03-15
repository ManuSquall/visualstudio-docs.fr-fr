---
title: "Les initialiseurs de tableau ne sont valides que pour les tableaux, mais le type de &#39;&lt;nom_variable&gt;&#39; est &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
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
  - "bc30679"
  - "vbc30679"
helpviewer_keywords: 
  - "BC30679"
ms.assetid: 3cf34882-7a58-4074-8ebb-52e58199a506
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les initialiseurs de tableau ne sont valides que pour les tableaux, mais le type de &#39;&lt;nom_variable&gt;&#39; est &#39;&lt;nom_type&gt;&#39;
Un utilisateur a tenté d’initialiser une variable non tableau avec une liste de valeurs.  
  
 **ID d’erreur :** BC30679  
  
### Pour corriger cette erreur  
  
-   Déclarez, puis initialisez la variable en tant que tableau. Par exemple :  
  
     `Dim intarray As Integer() = {1, 5, 9}`  
  
-   Initialisez la variable en tant que valeur unique. Par exemple :  
  
     `Dim intvalue As Integer = 1`  
  
## Voir aussi  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Déclaration de variable](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [Tableaux](/dotnet/visual-basic/programming-guide/language-features/arrays/index)