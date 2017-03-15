---
title: "IDiaStackFrame::get_registerValue | Microsoft Docs"
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
  - "IDiaStackFrame::get_registerValue (méthode)"
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait la valeur d'un registre spécifié stocké dans le frame de pile.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### Paramètres  
 `registerIndex`  
 \[in\]  L'une des valeurs d'énumération de [CV\_HREG\_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md) .  
  
 `pRetVal`  
 \[out\]  Valeur stockée dans le registre.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [CV\_HREG\_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)