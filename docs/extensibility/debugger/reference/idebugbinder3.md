---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97e3165be9d478d08f4de7eb623de5b93fd3433a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330862"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface fournit l’accès aux types, les alias et les services de visualiseur personnalisé.

## <a name="syntax"></a>Syntaxe

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un moteur de débogage implémente cette interface pour prendre en charge les alias, les services de visualiseur personnalisé et accès aux informations de type d’objet.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface obtient cette interface à l’aide de [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Outre les méthodes fournies par le [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface, cette interface implémente les éléments suivants :

|Méthode|Description|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Récupère un objet de mémoire qui représente la mémoire à laquelle cet objet est lié.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Récupère l’exception associée à cet objet (le cas échéant),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Récupère un alias de fonction de son nom,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Récupère un tableau de tous les alias pour cet objet,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Obtient le nombre de types d’arguments associée à cet objet,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Récupère une liste des types d’arguments associée à cet objet,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Obtient une interface pour un service de visualiseur|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Convertit une adresse mémoire de 64 bits ou un emplacement de l’objet à un contexte de la mémoire.|

## <a name="requirements"></a>Configuration requise
 En-tête : ee.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)