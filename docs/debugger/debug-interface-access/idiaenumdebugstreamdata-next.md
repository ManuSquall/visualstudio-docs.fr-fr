---
title: "IDiaEnumDebugStreamData::Next | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Next (méthode)"
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait un nombre d'enregistrements spécifié dans la séquence énumérée.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  Le nombre d'enregistrements à récupérer.  
  
 cbData  
 \[in\]  taille de la mémoire tampon de données, en octets.  
  
 pcbData  
 \[out\]  Retourne le nombre d'octets retournés.  Si `data` est NULL, alors `pcbData` contient le nombre total d'octets de données disponibles pour tous les enregistrements demandés.  
  
 données \[\]  
 \[out\]  une mémoire tampon qui doit être remplie avec les données d'enregistrement de flux de données de débogage.  
  
 pceltFetched  
 \[in, out\]  Retourne le nombre d'enregistrements dans `data`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` s'il ne reste plus d'enregistrements.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)