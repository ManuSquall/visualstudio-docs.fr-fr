---
description: Structure qui identifie une visionneuse personnalisée ou un visualiseur de type.
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 76c02956acd9277f203c67bede7369d6bb7a603a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096276"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Structure qui identifie une visionneuse personnalisée ou un visualiseur de type.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Membres
`dwID`\
ID permettant de différencier plusieurs visionneuses ou visualiseurs implémentés par un `GUID` .

`bstrMenuName`\
Texte qui s’affichera dans le menu déroulant.

`bstrDescription`\
Description de la visionneuse personnalisée ou du visualiseur de type (doit être une valeur null si elle n’est pas utilisée).

`guidLang`\
Langue de l’évaluateur d’expression fournissant.

`guidVendor`\
Fournisseur de l’évaluateur d’expression fournissant.

`bstrMetric`\
Mesure sous laquelle la visionneuse personnalisée ou le visualiseur de type `CLSID` est stocké.

## <a name="remarks"></a>Notes
Une liste de cette structure est retournée par un appel à la méthode [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (et, par extension, la méthode [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) ).

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
