---
title: "IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs"
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
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isAcceleratorGroupSharedLocal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une balise qui indique si le symbole correspond à une variable locale partagée de groupe dans le code compilé pour l'accélérateur C\+\+ ampère.  
  
## Syntaxe  
  
```cpp  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### Paramètres  
 `pFlag`  
 \[out\]  Un pointeur vers `BOOL` qui indique si le symbole correspond à une variable locale partagée de groupe dans le code compilé pour l'accélérateur C\+\+ ampère.  Si `TRUE`, `get_baseDataSlot` et des méthodes d' `get_baseDataOffset` peuvent être utilisés pour obtenir des informations d'emplacement de stockage pour la variable.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get\_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)