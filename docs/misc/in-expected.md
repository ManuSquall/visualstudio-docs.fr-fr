---
title: "&#39;In&#39; attendu | Microsoft Docs"
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
  - "bc36607"
  - "vbc36607"
helpviewer_keywords: 
  - "BC36607"
ms.assetid: f390bca5-12fe-4fe1-bd86-7f8ab66dfbd8
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;In&#39; attendu
Une clause `From` ou `Aggregate` a été spécifiée sans l’opérateur `In`. Vous utilisez l’opérateur `In` pour identifier la collection à interroger.  
  
 **ID d’erreur :** BC36607  
  
### Pour corriger cette erreur  
  
1.  Ajoutez l’opérateur `In` et les champs clés à la clause `From` ou `Aggregate`. Voici un exemple :  
  
    ```vb#  
    Dim names = From pers In people Select pers.FirstName, pers.LastName  
    ```  
  
## Voir aussi  
 [From Clause](/dotnet/visual-basic/language-reference/queries/from-clause)   
 [Aggregate Clause](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)