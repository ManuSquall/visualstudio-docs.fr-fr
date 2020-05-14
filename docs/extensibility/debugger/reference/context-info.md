---
title: CONTEXT_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4838df34c14b936af15b8a7a582a6d30ea12bee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737569"
---
# <a name="context_info"></a>CONTEXT_INFO
Cette structure décrit un contexte de mémoire ou un contexte de code.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Membres
`dwFields`\
Une combinaison de drapeaux de lui [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) énumération qui spécifie quels champs sont remplis<strong>.</strong>

`bstrModuleUrl`\
Le nom du module où se trouve le contexte.

`bstrFunction`\
Le nom de fonction où se trouve le contexte.

`posFunctionOffset`\
Une structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui identifie la ligne et la colonne offset de la fonction associée au contexte du code.

`bstrAddress`\
L’adresse dans le code où se trouve le contexte donné.

`bstrAddressOffset`\
La compensation de l’adresse dans le code où se trouve le contexte donné.

`bstrAddressAbsolute`\
L’adresse absolue dans la mémoire où se trouve le contexte donné.

## <a name="remarks"></a>Notes
Cette structure est revenue d’un appel à la méthode [GetInfo.](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)

Une utilisation typique pour cette structure est à l’appui d’une fenêtre de débogé de **mémoire.**

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
