---
description: Cette interface fournit des informations supplémentaires sur un objet.
title: IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c5e3b3f05ae205e30cff7085b71c1690d02c73e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084686"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface fournit des informations supplémentaires sur un objet.

## <a name="syntax"></a>Syntaxe

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression implémente cette interface pour offrir la prise en charge des alias et de l’accès aux informations sur l’objet.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Une interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) peut obtenir cette interface à l’aide de [QueryInterface](/cpp/atl/queryinterface). En outre, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) retourne cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable
 Outre les méthodes sur l’interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , l' `IDebugObject2` interface implémente les éléments suivants :

|Méthode|Description|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtient le champ ou la variable (le cas échéant) qui peut sauvegarder la propriété représentée par cet objet.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtient l’objet de code managé représentant la valeur de cet objet.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Crée un ID unique pour cet objet ou retourne un alias existant.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Obtient l’alias associé à cet objet, le cas échéant.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtient le type de cet objet.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Détermine si cet objet représente des données utilisateur.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Détermine si l’État Modifier & Continuer n’est plus valide.<br /><br /> Un évaluateur d’expression personnalisé n’implémente pas cette méthode (il doit toujours retourner `E_NOTIMPL` ).|

## <a name="remarks"></a>Notes
 Pour plus d’informations sur les alias, consultez [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="requirements"></a>Spécifications
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
