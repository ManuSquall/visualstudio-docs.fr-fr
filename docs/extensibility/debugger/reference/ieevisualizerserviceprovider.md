---
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40e811d33d23b35553ffb23338bed19dc207e1e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907800"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface donne accès à une méthode qui peut créer un service de visualiseur, qui est utilisé pour gérer les tâches de visualiseur de type pour l’IDE.

## <a name="syntax"></a>Syntaxe

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente cette interface pour créer un objet de service du visualiseur, qui à son tour est utilisé pour fournir `CLSID` les ID de classe des visualiseurs de type à l’IDE de Visual Studio.

## <a name="notes-for-callers"></a>Notes pour les appelants
 L’évaluateur d’expression (EE) appelle [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable

|Méthode|Description|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crée le service du visualiseur|

## <a name="remarks"></a>Remarques
 L' `IEEVisualizerServiceProvider` interface est obtenue pendant l’implémentation de [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Le service du visualiseur créé par cette interface est utilisé pour fournir des fonctionnalités à une interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , que l’EE est chargée d’implémenter. EE est également chargé d’implémenter une interface [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) qui permet aux visualiseurs de type d’afficher et de modifier la valeur d’une propriété.

 Pour plus d’informations sur la façon dont ces interfaces interagissent [, consultez visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="requirements"></a>Configuration requise
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)
