---
title: "Le param&#232;tre de type est d&#233;j&#224; d&#233;clar&#233; avec le nom &#39;&lt;nom_param&#232;tre_type&gt;&#39; | Microsoft Docs"
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
  - "vbc32049"
  - "bc32049"
helpviewer_keywords: 
  - "BC32049"
ms.assetid: d7affad0-0c3d-4fce-a1c2-a17f65514471
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre de type est d&#233;j&#224; d&#233;clar&#233; avec le nom &#39;&lt;nom_param&#232;tre_type&gt;&#39;
Un paramètre de type d’un type générique est déclaré avec le même nom qu’un paramètre de type du même type générique.  
  
 Dans la liste des paramètres de type d’un type générique, chaque paramètre de type doit avoir un nom différent de tous les noms suivants :  
  
-   Chaque autre paramètre de type dans la même liste de paramètres de type  
  
-   Chaque paramètre de type présent dans la liste des paramètres de type d’un type générique conteneur, et  
  
-   Le nom du type générique lui\-même  
  
 **ID d’erreur :** BC32049  
  
### Pour corriger cette erreur  
  
-   Renommez le paramètre de type pour qu’il soit distinct de chaque nom cité dans la liste de cette page d’aide.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)