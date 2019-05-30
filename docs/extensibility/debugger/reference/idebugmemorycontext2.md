---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1abe29a915d8ca2aaba1135d2e57946250bc3f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346969"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Cette interface représente une position dans l’espace d’adressage de l’ordinateur exécutant le programme en cours de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface pour représenter une adresse en mémoire.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Un appel à [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) ou [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) retourne cette interface. En outre, les appels à [ajouter](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) et [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) retourner nouvelles copies de cette interface, une fois l’opération arithmétique appropriée a été appliquée.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugMemoryContext2`.

|Méthode|Description|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtient le nom d’utilisateur affichable pour ce contexte.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtient des informations qui décrivent ce contexte.|
|[Ajouter](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Ajoute une valeur spécifiée à l’adresse du contexte actuel pour créer un nouveau contexte.|
|[Soustraire](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Soustrait une valeur spécifiée à partir de l’adresse du contexte actuel pour créer un nouveau contexte.|
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compare deux contextes de la manière indiquées par les indicateurs de comparaison.|

## <a name="remarks"></a>Notes
 De Visual Studio **mémoire** fenêtre appels [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) pour obtenir le `IDebugMemoryContext2` interface qui contient l’expression évaluée est utilisée pour l’adresse de mémoire. Ce contexte est ensuite transmis à [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) et [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) pour spécifier l’adresse pour lire ou écrire.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)