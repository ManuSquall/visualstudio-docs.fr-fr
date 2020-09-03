---
title: BUILT_TYPE | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737694"
---
# <a name="built_type"></a>BUILT_TYPE
Cette structure spécifie des informations sur un type de champ issu de métadonnées.

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
ID de l’application à partir de laquelle le symbole a été obtenu. Cela permet d’identifier de manière unique une instance de l’application.

`guidModule`\
GUID du module qui contient ce champ.

`pUnderlyingField`\
Objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) identifiant le champ sous-jacent associé à ce champ généré.

## <a name="remarks"></a>Notes
Cette structure apparaît dans le cadre de l’Union dans la structure [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) lorsque le `dwKind` champ de la `TYPE_INFO` structure a la valeur `TYPE_KIND_BUILT` (une valeur de l’énumération [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

## <a name="requirements"></a>Configuration requise
En-tête : SH. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
