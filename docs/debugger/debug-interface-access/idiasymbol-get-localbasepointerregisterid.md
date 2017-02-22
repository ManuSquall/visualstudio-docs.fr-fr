---
title: "IDiaSymbol::get_localBasePointerRegisterId | Microsoft Docs"
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
  - "IDiaSymbol::get_localBasePointerRegisterId (méthode)"
ms.assetid: 9cbcaf00-9ace-45e1-b164-7a9439e08083
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDiaSymbol::get_localBasePointerRegisterId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait l'ID du registre qui contient un pointeur de base aux variables locales sur la pile.  Utilisez lorsque [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) est défini à `SymTagFunction`.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_localBasePointerRegisterId (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne l'ID du registre qui contient un pointeur de base aux variables locales sur la pile.  
  
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