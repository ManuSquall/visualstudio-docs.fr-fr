---
title: FIELD_MODIFIERS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7a24345174854462a2118df626223a8a299cd7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736855"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Spécifie les modificateurs pour un type de champ.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="fields"></a>Champs
`FIELD_MOD_ACCESS_TYPE`\
Indique que le champ ne peut pas être consulté.

`FIELD_MOD_ACCESS_PUBLIC`\
Indique que le champ a accès au public.

`FIELD_MOD_ACCESS_PROTECTED`\
Indique que le champ a un accès protégé.

`FIELD_MOD_ACCESS_PRIVATE`\
Indique que le champ a un accès privé.

`FIELD_MOD_NOMODIFIERS`\
Indique que le champ n’a pas de modificateurs.

`FIELD_MOD_STATIC`\
Indique que le champ est statique.

`FIELD_MOD_CONSTANT`\
Indique que le champ est une constante.

`FIELD_MOD_TRANSIENT`\
Indique que le champ est transitoire.

`FIELD_MOD_VOLATILE`\
Indique que le champ est volatil.

`FIELD_MOD_ABSTRACT`\
Indique que le champ est abstrait.

`FIELD_MOD_NATIVE`\
Indique que le champ est indigène.

`FIELD_MOD_SYNCHRONIZED`\
Indique que le champ est synchronisé.

`FIELD_MOD_VIRTUAL`\
Indique que le champ est virtuel.

`FIELD_MOD_INTERFACE`\
Indique que le champ est une interface.

`FIELD_MOD_FINAL`\
Indique que le champ est final.

`FIELD_MOD_SENTINEL`\
Indique que le champ est une sentinelle.

`FIELD_MOD_INNERCLASS`\
Indique que le champ est une classe intérieure.

`FIELD_TYPE_OPTIONAL`\
Indique que le champ est facultatif.

`FIELD_MOD_BYREF`\
Indique que le domaine est un argument de référence. C’est spécifiquement pour les arguments de méthode.

`FIELD_MOD_HIDDEN`\
Indique que le champ doit être caché ou présenté dans un autre contexte; par exemple, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] les habitants statiques.

`FIELD_MOD_MARSHALASOBJECT`\
Indique que le champ représente `IUnknown` un objet avec une interface.

`FIELD_MOD_SPECIAL_NAME`\
Indique que le champ a un `.ctor` nom spécial,[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] par exemple, pour un constructeur (seulement).

`FIELD_MOD_HIDEBYSIG`\
Indique que le `Overloads` champ a le[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] mot clé appliqué à elle (seulement).

`FIELD_MOD_WRITEONLY`\
Indique que le champ est écrit uniquement. Cette valeur n’est pas incluse dans `FIELD_MOD_ALL`, car la seule utilisation de ces champs d’écriture seulement est pour l’évaluation de la fonction. Un utilisateur doit `FIELD_MOD_WRITEONLY` demander explicitement des champs.

`FIELD_MOD_ACCESS_MASK`\
Indique un masque pour l’accès au champ.

`FIELD_MOD_MASK`\
Indique un masque pour les modificateurs de champ.

## <a name="remarks"></a>Notes
Utilisé pour `dwModifiers` le membre de la structure [FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md)

Ces valeurs sont également transmises à la méthode [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) pour filtrer pour des champs spécifiques.

## <a name="requirements"></a>Spécifications
En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
