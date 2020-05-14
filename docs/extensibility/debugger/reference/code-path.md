---
title: CODE_PATH Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3148b75e56b61ee545c6bc82b972c13572199af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737668"
---
# <a name="code_path"></a>CODE_PATH
Décrit une méthode ou un appel de fonction.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagCODE_PATH { 
    BSTR                bstrName;
    IDebugCodeContext2* pCode;
} CODE_PATH;
```

```csharp
public struct CODE_PATH {
    public string            bstrName;
    public IDebugCodeContext pCode;
}
```

## <a name="members"></a>Membres
`bstrName`\
Le nom du chemin de code.

`pCode`\
[L’objet IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui identifie où dans le code entrer dans une fonction.

## <a name="remarks"></a>Notes
Cette structure est utilisée pour implémenter l’entrée dans une fonction. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) renvoie tous les appels à partir de l’emplacement actuel du programme en cours de déboptation. Cette structure représente l’un de ces appels.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
