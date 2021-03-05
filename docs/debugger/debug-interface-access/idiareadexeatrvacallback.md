---
description: Permet à une application cliente de fournir des octets d’un fichier exécutable comme spécifié par une adresse virtuelle relative.
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8efb088012af4fbcba259182465d53ee7ce8eac
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148044"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Permet à une application cliente de fournir des octets d’un fichier exécutable comme spécifié par une adresse virtuelle relative.

## <a name="syntax"></a>Syntaxe

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDiaReadExeAtRVACallback` .

|Méthode|Description|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Lit le nombre d’octets spécifié en commençant à l’adresse virtuelle relative (RVA) spécifiée à partir du fichier exécutable.|

## <a name="remarks"></a>Notes
 L’application cliente implémente cette interface afin de fournir les octets de l’exécutable à l’aide d’une adresse virtuelle relative dans le fichier de l’exécutable. Pour utiliser un décalage de fichier absolu, implémentez l’interface [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) .

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette méthode est implémentée par l’application cliente et transmise à la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) comme méthode alternative pour la lecture du fichier.

## <a name="requirements"></a>Configuration requise
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
