---
title: "IDiaEnumDebugStreams::Next | Microsoft Docs"
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
  - "IDiaEnumDebugStreams::Next (méthode)"
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreams::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un nombre spécifié de flux de données de débogage dans la séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next (   
   ULONG                     celt,   
   IDiaEnumDebugStreamData** rgelt,  
   ULONG*                    pceltFetched  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  **T**qu'il s'attendent des flux de données de débogage dans l'énumérateur à récupérer.  
  
 rgelt  
 \[out\]  Retourne un tableau d'objets d' [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) qui représente les flux de données de débogage qui sont récupérés.  
  
 pceltFetched  
 \[out\]  Retourne le nombre de flux de données de débogage retournés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` s'il n'y a plus de flux de données.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)