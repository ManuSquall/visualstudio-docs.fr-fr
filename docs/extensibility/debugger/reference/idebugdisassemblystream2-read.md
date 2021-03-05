---
description: Lit les instructions à partir de la position actuelle dans le flux de code machine.
title: 'IDebugDisassemblyStream2 :: Read | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b963bddc9d1ee04a6955b1110d73934b30196b21
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160197"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Lit les instructions à partir de la position actuelle dans le flux de code machine.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>Paramètres
`dwInstructions`\
dans Nombre d’instructions à désassembler. Cette valeur est également la longueur maximale du `prgDisassembly` tableau.

`dwFields`\
dans Combinaison d’indicateurs de l’énumération [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) qui indique les champs de `prgDisassembly` à remplir.

`pdwInstructionsRead`\
à Retourne le nombre d’instructions effectivement désassemblées.

`prgDisassembly`\
à Tableau de structures [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) qui est rempli avec le code désassemblé, une structure par instruction désassemblée. La longueur de ce tableau est dictée par le `dwInstructions` paramètre.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le nombre maximal d’instructions disponibles dans l’étendue actuelle peut être obtenu en appelant la méthode de la [méthode de recherche](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) .

 La position actuelle à partir de laquelle l’instruction suivante est lue peut être modifiée en appelant la méthode [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .

 L' `DSF_OPERANDS_SYMBOLS` indicateur peut être ajouté à l' `DSF_OPERANDS` indicateur dans le `dwFields` paramètre pour indiquer que les noms de symboles doivent être utilisés lors du désassemblage des instructions.

## <a name="see-also"></a>Voir aussi
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize,](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
