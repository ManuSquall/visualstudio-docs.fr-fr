---
title: "IDiaSession::findSymbolByVAEx | Microsoft Docs"
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
  - "IDiaSession::findSymbolByVAEx (méthode)"
ms.assetid: 11c685f6-cda2-4474-a432-214ecaae4ffa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findSymbolByVAEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un type spécifié de symboles qui contient, ou est le plus proche de, une adresse virtuelle et \(VA\) un offset spécifiés.  
  
## Syntaxe  
  
```cpp#  
HRESULT findSymbolByVAEx (   
   ULONGLONG    va,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### Paramètres  
 `va`  
 \[in\]  spécifie le VA.  
  
 `symtag`  
 \[in\]  type de symbole à rechercher.  Les valeurs sont récupérées l'énumération de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) .  
  
 `ppSymbol`  
 \[out\]  Retourne un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le symbole extrait.  
  
 `displacement`  
 \[out\]  Retourne une valeur qui spécifie un offset de l'adresse virtuelle donnée par `va`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByVAEx( va, SymTagFunction, &pFunc, &disp );  
```  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)