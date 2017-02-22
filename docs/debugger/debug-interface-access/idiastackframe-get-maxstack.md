---
title: "IDiaStackFrame::get_maxStack | Microsoft Docs"
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
  - "IDiaStackFrame::get_maxStack (méthode)"
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_maxStack
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le nombre maximal d'octets l'objet d'un push sur la pile dans le frame.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne le nombre maximal d'octets l'objet d'un push sur la pile.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si la propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)