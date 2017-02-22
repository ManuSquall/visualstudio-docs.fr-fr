---
title: "IDiaLoadCallback2::RestrictSystemRootAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictSystemRootAccess (méthode)"
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaLoadCallback2::RestrictSystemRootAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Détermine si est autorisé à rechercher des fichiers .pdb dans le répertoire racine du système.  
  
## Syntaxe  
  
```cpp#  
HRESULT RestrictSystemRootAccess();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Tout code de retour autre qu' `S_OK` empêché rechercher la racine du système pour les fichiers .pdb.  
  
## Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)