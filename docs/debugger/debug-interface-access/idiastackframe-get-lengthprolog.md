---
title: "IDiaStackFrame::get_lengthProlog | Microsoft Docs"
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
  - "IDiaStackFrame::get_lengthProlog (méthode)"
ms.assetid: 9894c5ca-835f-41e9-a35e-70e046dfb7f0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaStackFrame::get_lengthProlog
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le nombre d'octets du code de prologue dans le bloc.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_lengthProlog (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne le nombre d'octets du code de prologue.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si la propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)