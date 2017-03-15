---
title: "IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Donné une valeur correspondante de balise, cette méthode retourne une énumération de symboles qui sont contenus dans une fonction parente spécifiée stub d'accélérateur à une adresse virtuelle relative spécifiée.  
  
## Syntaxe  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Paramètres  
 `parent`  
 \[in\]  `IDiaSymbol` qui correspond à la fonction du stub d'accélérateur à rechercher.  
  
 `tagValue`  
 \[in\]  La valeur de la balise du pointeur.  
  
 `rva`  
 \[in\]  Adresse virtuelle associée.  
  
 `ppResult`  
 \[out\]  Un pointeur vers un pointeur d'interface de `IDiaEnumSymbols` qui est initialisé avec le résultat.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## Notes  
 Appelez cette méthode uniquement sur une interface d' `IDiaSymbol` qui correspond à une fonction stub d'accélérateur.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)