---
description: Obtient le contexte de mémoire qui représente l’adresse de la valeur de l’objet.
title: 'IDebugObject :: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54df34a989d56ac9c1a962943eeda172c90e5554
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081852"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Obtient le contexte de mémoire qui représente l’adresse de la valeur de l’objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMemoryContext( 
   IDebugMemoryContext2** pContext
);
```

```csharp
int GetMemoryContext(
   ref IDebugMemoryContext2 pContext
);
```

## <a name="parameters"></a>Paramètres
`pContext`\
à Retourne un objet [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui représente l’adresse de la valeur de l’objet.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le contexte de mémoire retourné spécifie l’adresse de la valeur telle qu’elle est représentée par cet objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
