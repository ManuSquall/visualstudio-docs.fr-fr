---
title: "IDiaLoadCallback2::RestrictDBGAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictDBGAccess (méthode)"
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaLoadCallback2::RestrictDBGAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Détermine si la recherche d'informations de débogage est autorisé à partir de les fichiers de .dbg.  
  
## Syntaxe  
  
```cpp#  
HRESULT RestrictDBGAccess();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Toute valeur de retour autre qu' `S_OK` pour empêcher rechercher des informations de débogage à partir de les fichiers de .dbg.  
  
## Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)