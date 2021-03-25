---
description: Sélectionne différents types de constructeurs.
title: CONSTRUCTOR_ENUM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7f58dd088b37d3f1a404677c6c76bb09160b438
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067593"
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
Sélectionne des constructeurs non statiques.

`crStatic`\
Sélectionne des constructeurs statiques.

## <a name="remarks"></a>Notes
Passé comme argument à la méthode [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) .

## <a name="requirements"></a>Spécifications
En-tête : SH. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
