---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99b57aece9b835ac1f2277fdd626a9fdff7b903f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705097"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Cette interface permet à la session de débogage manager (SDM) attacher à un programme et obtenir le nœud de programme associé à un programme.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface sur le même objet que le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface afin de permettre le SDM attacher à un programme, même si en même temps, ce qui permet le fournisseur de port effectuer le suivi de toutes les sessions attaché à la programme. Le fournisseur de port personnalisé peut implémenter cette interface si elle choisit.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Les appels SDM [QueryInterface](/cpp/atl/queryinterface) sur un `IDebugProgram2` interface pour obtenir cette interface pour effectuer le suivi des sessions qui ont associés à des programmes.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProgramEx2`.

|Méthode|Description|
|------------|-----------------|
|[Attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Attache un programme à une session.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtient le nœud de programme associé à un programme.|

## <a name="remarks"></a>Notes
 Cette interface est privée entre le SDM et le programme.

## <a name="requirements"></a>Spécifications
 En-tête : Portpriv.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)