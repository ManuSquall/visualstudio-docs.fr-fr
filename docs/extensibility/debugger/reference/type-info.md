---
description: Cette structure spécifie différents genres d’informations sur le type d’un champ.
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b83c4a829a050b9e78b65a9a68be96d2397ea8c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070737"
---
# <a name="type_info"></a>TYPE_INFO
Cette structure spécifie différents genres d’informations sur le type d’un champ.

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
 Valeur de l’énumération [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) qui détermine comment interpréter l’Union.

 `type.typeMeta`\
 [C++ uniquement] Contient une structure [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) si `dwKind` est `TYPE_KIND_METADATA` .

 `type.typePdb`\
 [C++ uniquement] Contient une structure [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) si `dwKind` est `TYPE_KIND_PDB` .

 `type.typeBuilt`\
 [C++ uniquement] Contient une structure [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) si `dwKind` est `TYPE_KIND_BUILT` .

 `type.unused`\
 Remplissage inutilisé.

 `type`\
 Nom de l’Union.

 `unionmember`\
 [C# uniquement] Marshalez-le vers le type de structure approprié en fonction de `dwKind` .

## <a name="remarks"></a>Notes
 Cette structure est transmise à la méthode [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) où elle est remplie. La façon dont le contenu de la structure est interprété est basée sur le `dwKind` champ.

> [!NOTE]
> [C++ uniquement] Si est `dwKind` égal `TYPE_KIND_BUILT` à, il est nécessaire de libérer l’objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) sous-jacent lors de la destruction de la `TYPE_INFO` structure. Pour ce faire, il suffit d'appeler `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [C# uniquement] Le tableau suivant indique comment interpréter le `unionmember` membre pour chaque genre de type. L’exemple montre comment effectuer cette opération pour un genre de type.

|`dwKind`|`unionmember` interprété comme|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Exemple
 Cet exemple montre comment interpréter le `unionmember` membre de la `TYPE_INFO` structure en C#. Cet exemple illustre l’interprétation d’un seul type ( `TYPE_KIND_METADATA` ), mais les autres sont interprétés exactement de la même façon.

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
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
