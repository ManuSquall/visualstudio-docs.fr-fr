---
title: "IDiaEnumSegments::Skip | Microsoft Docs"
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
  - "IDiaEnumSegments::Skip (méthode)"
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ignore un nombre spécifié de segments dans une séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  Le nombre de segments de la séquence d'énumération à ignorer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` s'il n'y a plus de segments à ignorer.  
  
## Voir aussi  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)