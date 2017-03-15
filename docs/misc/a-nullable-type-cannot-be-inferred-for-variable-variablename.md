---
title: "Impossible de d&#233;duire un type Nullable pour la variable &#39;&lt;nom_variable&gt;&#39; | Microsoft Docs"
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
  - "bc36628"
  - "vbc36628"
helpviewer_keywords: 
  - "BC36628"
ms.assetid: 3e92ae19-6a19-4b0b-9dd9-fba31cdb85a6
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire un type Nullable pour la variable &#39;&lt;nom_variable&gt;&#39;
Un type Nullable ne peut pas être déduit d’un type référence, tel qu’un tableau, une classe ou un `String`. La valeur de laquelle est déduit le type de données doit être un type valeur. Le code suivant illustre cette erreur :  
  
```vb#  
'' Not valid.   
'Dim arrList? = New ArrayList  
'Dim except? = New Exception  
'Dim obj? = New Object  
'Dim stringVar? = "Open the application."  
  
' Valid.  
Dim intVar? = 10  
```  
  
 **ID d’erreur :** BC36628  
  
### Pour corriger cette erreur  
  
-   Supprimez la désignation Nullable.  
  
## Voir aussi  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)