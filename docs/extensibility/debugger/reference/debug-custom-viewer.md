---
title: DEBUG_CUSTOM_VIEWER Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3de9b8f7ef30cffbdd78399dc831060e413ba51b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737545"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Une structure qui identifie un visualiseur personnalisé ou un visualisateur de type.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Membres
`dwID`\
Un ID pour différencier plusieurs spectateurs `GUID`ou visualisateurs mis en œuvre par un .

`bstrMenuName`\
Le texte qui apparaîtra dans le menu de décrochage.

`bstrDescription`\
Une description du visualiseur personnalisé ou du visualisateur de type (doit être une valeur nulle si elle n’est pas utilisée).

`guidLang`\
Langue de l’évaluateur d’expression de fournir.

`guidVendor`\
Vendeur de l’évaluateur d’expression de fournir.

`bstrMetric`\
Mesure sous laquelle le visualiseur personnalisé ou le visualisateur de `CLSID` type est stocké.

## <a name="remarks"></a>Notes
Une liste de cette structure est retournée par un appel à la méthode [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (et, par extension, la méthode [GetCustomViewerList).](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
