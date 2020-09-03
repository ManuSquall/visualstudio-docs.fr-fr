---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737387"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Spécifie les informations à récupérer sur un objet de référence de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Champs
`DEBUGREF_INFO_NAME`\
Initialisez/utilisez le `bstrName` champ de la structure.

`DEBUGREF_INFO_TYPE`\
Initialisez/utilisez le `bstrType` champ de la structure.

`DEBUGREF_INFO_VALUE`\
Initialisez/utilisez le `bstrValue` champ de la structure.

`DEBUGREF_INFO_ATTRIB`\
Initialisez/utilisez le `dwAttrib` champ de la structure.

`DEBUGREF_INFO_REFTYPE`\
Initialisez/utilisez le `dwRefType` champ de la structure.

`DEBUGREF_INFO_REF`\
Initialisez/utilisez le `pReference` champ de la structure.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Le champ valeur doit contenir la valeur développée automatiquement, si elle est disponible, pour ce type d’objet.

`DEBUGREF_INFO_NONE`\
Indique qu’aucun indicateur n’est défini.

`DEBUGREF_INFO_ALL`\
Indique un masque des indicateurs.

## <a name="remarks"></a>Notes
Ces indicateurs sont passés aux méthodes [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) et [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) pour indiquer les champs de la structure [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) qui doivent être initialisés.

Utilisé pour le `dwFields` membre de la `DEBUG_REFERENCE_INFO` structure pour indiquer les champs qui sont utilisés et valides lorsque la structure est retournée.

Ces valeurs peuvent être combinées avec une opération de bits `OR` .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
