---
title: FIELD_MODIFIERS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b22559af26a0a5f6c8af68726a5ba336e1bcfb4a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689627"
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
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

## <a name="members"></a>Membres
FIELD_MOD_ACCESS_TYPE indique que le champ n’est pas accessible.

FIELD_MOD_ACCESS_PUBLIC indique que le champ possède un accès public.

FIELD_MOD_ACCESS_PROTECTED indique que le champ a un accès protégé.

FIELD_MOD_ACCESS_PRIVATE indique que le champ a un accès privé.

FIELD_MOD_NOMODIFIERS indique que le champ possède pas de modificateur.

FIELD_MOD_STATIC indique que le champ est statique.

FIELD_MOD_CONSTANT indique que le champ est une constante.

FIELD_MOD_TRANSIENT indique que le champ est temporaire.

FIELD_MOD_VOLATILE indique que le champ est volatil.

FIELD_MOD_ABSTRACT indique que le champ est abstrait.

FIELD_MOD_NATIVE indique que le champ est natif.

FIELD_MOD_SYNCHRONIZED indique que le champ doit être synchronisé.

FIELD_MOD_VIRTUAL indique que le champ est virtuel.

FIELD_MOD_INTERFACE indique que le champ est une interface.

FIELD_MOD_FINAL indique que le champ est définitive.

FIELD_MOD_SENTINEL indique que le champ est un objet sentinel.

FIELD_MOD_INNERCLASS indique que le champ est une classe interne.

FIELD_TYPE_OPTIONAL indique que le champ est facultatif.

FIELD_MOD_BYREF indique que le champ est un argument de référence. Il s’agit en particulier pour les arguments de méthode.

FIELD_MOD_HIDDEN indique que le champ doit être masqué ou présenté dans un autre contexte ; par exemple, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] variables locales statiques.

FIELD_MOD_MARSHALASOBJECT indique que le champ représente un objet avec un `IUnknown` interface.

FIELD_MOD_SPECIAL_NAME indique que le champ a un nom spécial, par exemple, `.ctor` pour un constructeur ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] uniquement).

FIELD_MOD_HIDEBYSIG indique que le champ a le `Overloads` mot clé appliqué à celui-ci ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] uniquement).

FIELD_MOD_WRITEONLY indique que le champ est en écriture seule. Cette valeur n’est pas incluse dans `FIELD_MOD_ALL`, comme l’utilisation seule de ces champs en écriture seule est pour l’évaluation de fonction. Un utilisateur doit demander explicitement `FIELD_MOD_WRITEONLY` champs.

FIELD_MOD_ACCESS_MASK indique un masque d’accès au champ.

FIELD_MOD_MASK indique un masque pour les modificateurs de champ.

## <a name="remarks"></a>Notes
Utilisé pour le `dwModifiers` membre de la [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) structure.

Ces valeurs sont également transmis à la [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) méthode pour filtrer les champs spécifiques.

## <a name="requirements"></a>Spécifications
En-tête : sh.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
