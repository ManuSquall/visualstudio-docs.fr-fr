---
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11f56758f6cfd8219e11dad9bd88bfa88c50dbd6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310156"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface donne accès à une méthode qui peut créer un service de visualiseur, qui est utilisé pour gérer des tâches de visualiseur de type pour l’IDE.

## <a name="syntax"></a>Syntaxe

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Visual Studio implémente cette interface pour créer un objet de service de visualiseur, qui à son tour, est utilisé pour fournir l’ID de classe (`CLSID`s) de visualiseurs de type à l’IDE Visual Studio.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 L’évaluateur d’expression (EE) appelle [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable

|Méthode|Description|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crée le service de visualiseur|

## <a name="remarks"></a>Notes
 Le `IEEVisualizerServiceProvider` interface est obtenue au cours de l’implémentation de [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Le service de visualiseur qui crée cette interface est utilisé pour fournir des fonctionnalités à une [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) d’interface, c'est-à-dire le EE responsable de l’implémentation. Le EE est également chargé d’implémenter un [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interface qui permet des visualiseurs de type afficher et modifier la valeur d’une propriété.

 Consultez [visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d’informations sur la façon dont ces interfaces interagissent.

## <a name="requirements"></a>Configuration requise
 En-tête : ee.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)