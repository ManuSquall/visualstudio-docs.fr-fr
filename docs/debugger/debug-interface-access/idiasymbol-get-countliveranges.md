---
title: "IDiaSymbol::get_countLiveRanges | Microsoft Docs"
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
  - "IDiaSymbol::get_countLiveRanges"
ms.assetid: 55f79e1a-d4c2-42cd-ab37-d8253b20e34c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_countLiveRanges
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le nombre de plages d'adresses valides associées au symbole local.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_countLiveRanges (   
   DWORD* count  
);  
```  
  
#### Paramètres  
 `count`  
 \[out\]  Retourne le nombre de plages d'adresses.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia100.dll  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)