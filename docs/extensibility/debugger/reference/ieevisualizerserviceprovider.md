---
title: IEEVisualizerServiceProvider ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44d8a73589a4248736ac6c4d73814166056a1f90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717889"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Cette interface donne accès à une méthode qui peut créer un service de visualisation, qui est utilisé pour gérer les tâches de visualisation de type pour l’IDE.

## <a name="syntax"></a>Syntaxe

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente cette interface pour créer un objet de service de`CLSID`visualisation, qui à son tour est utilisé pour fournir des ID de classe (s) de visualisations de type à l’IDE Visual Studio.

## <a name="notes-for-callers"></a>Notes pour les appelants
 L’évaluateur d’expression (EE) appelle [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable

|Méthode|Description|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crée le service de visualisation|

## <a name="remarks"></a>Notes
 L’interface `IEEVisualizerServiceProvider` est obtenue lors de la mise en œuvre de [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Le service de visualisation créé par cette interface est utilisé pour fournir des fonctionnalités à une interface [IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) que l’EE est responsable de la mise en œuvre. L’EE est également responsable de la mise en œuvre d’une interface [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) qui permet aux visualisateurs de type de visualiser et de modifier la valeur d’une propriété.

 Voir [Visualizing and Viewing Data](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus de détails sur la façon dont ces interfaces interagissent.

## <a name="requirements"></a>Spécifications
 En-tête: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)
