---
title: "IDiaSymbol::get_isOptimizedAway | Microsoft Docs"
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
ms.assetid: c18b1e38-b152-4a13-aba0-59faded5b2e6
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isOptimizedAway
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie si la variable est optimisée approfondie.  
  
## Syntaxe  
  
```cpp  
HRESULT get_isOptimizedAway(   
   BOOL* pRetVal);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Un pointeur vers `BOOL` qui spécifie si la variable est optimisée approfondie.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)