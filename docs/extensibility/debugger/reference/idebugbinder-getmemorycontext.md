---
description: Cette méthode convertit un emplacement de l’objet ou une adresse mémoire en un contexte de mémoire.
title: 'IDebugBinder :: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a9fe7c0ee2d7902d24df1bdea773b4b2745a96f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067450"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Cette méthode convertit un emplacement de l’objet ou une adresse mémoire en un contexte de mémoire.

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
dans [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant l’objet à rechercher. Si `NULL` , utilisez à la `dwConstant` place.

`dwConstant`\
dans Adresse mémoire constante, telle que 0x5000.

`ppMemCxt`\
à Retourne l’interface [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui représente l’adresse de l’objet ou l’adresse en mémoire.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
