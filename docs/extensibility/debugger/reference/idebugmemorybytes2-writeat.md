---
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4e23ec439e352f6aa4e3b4d307bea76ebfdcf00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918792"
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

#### <a name="parameters"></a>Paramètres
 `pStartContext`

 [in] Le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objet qui spécifie l’emplacement où commencer l’écriture d’octets.

 `dwCount`

 [in] Le nombre d’octets à écrire.

 `rgbMemory`

 [in] Octets à écrire. Ce tableau est censé pour être au moins `dwCount` octets de taille.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` si tous les octets peut être écrite ou retourne un code d’erreur (généralement `E_FAIL`).

## <a name="remarks"></a>Notes
 Si l’adresse de départ n’est pas dans la fenêtre mémoire représentée par ce [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) de l’objet, aucune écriture ne se produit et le code d’erreur `E_FAIL` est retourné, même si la quantité pour écrire des chevauchements dans l’espace de mémoire.

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)