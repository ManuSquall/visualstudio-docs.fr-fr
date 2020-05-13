---
title: DEBUG_REFERENCE_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737418"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Décrit une référence.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>Membres
`dwFields`\
Une combinaison de drapeaux de [l’DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) énumération qui précise quels champs sont remplis.

`bstrName`\
Le nom spécifié par l’utilisateur de l’objet [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md)

`bstrType`\
Le type de référence comme une chaîne formatée.

`bstrValue`\
La valeur de référence en tant que chaîne formatée

`dwAttrib`\
Une combinaison de drapeaux de [l’énumération DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) qui spécifie les drapeaux pour les attributs de propriété de débogé.

`dwRefType`\
Une valeur du [recensement REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) qui précise si le type de référence est fort ou faible.

`m_pReference`\
Un objet [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) qui spécifie les informations de référence.

## <a name="remarks"></a>Notes
Cette structure est transmise à un appel à la méthode [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) à remplir. Cette structure est également retournée dans le cadre d’une liste de [l’interface IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) qui, à son tour, est retournée d’un appel à la méthode [EnumChildren.](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
