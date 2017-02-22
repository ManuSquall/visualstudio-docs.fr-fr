---
title: "IDiaLineNumber::get_addressOffset | Microsoft Docs"
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
  - "IDiaLineNumber::get_addressOffset (méthode)"
ms.assetid: 3bcb5500-b26c-4d3c-9d81-0a389a3715c3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_addressOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait la partie d'offset de l'adresse mémoire où un bloc démarre.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne la partie d'offset de l'adresse mémoire où un bloc démarre.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Exemple  
  
```cpp#  
CComPtr< IDiaLineNumber > pLine;  
DWORD offset;  
pLine->get_addressOffset( &offset);  
```  
  
## Voir aussi  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaLineNumber::get\_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)