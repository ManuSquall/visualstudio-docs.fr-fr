---
title: IPropertyProxyEESide - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89cecbf22091a45e31c307c5b523ac8aa4c924e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714858"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Cette interface fournit des méthodes pour afficher les données sur l’objet associé. Cette interface fait partie du support pour les visualisateurs de type.

## <a name="syntax"></a>Syntaxe

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un évaluateur d’expression implémente cette interface pour prendre en charge les visualisateurs de type.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir cette interface. Appelez [QueryInterface](/cpp/atl/queryinterface) sur une interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) pour obtenir l’interface [IPropertyProxyProvider.](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Les méthodes suivantes sont mises en œuvre par cette interface :

|Méthode|Description|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Initialise un fournisseur de source de données afin que les données de l’objet puissent être consultées.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Récupère des informations sur l’assemblage de l’objet.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Obtient les données initiales pour l’objet.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Crée une copie d’un stockage de données existant.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Crée une référence à un stockage de données existant.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Récupère des informations sur un assemblage spécifique dans le cadre de l’assemblage contenant cet objet.|

## <a name="remarks"></a>Notes
 Un visualisateur de type utilise cette interface pour accéder aux valeurs associées à l’objet dont cette interface fait partie. Les données sont accessibles via l’interface [IEEDataStorage,](../../../extensibility/debugger/reference/ieedatastorage.md) qui fournit une vue de lecture uniquement des données.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
