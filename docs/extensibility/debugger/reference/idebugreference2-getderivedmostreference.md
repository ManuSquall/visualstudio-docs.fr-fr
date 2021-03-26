---
description: Obtient la référence la plus dérivée d’une référence.
title: 'IDebugReference2 :: GetDerivedMostReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c482b05620f280b2948aefe7e95eb38682268c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071439"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Obtient la référence la plus dérivée d’une référence. Réservé pour un usage futur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>Paramètres
`ppDerivedMost`\
à Retourne un objet [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) qui représente la propriété la plus dérivée.

## <a name="return-value"></a>Valeur renvoyée
 Retourne toujours `E_NOTIMPL`.

## <a name="remarks"></a>Notes
 Par exemple, si cette propriété décrit un objet qui implémente `ClassRoot` , mais qui est en fait une instanciation de `ClassDerived` qui est dérivée de `ClassRoot` , cette méthode retourne un objet [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) représentant une référence à l' `ClassDerived` objet.

## <a name="see-also"></a>Voir aussi
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
