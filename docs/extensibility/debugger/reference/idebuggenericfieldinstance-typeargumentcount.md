---
title: 'IDebugGenericFieldInstance :: TypeArgumentCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b811780bf135a700f0ea451ef148598fe621e4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928352"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Retourne le nombre d’arguments de paramètre de type pour cette instance.

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
[in, out] Nombre d’arguments de paramètre de type pour cette instance.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Par exemple, si liste \<int> , cette méthode retourne 1, et, si \<int,float2> cette méthode retourne la valeur 2. Cette méthode retourne 0 s’il n’y a pas d’arguments de type.

## <a name="see-also"></a>Voir aussi
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
