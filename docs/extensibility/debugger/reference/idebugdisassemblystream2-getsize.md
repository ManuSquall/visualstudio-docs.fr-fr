---
title: IDebugDisassemblyStream2::GetSize Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75fa12b1e9e70601626667dd3707f1e230f5de0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732105"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Obtient la taille dans les instructions de ce flux démonté.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>Paramètres
`pnSize`\
[out] Retourne la taille, dans les instructions.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 La valeur retournée de cette méthode peut être utilisée pour allouer un éventail de structures [de disassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) qui est ensuite transmise à la méthode [Lire.](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)

## <a name="see-also"></a>Voir aussi
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lire](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
