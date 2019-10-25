---
title: IDiaReadExeAtOffsetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8498b0189a1d5bfb876417d4719adb3487065d5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742812"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Permet à une application cliente de fournir des octets d’un fichier exécutable comme spécifié par la position de fichier.

## <a name="syntax"></a>Syntaxe

```
IDiaReadExeAtOffsetCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDiaReadExeAtOffsetCallback`.

|Méthode|Description|
|------------|-----------------|
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Lit le nombre d’octets spécifié en commençant à l’offset spécifié à partir d’un fichier exécutable.|

## <a name="remarks"></a>Notes
 L’application cliente implémente cette interface afin de fournir les octets de l’exécutable à l’aide d’un offset absolu dans le fichier de l’exécutable. Pour utiliser une adresse virtuelle relative, implémentez l’interface [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette méthode est implémentée par l’application cliente et transmise à la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) comme méthode alternative pour la lecture du fichier.

## <a name="requirements"></a>spécifications
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : Msdia80. dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)