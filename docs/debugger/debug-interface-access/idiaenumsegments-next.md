---
title: "IDiaEnumSegments::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSegments::Next (méthode)"
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un nombre spécifié de segments de la séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  Le nombre de segments dans l'énumérateur à récupérer.  
  
 rgelt  
 \[out\]  Un tableau qui doit être effectuée avec les objets suffit d' [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) qui représentent les segments.  
  
 pceltFetched  
 \[out\]  Retourne le nombre de segments dans l'énumérateur extrait.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` s'il n'y a plus de segments.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)