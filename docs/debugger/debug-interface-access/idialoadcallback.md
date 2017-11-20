---
title: IDiaLoadCallback | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7dc5034967fe94b8be6503a9c86f7b6bc6ee14ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Reçoit les rappels de symbole DIA procédure de localisation, ce qui permet une interface utilisateur d’un rapport sur la progression de la tentative de l’emplacement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Les méthodes suivantes sont exposées par cette interface :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Appelé lorsqu’un répertoire de débogage a été trouvé dans le fichier .exe.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Appelé lorsqu’un fichier .dbg de candidat a été ouvert.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Appelé lorsqu’un fichier .pdb de candidat a été ouvert.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Détermine si les requêtes du Registre peuvent être utilisés pour localiser les chemins de recherche de symbole.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Détermine si l’accès est autorisé à un serveur de symboles pour résoudre les symboles.|  
  
## <a name="remarks"></a>Remarques  
 L’application cliente implémente cette interface et fournit une référence à celle-ci dans l’appel à la [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (méthode).  
  
 Pour connaître les restrictions supplémentaires qui peuvent être imposées sur un processus de chargement, consultez la [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) interface.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)