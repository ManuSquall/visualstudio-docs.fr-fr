---
title: IPropertyProxyProvider - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71d993c7f99cade5b866e67298132a325986e3a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714791"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Cette interface fournit une interface proxy pour afficher et modifier les données d’un objet.

## <a name="syntax"></a>Syntaxe

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression (EE) implémente cette interface sur le même objet qui implémente l’interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dans le cadre du support de l’EE des visualisateurs de type.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) `IDebugProperty3` sur une interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 L’interface `IPropertyProxyProvider` implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Récupère une interface proxy de propriété pour afficher les données sur un objet.|

## <a name="remarks"></a>Notes
 Bien que l’EE implémente cette interface, la mise en œuvre de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) est généralement gérée par [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Voir [Visualizing and Viewing Data](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus de détails sur l’obtention de l’interface IEEVisualizerService.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)
