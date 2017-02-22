---
title: "IDiaSymbol::get_baseSymbol | Microsoft Docs"
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
ms.assetid: cabb5a18-bda7-47e8-9e46-5f4718579fc9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_baseSymbol
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le symbole dont le pointeur est basé.  
  
## Syntaxe  
  
```cpp  
HRESULT get_baseSymbol(   
   IDiaSymbol** pRetVal);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Pointeur vers le symbole à partir duquel le pointeur est basé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)