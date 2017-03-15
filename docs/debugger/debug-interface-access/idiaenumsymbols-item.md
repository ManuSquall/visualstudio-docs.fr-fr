---
title: "IDiaEnumSymbols::Item | Microsoft Docs"
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
  - "IDiaEnumSymbols::Item (méthode)"
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbols::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un symbole au moyen d'un index.  
  
## Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD        index,  
   IDiaSymbol** symbol  
);  
```  
  
#### Paramètres  
 index  
 \[in\]  Index de l'objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) à récupérer.  L'index est comprise entre 0 et `count`\-1, où `count` est retourné par la méthode d' [IDiaEnumSymbols::get\_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) .  
  
 symbole  
 \[out\]  Retourne un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le symbole souhaité.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)