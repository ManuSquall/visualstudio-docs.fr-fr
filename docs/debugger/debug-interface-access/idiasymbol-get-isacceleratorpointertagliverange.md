---
title: "IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs"
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
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isAcceleratorPointerTagLiveRange
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une balise qui indique si le symbole correspond *au symbole d'intervalle de définition* pour le composant de balise d'une variable pointeur dans le code compilé pour l'accélérateur C\+\+ ampère.  Le symbole d'intervalle de définition est l'emplacement d'une variable pour une plage d'adresses.  
  
## Syntaxe  
  
```cpp  
HRESULT get_isAcceleratorPointerTagLiveRange(   
   BOOL* pFlag);  
```  
  
#### Paramètres  
 `pFlag`  
 \[out\]  Un pointeur vers `BOOL` qui indique si le symbole correspond au symbole d'intervalle de définition.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)