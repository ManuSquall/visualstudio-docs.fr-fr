---
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84661f5cd51da17cf20577490b2fe458e71ef71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863738"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Facilite le parcours de la pile à l’aide du fichier de base de données de débogage de programme (. pdb).

## <a name="syntax"></a>Syntaxe

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre VTable
 Le tableau ci-dessous montre les méthodes de `IDiaStackWalkHelper` :

|Méthode|Description|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Récupère la valeur d’un registre.|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Définit la valeur d’un registre.|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Lit un bloc de données à partir de l’image de l’exécutable en mémoire.|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Recherche l’adresse de retour de la fonction la plus proche dans le frame de pile spécifié.|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Recherche dans le frame de pile spécifié une adresse de retour à l’adresse de la pile spécifiée ou à proximité de celle-ci.|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Récupère le frame de pile qui contient l’adresse virtuelle spécifiée.|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Récupère le symbole qui contient l’adresse virtuelle spécifiée. **Remarque :**  Le symbole doit avoir le type `SymTagFunctionType` (une valeur de l’énumération d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Retourne le bloc de données PDATA associé à l’adresse virtuelle spécifiée.|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Récupère l’adresse virtuelle de début d’un exécutable, en fonction d’une adresse virtuelle à un endroit quelconque dans l’espace mémoire de l’exécutable.|

## <a name="remarks"></a>Remarques
 Cette interface est appelée par le code DIA pour obtenir des informations sur l’exécutable afin de construire une liste de frames de pile pendant l’exécution du programme.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Une application cliente implémente cette interface pour prendre en charge le parcours de la pile pendant l’exécution du programme. Une instance de cette interface est passée aux méthodes [IDiaStackWalker :: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) ou [IDiaStackWalker :: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .

## <a name="requirements"></a>Configuration requise
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)