---
title: "IDiaSession::findSymbolByToken | Microsoft Docs"
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
  - "IDiaSession::findSymbolByToken (méthode)"
ms.assetid: 3c92149c-6eef-454f-86be-66e89557b9e6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findSymbolByToken
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le symbole qui contient un jeton de métadonnées spécifié.  
  
## Syntaxe  
  
```cpp#  
HRESULT findSymbolByToken (   
   ULONG        token,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### Paramètres  
 `token`  
 \[in\]  spécifie le jeton.  
  
 `symtag`  
 \[in\]  type de symbole à rechercher.  Les valeurs sont récupérées l'énumération de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) .  
  
 `ppSymbol`  
 \[out\]  Retourne un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le symbole extrait.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByToken( token, SymTagFunction, &pFunc );  
```  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)