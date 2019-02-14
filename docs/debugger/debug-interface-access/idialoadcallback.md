---
title: IDiaLoadCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a9f3609f97d74cad8a9abb8aad511345d3120c4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977640"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Reçoit des rappels du symbole DIA procédure de localisation, ce qui permet une interface utilisateur pour signaler l’avancement de la tentative d’emplacement.  
  
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
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Détermine si les requêtes de Registre peuvent être utilisées pour localiser les chemins de recherche de symbole.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Détermine si l’accès est autorisé à un serveur de symboles pour résoudre les symboles.|  
  
## <a name="remarks"></a>Remarques  
 L’application cliente implémente cette interface et fournit une référence à celle-ci dans l’appel à la [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (méthode).  
  
 Pour connaître les restrictions supplémentaires qui peuvent être imposées sur un processus de chargement, consultez la [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) interface.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Kit SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)