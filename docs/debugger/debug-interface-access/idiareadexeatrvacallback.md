---
title: IDiaReadExeAtRVACallback | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fdc876897d5106f4d03d5b25b51dec5572837f21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Permet à une application cliente fournir des octets d’un fichier exécutable, comme spécifié par une adresse virtuelle relative.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaReadExeAtRVACallback`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Lit le nombre spécifié d’octets commençant au niveau de le spécifié adresse virtuelle relative (RVA) du fichier exécutable.|  
  
## <a name="remarks"></a>Notes  
 L’application cliente implémente cette interface afin de fournir les octets de l’exécutable à l’aide d’une adresse virtuelle relative dans le fichier de l’exécutable. Pour utiliser un décalage de fichier absolu, implémenter la [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette méthode est implémentée par l’application cliente et passée à la [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) méthode comme une méthode alternative pour la lecture du fichier.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)