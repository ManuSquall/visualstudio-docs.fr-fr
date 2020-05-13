---
title: IDebugMemoryContext2::Compare Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727489"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Compare le contexte de mémoire à chaque contexte dans le tableau donné de la manière indiquée par la comparaison des drapeaux, en retournant un index du premier contexte qui correspond.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>Paramètres
`compare`\
[dans] Une valeur de [l’énumération CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) qui détermine le type de comparaison.

`rgpMemoryContextSet`\
[dans] Un éventail de références aux objets [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) à comparer.

`dwMemoryContextSetLen`\
[dans] Le nombre de contextes dans le `rgpMemoryContextSet` tableau.

`pdwMemoryContext`\
[out] Retourne l’index du premier contexte de mémoire qui satisfait la comparaison.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retours `E_COMPARE_CANNOT_COMPARE` si les deux contextes ne peuvent pas être comparés.

## <a name="remarks"></a>Notes
 Un moteur de débogé (DE) n’a pas à soutenir tous `CONTEXT_EQUAL` `CONTEXT_LESS_THAN`les `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE`types de comparaisons, mais il doit prendre en charge au moins , , et .

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
