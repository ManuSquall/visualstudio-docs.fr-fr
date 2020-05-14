---
title: IDebugMemoryBytes2 - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727508"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Cette interface représente des octets de mémoire.

## <a name="syntax"></a>Syntaxe

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour représenter les octets en mémoire.

## <a name="notes-for-callers"></a>Notes pour les appelants
- [GetMemoryBytes renvoie](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) cette interface pour donner accès à la mémoire du système. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) et [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) retournent cette interface pour donner accès aux octets d’un objet.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugMemoryBytes2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Lit une séquence d’octets, à partir d’un endroit donné.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Écrit `dwCount` octets, `pStartContext`à partir de .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Obtient la taille, dans les octets, de la mémoire représentée par cette interface.|

## <a name="remarks"></a>Notes
 Pour les propriétés, une interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) représentant un tableau fournit une `IDebugMemoryBytes2` interface pour accéder aux valeurs de ce tableau.

 Visual Studio’s **Memory View** appelle [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) pour récupérer une `IDebugMemoryBytes2` interface pour accéder à la mémoire du système. L’adresse à accéder est obtenue en analyseant l’expression saisie comme une adresse dans la vue de mémoire, `IDebugProperty2` puis en évaluant l’expression analysée à l’aide [d’EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour obtenir une interface. Un appel à [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) renvoie [l’IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui décrit l’adresse mémoire. Ce contexte de mémoire est ensuite transmis à [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) et [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
