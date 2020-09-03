---
title: IDebugArrayField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dab01c1e956ced7e6894b951ab16f4ce68eb778b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736297"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Cette interface décrit un symbole ou un type de tableau.

## <a name="syntax"></a>Syntaxe

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le fournisseur de symboles implémente cette interface sur le même objet qui implémente l’interface [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Cette interface est une spécialisation qui représente des objets de tableau.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de l’interface [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retourne l’indicateur `FIELD_TYPE_ARRAY` .

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes sur les interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , cette interface implémente les éléments suivants :

|Méthode|Description|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Obtient le nombre d’éléments contenus dans le tableau.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Obtient le type d’élément dans le tableau.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Obtient le rang du tableau.|

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
