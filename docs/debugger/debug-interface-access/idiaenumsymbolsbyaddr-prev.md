---
title: "IDiaEnumSymbolsByAddr::Prev | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::Prev (méthode)"
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les symboles précédents dans l'ordre par l'adresse.  
  
## Syntaxe  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  Le nombre de symboles à l'énumérateur à récupérer.  
  
 rgelt  
 \[out\]  Un tableau qui doit être effectuée avec les objets d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représentent les symboles souhaités.  
  
 pceltFetched  
 \[out\]  Retourne le nombre de symboles à l'énumérateur extrait.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` s'il n'y a aucun symbole précédent.  Sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode met à jour la position d'énumérateur par le nombre d'éléments récupérés.  
  
## Voir aussi  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)