---
title: IDebugPrimitiveTypeField::GetPrimitiveType (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetPrimitiveType
- IDebugPrimitiveTypeField::GetPrimitiveType
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a66c7c2e312795fa4303c8702e70cd509536de98
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724281"
---
# <a name="idebugprimitivetypefieldgetprimitivetype"></a>IDebugPrimitiveTypeField::GetPrimitiveType
Récupère le type primitif qui est associé à ce champ.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPrimitiveType (
   DWORD* pdwType
);
```

```csharp
int GetPrimitiveType (
   out uint pdwType
);
```

## <a name="parameters"></a>Paramètres
`pdwType`\
[out] Valeur de [l’énumération CorElementType](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) qui représente le type primitif.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, `S_FALSE`les retours .

## <a name="see-also"></a>Voir aussi
- [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)
