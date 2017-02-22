---
title: "IDiaSymbol::get_isSafeBuffers | Microsoft Docs"
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
  - "IDiaSymbol::get_isSafeBuffers (méthode)"
ms.assetid: f29e373d-e7bb-4181-ab9f-bf708d401d83
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDiaSymbol::get_isSafeBuffers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait une balise qui spécifie si la directive de préprocesseur pour une mémoire tampon sécurisée est utilisée.  Utilisez lorsque [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) est défini à `SymTagFunction`.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_isSafeBuffers(   
   BOOL* pRetVal)  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne `TRUE` si le pointeur utilise une directive de préprocesseur pour une mémoire tampon sécurisée ; sinon, retourne `FALSE`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia100.dll  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [strict\_gs\_check](/visual-cpp/preprocessor/strict-gs-check)