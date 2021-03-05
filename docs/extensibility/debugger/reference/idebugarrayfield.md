---
description: Cette interface décrit un symbole ou un type de tableau.
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3926bb47e1ea8a91289a7454f289cd3806e97f7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158720"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Cette interface décrit un symbole ou un type de tableau.

## <a name="syntax"></a>Syntaxe

```
IDebugArrayField : IDebugContainerField
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
