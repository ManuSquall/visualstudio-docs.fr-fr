---
title: "IDiaSession::findSymbolByRVAEx | Microsoft Docs"
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
  - "IDiaSession::findSymbolByRVAEx (méthode)"
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findSymbolByRVAEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un type spécifié de symboles qui contient, ou est le plus proche de, une adresse virtuelle et un \(RVA\) offset connexes spécifiés.  
  
## Syntaxe  
  
```cpp#  
HRESULT findSymbolByRVAEx (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### Paramètres  
 `rva`  
 \[in\]  Spécifie le CONCERNANT.  
  
 `symtag`  
 \[in\]  type de symbole à rechercher.  Les valeurs sont récupérées l'énumération de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) .  
  
 `ppSymbol`  
 \[out\]  Retourne un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le symbole extrait.  
  
 `displacement`  
 \[out\]  Retourne une valeur spécifiant un offset de l'adresse virtuelle relative spécifiée dans `rva`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );  
```  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)