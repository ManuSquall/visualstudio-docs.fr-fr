---
title: IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726316"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface représente un objet que le Binder crée pour encapsuler les valeurs des symboles et des expressions.

## <a name="syntax"></a>Syntaxe

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un évaluateur d’expression implémente cette interface pour représenter un objet.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est la classe de base pour tous les objets utilisés par l’évaluateur d’expression dans les expressions analysées. Elle est retournée par un appel à la méthode de [liaison](../../../extensibility/debugger/reference/idebugbinder-bind.md) . [QueryInterface](/cpp/atl/queryinterface) obtient les interfaces plus spécialisées à partir de cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugObject` .

|Méthode|Description|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Obtient la taille de l’objet.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Obtient la valeur de l’objet sous la forme d’une série d’octets consécutive.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Définit la valeur de l’objet à partir d’une série consécutive d’octets.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Définit la valeur de référence de cet objet.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Obtient le contexte de mémoire qui représente l’adresse de la valeur de l’objet.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crée une copie de l’objet managé dans l’espace d’adressage du moteur de débogage.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Teste si cet objet est une référence null.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Compare un objet à celui-ci.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Détermine si cet objet est en lecture seule.|
|[Proxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Détermine si l’objet est un proxy transparent.|

## <a name="remarks"></a>Notes
 L’évaluateur d’expression utilise cette interface comme classe de base pour représenter des objets dans une arborescence d’analyse.

## <a name="requirements"></a>Configuration requise
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Établis](../../../extensibility/debugger/reference/idebugbinder-bind.md)
