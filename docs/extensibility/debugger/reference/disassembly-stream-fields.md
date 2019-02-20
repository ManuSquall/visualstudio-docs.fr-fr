---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73214385e3bc2b8ac6dbe2dff8705377d6f14e12
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413590"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Spécifie les informations à récupérer sur un champ de code machine.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="members"></a>Membres
DSF_ADDRESS  
Initialize/utiliser le `bstrAddress` champ.

DSF_ADDRESSOFFSET  
Initialize/utiliser le `bstrAddressOffset` champ.

DSF_CODEBYTES  
Initialize/utiliser le `bstrCodeBytes` champ.

DSF_OPCODE  
Initialize/utiliser le `bstrOpCode` champ.

DSF_OPERANDS  
Initialize/utiliser le `bstrOperands` champ.

DSF_SYMBOL  
Initialize/utiliser le `bstrSymbol` champ.

DSF_CODELOCATIONID  
Initialize/utiliser le `uCodeLocationId` champ.

DSF_POSITION  
Initialize/utiliser le `posBeg` et `posEnd` champs.

DSF_DOCUMENTURL  
Initialize/utiliser le `bstrDocumentUrl` champ.

DSF_BYTEOFFSET  
Initialize/utiliser le `dwByteOffset` champ.

DSF_FLAGS  
Initialize/utiliser le `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) champ.

DSF_OPERANDS_SYMBOLS  
Inclure les noms de symboles dans le `bstrOperands` champ.

DSF_ALL  
Spécifie tous les champs pour le flux de code machine.

## <a name="remarks"></a>Notes
Passé en tant que paramètre à la [en lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) méthode pour indiquer les champs de la [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) structure doivent être initialisées.

Utilisé pour le `dwFields` membre de la `DisassemblyData` structure pour indiquer quels champs sont utilisés et valide lors de la structure est retournée.

Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
[Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)  
[DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
