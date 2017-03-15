---
title: "IDiaLoadCallback2 | Microsoft Docs"
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
  - "IDiaLoadCallback2 (interface)"
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Reçoit les rappels sur le symbole de diamètre recherche de la procédure, autorisant les restrictions à appliquer au processus le trouvant.  
  
## Syntaxe  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## méthodes en commande de Vtable  
 En plus de les méthodes dans l'interface d' [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) , cette interface expose les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Détermine si la recherche d'un fichier .pdb dans le répertoire d'origine de débogage.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../Topic/IDiaLoadCallback2::RestrictReferencePathAccess.md)|Détermine si la recherche d'un fichier .pdb est autorisée dans le chemin d'accès du fichier .exe est localisé.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Détermine si la recherche d'informations de débogage est autorisé à partir de les fichiers de .dbg.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Détermine si est autorisé à rechercher des fichiers .pdb dans le répertoire racine du système.|  
  
## Notes  
 L'application cliente implémente cette interface et fournit une référence à celui\-ci dans l'appel à la méthode d' [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  N'oubliez pas d'implémenter toutes les méthodes dans l'interface d' [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) également.  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)