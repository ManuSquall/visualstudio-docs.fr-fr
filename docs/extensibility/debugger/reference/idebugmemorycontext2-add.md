---
title: IDebugMemoryContext2::Ajouter Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a21fa2ec6d48bb1d6bf17bbc0d2ebf0d90a25a9f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727484"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Ajoute la valeur spécifiée au contexte actuel et retourne un nouveau contexte.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Paramètres
`dwCount`\
[dans] La valeur à ajouter au contexte actuel.

`ppMemCxt`\
[out] Retourne un nouvel objet [IDebugMemoryContext2.](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un contexte de mémoire est une adresse, donc ajouter une valeur à une adresse produit une nouvelle adresse qui nécessite une nouvelle interface contextuelle.

 Cette méthode doit toujours produire un nouveau contexte, même si l’adresse résultante est en dehors de l’espace de mémoire associé à ce contexte. La seule exception à cela est si aucune mémoire ne `ppMemCxt` peut être allouée pour le nouveau contexte ou si est une valeur nulle (qui est une erreur).

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
