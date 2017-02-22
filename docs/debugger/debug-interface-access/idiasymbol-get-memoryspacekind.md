---
title: "IDiaSymbol::get_memorySpaceKind | Microsoft Docs"
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
ms.assetid: 9a63b298-8577-4c15-8595-530558d41bf1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_memorySpaceKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le type d'espace mémoire.  
  
## Syntaxe  
  
```cpp  
HRESULT get_memorySpaceKind(   
   DWORD* pRetVal);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Un pointeur vers `DWORD` qui juge l'espace mémoire kind.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)