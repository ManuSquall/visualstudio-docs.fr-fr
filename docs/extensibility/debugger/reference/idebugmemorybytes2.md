---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56cb234e2295c5c9c08c2a2e9271e1c173524875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727508"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Cette interface représente les octets de mémoire.

## <a name="syntax"></a>Syntaxe

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur DE débogage (DE) implémente cette interface pour représenter des octets en mémoire.

## <a name="notes-for-callers"></a>Notes pour les appelants
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) retourne cette interface pour fournir l’accès à la mémoire système. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) et [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) retournent cette interface pour fournir l’accès aux octets d’un objet.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugMemoryBytes2` .

|Méthode|Description|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Lit une séquence d’octets, en commençant à un emplacement donné.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Écrit `dwCount` des octets, à partir de `pStartContext` .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Obtient la taille, en octets, de la mémoire représentée par cette interface.|

## <a name="remarks"></a>Notes
 Pour les propriétés, une interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) représentant un tableau fournit une `IDebugMemoryBytes2` interface pour accéder aux valeurs de ce tableau.

 L’affichage de la **mémoire** de Visual Studio appelle [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) pour récupérer une `IDebugMemoryBytes2` interface qui permet d’accéder à la mémoire système. L’adresse à accéder est obtenue en analysant l’expression entrée comme une adresse dans la vue mémoire, puis en évaluant l’expression analysée à l’aide de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour obtenir une `IDebugProperty2` interface. Un appel à [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) retourne le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui décrit l’adresse mémoire. Ce contexte de mémoire est ensuite passé à [readatum](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) et [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
