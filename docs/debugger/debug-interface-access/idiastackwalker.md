---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9ec4267a0f5de93b32a4a56a61742a9148f2d9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863857"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Fournit des méthodes pour effectuer un parcours de la pile à l’aide des informations contenues dans le fichier. pdb.

## <a name="syntax"></a>Syntaxe

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaStackWalker` .

|Méthode|Description|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Récupère un énumérateur de frame de pile pour les plateformes x86.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Récupère un énumérateur de frame de pile pour un type de plateforme spécifique.|

## <a name="remarks"></a>Remarques
Cette interface est utilisée pour obtenir une liste de frames de pile pour un module chargé. Chaque méthode reçoit un objet [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (implémenté par l’application cliente) qui fournit les informations nécessaires à la création de la liste des frames de pile.

## <a name="notes-for-callers"></a>Notes pour les appelants
Cette interface est obtenue en appelant la `CoCreateInstance` méthode avec l’identificateur de classe `CLSID_DiaStackWalker` et l’ID d’interface de `IID_IDiaStackWalker` . L’exemple montre comment cette interface est obtenue.

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir l' `IDiaStackWalker` interface.

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Configuration requise
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
