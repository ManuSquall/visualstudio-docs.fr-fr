---
title: REFERENCE_TYPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ce6ad17aa32b98fd28914c422a49bd8bcc14b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713659"
---
# <a name="reference_type"></a>REFERENCE_TYPE
Spécifie le type de référence.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
typedef DWORD REFERENCE_TYPE;
```

```csharp
public enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
```

## <a name="fields"></a>Champs
 `REF_TYPE_WEAK`\
 Spécifie une référence faible. Impossible de `REF_TYPE_STRONG`combiner avec .

 `REF_TYPE_STRONG`\
 Spécifie une référence forte. Impossible de `REF_TYPE_WEAK`combiner avec .

## <a name="remarks"></a>Notes
 Utilisé comme `dwRefType` membre de la structure [DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md)

 Passé comme paramètre à la méthode [SetReferenceType.](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)
