---
title: IDebugBinder::GetMemoryContext Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d50126e26b836f7b53ee1abeb5c4988b74a2eed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735995"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Cette méthode convertit soit un emplacement d’objet, soit une adresse mémoire en contexte de mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Paramètres
`pField`\
[dans] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant l’objet à localiser. Si `NULL`, `dwConstant` puis utiliser à la place.

`dwConstant`\
[dans] Une adresse mémoire constante, comme 0x5000.

`ppMemCxt`\
[out] Retourne l’interface [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui représente l’adresse de l’objet, ou l’adresse en mémoire.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
