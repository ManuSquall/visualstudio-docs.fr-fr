---
title: IEEVisualizerDataProvider ( Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718055"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Cette interface permet de modifier la valeur d’un objet grâce à un visualiseur de type.

## <a name="syntax"></a>Syntaxe

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression implémente cette interface pour prendre en charge la modification des données sur un objet de propriété par le biais d’un visualiseur de type.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est utilisée dans la création de [l’objet IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) par le biais d’un appel à [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Voir [Visualizing and Viewing Data](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus de détails.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable

|Méthode|Description|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Détermine s’il est possible de mettre à jour l’objet (et par la suite, sa valeur) que représente ce visualisateur.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Force une réévaluation de l’objet pour ce visualiseur.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtient un objet existant pour ce visualiseur (aucune évaluation n’est faite).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Mise à jour de l’objet pour ce visualiseur, changeant ainsi la valeur du visualiseur présente.|

## <a name="remarks"></a>Notes
 Le service de visualisation (représenté par [l’interface IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) et retourné par [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) conserve une référence à l’objet implémentant l’interface. `IEEVisualizerDataProvider` En conséquence, `IEEVisualizerDataProvider` l’interface ne doit pas être implémentée sur le même objet qui implémente [l’IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) si cet objet maintient une référence à l’objet `IEEVisualizerService` : une référence circulaire résulte et une impasse se produit lorsque les objets sont détruits. L’approche recommandée `IEEVisualizerDataProvider` consiste à mettre en `IDebugProperty2` œuvre `IUnknown::AddRef` sur un objet distinct auquel l’objet délègue sans en faire appel.

## <a name="requirements"></a>Spécifications
 En-tête: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)
