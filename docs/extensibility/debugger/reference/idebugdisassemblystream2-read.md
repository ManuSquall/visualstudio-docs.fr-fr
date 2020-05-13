---
title: IDebugDisassemblyStream2::Lire Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732098"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Lit les instructions à partir de la position actuelle dans le flux de démontage.

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
[dans] Le nombre d’instructions à démonter. Cette valeur est également la `prgDisassembly` longueur maximale de la gamme.

`dwFields`\
[dans] Une combinaison de drapeaux de [l’DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) énumération qui `prgDisassembly` indiquent quels champs de sont à remplir.

`pdwInstructionsRead`\
[out] Retourne le nombre d’instructions effectivement démontées.

`prgDisassembly`\
[out] Un éventail de structures [de démontageData](../../../extensibility/debugger/reference/disassemblydata.md) qui est rempli avec le code démonté, une structure par instruction démontée. La longueur de ce tableau `dwInstructions` est dictée par le paramètre.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le nombre maximal d’instructions disponibles dans la portée actuelle peut être obtenu en appelant la méthode [GetSize.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)

 La position actuelle d’où l’instruction suivante est lue peut être modifiée en appelant la méthode [Seek.](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)

 Le `DSF_OPERANDS_SYMBOLS` drapeau peut être `DSF_OPERANDS` ajouté `dwFields` au drapeau dans le paramètre pour indiquer que les noms des symboles doivent être utilisés lors du démontage des instructions.

## <a name="see-also"></a>Voir aussi
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
