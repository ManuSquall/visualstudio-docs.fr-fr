---
title: FIELD_KIND_EX Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0c13d83f80b311838eca32945462c1f17ca23f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736878"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
Énumère d’autres types de champs qu’un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) peut contenir. Cette énumération prolonge [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) le FIELD_KIND’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
typedef DWORD FIELD_KIND_EX;
```

```csharp
public enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
```

## <a name="fields"></a>Champs
`FIELD_KIND_EX_NONE`\
Le champ ne contient pas un type étendu.

`FIELD_TYPE_EX_METHODVAR`\
Le champ contient une variable de méthode.

`FIELD_TYPE_EX_CLASSVAR`\
Field contient une variable de classe.

## <a name="requirements"></a>Spécifications
En-tête: Sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
