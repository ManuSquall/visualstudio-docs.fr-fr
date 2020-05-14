---
title: IDebugMemoryBytes2::WriteAt Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727518"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Écrit le nombre spécifié d’octets de mémoire, à partir de l’adresse spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Paramètres
`pStartContext`\
[dans] [L’objet IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui spécifie par où commencer à écrire des octets.

`dwCount`\
[in] Nombre d'octets à écrire.

`rgbMemory`\
[dans] Les octets à écrire. Ce tableau est supposé `dwCount` être au moins des octets de taille.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, `S_FALSE` les retours, sinon tous les octets, `E_FAIL`peuvent être écrits ou renvoient un code d’erreur (généralement ).

## <a name="remarks"></a>Notes
 Si l’adresse de départ n’est pas dans la fenêtre de mémoire représentée par cet objet `E_FAIL` [IDebugMemoryBytes2,](../../../extensibility/debugger/reference/idebugmemorybytes2.md) aucune écriture ne se produit et un code d’erreur de est retourné - même si la quantité d’écrire se chevauche dans l’espace de mémoire.

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
