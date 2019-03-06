---
title: BP_LOCATION_CODE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cce96e2edfcbc0dcb6dc4c6ff0e58617ad792ad8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697999"
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
Décrit l’emplacement d’un point d’arrêt à une adresse dans le code.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Membres
`bstrContext` Le contexte du point d’arrêt, généralement un nom de méthode ou fonction tels que présentés sur une pile des appels.

`bstrModuleUrl` L’URL du module qui contient le point d’arrêt.

`bstrFunction` Le nom de la fonction qui contient le point d’arrêt.

`bstrAddress` L’adresse du point d’arrêt, ce qui est analysé par un évaluateur d’expression pour le lier à un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objet.

## <a name="remarks"></a>Notes
Cette structure est un membre de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) structure dans le cadre d’une union.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
