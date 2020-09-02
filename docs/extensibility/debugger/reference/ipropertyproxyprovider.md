---
title: IPropertyProxyProvider | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714791"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Cette interface fournit une interface de proxy permettant d’afficher et de modifier les données d’un objet.

## <a name="syntax"></a>Syntaxe

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression (EE) implémente cette interface sur le même objet qui implémente l’interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dans le cadre de la prise en charge par EE des visualiseurs de type.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur une `IDebugProperty3` interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable
 L' `IPropertyProxyProvider` interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Récupère une interface de proxy de propriété pour afficher les données sur un objet.|

## <a name="remarks"></a>Notes
 Bien que l’EE implémente cette interface, l’implémentation de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) est généralement gérée par [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Pour plus d’informations sur l’obtention de l’interface IEEVisualizerService [, consultez visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)
