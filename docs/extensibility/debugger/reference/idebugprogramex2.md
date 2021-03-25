---
description: Cette interface permet au gestionnaire de débogage de session (SDM) de s’attacher à un programme et d’obtenir le nœud de programme associé à un programme.
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e39a469d04ac14f3ed36366d035bf4ca01a9d2ef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087325"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Cette interface permet au gestionnaire de débogage de session (SDM) de s’attacher à un programme et d’obtenir le nœud de programme associé à un programme.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface sur le même objet que l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) afin de permettre au fournisseur SDM de s’attacher à un programme tout en autorisant le fournisseur de ports à suivre toutes les sessions attachées au programme. Le fournisseur de port personnalisé peut implémenter cette interface s’il le souhaite.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le SDM appelle [QueryInterface](/cpp/atl/queryinterface) sur une `IDebugProgram2` interface pour obtenir cette interface afin d’effectuer le suivi des sessions attachées aux programmes.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProgramEx2` .

|Méthode|Description|
|------------|-----------------|
|[Attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Joint un programme à une session.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtient le nœud de programme associé à un programme.|

## <a name="remarks"></a>Notes
 Cette interface est privée entre le SDM et le programme.

## <a name="requirements"></a>Spécifications
 En-tête : Portpriv. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
