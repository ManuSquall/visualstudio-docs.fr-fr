---
title: IDiaLoadCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 435dc337ea3f1caad2ad99031d9be872d80337e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466720"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Reçoit des rappels de la procédure de localisation de symboles DIA, permettant ainsi à une interface utilisateur de signaler la progression de la tentative d’emplacement.

## <a name="syntax"></a>Syntaxe

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Les méthodes suivantes sont exposées par cette interface :

|Méthode|Description|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Appelé lorsqu’un répertoire de débogage a été trouvé dans le fichier. exe.|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Appelée lorsqu’un fichier candidat. dbg a été ouvert.|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Appelé lorsqu’un fichier candidat. pdb a été ouvert.|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Détermine si les requêtes de Registre peuvent être utilisées pour rechercher des chemins de recherche de symboles.|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Détermine si l’accès est autorisé à un serveur de symboles pour résoudre les symboles.|

## <a name="remarks"></a>Notes
 L’application cliente implémente cette interface et fournit une référence à celle-ci dans l’appel à la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

 Pour obtenir des restrictions supplémentaires qui peuvent être imposées sur un processus de chargement, consultez l’interface [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) .

## <a name="requirements"></a>Configuration requise
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)