---
title: IDebugReference2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720262"
---
# <a name="idebugreference2"></a>IDebugReference2
Cette interface représente une référence à une propriété de cadre de pile ou à une autre propriété.

> [!NOTE]
> `IDebugReference2`est réservé à une utilisation future, `E_NOTIMPL`et toutes ses méthodes devraient revenir .

## <a name="syntax"></a>Syntaxe

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour représenter une référence à un type particulier de valeur. Par exemple, la valeur pourrait être une valeur numérique à la suite d’une évaluation d’expression, d’un contexte de mémoire utilisé pour afficher la mémoire, ou d’une liste de registres et de leurs valeurs.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) pour obtenir cette interface. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) et [GetDerivedMostReference retournent](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) également cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugReference2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Obtient la [structure DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) qui décrit cette référence.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Définit la valeur de cette référence à partir d’une chaîne.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Définit la valeur de cette référence à partir d’une autre référence.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Énumère les enfants de cette référence.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Obtient le parent de cette référence.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Obtient la référence la plus dérivée de cette référence.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Obtient les octets de mémoire auxquels cette référence se réfère.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Obtient un contexte de mémoire pour cette référence.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Obtient la taille, dans les octets, de cette référence.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Définit ce type de référence.|
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Compare cette référence à une autre.|

## <a name="remarks"></a>Notes

> [!NOTE]
> Cette utilisation de la «propriété» ne doit pas être confondue `IDebugReference2` avec ce qui signifie une variable membre d’une classe, bien qu’un peut représenter une telle entité.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) représente une `IDebugReference2` propriété, tout en se référant à une propriété, généralement une référence à un objet dans le programme en cours de déboisation.

 La principale différence entre une propriété et une référence est qu’une propriété se réfère à une instance désignée d’un objet, tandis qu’une référence se réfère à une instance anonyme. Par exemple, une propriété peut se référer à un `"a.b"`objet dans le tas du programme par . Une autre propriété peut se `"c.d"`référer au même objet que . La façon de se référer `"a.b"` `"c.d"` à cette propriété exige cela ou être dans la portée. Une référence à ce même objet est sans nom; l’objet peut être appelé à tant que la mémoire de cet objet est valide.

 Une `IDebugProperty2` interface peut être considérée comme une valeur avec un nom, un type et une adresse. Un `IDebugReference2`, d’autre part, peut être considéré comme un type et une adresse.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference (en)](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
