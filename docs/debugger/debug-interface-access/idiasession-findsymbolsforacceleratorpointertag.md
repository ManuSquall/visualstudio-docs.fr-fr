---
title: "IDiaSession::findSymbolsForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findSymbolsForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retourne une énumération de symboles pour la variable à la valeur spécifiée de balises correspond à dans la fonction parente stub d'accélérateur.  
  
## Syntaxe  
  
```cpp#  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Paramètres  
 `parent`  
 \[in\]  Un IDiaSymbol qui correspond à la fonction du stub d'accélérateur à rechercher.  
  
 `tagValue`  
 \[in\]  La valeur de la balise du pointeur.  
  
 `ppResult`  
 \[out\]  Un pointeur vers un pointeur d'interface de `IDiaEnumSymbols` qui est initialisé avec le résultat.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)