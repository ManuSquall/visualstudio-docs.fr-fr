---
title: "IDiaSession::findSymbolByAddr | Microsoft Docs"
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
  - "IDiaSession::findSymbolByAddr (méthode)"
ms.assetid: c130abc5-4d0a-4d2d-8286-94fde36ddd4a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findSymbolByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un type spécifié de symboles qui contient, ou est le plus proche de, une adresse spécifiée.  
  
## Syntaxe  
  
```cpp#  
HRESULT findSymbolByAddr (   
   DWORD        isect,  
   DWORD        offset,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### Paramètres  
 `isect`  
 \[in\]  spécifie le composant de section de l'adresse.  
  
 `offset`  
 \[in\]  spécifie le composant d'offset de l'adresse.  
  
 `symtag`  
 \[in\]  type de symbole à rechercher.  Les valeurs sont récupérées l'énumération de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) .  
  
 `ppSymbol`  
 \[out\]  Retourne un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le symbole extrait.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByAddr( isect, offset, SymTagFunction, &pFunc );  
```  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)