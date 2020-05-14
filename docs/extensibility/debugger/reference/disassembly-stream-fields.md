---
title: DISASSEMBLY_STREAM_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737357"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Précise les informations à récupérer sur un champ de démontage.

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

## <a name="fields"></a>Champs
`DSF_ADDRESS`\
Initialiser/utiliser `bstrAddress` le champ.

`DSF_ADDRESSOFFSET`\
Initialiser/utiliser `bstrAddressOffset` le champ.

`DSF_CODEBYTES`\
Initialiser/utiliser `bstrCodeBytes` le champ.

`DSF_OPCODE`\
Initialiser/utiliser `bstrOpCode` le champ.

`DSF_OPERANDS`\
Initialiser/utiliser `bstrOperands` le champ.

`DSF_SYMBOL`\
Initialiser/utiliser `bstrSymbol` le champ.

`DSF_CODELOCATIONID`\
Initialiser/utiliser `uCodeLocationId` le champ.

`DSF_POSITION`\
Initialiser/utiliser `posBeg` les `posEnd` champs et les champs.

`DSF_DOCUMENTURL`\
Initialiser/utiliser `bstrDocumentUrl` le champ.

`DSF_BYTEOFFSET`\
Initialiser/utiliser `dwByteOffset` le champ.

`DSF_FLAGS`\
Initialiser/utiliser `dwFlags` le champ ([DISASSEMBLY_FLAGS).](../../../extensibility/debugger/reference/disassembly-flags.md)

`DSF_OPERANDS_SYMBOLS`\
Inclure des noms `bstrOperands` de symboles sur le terrain.

`DSF_ALL`\
Spécifie tous les champs pour le flux de démontage.

## <a name="remarks"></a>Notes
Passé comme paramètre à la méthode [Lire](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) pour indiquer quels champs de la structure [de démonmblyData](../../../extensibility/debugger/reference/disassemblydata.md) doivent être paralysés.

Utilisé pour `dwFields` le `DisassemblyData` membre de la structure pour indiquer quels champs sont utilisés et valides lorsque la structure est retournée.

Ces valeurs peuvent être combinées avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lire](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
