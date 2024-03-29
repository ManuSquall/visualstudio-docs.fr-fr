---
description: Cette interface permet à l’évaluateur d’expression (EE) d’appeler des propriétés ou des méthodes sur des instances de classes de valeur (par exemple, System. Decimal) et de définir leur valeur sans appeler Evaluate sur le programme en cours de débogage.
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88eadb33aaccc09a7c4667ad01d9acee538169f2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076860"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface permet à l’évaluateur d’expression (EE) d’appeler des propriétés ou des méthodes sur des instances de classe value (par exemple, `System.Decimal` ) et de définir leur valeur sans appeler [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) sur le programme en cours de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un évaluateur d’expression implémente cette interface pour représenter un objet de code managé comme une variable.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Pour obtenir cette interface, appelez [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) sur un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente une instance d’une classe value.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes héritées de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), l' `IDebugManagedObject` interface expose les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Retourne une interface qui représente l’objet de code managé et à partir de laquelle toute interface de code managé appropriée peut être obtenue.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Affecte à la valeur de cet objet la valeur d’un objet de code managé spécifié.|

## <a name="remarks"></a>Notes
 Un évaluateur d’expression utilise cette interface pour stocker un objet de code managé dans une arborescence d’analyse.

## <a name="requirements"></a>Spécifications
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Évaluer](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
