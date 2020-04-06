---
title: BUILT_TYPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 885f17b0841a39672c87be5bc7c947b2e0d9c7e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737694"
---
# <a name="built_type"></a>BUILT_TYPE
Cette structure spécifie des informations sur un type de terrain tiré des métadonnées.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Membres
`ulAppDomainID`\
ID de l’application à partir de laquelle le symbole est venu. Ceci est utilisé pour identifier de façon unique un exemple de l’application.

`guidModule`\
Le GUID du module qui contient ce champ.

`pUnderlyingField`\
Un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) identifiant le champ sous-jacent associé à ce champ construit.

## <a name="remarks"></a>Notes
Cette structure fait partie du [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) syndicat dans la structure `dwKind` TYPE_INFO `TYPE_INFO` lorsque le `TYPE_KIND_BUILT` champ de la structure est fixé à (une valeur de [l’dwTYPE_KIND’énumération).](../../../extensibility/debugger/reference/dwtype-kind.md)

## <a name="requirements"></a>Spécifications
En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
