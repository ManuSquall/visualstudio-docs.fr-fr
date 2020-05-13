---
title: IDebugProgram2::GetDisassemblyStream (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2160f963ad1f3f37291519ced30b8096e33a6116
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722868"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Obtient le flux de démontage pour ce programme ou une partie de ce programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>Paramètres
`dwScope`\
[dans] Spécifie une valeur du [recensement DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) qui définit la portée du flux de démontage.

`pCodeContext`\
[dans] Un objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui représente la position de l’endroit où démarrer le flux de démontage.

`ppDisassemblyStream`\
[out] Retourne un objet [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) qui représente le flux de démontage.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retours `E_DISASM_NOTSUPPORTED` si le démontage n’est pas pris en charge pour cette architecture particulière.

## <a name="remarks"></a>Notes
 Si `dwScopes` le paramètre a le `DSS_HUGE` drapeau de [l’ensemble](../../../extensibility/debugger/reference/disassembly-stream-scope.md) de recensement DISASSEMBLY_STREAM_SCOPE, le démontage devrait retourner un grand nombre d’instructions de démontage, par exemple, pour un fichier ou un module entier. Si `DSS_HUGE` le drapeau n’est pas fixé, on s’attend à ce que le démontage soit confiné à une petite région, généralement celle d’une seule fonction.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
