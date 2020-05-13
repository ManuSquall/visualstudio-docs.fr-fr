---
title: IDebugProperty2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b04abdac135143ccbbd1b8e5632bf85c974f29d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721228"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Cette interface représente une propriété de cadre de pile, une propriété de document de programme, ou une autre propriété. La propriété est généralement le résultat d’une évaluation d’expression.

> [!NOTE]
> Cette utilisation de la «propriété» ne doit pas être confondue `IDebugProperty2` avec ce qui signifie une variable membre d’une classe, bien qu’un peut représenter une telle entité.

## <a name="syntax"></a>Syntaxe

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour représenter un type particulier de valeur. Par exemple, la valeur pourrait être une valeur numérique à la suite d’une évaluation d’expression, d’un contexte de mémoire utilisé pour afficher la mémoire, ou d’une liste de registres et de leurs valeurs.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir cette interface, ce qui représente le résultat d’une évaluation. `IDebugExpression2::EvaluateAsync`retourne cette interface en envoyant une interface [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) au SDM, qui appelle à son tour [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) pour récupérer la propriété.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) renvoie cette interface pour fournir le document de script associé.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) retourne cette interface pour représenter la valeur de retour d’une fonction.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) renvoie cette interface pour représenter diverses propriétés du programme telles qu’un nom ou un contexte de mémoire.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) renvoie cette interface pour représenter diverses propriétés du cadre de pile telles que les variables locales.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugProperty2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetPropertyInfo (en anglais)](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Remplit une structure [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) qui décrit une propriété.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Définit la valeur d’une propriété à partir d’une chaîne.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Définit la valeur de la propriété à partir de la valeur d’une référence donnée.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Énumère les enfants d’une propriété.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Retourne le parent d’une propriété.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Retourne la propriété qui décrit la propriété la plus dérivée d’une propriété.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Retourne les octets de mémoire qui composent la valeur d’une propriété.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Retourne le contexte de mémoire pour une valeur de propriété.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Retourne la taille, dans les octets, de la valeur de la propriété.|
|[GetReference (en)](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Renvoie une référence à la valeur de cette propriété.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Retourne l’information étendue d’une propriété.|

## <a name="remarks"></a>Notes
 Une propriété, représentée par `IDebugProperty2` une interface, peut être considérée comme une valeur avec un nom, un type et une adresse. En termes plus `IDebugProperty2` généraux, un peut représenter tout ce qui a une structure hiérarchique, avec les parents et les nœuds d’enfant.

 Une propriété est généralement transitoire, ne dure que tant que le cadre de pile actuel, par exemple. D’autre part, une référence, représentée par une interface [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) dure aussi longtemps que la valeur reste dans la mémoire.

 L’IDE peut `IDebugProperty2` utiliser l’interface pour permettre aux utilisateurs de parcourir et de modifier les propriétés au moment de l’exécution.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
