---
title: IEnumDebugFrameInfo2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::Skip
helpviewer_keywords:
- IEnumDebugFrameInfo2::Skip
ms.assetid: 68cd3948-022a-41ad-bd9f-9ab776cf6248
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95df5a3939256c8b4c4b7ff80cb9d0f0dc483e24
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696673"
---
# <a name="ienumdebugframeinfo2skip"></a>IEnumDebugFrameInfo2::Skip
Ignore le nombre spécifié d’éléments.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

#### <a name="parameters"></a>Paramètres
 `celt`

 [in] Nombre d’éléments à ignorer.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si `celt` est supérieur au nombre d’éléments restants ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Si `celt` spécifie une valeur supérieure au nombre d’éléments restants, l’énumération est définie à la fin et `S_FALSE` est retourné.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)