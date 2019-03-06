---
title: CODE_PATH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e09cd77308f83c2b9fb1b9cba70076ad797eb2e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714944"
---
# <a name="codepath"></a>CODE_PATH
Décrit un appel de méthode ou fonction.

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
bstrName le nom du chemin d’accès du code.

pCode le [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet qui identifie où dans le code pas à pas détaillé dans une fonction.

## <a name="remarks"></a>Notes
Cette structure est utilisée pour implémenter le pas à pas détaillé dans une fonction. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) retourne tous les appels à partir de l’emplacement actuel dans le programme en cours de débogage. Cette structure représente un appel de ce type.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
