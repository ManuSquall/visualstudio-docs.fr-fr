---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 86212a5ef6f417dae2ae345b1367e041c3cf9095
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316129"
---
# <a name="typeinfo"></a>TYPE_INFO
Cette structure spécifie plusieurs types d’informations sur un type de champ.

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
 Une valeur comprise entre le [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) énumération qui détermine l’interprétation de l’union.

 `type.typeMeta`\
 [C++ uniquement] Contient un [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) structure si `dwKind` est `TYPE_KIND_METADATA`.

 `type.typePdb`\
 [C++ uniquement] Contient un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) structure si `dwKind` est `TYPE_KIND_PDB`.

 `type.typeBuilt`\
 [C++ uniquement] Contient un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) structure si `dwKind` est `TYPE_KIND_BUILT`.

 `type.unused`\
 Remplissage inutilisé.

 `type`\
 Nom de l’union.

 `unionmember`\
 [C# uniquement] Cette option pour le type de structure appropriée en fonction de marshaler `dwKind`.

## <a name="remarks"></a>Notes
 Cette structure est passée à la [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) méthode où il est renseigné. Comment le contenu de la structure est interprété selon le `dwKind` champ.

> [!NOTE]
> [C++ uniquement] Si `dwKind` est égal à `TYPE_KIND_BUILT`, il est nécessaire pour libérer des sous-jacent [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) lors de la destruction de l’objet le `TYPE_INFO` structure. Pour ce faire, il suffit d'appeler `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [C# uniquement] Le tableau suivant indique comment interpréter le `unionmember` membre pour chaque genre de type. L’exemple montre comment procéder pour un seul type de type.

|`dwKind`|`unionmember` interprété en tant que|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Exemple
 Cet exemple montre comment interpréter le `unionmember` membre de la `TYPE_INFO` structure en c#. Cet exemple montre l’interprétation qu’un seul type (`TYPE_KIND_METADATA`), mais les autres sont interprétées de la même façon.

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
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)