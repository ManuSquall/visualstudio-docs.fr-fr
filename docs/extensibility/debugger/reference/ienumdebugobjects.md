---
title: IEnumDebugObjects - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c04409fb695613fea5d54b285946c04719fbe5b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716266"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Cette interface représente une collection d’objets implémentant l’interface [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)

## <a name="syntax"></a>Syntaxe

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression implémente cette interface pour fournir des ensembles d’objets qui implémentent l’interface [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md) Notez qu’il ne s’agit pas d’un recensement COM standard en raison de la présence de la méthode [GetCount.](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
- [GetElements renvoie](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Cette interface implémente les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Récupère le prochain ensemble d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de l’énumération.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Passe un nombre précis d’entrées.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Réinitialise l’énumération à la première entrée.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Récupère une copie de l’énumération actuelle.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Récupère le nombre d’entrées dans le recensement.|

## <a name="remarks"></a>Notes
 Cette interface permet à un moteur de débogé de énumérer sur un ensemble d’objets dans un tableau.

## <a name="requirements"></a>Spécifications
 En-tête: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
