---
title: IDebugMemoryContext2::Subtract Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c858beb8c3f9f587633dbae8b3b1fe73fd789663
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727435"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Soustrait la valeur spécifiée du contexte actuel et retourne un nouveau contexte.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Paramètres
`dwCount`\
[dans] Le nombre d’octets de mémoire à la décroissation.

`ppMemCxt`\
[out] Retourne un nouvel objet [IDebugMemoryContext2.](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un contexte de mémoire est une adresse, donc soustraire une valeur d’une adresse produit une nouvelle adresse qui nécessite une nouvelle interface contextuelle.

 Cette méthode doit toujours produire un nouveau contexte, même si l’adresse résultante est en dehors de l’espace de mémoire associé à ce contexte. La seule exception à cela est si aucune mémoire ne `ppMemCxt` peut être allouée pour le nouveau contexte ou si est une valeur nulle (qui est une erreur).

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
