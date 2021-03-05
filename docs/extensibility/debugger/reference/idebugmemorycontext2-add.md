---
description: Ajoute la valeur spécifiée au contexte actuel et retourne un nouveau contexte.
title: 'IDebugMemoryContext2 :: Add | Microsoft Docs'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59daddd38daff2f04f12bc0d1be4e06ec90cf723
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166422"
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
dans Valeur à ajouter au contexte actuel.

`ppMemCxt`\
à Retourne un nouvel objet [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Comme un contexte de mémoire est une adresse, l’ajout d’une valeur à une adresse produit une nouvelle adresse qui requiert une nouvelle interface de contexte.

 Cette méthode doit toujours produire un nouveau contexte, même si l’adresse résultante est en dehors de l’espace mémoire associé à ce contexte. La seule exception est si aucune mémoire ne peut être allouée pour le nouveau contexte ou si `ppMemCxt` est une valeur null (qui est une erreur).

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
