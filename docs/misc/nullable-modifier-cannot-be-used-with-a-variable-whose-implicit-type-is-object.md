---
title: "Impossible d’utiliser un modificateur autorisant les valeurs Null avec une variable dont le type implicite est &#39;Object&#39; | Microsoft Docs"
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
  - "bc33112"
  - "vbc33112"
helpviewer_keywords: 
  - "BC33112"
ms.assetid: 50b2a2ad-248d-4faa-820d-bcdf0e8b4aad
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’utiliser un modificateur autorisant les valeurs Null avec une variable dont le type implicite est &#39;Object&#39;
Une déclaration de variable inclut le modificateur de type Nullable \(?\), mais ne spécifie ni ne déduit un type en affectant une valeur à la variable déclarée.  
  
 **ID d’erreur :** BC33112  
  
### Pour corriger cette erreur  
  
-   Spécifiez un type au moment de déclarer la variable Nullable. Le type ne peut pas être <xref:System.Object>.  
  
-   Affectez une valeur au moment de déclarer la variable Nullable. Le type de la variable Nullable est déduit de la valeur affectée. Le type de la valeur ne peut pas être <xref:System.Object>.  
  
## Voir aussi  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)