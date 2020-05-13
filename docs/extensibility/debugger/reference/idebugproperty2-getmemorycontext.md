---
title: IDebugProperty2::GetMemoryContext Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryContext
helpviewer_keywords:
- IDebugProperty2::GetMemoryContext
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8fa610af3ae00d30462c1a3a0c825e5a85722cdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721462"
---
# <a name="idebugproperty2getmemorycontext"></a>IDebugProperty2::GetMemoryContext
Obtient le contexte de mémoire de la valeur de la propriété.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext(
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>Paramètres
`ppMemory`\
[out] Retourne [l’objet IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui représente la mémoire associée à cette propriété.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; retourne autrement le code d’erreur. Retourne `S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT` s’il n’y a pas de contexte de mémoire à récupérer.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
