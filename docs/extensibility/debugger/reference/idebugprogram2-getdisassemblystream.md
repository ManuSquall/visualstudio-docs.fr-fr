---
description: Obtient le flux de code machine pour ce programme ou une partie de ce programme.
title: 'IDebugProgram2 :: GetDisassemblyStream | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e000ada618c21af865743bfb2bd9fd6b60a80a4b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159924"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Obtient le flux de code machine pour ce programme ou une partie de ce programme.

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
dans Spécifie une valeur de l’énumération [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) qui définit la portée du flux de code machine.

`pCodeContext`\
dans Objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui représente la position de démarrage du flux de code machine.

`ppDisassemblyStream`\
à Retourne un objet [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) qui représente le flux de code machine.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne `E_DISASM_NOTSUPPORTED` si le code machine n’est pas pris en charge pour cette architecture particulière.

## <a name="remarks"></a>Notes
 Si le `dwScopes` paramètre a l' `DSS_HUGE` indicateur du jeu d’énumération [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) , le code machine est supposé retourner un grand nombre d’instructions de code machine, par exemple, pour un fichier ou un module entier. Si l' `DSS_HUGE` indicateur n’est pas défini, le désassemblage est supposé être confiné dans une petite zone, généralement celle d’une fonction unique.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
