---
description: Cette interface représente une propriété de frame de pile, une propriété de document de programme ou une autre propriété.
title: IDebugProperty2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5d20f0bd3727860f32e111baad2d2513590e880
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064798"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Cette interface représente une propriété de frame de pile, une propriété de document de programme ou une autre propriété. La propriété est généralement le résultat d’une évaluation d’expression.

> [!NOTE]
> Cette utilisation de « Property » ne doit pas être confondue avec une variable membre d’une classe, bien qu’un `IDebugProperty2` puisse représenter une telle entité.

## <a name="syntax"></a>Syntaxe

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour représenter un genre particulier de valeur. Par exemple, la valeur peut être une valeur numérique à la suite de l’évaluation d’une expression, d’un contexte de mémoire utilisé pour afficher la mémoire ou d’une liste de registres et de leurs valeurs.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir cette interface, qui représente le résultat d’une évaluation. `IDebugExpression2::EvaluateAsync` retourne cette interface en envoyant une interface [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) au SDM, qui à son tour appelle [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) pour récupérer la propriété.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) retourne cette interface pour fournir le document de script associé.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) retourne cette interface pour représenter la valeur de retour d’une fonction.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) retourne cette interface pour représenter diverses propriétés du programme, telles qu’un nom ou un contexte de mémoire.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) retourne cette interface pour représenter diverses propriétés du frame de pile, telles que les variables locales.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProperty2` .

|Méthode|Description|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Remplit une structure [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) qui décrit une propriété.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Définit la valeur d’une propriété à partir d’une chaîne.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Définit la valeur de la propriété à partir de la valeur d’une référence donnée.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Énumère les enfants d’une propriété.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Retourne le parent d’une propriété.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Retourne la propriété qui décrit la propriété la plus dérivée d’une propriété.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Retourne les octets de mémoire qui composent la valeur d’une propriété.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Retourne le contexte de la mémoire pour une valeur de propriété.|
|[GetSize,](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Retourne la taille, en octets, de la valeur de la propriété.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Retourne une référence à la valeur de cette propriété.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Retourne les informations étendues d’une propriété.|

## <a name="remarks"></a>Notes
 Une propriété, telle qu’elle est représentée par une `IDebugProperty2` interface, peut être considérée comme une valeur avec un nom, un type et une adresse. En termes plus généraux, un `IDebugProperty2` peut représenter tout ce qui a une structure hiérarchique, avec des nœuds parents et enfants.

 Une propriété est généralement transitoire, ce qui n’est pas le cas du frame de pile actuel, par exemple. En revanche, une référence, telle qu’elle est représentée par une interface [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , est valable tant que la valeur reste en mémoire.

 L’IDE peut utiliser l' `IDebugProperty2` interface pour permettre aux utilisateurs de parcourir et de modifier les propriétés au moment de l’exécution.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
