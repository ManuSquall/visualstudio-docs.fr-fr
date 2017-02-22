---
title: "IDiaSession::symsAreEquiv | Microsoft Docs"
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
  - "IDiaSession::symsAreEquiv (méthode)"
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vérifie si deux symboles sont équivalents.  
  
## Syntaxe  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### Paramètres  
 `symbolA`  
 \[in\]  le premier objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) utilisé dans la comparaison.  
  
 `symbolB`  
 \[in\]  le deuxième objet d' `IDiaSymbol` utilisé dans la comparaison.  
  
## Valeur de retour  
 Si les symboles sont équivalents, retourne `S_OK`; sinon, la `S_FALSE`, les symboles ne sont différents.  Sinon, le code d'erreur.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)