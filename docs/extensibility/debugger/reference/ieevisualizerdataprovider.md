---
title: IEEVisualizerDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718055"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface offre la possibilité de modifier la valeur d’un objet via un visualiseur de type.

## <a name="syntax"></a>Syntaxe

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression implémente cette interface pour prendre en charge la modification des données sur un objet de propriété via un visualiseur de type.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est utilisée pour créer l’objet [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) via un appel à [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Pour plus d’informations [, consultez visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable

|Méthode|Description|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Détermine s’il est possible de mettre à jour l’objet (et par la suite, sa valeur) que ce visualiseur représente.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Force une réévaluation de l’objet pour ce visualiseur.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtient un objet existant pour ce visualiseur (aucune évaluation n’est effectuée).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Met à jour l’objet pour ce visualiseur, en modifiant ainsi la valeur présente dans le visualiseur.|

## <a name="remarks"></a>Notes
 Le service du visualiseur (tel qu’il est représenté par l’interface [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) et retourné par [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) conserve une référence à l’objet qui implémente l' `IEEVisualizerDataProvider` interface. Par conséquent, l' `IEEVisualizerDataProvider` interface ne doit pas être implémentée sur le même objet qui implémente le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) si cet objet gère une référence à l' `IEEVisualizerService` objet : une référence circulaire se produit et un interblocage se produit lorsque les objets sont détruits. L’approche recommandée consiste à implémenter `IEEVisualizerDataProvider` sur un objet distinct auquel l' `IDebugProperty2` objet délègue sans appeler `IUnknown::AddRef` dessus.

## <a name="requirements"></a>Configuration requise
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)
