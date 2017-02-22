---
title: "IDiaSymbol::get_framePointerPresent | Microsoft Docs"
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
  - "IDiaSymbol::get_framePointerPresent (méthode)"
ms.assetid: d036090a-1651-454d-9130-b798f58ba053
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDiaSymbol::get_framePointerPresent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait une balise qui spécifie si le pointeur de frame est présent.  Utilisez lorsque [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) est défini à `SymTagFunction`.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_framePointerPresent(   
   BOOL* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  \] Retourne `TRUE` si le pointeur de frame est présent ; sinon, retourne `FALSE`.  
  
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