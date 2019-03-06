---
title: IDebugProperty3::GetCustomViewerList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf31379f99c9cde8b0050b080797f3a4e70acea
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722731"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Obtient une liste des visionneuses personnalisées associées à cette propriété.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomViewerList(
    ULONG                celtSkip,
    ULONG                celtRequested,
    DEBUG_CUSTOM_VIEWER* rgViewers,
    ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
    uint                  celtSkip,
    uint                  celtRequested,
    DEBUG_CUSTOM_VIEWER[] rgViewers,
    out uint              pceltFetched
);
```

#### <a name="parameters"></a>Paramètres
`celtSkip`

 [in] Le nombre de visionneuses à ignorer.

`celtRequested`

 [in] Le nombre des visionneuses pour récupérer (spécifie également la taille de la `rgViewers` tableau).

`rgViewers`

 [in, out] Tableau de [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) structures doit être renseigné.

`pceltFetched`

 [out] Le nombre réel de visionneuses retourné.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
Pour prendre en charge les visualiseurs de type, cette méthode transfère l’appel à la [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) (méthode). Si l’évaluateur d’expression prend également en charge les visionneuses personnalisées pour ce type de propriété, cette méthode peut ajouter des visionneuses personnalisées appropriées à la liste.

Consultez [visualiseur de Type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) pour plus d’informations sur les différences entre les visualiseurs de type et les visionneuses personnalisées.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un **CProperty** objet qui expose le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface.

```cpp
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)
{
    if (NULL == prgViewers)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
