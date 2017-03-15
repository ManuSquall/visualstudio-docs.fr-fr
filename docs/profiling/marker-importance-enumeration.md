---
title: "marker_importance, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_importance"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_importance (énumération)"
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_importance, &#233;num&#233;ration
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Représente le niveau d'importance du marqueur du visualiseur concurrentiel.  
  
## Syntaxe  
  
```  
enum marker_importance;  
```  
  
## Membres  
  
### Valeurs  
  
|Name|Description|  
|----------|-----------------|  
|`critical_importance`|Spécifie que le marqueur est d'une importance primordiale.|  
|`high_importance`|Spécifie que le marqueur est d'une importance élevée.|  
|`low_importance`|Spécifie que le marqueur est peu important.|  
|`normal_importance`|Spécifie que le marqueur est d'une importance normale.|  
  
## Configuration requise  
 **en\-tête :** cvmarkersobj.h  
  
 **Espace de nom:** Concurrency::diagnostic  
  
## Voir aussi  
 [diagnostic, espace de noms](../profiling/diagnostic-namespace.md)