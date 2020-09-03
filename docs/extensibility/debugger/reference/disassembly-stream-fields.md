---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737357"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Spécifie les informations à récupérer à propos d’un champ Code machine.

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
Initialiser/utiliser le `bstrAddress` champ.

`DSF_ADDRESSOFFSET`\
Initialiser/utiliser le `bstrAddressOffset` champ.

`DSF_CODEBYTES`\
Initialiser/utiliser le `bstrCodeBytes` champ.

`DSF_OPCODE`\
Initialiser/utiliser le `bstrOpCode` champ.

`DSF_OPERANDS`\
Initialiser/utiliser le `bstrOperands` champ.

`DSF_SYMBOL`\
Initialiser/utiliser le `bstrSymbol` champ.

`DSF_CODELOCATIONID`\
Initialiser/utiliser le `uCodeLocationId` champ.

`DSF_POSITION`\
Initialisez/utilisez les `posBeg` `posEnd` champs et.

`DSF_DOCUMENTURL`\
Initialiser/utiliser le `bstrDocumentUrl` champ.

`DSF_BYTEOFFSET`\
Initialiser/utiliser le `dwByteOffset` champ.

`DSF_FLAGS`\
Initialisez/utilisez le `dwFlags` champ ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).

`DSF_OPERANDS_SYMBOLS`\
Incluez les noms de symboles dans le `bstrOperands` champ.

`DSF_ALL`\
Spécifie tous les champs du flux de code machine.

## <a name="remarks"></a>Notes
Passé en tant que paramètre à la méthode [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) pour indiquer les champs de la structure [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) à initialiser.

Utilisé pour le `dwFields` membre de la `DisassemblyData` structure pour indiquer les champs qui sont utilisés et valides lorsque la structure est retournée.

Ces valeurs peuvent être combinées avec une opération de bits `OR` .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lire](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
