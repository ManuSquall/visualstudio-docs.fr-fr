---
description: Spécifie le type de champ contenu dans un objet IDebugField.
title: FIELD_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 519b18f9e4b0329ded9b17ec0152f36e37377df0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150859"
---
# <a name="field_kind"></a>FIELD_KIND
Spécifie le type de champ contenu dans un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
typedef DWORD FIELD_KIND;
```

```csharp
public enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
```

## <a name="fields"></a>Champs
`FIELD_KIND_TYPE`\
Indique que le champ est un type uniquement.

`FIELD_KIND_SYMBOL`\
Indique que le champ est un symbole, avec le type, le nom et d’autres informations.

`FIELD_TYPE_PRIMITIVE`\
Indique que le champ est un type de données primitif.

`FIELD_TYPE_STRUCT`\
Indique que le champ est une structure.

`FIELD_TYPE_CLASS`\
Indique que le champ est une classe.

`FIELD_TYPE_INTERFACE`\
Indique que le champ est une interface.

`FIELD_TYPE_UNION`\
Indique que le champ est une Union.

`FIELD_TYPE_ARRAY`\
Indique que le champ est un tableau.

`FIELD_TYPE_METHOD`\
Indique que le champ est une méthode.

`FIELD_TYPE_BLOCK`\
Indique que le champ est un bloc.

`FIELD_TYPE_POINTER`\
Indique que le champ est un pointeur.

`FIELD_TYPE_ENUM`\
Indique que le champ est un type de données énuméré.

`FIELD_TYPE_LABEL`\
Indique que le champ est une étiquette.

`FIELD_TYPE_TYPEDEF`\
Indique que le champ est un typedef.

`FIELD_TYPE_BITFIELD`\
Indique que le champ est un champ de binaire.

`FIELD_TYPE_NAMESPACE`\
Indique que le champ est un espace de noms.

`FIELD_TYPE_MODULE`\
Indique que le champ est un module.

`FIELD_TYPE_DYNAMIC`\
Indique que le champ est dynamique.

`FIELD_TYPE_PROP`\
Indique que le champ est une propriété.

`FIELD_TYPE_INNERCLASS`\
Indique que le champ est une classe interne.

`FIELD_TYPE_REFERENCE`\
Indique que le champ est une référence.

`FIELD_TYPE_EXTENDED`\
Réservé pour un usage futur.

`FIELD_SYM_MEMBER`\
Indique que le champ est un membre.

`FIELD_SYM_LOCAL`\
Indique que le champ est local.

`FIELD_SYM_PARAMETER`\
Indique que le champ est un paramètre.

`FIELD_SYM_THIS`\
Indique que le champ est le pointeur « this ».

`FIELD_SYM_GLOBAL`\
Indique que le champ est global.

`FIELD_SYM_PROP_GETTER`\
Indique que le champ récupère les propriétés.

`FIELD_SYM_PROP_SETTER`\
Indique que le champ définit des propriétés.

`FIELD_SYM_EXTENDED`\
Réservé pour un usage futur.

`FIELD_KIND_MASK`\
Indique un masque pour les genres de champs.

`FIELD_TYPE_MASK`\
Indique un masque pour les types de champs.

`FIELD_SYM_MASK`\
Indique un masque pour les informations de symbole.

## <a name="remarks"></a>Notes
Retourné à partir d’un appel à la méthode [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) .

Selon le type de champ, [QueryInterface](/cpp/atl/queryinterface) peut être appelé sur l’interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) pour une forme d’interface plus spécifique. Par exemple, si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retourne `FIELD_TYPE_METHOD` , vous pouvez appeler `QueryInterface` sur I `DebugField` pour obtenir l’interface [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) .

## <a name="requirements"></a>Configuration requise
En-tête : SH. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
