---
title: "IDiaSymbol::get_isPointerBasedOnSymbolValue | Microsoft Docs"
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
ms.assetid: 577c8011-9269-4373-8577-b4822a983724
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isPointerBasedOnSymbolValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie si le pointeur d' `this` est basé sur une valeur du symbole.  
  
## Syntaxe  
  
```cpp  
HRESULT get_isPointerBasedOnSymbolValue(   
   BOOL* pRetVal);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Un pointeur vers `BOOL` qui spécifie si le pointeur d' `this` est basé sur une valeur du symbole.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)