---
title: "IDiaSymbol::get_isSdl | Microsoft Docs"
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
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isSdl
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie si le module est compilé avec l'option \/SDL.  
  
## Syntaxe  
  
```cpp  
HRESULT get_isSdl(  
   BOOL *pRetVal);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Un pointeur vers `BOOL` qui spécifie si le module est compilé avec l'option \/SDL.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)