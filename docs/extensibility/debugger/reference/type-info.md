---
title: TYPE_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713327"
---
# <a name="type_info"></a>TYPE_INFO
Cette structure spécifie divers types d’informations sur le type d’un champ.

## <a name="syntax"></a>Syntaxe

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>Membres
 `dwKind`\
 Une valeur du [recensement dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) qui détermine comment interpréter le syndicat.

 `type.typeMeta`\
 [C seulement] Contient [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) une structure METADATA_TYPE `dwKind` `TYPE_KIND_METADATA`si elle est .

 `type.typePdb`\
 [C seulement] Contient une structure [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) `dwKind` si `TYPE_KIND_PDB`elle est .

 `type.typeBuilt`\
 [C seulement] Contient une structure [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) `dwKind` si `TYPE_KIND_BUILT`elle est .

 `type.unused`\
 Rembourrage inutilisé.

 `type`\
 Nom du syndicat.

 `unionmember`\
 [C seulement] Enchôte ceci au `dwKind`type de structure approprié basé sur .

## <a name="remarks"></a>Notes
 Cette structure est transmise à la méthode [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) où elle est remplie. La façon dont le contenu de `dwKind` la structure est interprété est basée sur le terrain.

> [!NOTE]
> [C seulement] Si `dwKind` elle `TYPE_KIND_BUILT`est égale, alors il est nécessaire de libérer l’objet sous-jacent [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) lors de la destruction de la `TYPE_INFO` structure. Pour ce faire, il suffit d'appeler `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [C seulement] Le tableau suivant montre `unionmember` comment interpréter le membre pour chaque type de type. L’exemple montre comment cela se fait pour un type de type.

|`dwKind`|`unionmember`interprété comme|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Exemple
 Cet exemple montre comment `unionmember` interpréter `TYPE_INFO` le membre de la structure dans le C. Cet exemple montre l’interprétation`TYPE_KIND_METADATA`d’un seul type () mais les autres sont interprétés exactement de la même manière.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
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
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo (en anglais)](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
