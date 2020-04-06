---
title: DEBUG_PROPERTY_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34fc1b5103949a767a3ee448618cbb708ea6a48b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737452"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
Contient des informations sur une propriété de débogé.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>Membres
`dwValidFields`\
Une combinaison de drapeaux de [l’DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) énumération qui précise quels champs sont remplis.

`bstrFullName`\
Le nom complet de la propriété.

`bstrName`\
Le nom de la propriété dans un contexte.

`bstrType`\
Le type de propriété comme une chaîne formatée.

`bstrValue`\
La valeur de la propriété comme une chaîne formatée.

`pProperty`\
[L’objet IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) décrit par cette structure.

`dwAttrib`\
Une combinaison de drapeaux de [l’DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) énumération décrivant les attributs de cette propriété.

## <a name="remarks"></a>Notes
Une propriété est un objet de nature hiérarchique qui a un nom, un type et une valeur. Par exemple, une propriété peut décrire les variables, les paramètres, les variables et les expressions de surveillance locales et les registres.

Cette structure est transmise à la méthode [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) où elle est remplie. Cette structure est également retournée dans le cadre d’une liste de cette structure de [l’interface IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) qui, à son tour, est retourné d’un appel aux méthodes [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) et [EnumProperties.](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo (en anglais)](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
