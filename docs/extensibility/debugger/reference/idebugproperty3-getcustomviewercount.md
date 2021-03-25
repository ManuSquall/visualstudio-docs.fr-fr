---
description: Obtient le nombre de visionneuses personnalisées qui peuvent être disponibles pour cette propriété.
title: 'IDebugProperty3 :: GetCustomViewerCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7b74c1ae5a29b785de42295af3260f17655986c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064681"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Obtient le nombre de visionneuses personnalisées qui peuvent être disponibles pour cette propriété.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>Paramètres
`pcelt`\
à Nombre de visionneuses personnalisées disponibles pour cette propriété.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Pour prendre en charge les visualiseurs de type, cette méthode transfère l’appel à la méthode [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . Si l’évaluateur d’expression prend également en charge les visionneuses personnalisées pour le type de cette propriété, cette méthode ajoute le nombre de visionneuses personnalisées à la valeur retournée.

Pour plus d’informations sur les différences entre les visualiseurs de type et les visionneuses personnalisées, consultez [visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **CProperty** qui expose l’interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) .

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
