---
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae5c7e1916c77e3743de63df8903e62feea4fe28
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327323"
---
# <a name="builttype"></a>BUILT_TYPE
Cette structure spécifie des informations sur un type de champ extraites à partir des métadonnées.

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
ID de l’application d'où provenance le symbole. Cela est utilisé pour identifier de manière unique une instance de l’application.

`guidModule`\
Le GUID du module qui contient ce champ.

`pUnderlyingField`\
Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet identifiant le champ sous-jacent associé à ce champ généré.

## <a name="remarks"></a>Notes
Cette structure apparaît dans le cadre de l’union dans le [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) structure lorsque le `dwKind` champ la `TYPE_INFO` structure est définie sur `TYPE_KIND_BUILT` (une valeur comprise entre le [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) énumération).

## <a name="requirements"></a>Configuration requise
En-tête : sh.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
