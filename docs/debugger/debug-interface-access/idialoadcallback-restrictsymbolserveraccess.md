---
title: "IDiaLoadCallback::RestrictSymbolServerAccess | Microsoft Docs"
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
  - "IDiaLoadCallback::RestrictSymbolServerAccess (méthode)"
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::RestrictSymbolServerAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Détermine si l'accès à un serveur de symboles aux symboles de la résolution.  
  
## Syntaxe  
  
```cpp#  
HRESULT RestrictSymbolServerAccess();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Tout code de retour autre qu' `S_OK` empêché l'utilisation d'un serveur de symboles de résoudre les symboles.  
  
## Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)