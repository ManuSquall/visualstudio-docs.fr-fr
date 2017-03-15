---
title: "IDiaEnumFrameData::Next | Microsoft Docs"
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
  - "IDiaEnumFrameData::Next (méthode)"
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un nombre spécifié d'éléments de données de frame de la séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  Le nombre d'éléments de données de frame dans l'énumérateur à récupérer.  
  
 rgelt  
 \[out\]  Un tableau d'objets d' [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) à remplir avec des éléments de données demandés de frame.  
  
 pceltFetched  
 \[out\]  Retourne le nombre d'éléments de données de frame dans l'énumérateur extrait.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` s'il ne reste plus d'enregistrements.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)