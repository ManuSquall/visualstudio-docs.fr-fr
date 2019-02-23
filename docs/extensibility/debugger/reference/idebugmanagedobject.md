---
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 295e1829f51ff983e66c11e8f2ae2e5886ee7741
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707967"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface permet à l’évaluateur d’expression (EE) pour appeler des méthodes ou propriétés sur les instances de classe de valeur (par exemple, `System.Decimal`) et pour définir leur valeur sans appeler [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) sur le programme en cours de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un évaluateur d’expression implémente cette interface pour représenter un objet de code managé comme une variable.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Pour obtenir cette interface, appelez [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) sur un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente une instance d’une classe value.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes héritées de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), le `IDebugManagedObject` interface expose les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Retourne une interface qui représente l’objet de code managé et à partir de quels tout code managé approprié interface peut être obtenue.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Définit la valeur de cet objet à la valeur d’un objet de code managé spécifié.|

## <a name="remarks"></a>Notes
 Un évaluateur d’expression utilise cette interface pour stocker un objet de code managé dans une arborescence d’analyse.

## <a name="requirements"></a>Spécifications
 En-tête : ee.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)