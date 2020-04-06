---
title: BP_LOCATION_CODE_FILE_LINE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: e338c3b24ade2cf7663b77abea64f58425d3a068
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738011"
---
# <a name="bp_location_code_file_line"></a>BP_LOCATION_CODE_FILE_LINE
Contient les données pour l’emplacement d’un point d’arrêt à une ligne spécifique dans un fichier source de code.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_LOCATION_CODE_FILE_LINE {
    BSTR                     bstrContext;
    IDebugDocumentPosition2* pDocPos;
} BP_LOCATION_CODE_FILE_LINE;
```

## <a name="members"></a>Membres
`bstrContext`\
Le contexte du point d’arrêt, généralement une méthode ou un nom de fonction vu sur une pile d’appels.

`pDocPos`\
[L’objet IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) qui représente la position du document du point d’arrêt.

## <a name="remarks"></a>Notes
Cette structure est membre de la structure [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d’un syndicat.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
