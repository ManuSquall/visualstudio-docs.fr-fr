---
title: CONSTRUCTOR_ENUM Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f9e123399ed2378eaf63944f9a1527ef024c0cd6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737616"
---
# <a name="constructor_enum"></a>CONSTRUCTOR_ENUM
Sélectionne différents types de constructeurs.

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
} CONSTRUCTOR_ENUM;
```

```csharp
public enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
};
```

## <a name="fields"></a>Champs
`crAll`\
Sélectionne tous les constructeurs.

`crNonStatic`\
Sélectionne les constructeurs non statiques.

`crStatic`\
Sélectionne les constructeurs statiques.

## <a name="remarks"></a>Notes
Passé comme argument à la méthode [EnumConstructors.](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)

## <a name="requirements"></a>Spécifications
En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
