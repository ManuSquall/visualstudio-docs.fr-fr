---
title: "IDiaSymbol::get_sizeInUdt | Microsoft Docs"
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
ms.assetid: a82ab896-0185-46a4-b4d5-babfcc660fe1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_sizeInUdt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait la taille d'un membre d'un type défini par l'utilisateur.  
  
## Syntaxe  
  
```cpp  
HRESULT get_sizeInUdt(   
   DWORD* pRetVal);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Un pointeur vers `DWORD` qui spécifie la taille du membre.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)