---
title: IDebugGenericFieldInstance::TypeArgumentCount (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f0272e86f5c1bbbd840ee222b2048440338302d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728156"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Retourne le nombre d’arguments de paramètres de type pour cette instance.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

## <a name="parameters"></a>Paramètres
`pcArgs`\
[dans, dehors] Nombre d’arguments de paramètres de type pour cette instance.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Par exemple,\<si Liste int>, cette méthode renvoie\<1, et, si Liste int,float2> cette méthode renvoie 2. Cette méthode renvoie 0 s’il n’y a pas d’arguments de type.

## <a name="see-also"></a>Voir aussi
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
