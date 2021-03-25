---
description: Cette interface représente une référence à une propriété de frame de pile ou à une autre propriété.
title: IDebugReference2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6b1c30b2da2862e17a1ebf16cc41008341127c5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075755"
---
# <a name="idebugreference2"></a>IDebugReference2
Cette interface représente une référence à une propriété de frame de pile ou à une autre propriété.

> [!NOTE]
> `IDebugReference2` est réservé pour une utilisation ultérieure, et toutes ses méthodes doivent retourner `E_NOTIMPL` .

## <a name="syntax"></a>Syntaxe

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour représenter une référence à un type de valeur particulier. Par exemple, la valeur peut être une valeur numérique à la suite de l’évaluation d’une expression, d’un contexte de mémoire utilisé pour afficher la mémoire ou d’une liste de registres et de leurs valeurs.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [getReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) pour obtenir cette interface. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) et [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) retournent également cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugReference2` .

|Méthode|Description|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Obtient la structure [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) qui décrit cette référence.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Définit la valeur de cette référence à partir d’une chaîne.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Définit la valeur de cette référence à partir d’une autre référence.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Énumère les enfants de cette référence.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Obtient le parent de cette référence.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Obtient la référence la plus dérivée de cette référence.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Obtient les octets de mémoire auxquels cette référence fait référence.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Obtient un contexte de mémoire pour cette référence.|
|[GetSize,](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Obtient la taille, en octets, de cette référence.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Définit ce type de référence.|
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Compare cette référence à une autre.|

## <a name="remarks"></a>Notes

> [!NOTE]
> Cette utilisation de « Property » ne doit pas être confondue avec une variable membre d’une classe, bien qu’un `IDebugReference2` puisse représenter une telle entité.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) représente une propriété, tandis que `IDebugReference2` représente une référence à une propriété, généralement une référence à un objet dans le programme en cours de débogage.

 La principale différence entre une propriété et une référence est qu’une propriété fait référence à une instance nommée d’un objet, tandis qu’une référence fait référence à une instance sans nom. Par exemple, une propriété peut faire référence à un objet dans le tas du programme par `"a.b"` . Une autre propriété peut faire référence au même objet que `"c.d"` . La façon de faire référence à cette propriété requiert `"a.b"` ou `"c.d"` être dans la portée. Une référence à ce même objet est sans valeur ; l’objet peut être référencé tant que la mémoire de cet objet est valide.

 Une `IDebugProperty2` interface peut être considérée comme une valeur avec un nom, un type et une adresse. Un `IDebugReference2` , en revanche, peut être considéré comme un type et une adresse.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
