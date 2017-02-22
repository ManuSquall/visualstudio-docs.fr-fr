---
title: "marker_series::write_alert, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert"
helpviewer_keywords: 
  - "Concurrency::diagnostic:marker_series::write_alert (méthode)"
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series::write_alert, m&#233;thode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Écrit une alerte dans le fichier de suivi du visualiseur concurrentiel.  
  
## Syntaxe  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Paramètres  
 `_Format`  
 Un composite formate des chaînes de caractères qui contiennent du texte avec aucun ou plusieurs éléments de mise en forme, qui correspondent à des objets dans une liste d'arguments.  
  
## Configuration requise  
 **En\-tête :** cvmarkersobj.h  
  
 **Espace de noms :** Concurrency::diagnostic  
  
## Voir aussi  
 [marker\_series, classe](../profiling/marker-series-class.md)