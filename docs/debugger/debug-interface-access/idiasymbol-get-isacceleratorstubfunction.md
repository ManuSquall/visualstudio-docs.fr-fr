---
title: "IDiaSymbol::get_isAcceleratorStubFunction | Microsoft Docs"
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
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isAcceleratorStubFunction
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Indique si le symbole correspond à un symbole de niveau supérieur de fonction pour un shader compilé pour un accélérateur qui correspond à un appel d' `parallel_for_each` .  
  
## Syntaxe  
  
```cpp  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### Paramètres  
 `pFlag`  
 \[out\]  Un pointeur vers `BOOL` qui indique si le symbole correspond à un symbole de niveau supérieur de fonction pour un shader compilé pour un accélérateur qui correspond à un appel d' `parallel_for_each` .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)