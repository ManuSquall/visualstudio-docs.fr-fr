---
title: "IDiaReadExeAtRVACallback | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback (interface)"
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Permet à une application cliente de fournir des octets d'un fichier exécutable comme spécifié par une adresse virtuelle associée.  
  
## Syntaxe  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaReadExeAtRVACallback`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Lit le nombre d'octets spécifié à partir de l'adresse virtuelle relative spécifiée \(RVA\) du fichier exécutable.|  
  
## Notes  
 L'application cliente implémente cette interface pour fournir les octets du fichier exécutable utilisant une adresse virtuelle relative dans le fichier de fichier exécutable.  pour utiliser un offset de fichier absolu, implémentez l'interface d' [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) .  
  
## Remarques pour les appelants  
 Cette méthode est implémentée par l'application cliente et passée à la méthode d' [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) comme autre méthode pour lire le fichier.  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)