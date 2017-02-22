---
title: "IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictOriginalPathAccess (méthode)"
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Détermine s'il est correct de rechercher un fichier .pdb dans le répertoire d'origine de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Tout code de retour autre qu' `S_OK` empêché rechercher un fichier .pdb dans le répertoire d'origine de débogage.  Le répertoire d'origine de débogage est le chemin d'accès au fichier de symboles compilé dans le fichier exécutable lorsque le débogage est activé.  Ce chemin d'accès n'est pas nécessairement que le chemin d'accès du fichier exécutable existe.  
  
## Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)