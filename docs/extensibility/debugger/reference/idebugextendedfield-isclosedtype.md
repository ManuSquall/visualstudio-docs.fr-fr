---
title: IDebugExtendedField::IsClosedType (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4524d7c899480518e669f1f77a4756a83e0cf52f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729050"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Détermine si le champ représente un type fermé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Valeur de retour
 Si le champ est un `S_OK`type fermé, retourne; autrement, `S_FALSE`les retours .

## <a name="see-also"></a>Voir aussi
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
