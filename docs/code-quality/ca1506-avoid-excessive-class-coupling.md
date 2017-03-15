---
title: "CA1506&#160;: &#201;viter les couplages de classe excessifs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
helpviewer_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1506&#160;: &#201;viter les couplages de classe excessifs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|Catégorie|Microsoft.Maintainability|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type ou une méthode est associée à de nombreux autres types.  
  
## Description de la règle  
 Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode.  
  
 Les types et méthodes comportant un degré élevé d'accouplement de classes peuvent être difficiles à maintenir.  Il est conseillé d'avoir des types et méthodes qui présentent un accouplement faible et une cohésion élevée.  
  
## Comment corriger les violations  
 Pour résoudre cette violation, essayez de reconcevoir le type ou la méthode pour réduire le nombre de types auxquels elle est associée.  
  
## Quand supprimer les avertissements  
 Excluez cet avertissement lorsqu'une méthode ou un type est considéré comme possible à maintenir en dépit de son grand nombre de dépendances par rapport à d'autres types.  
  
## Voir aussi  
 [Avertissements liés à la facilité de maintenance](../code-quality/maintainability-warnings.md)   
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)