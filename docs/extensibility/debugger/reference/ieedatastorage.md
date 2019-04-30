---
title: IEEDataStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeb34d9574a6070b2d1f658575d345d74aa72972
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915250"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Cette interface représente un tableau d’octets.

## <a name="syntax"></a>Syntaxe

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 L’évaluateur d’expression (EE) implémente cette interface pour représenter un tableau d’octets (utilisé par les visualiseurs de type pour extraire et modifier des données via le [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface). En général, le EE implémente cette interface pour prendre en charge les visualiseurs de type externe.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Les méthodes sur le `IPropertyProxyEESide` interface tous les retourner cette interface. Appelez [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir le [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface. Appelez [QueryInterface](/cpp/atl/queryinterface) sur un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface pour obtenir le [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Le `IEEDataStorage` interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Récupère le nombre spécifié d’octets de données dans une mémoire tampon fournie.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Récupère le nombre d’octets de données disponibles.|

## <a name="remarks"></a>Notes
 Cette interface est utilisée par un visualiseur de type pour accéder aux données détenues par un objet spécifique. Les données sont traitées en tant que tableau d’octets, ce qui permet le visualiseur de type manipuler de façon est nécessaire pour présenter à l’utilisateur.

 Une visionneuse personnalisée peut également utiliser cette interface, si vous le souhaitez, bien qu’en règle générale, une visionneuse personnalisée utilisent une interface personnalisée, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ou [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (pour les données orientée sur la chaîne).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)