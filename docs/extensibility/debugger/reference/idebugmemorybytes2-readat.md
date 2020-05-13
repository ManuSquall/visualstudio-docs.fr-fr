---
title: IDebugMemoryBytes2::ReadAt Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727537"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Lit une séquence d’octets, à partir d’un endroit donné.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>Paramètres
`pStartContext`\
[dans] [L’objet IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui spécifie par où commencer à lire les octets.

`dwCount`\
[dans] Le nombre d’octets à lire. Spécifie également `rgbMemory` la longueur du tableau.

`rgbMemory`\
[dans, dehors] Array rempli avec les octets effectivement lu.

`pdwRead`\
[out] Retourne le nombre d’octets contigus effectivement lu.

`pdwUnreadable`\
[dans, dehors] Retourne le nombre d’octets illisibles. Peut être une valeur nulle si le client n’est pas intéressé par le nombre d’octets illisibles.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Si 100 octets sont demandés et que les 50 premiers sont lisibles, les 20 suivants sont illisibles, et les 30 autres sont lisibles, cette méthode revient :

 *`pdwRead`50 euros

 *`pdwUnreadable`20 euros

 Dans ce cas, parce que `*pdwRead + *pdwUnreadable < dwCount`, l’appelant doit faire un appel supplémentaire pour lire les 30 octets restants des 100 originaux demandés et [l’objet IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) passé dans le `pStartContext` paramètre doit être avancé par 70.

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
