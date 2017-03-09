---
title: "Le type de contrainte &#39;&lt;nom_type&gt;&#39; est d&#233;j&#224; sp&#233;cifi&#233; pour ce param&#232;tre de type | Microsoft Docs"
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
  - "BC32071"
  - "vbc32071"
helpviewer_keywords: 
  - "BC32071"
ms.assetid: 6b0e85e9-3ac8-4181-97de-ca690b95a63c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type de contrainte &#39;&lt;nom_type&gt;&#39; est d&#233;j&#224; sp&#233;cifi&#233; pour ce param&#232;tre de type
Une liste de contraintes inclut plusieurs fois une contrainte de classe ou d’interface.  
  
 Une liste de contraintes impose des exigences sur l’argument de type passé au paramètre de type. Vous pouvez spécifier les exigences suivantes dans toute combinaison :  
  
-   L’argument de type doit implémenter une ou plusieurs interfaces.  
  
-   L’argument de type doit hériter d’une classe au plus.  
  
 Un type ne peut pas implémenter ou hériter du même type plusieurs fois, et vous ne pouvez pas spécifier plusieurs fois un type dans la même liste de contraintes.  
  
 **ID d’erreur :** BC32071  
  
### Pour corriger cette erreur  
  
-   Supprimez les spécifications redondantes de la même classe ou interface. Elle ne doit apparaître qu’une seule fois dans la liste de contraintes.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)