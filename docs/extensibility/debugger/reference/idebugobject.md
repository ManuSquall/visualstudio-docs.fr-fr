---
title: IDebugObject - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726316"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Cette interface représente un objet que le liant crée pour encapsuler les valeurs des symboles et des expressions.

## <a name="syntax"></a>Syntaxe

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un évaluateur d’expression implémente cette interface pour représenter un objet.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est la classe de base pour tous les objets que l’évaluateur d’expression utilise dans les expressions analysées. Il est retourné par un appel à la méthode [Bind.](../../../extensibility/debugger/reference/idebugbinder-bind.md) [QueryInterface](/cpp/atl/queryinterface) obtient les interfaces les plus spécialisées à partir de cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugObject`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Obtient la taille de l’objet.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Obtient la valeur de l’objet comme une série consécutive d’octets.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Définit la valeur de l’objet à partir d’une série consécutive d’octets.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Définit la valeur de référence de cet objet.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Obtient le contexte de mémoire qui représente l’adresse de la valeur de l’objet.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crée une copie de l’objet géré dans l’espace d’adresse du moteur de débogé.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Teste si cet objet est une référence nulle.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Compare un objet à celui-ci.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Détermine si cet objet est lu uniquement.|
|[Proxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Détermine si l’objet est un proxy transparent.|

## <a name="remarks"></a>Notes
 L’évaluateur d’expression utilise cette interface comme classe de base pour représenter des objets dans un arbre d’analyse.

## <a name="requirements"></a>Spécifications
 En-tête: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md)
