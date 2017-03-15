---
title: "La contrainte &#39;New&#39; ne peut pas &#234;tre sp&#233;cifi&#233;e plusieurs fois pour le m&#234;me param&#232;tre de type | Microsoft Docs"
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
  - "vbc32081"
  - "BC32081"
helpviewer_keywords: 
  - "BC32081"
ms.assetid: afcb30da-3973-4452-9cf3-c027f9866589
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La contrainte &#39;New&#39; ne peut pas &#234;tre sp&#233;cifi&#233;e plusieurs fois pour le m&#234;me param&#232;tre de type
Une liste de contraintes inclut plusieurs fois la contrainte [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator).  
  
 Une liste de contraintes appliquée à un paramètre de type peut spécifier que l’argument de type passé à ce paramètre de type doit exposer un constructeur sans paramètre et auquel le code de création peut accéder. Un type ne peut pas avoir plus d’un constructeur sans paramètre, et vous ne pouvez pas spécifier plusieurs fois cette exigence.  
  
 **ID d’erreur :** BC32081  
  
### Pour corriger cette erreur  
  
-   Supprimez les mots clés `New` redondants. La liste de contraintes ne doit en avoir qu’un.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)