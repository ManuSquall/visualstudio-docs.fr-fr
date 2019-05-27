---
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8b93aa895588f743f4cc7c6b6adfa207590936d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210559"
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
[in] Le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objet qui spécifie l’emplacement où commencer la lecture des octets.

`dwCount`\
[in] Le nombre d’octets à lire. Spécifie également la longueur de la `rgbMemory` tableau.

`rgbMemory`\
[in, out] Tableau rempli avec les octets réellement lus.

`pdwRead`\
[out] Retourne le nombre d’octets contigus réellement lus.

`pdwUnreadable`\
[in, out] Retourne le nombre d’octets illisibles. Peut-être une valeur null si le client ne souhaite pas le nombre d’octets illisibles.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Si 100 octets sont demandés et les 50 premières sont lisibles, les 20 suivants sont illisibles, et le 30 restants sont lisibles, cette méthode retourne :

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 Dans ce cas, étant donné que `*pdwRead + *pdwUnreadable < dwCount`, l’appelant doit effectuer un appel supplémentaire à lire les octets restants 30 des 100 d’origine demandé et le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objet passé dans le `pStartContext` paramètre doit être avancé par 70.

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)