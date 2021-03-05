---
description: Reçoit des rappels de la procédure de localisation de symboles DIA, ce qui permet d’imposer des restrictions au processus de localisation.
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9103157791f5ce67bb14bb05e708f7ffd87ee435
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148198"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Reçoit des rappels de la procédure de localisation de symboles DIA, ce qui permet d’imposer des restrictions au processus de localisation.

## <a name="syntax"></a>Syntaxe

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes de l’interface [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) , cette interface expose les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Détermine si la recherche d’un fichier. pdb dans le répertoire de débogage d’origine.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Détermine si la recherche d’un fichier. pdb est autorisée dans le chemin d’accès où se trouve le fichier. exe.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Détermine si la recherche d’informations de débogage est autorisée à partir des fichiers. dbg.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Détermine si la recherche de fichiers. pdb est autorisée dans le répertoire racine système.|

## <a name="remarks"></a>Notes
 L’application cliente implémente cette interface et fournit une référence à celle-ci dans l’appel à la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) . N’oubliez pas d’implémenter toutes les méthodes dans l’interface [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) également.

## <a name="requirements"></a>Configuration requise
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
