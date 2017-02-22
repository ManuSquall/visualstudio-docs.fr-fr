---
title: "IDiaEnumSymbols::Skip | Microsoft Docs"
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
  - "IDiaEnumSymbols::Skip (méthode)"
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbols::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ignore un nombre spécifié de symboles dans une séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  le nombre de symboles dans la séquence d'énumération à ignorer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` s'il n'y a plus de symboles à ignorer.  
  
## Voir aussi  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)