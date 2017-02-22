---
title: "marker_series::write_flag, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_flag (méthode)"
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series::write_flag, m&#233;thode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Écrit un indicateur dans le fichier de suivi du visualiseur concurrentiel.  
  
## Syntaxe  
  
```  
void write_flag(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Paramètres  
 `_Format`  
 Un composite formate des chaînes de caractères qui contiennent du texte avec aucun ou plusieurs éléments de mise en forme, qui correspondent à des objets dans une liste d'arguments.  
  
 `_Importance`  
 Niveau d'importance.  
  
 `_Category`  
 Catégorie.  
  
## Configuration requise  
 **en\-tête :** cvmarkersobj.h  
  
 **Espace de nom:** Concurrency::diagnostic  
  
## Voir aussi  
 [marker\_series, classe](../profiling/marker-series-class.md)