---
title: "marker_series, classe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series (classe)"
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series, classe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Représente une chaîne d'événements en série générés par un fournisseur unique.  
  
## Syntaxe  
  
```  
class marker_series;  
```  
  
## Membres  
  
### Constructeurs publics  
  
|Name|Description|  
|----------|-----------------|  
|[marker\_series::marker\_series, constructeur](../Topic/marker_series::marker_series%20Constructor.md)|Initialise une nouvelle instance de la classe `marker_series`.|  
|[marker\_series::~marker\_series, destructeur](../profiling/marker-series-tilde-marker-series-destructor.md)|Détruit l'objet marker\_series et libère toutes les ressources allouées.|  
  
### Méthodes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[marker\_series::is\_enabled, méthode](../Topic/marker_series::is_enabled%20Method.md)|Détermine si une session a activé le fournisseur.|  
|[marker\_series::write\_alert, méthode](../profiling/marker-series-write-alert-method.md)|Écrit une alerte dans le fichier de suivi du visualiseur concurrentiel.|  
|[marker\_series::write\_flag, méthode](../profiling/marker-series-write-flag-method.md)|Écrit un indicateur dans le fichier de suivi du visualiseur concurrentiel.|  
|[marker\_series::write\_message, méthode](../profiling/marker-series-write-message-method.md)|Écrit un message dans le fichier de suivi du visualiseur concurrentiel.|  
  
## Hiérarchie d'héritage  
 `marker_series`  
  
## Configuration requise  
 **en\-tête :** cvmarkersobj.h  
  
 **Espace de nom:** Concurrency::diagnostic  
  
## Voir aussi  
 [diagnostic, espace de noms](../profiling/diagnostic-namespace.md)