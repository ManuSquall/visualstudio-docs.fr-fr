---
title: ADDRESS_KIND Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1298df79bbe34b240d6e7b186f42e20b3d1a89de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738148"
---
# <a name="address_kind"></a>ADDRESS_KIND
Spécifie le genre d’adresses.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>Champs
`ADDRESS_KIND_NATIVE`\
Une adresse native, représentée par la [structure NATIVE_ADDRESS.](../../../extensibility/debugger/reference/native-address.md)

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Une adresse non gestion par `this` `Me` rapport à un pointeur (dans Visual Basic) et représentée par la structure [UNMANAGED_ADDRESS_THIS_RELATIVE.](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
Une adresse physique non gémanie, représentée par la structure [UNMANAGED_ADDRESS_PHYSICAL.](../../../extensibility/debugger/reference/unmanaged-address-physical.md)

`ADDRESS_KIND_METHOD`\
Une méthode de classe, représentée par la [structure METADATA_ADDRESS_METHOD.](../../../extensibility/debugger/reference/metadata-address-method.md)

`ADDRESS_KIND_FIELD`\
Un champ de classe, représenté par la structure [METADATA_ADDRESS_FIELD.](../../../extensibility/debugger/reference/metadata-address-field.md)

`ADDRESS_KIND_LOCAL`\
L’adresse est pour une variable locale et est représentée par la structure [METADATA_ADDRESS_LOCAL.](../../../extensibility/debugger/reference/metadata-address-local.md)

`ADDRESS_KIND_PARAM`\
Une méthode ou un paramètre de fonction, représenté par la structure [METADATA_ADDRESS_PARAM.](../../../extensibility/debugger/reference/metadata-address-param.md)

`ADDRESS_KIND_ARRAYELEM`\
Un élément de tableau, représenté par la structure [METADATA_ADDRESS_ARRAYELEM.](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)

`ADDRESS_KIND_RETVAL`\
Une valeur de retour, représentée par la structure [METADATA_ADDRESS_RETVAL.](../../../extensibility/debugger/reference/metadata-address-retval.md)

## <a name="remarks"></a>Notes
La méthode [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) renvoie la structure [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) qui contient une union de structures possibles, la structure [DEBUG_ADDRESS_UNION.](../../../extensibility/debugger/reference/debug-address-union.md) Le `dwKind` domaine `DEBUG_ADDRESS_UNION` de la `ADDRESS_KIND` structure détient la valeur et décrit comment interpréter le champ syndical.

## <a name="requirements"></a>Spécifications
En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
