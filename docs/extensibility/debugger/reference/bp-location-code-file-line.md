---
description: Contient les données relatives à l’emplacement d’un point d’arrêt au niveau d’une ligne spécifique dans un fichier source de code.
title: BP_LOCATION_CODE_FILE_LINE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 2ad3452e0fce6ec7339fe2d8e67a2aee4585828c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144388"
---
# <a name="bp_location_code_file_line"></a>BP_LOCATION_CODE_FILE_LINE
Contient les données relatives à l’emplacement d’un point d’arrêt au niveau d’une ligne spécifique dans un fichier source de code.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_LOCATION_CODE_FILE_LINE {
    BSTR                     bstrContext;
    IDebugDocumentPosition2* pDocPos;
} BP_LOCATION_CODE_FILE_LINE;
```

## <a name="members"></a>Membres
`bstrContext`\
Contexte du point d’arrêt, en général une méthode ou un nom de fonction tel qu’il apparaît sur une pile des appels.

`pDocPos`\
Objet [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) qui représente la position du document du point d’arrêt.

## <a name="remarks"></a>Notes
Cette structure est un membre de la structure [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d’une Union.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
