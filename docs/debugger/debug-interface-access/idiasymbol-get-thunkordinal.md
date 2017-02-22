---
title: "IDiaSymbol::get_thunkOrdinal | Microsoft Docs"
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
  - "IDiaSymbol::get_thunkOrdinal (méthode)"
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le type de conversion de code d'une fonction.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne une valeur de l'énumération de [THUNK\_ORDINAL, énumération](../../debugger/debug-interface-access/thunk-ordinal.md) qui spécifie le type de conversion de code d'une fonction.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 Cette propriété est valide uniquement si le symbole comme valeur de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) d' `SymTagThunk`.  
  
 Une « conversion de code » est un peu de code qui convertit entre une espace adresse d'adresse mémoire 32 bits \(également appelée l'espace d'adressage en deux dimensions\) et un espace d'adressage 16 bits \(appelé un espace d'adressage segmenté\).  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK\_ORDINAL, énumération](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)