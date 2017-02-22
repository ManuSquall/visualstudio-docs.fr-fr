---
title: "IDiaEnumDebugStreamData::Item | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Item (méthode)"
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait l'enregistrement spécifié.  
  
## Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Paramètres  
 index  
 \[in\]  Index de l'enregistrement à récupérer.  L'index est comprise entre 0 et `count`\-1, où `count` est retourné par [IDiaEnumDebugStreamData::get\_Count](../Topic/IDiaEnumDebugStreamData::get_Count.md).  
  
 cbData  
 \[in\]  taille de la mémoire tampon de données, en octets.  
  
 pcbData  
 \[out\]  Retourne le nombre d'octets retournés.  Si `data` est `NULL`, alors `pcbData` contient le nombre total d'octets de données disponibles dans l'enregistrement spécifié.  
  
 données \[\]  
 \[out\]  Une mémoire tampon qui est terminée avec les données d'enregistrement de flux de données de débogage.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_INVALIDARG` pour les paramètres incorrects et si le paramètre d' `index` est hors limites.  
  
## Voir aussi  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreamData::get\_Count](../Topic/IDiaEnumDebugStreamData::get_Count.md)   
 [IDiaEnumDebugStreamData::Skip](../Topic/IDiaEnumDebugStreamData::Skip.md)