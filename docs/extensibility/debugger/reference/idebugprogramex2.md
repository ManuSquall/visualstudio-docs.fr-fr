---
title: IDebugProgramEx2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722334"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Cette interface permet au gestionnaire de déboiffés de session (SDM) de s’attacher à un programme et d’obtenir le nœud de programme associé à un programme.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface sur le même objet que l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) afin de laisser le SDM s’attacher à un programme tout en permettant au fournisseur de port de suivre toutes les sessions attachées au programme. Le fournisseur de ports personnalisé peut implémenter cette interface s’il le souhaite.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le SDM appelle [QuestionryInterface](/cpp/atl/queryinterface) sur une `IDebugProgram2` interface pour obtenir cette interface pour suivre les sessions qui se sont jointes aux programmes.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugProgramEx2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Attache un programme à une session.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtient le nœud de programme associé à un programme.|

## <a name="remarks"></a>Notes
 Cette interface est privée entre le SDM et le programme.

## <a name="requirements"></a>Spécifications
 En-tête: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
