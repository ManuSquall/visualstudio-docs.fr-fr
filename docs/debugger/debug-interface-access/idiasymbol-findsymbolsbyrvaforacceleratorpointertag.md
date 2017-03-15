---
title: "IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Donné une valeur correspondante de balise, cette méthode retourne une énumération de symboles qui sont contenus dans cette fonction stub à une adresse virtuelle relative spécifiée.  
  
## Syntaxe  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### Paramètres  
 `tagValue`  
 \[in\]  La valeur de la balise de pointeur pour laquelle le symbole de pointee stocke sont introuvables.  
  
 `rva`  
 \[in\]  Le rva utilisé pour filtrer les symboles qui correspondent à la variable de pointee avec la valeur spécifiée de balise.  
  
 `ppResult`  
 \[out\]  Un pointeur vers un pointeur d'interface de `IDiaEnumSymbols` qui est initialisé avec le résultat.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Notes  
 Appelez cette méthode uniquement sur une interface d' `IDiaSymbol` qui correspond à une fonction stub d'accélérateur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)