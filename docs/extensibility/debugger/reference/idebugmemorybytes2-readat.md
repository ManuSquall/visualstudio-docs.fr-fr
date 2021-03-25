---
description: Lit une séquence d’octets, en commençant à un emplacement donné.
title: 'IDebugMemoryBytes2 :: readatum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1fdcdf46f7f57f3ee6035bf9af8be5a7e99739f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076821"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Lit une séquence d’octets, en commençant à un emplacement donné.

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
dans Objet [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui spécifie où commencer la lecture des octets.

`dwCount`\
dans Nombre d’octets à lire. Spécifie également la longueur du `rgbMemory` tableau.

`rgbMemory`\
[in, out] Tableau rempli avec les octets réellement lus.

`pdwRead`\
à Retourne le nombre d’octets contigus réellement lus.

`pdwUnreadable`\
[in, out] Retourne le nombre d’octets illisibles. Peut être une valeur null si le client n’est pas intéressé par le nombre d’octets illisibles.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Si 100 octets sont demandés et que les 50 premiers sont lisibles, les 20 suivants sont illisibles et les 30 restants sont lisibles, cette méthode retourne :

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 Dans ce cas, comme `*pdwRead + *pdwUnreadable < dwCount` , l’appelant doit effectuer un appel supplémentaire pour lire les 30 octets restants du 100 d’origine demandé et l’objet [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) passé dans le `pStartContext` paramètre doit être avancé par 70.

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
