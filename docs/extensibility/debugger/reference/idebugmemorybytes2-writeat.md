---
title: 'IDebugMemoryBytes2 :: WriteAt | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727518"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Écrit le nombre spécifié d’octets de mémoire, en commençant à l’adresse spécifiée.

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
dans Objet [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui spécifie l’emplacement où commencer l’écriture des octets.

`dwCount`\
[in] Nombre d'octets à écrire.

`rgbMemory`\
dans Octets à écrire. Ce tableau est supposé avoir une taille d’au moins `dwCount` octets.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` si tous les octets n’ont pas pu être écrits ou retourne un code d’erreur (généralement `E_FAIL` ).

## <a name="remarks"></a>Notes
 Si l’adresse de départ n’est pas dans la fenêtre mémoire représentée par cet objet [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , aucun enregistrement n’est effectué et un code d’erreur de `E_FAIL` est retourné, même si la valeur d’écriture chevauche dans l’espace mémoire.

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
