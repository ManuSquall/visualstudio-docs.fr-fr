---
title: IDebugAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ad298d83efd16112a0cf1be3171601b93342a55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944717"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Représente un alias numérique pour une variable. Un alias est simplement un nom différent pour une variable.

## <a name="syntax"></a>Syntaxe

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression (EE) implémente cette interface pour prendre en charge des alias numériques pour les variables.

## <a name="notes-for-callers"></a>Notes pour les appelants
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) crée un alias pour un objet particulier. Pour rechercher des alias, utilisez [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) ou [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Les méthodes suivantes sont définies dans l' `IDebugAlias` interface.

|Méthode|Description|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Obtient l’objet auquel cet alias fait référence.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Obtient le nom de l’alias.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Récupère une `ICorDebugValue` interface qui fournit l’accès aux informations de code managé sur cet objet (code managé uniquement).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Marque cet alias comme n’étant plus utilisé.|

## <a name="remarks"></a>Notes
 Un alias est un nombre décimal sous forme de chaîne suivi du caractère #, par exemple 1001 #.

## <a name="requirements"></a>Configuration requise
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
