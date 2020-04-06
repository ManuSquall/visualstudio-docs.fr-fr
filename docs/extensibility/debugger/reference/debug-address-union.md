---
title: DEBUG_ADDRESS_UNION Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737527"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Décrit différents types d’adresses.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Membres
`dwKind`\
Une valeur de [l’énumération ADDRESS_KIND,](../../../extensibility/debugger/reference/address-kind.md) précisant comment interpréter le syndicat.

`addr.addrNative`\
[C seulement] Contient [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) la structure NATIVE_ADDRESS `dwKind` si ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[C seulement] Contient la structure[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) `dwKind` si ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[C seulement] Contient la structure[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) `dwKind` si ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[C seulement] Contient[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) la structure METADATA_ADDRESS_METHOD `dwKind` si ADDRESS_KIND_METHOD.

`addr.addrField`\
[C seulement] Contient la structure[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) `dwKind` si ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[C seulement] Contient la structure[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) `dwKind` si ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[C seulement] Contient la structure[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) `dwKind` si ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[C seulement] Contient la structure[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) `dwKind` si ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[C seulement] Contient la structure[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) `dwKind` si ADDRESS_KIND_RETVAL.

`addr.unused`\
Rembourrage [Cmd seulement].

`addr`\
[C seulement] Le nom du syndicat.

`unionmember`\
[C seulement] Cette valeur doit être consacrée au type `dwKind`de structure approprié basé sur . Voir Remarques pour `dwKind` l’association entre et interprétation du syndicat.

## <a name="remarks"></a>Notes
Cette structure fait partie de la structure [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) et représente l’un `DEBUG_ADDRESS` des différents types d’adresses (la structure est remplie par un appel à la méthode [GetAddress).](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)

 [C seulement] Le tableau suivant montre `unionmember` comment interpréter le membre pour chaque type d’adresse. L’exemple montre comment cela se fait pour un type d’adresse.

|`dwKind`|`unionmember`interprété comme|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Exemple
Cet exemple montre comment interpréter un`METADATA_ADDRESS_ARRAYELEM`type `DEBUG_ADDRESS_UNION` d’adresse () de la structure dans le C. Les éléments restants peuvent être interprétés exactement de la même manière.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>Spécifications
En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
