---
title: "marker_series::write_message, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::write_message"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_message (méthode)"
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series::write_message, m&#233;thode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Écrit un message dans le fichier de suivi du visualiseur concurrentiel.  
  
## Syntaxe  
  
```  
void write_message(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
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
 Catgorie. Niveau d'importance.  
  
## Configuration requise  
 **en\-tête :** cvmarkersobj.h  
  
 **Espace de nom:** Concurrency::diagnostic  
  
## Voir aussi  
 [marker\_series, classe](../profiling/marker-series-class.md)